---
description: ALMでのAPIの変更
jcr-language: en_us
title: 4月リリースのAPIの変更
source-git-commit: 3b35c16d74c83329cee24ee9ad007a53ccbd8cf3
workflow-type: tm+mt
source-wordcount: '4093'
ht-degree: 0%

---


# 2026年4月リリースのAPIの変更

Adobe Learning Managerの2026年4月リリースでは、代替と同等の機能、コンテンツへの時間枠によるアクセス、コンテンツ駆動型クイズの試行、ログインなしのエクスペリエンス、作業計画書の処理に関するパブリックAPIの重点的な機能強化が導入されています。 この変更は、下位互換性が高く、より正確な統合が可能になるように設計されています。

## 学習パスの適応型学習

このリリースでは、アダプティブ学習パスの完全なパブリックAPIサポートが追加されています。 学習パス(LP)では、どのセクションおよびサブ学習オブジェクト（サブLO）を、様々な学習者グループに対して表示するかを制御する、適応型ルールを定義できるようになりました。また、パブリックAPIはこの動作を反映します。

影響を受けるエンドポイントは次のとおりです。

- GET /primeapi/v2/learningObjects?filter.loTypes=learningPath
- GET /primeapi/v2/learningObjects/{loId}

新しいブール属性attributes.isAdaptiveは、学習プログラムがアダプティブルールを使用することを示します。 このフラグがtrueの場合、sections属性が適応的に解釈されます。

学習者呼び出しの場合は、現在の学習者に表示されているセクションのみが返されます。 各セクションには、セクションIDとともに、その学習者の適応設定に基づいて計算される学習目標ID(loId)、必須フラグおよびmandatoryLOCountのリストが含まれます。 relationships.subLOsリレーションもフィルタリングされるようになり、その学習者に表示されるサブ学習オブジェクトのみが含まれるようになりました。

管理者呼び出しの場合、セクションはadaptiveConfig配列をさらに公開できます。 userGroupId、userGroupName、およびそのグループにセクションが必須であるかどうかなど、ユーザーグループごとの適応規則を説明します。 管理者向けのツールでは、これを使用してアダプティブルールを視覚化および管理できます。

学習プログラムの完了のリセット

このリリースでは、適応型学習プログラムなどの学習目標に対して、__更新（リセット）完了__&#x200B;のAPIが導入されています。 これにより、再トレーニング、定期的なコンプライアンス更新、プログラムの再起動などのシナリオがサポートされます。

新しいエンドポイントを使用できます。

```
POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion
```

この操作には適切な書き込み権限が必要で、指定されたユーザーコンテキスト内の指定された学習オブジェクトインスタンスの完了状態がリセットされます。 これは、管理者側の自動化または慎重に範囲を設定した学習者ツールでの使用を目的としています。

この機能の一括バージョンは、ジョブAPIを介して計画されます。 「リクエスト」シェイプは、電子メール、ユーザーID、またはユーザーグループIDでユーザーをターゲットにするように設計されています。例：

```
{  
  "emails": ["[user1@example.com](mailto:user1@example.com)", "[user2@example.com](mailto:user2@example.com)"],  
  "userIds": ["12345", "67890"],  
  "userGroupIds": ["ug1", "ug2"]  
}  
```

統合では、各プログラムまたはコースで学習者を再起動する必要がある場合、このAPIを使用する必要があります。 クライアントはエラー応答を適切に処理する必要があります。リセットを適用できない場合（完了が存在しない、サポートされていない学習オブジェクトタイプの場合など）、APIは更新要求を拒否することがあります。

## 対応する補完と代替補完

複数の学習オブジェクトが同じ要件を満たすことができる実装をサポートするために、このリリースでは同等の機能と代替機能の完了がパブリックAPIとして導入されています。

これで、学習目標エンドポイントに次の情報が含まれるようになります。

```
- GET /primeapi/v2/learningObjects
- GET /primeapi/v2/learningObjects/{loId}
```

新しいブール属性attributes.isAlternateCompleteは、特定の学習オブジェクトに対する学習者の完了が、オブジェクト自体ではなく代替または同等の学習オブジェクトのどちらに基づくかを示します。 これがtrueの場合、 relationships.alternateCompletions関係に、代替文字として機能した学習目標がリストされます。 これにより、ダウンストリーム・レポートおよびダッシュボードで、直接完了と代替完了を区別し、要件を満たした代替完了を表示できます。

さらに、関連学習目標ビューでは、学習目標を満たす可能性のある代替案を検出できます。 この情報は、次の方法で公開されます。

```
GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}
```

この応答は、代替文字として機能できる学習オブジェクトを返します。また、現在の制限とは無関係に、そのような代替文字の総数を示すmeta.countフィールドが含まれています。 統合はこれを使用して、推奨される同等の機能を提供したり、代替マッピングの管理ビューを作成したりできます。

## レポートと分析のユースケース

レポートまたは分析を生成するユーザーは、ロジックを更新して、isAlternateCompleteとalternateCompletionsをレポートワークフローに追加する必要があります。

完了データ（LTエクスポート、カスタムデータウェアハウスフィード、BIダッシュボードなど）を消費するレポート統合では、LO APIからattributes.isAlternateCompleteとrelationships.alternateCompletionsの両方を読み取って保持するようにロジックが拡張される必要があります。

- isAlternateCompleteがfalse==場合：\
  レコードをLOの&#x200B;__直接完了__&#x200B;として現在のように扱います。
- isAlternateCompleteがtrue==場合：
   - レコードに&#x200B;__代替の完了__&#x200B;としてレポートにフラグを付けます（たとえば、値がDIRECTとALTERNATEの列の「完了方法」列）。
   - relationships.alternateCompletions.data[*].idを使用して、この完了を付与された&#x200B;__どのソースLO__&#x200B;を取得します（例：「代替コースAを介してコースBが完了しました」）。

一般的な使用例：

- _準拠レポート_ – 準拠コースが承認済みの同等のコースを介して完了したことを示し、要件を満たしたソースコースを一覧表示します。
- _Program progress dashboards_ – distinguish learners who completed a path _directly_ vs those who satisfied it via alternates, for more accurate progress and remediation views.
- _Audit trails_ – for any LO marked isAlternateComplete=true, auditors can see exactly which alternate training(s) were used to grant that completion.

Without incorporating these two fields, downstream reports will treat alternate completions as regular completions and will _not be able to explain_ *why* a learner shows as completed a training they never took directly.

## Learner vs Admin LO API behavior

The multi language job aid structure is identical in both learner and admin LO APIs. Learner scope returns only those job aids visible to the learner, but for each visible job aid it exposes all configured locales via multiple resource entities (one per locale) and multi locale localizedMetadata. Admin scope returns all job aids the admin can manage, with the same LO model and locale specific resource IDs. Clients with learner scope should choose the resource whose attributes.locale best matches the learner&#39;s content language, while admin tools can enumerate all locales for reporting and management.

## Checklist with commenting capability

To support workflows where reviewers can share structured feedback on checklist‑based activities, this release surfaces *checklist comments* and reviewer visibility controls through the learning object resource API.

Checklist‑related metadata is exposed on learningObjectResource entities (JApiLOResource, &quot;type&quot;: &quot;learningObjectResource&quot;) that represent checklist resources within a course or other learning object.

The information is available via:

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

When the learning object instance contains checklist‑type resources, the corresponding learningObjectResource entries in the included array expose comment and reviewer‑visibility attributes under attributes, and reviewer identity under relationships.

### New checklist comment attributes

For checklist resources, the following attributes may be present on the learningObjectResource:

- attributes.checklistComment\
  A free‑text comment left by the reviewer for the learner, for example:\
  &quot;checklistComment&quot;: &quot;Excellent performance! All safety protocols followed correctly.&quot;\
  This attribute is populated _only if_:
   - showChecklistComment is true, and
   - the checklist configuration has enable_reviewer_remarks enabled.
- attributes.showChecklistComment\
  A Boolean flag indicating whether reviewer remarks should be shown to the learner:\
  &quot;showChecklistComment&quot;: true\
  この属性は、チェックリスト構成で&#x200B;_enable_ reviewer_remarksが有効になっている場合にのみ_存在します。\
  クライアントは、このフラグを使用して、学習者エクスペリエンスでchecklistCommentをレンダリングするかどうかを決定する必要があります。
- attributes.showReviewerNameToLearner\
  学習者がレビュー担当者のIDを表示するかどうかを制御するブール値フラグ。\
  &quot;showReviewerNameToLearner&quot;: true\
  trueの場合、クライアントはchecklistReviewedBy関係（以下を参照）を使用して、レビューアーの名前を解決および表示できます（例：ユーザールックアップAPIを介して）。

checklistEvaluationStatus、isChecklistMandatory、resourceSubType:「CHECKLIST」、submissionDateなどのその他のチェックリスト固有のコンテキストも同じlearningObjectResourceで使用でき、豊富なチェックリストUIとレポートをサポートします。

### レビュー担当者のID関係

レビュー担当者の名前を表示する場合、learningObjectResourceには、レビュー担当者のユーザーを指す関係が含まれます。

```
"relationships": {
  "checklistReviewedBy": {
    "data": {
      "id": "user_id",
      "type": "user"
    }
  }
}
```

このリレーションシップは、_の場合にのみ_&#x200B;入力されます：

- showReviewerNameToLearnerがtrueで、
- checklistReviewedByがnullでない（つまり、チェックリストがレビューされている）。

クライアントアプリケーションは次の条件を満たす必要があります。

1. attributes.showReviewerNameToLearnerを確認します。
2. trueでrelationships.checklistReviewedBy.dataが存在する場合は、適切なユーザーAPIを呼び出して、「id」:「user_id」を表示名に解決します。
3. 必要に応じて、チェックリストコメントまたはステータスの横にレビューアー名を表示します。

### チェックリストのリソースとコメントへのアクセス

特定の学習目標に関するチェックリストリソースとそのコメントを取得するには、クライアントは次のことを行う必要があります。

- 通話

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

- 応答で次の操作を行います。
   - メインのlearningObjectのrelationships.instancesを使用して、含まれている関連するlearningObjectInstanceエントリを検索します。
   - 各learningObjectInstanceからrelationships.loResourcesに従って、learningObjectResourceエントリを見つけます。
   - 次の条件を満たすlearningObjectResourceエントリをフィルター：
      - attributes.resourceSubType == &quot;CHECKLIST&quot;（チェックリソース用）
      - オプションでattributes.showChecklistComment==trueに設定すると、学習者が表示できるコメントを含むチェックリストが検索されます。

- 各チェックリストlearningObjectResourceについて、次を利用します。
   - attributes.checklistComment （存在し、showChecklistCommentがtrueの場合）
   - attributes.checklistEvaluationStatus（「PASSED」など）
   - attributes.showReviewerNameToLearner
   - relationships.checklistReviewedBy （存在する場合）を使用して、レビュー担当者を識別します。

このパターンにより、ヘッドレスまたはカスタムクライアントは、ステータス、必須/オプションフラグ、レビュー担当者のフィードバックなどの包括的なチェックリストエクスペリエンスをPrime APIから直接レンダリングできます。

### レポート作成とUXに関する考慮事項

- _レポートと分析_
チェックリストで学習者のパフォーマンスを追跡する統合には、次のものを組み込むことができます。
   - 合格/不合格またはその他のステータスインジケーターのchecklistEvaluationStatus。
   - 必須と任意のチェックリストのアクティビティを区別するためのisChecklistMandatory。
   - フィードバック範囲の監査に関するchecklistCommentおよびshowChecklistCommentの有無。
- _学習者のエクスペリエンス_
UIの実装は以下の条件を満たす必要があります。
   - コメントを表示する前に、showChecklistCommentを尊重します。
   - showReviewerNameToLearnerおよびchecklistReviewedByを使用して、レビュー担当者の名前を表示するか、レビューを匿名のままにするかを決定します。
   - コメントが無効になっている場合、またはコメントが存在しない場合に、評価ステータスと提出情報を引き続き表示して、スムーズに折り返します。

## 作業計画書の多言語サポート

作業計画書を複数の言語で学習者と管理者の両方に配布する必要がある実装をサポートするために、このリリースでは作業計画書の処理が拡張され、*ロケールごとに1つのリソース*&#x200B;を返します。ハードコードされたen-USリソースは1つではありません。

多言語の作業計画書では、既存の階層が引き続き使用されます。

_学習目標_ (lo) → _learningObjectResource_ (loResource) → _リソース_

API契約に変更を加える必要はありません。 ローカライズされた作業計画書は、ロケールごとに個別のリソースエンティティを持ち、ローカライズされたメタデータをlearningObject/learningObjectResourceレベルで共有することで、自然にこの構造に適合します。

作業計画書のデータは、次の方法で公開されます。

```
GET /primeapi/v2/learningObjects/jobAid:{jobAidId}?include=instances.loResources.resources
```

作業計画書に複数の言語のバリアントが含まれている場合、含まれる配列には複数の「タイプ」、「リソース」エントリが含まれます。これは、ロケールごとに1つ（en-US、fr-FR、es-ESなど）のエントリで、すべて単一のlearningObjectResourceからリンクされています。

### 多言語の作業計画書の構造

多言語の作業計画書の使用：

- _learningObject （型： learningObject）_
   - 複数のエントリ（en-US、fr-FRなど）を持つlocalizedMetadataが含まれているため、クライアントは作業計画書のタイトル/説明を適切な言語で表示できます。
- _learningObjectInstance （型： learningObjectInstance）_
   - relationships.loResourcesを介して1つ以上のlearningObjectResourceエントリを参照します。
- _learningObjectResource （型： learningObjectResource）_
   - 共通の構成（コンテンツ・タイプ、バージョンなど）を保持 および複数ロケールlocalizedMetadata.
   - relationships.resourcesを介して1つ以上のリソースエンティティにリンクします。
- _リソース（種類：リソース）_
   - *ロケールごとに1つ*。それぞれに独自のID、ロケール、名前、およびURL （場所/downloadUrl）があります。

多言語の作業計画書の場合、一般的なパターンは次のとおりです。

- en-USおよびfr-FRのlocalizedMetadataを含むlearningObjectResource
- relationships.resources.dataの参照先：
   - ロケールを含むリソース：「en-US」
   - ロケールを含むリソース：&quot;fr-FR&quot;

学習者のロケールをresource.attributes.localeフィールドと一致させることで、クライアントは適切なリソースを選択できます。

### 作業計画書の新しいリソースID形式

作業計画書リソースの複数のローカライズされたバリエーションを正しく区別するために、_リソースIDの形式が変更されました_。

_古い（レガシ）リソースID形式_

以前は、作業計画書のリソースで、次のような不透明なID形式が使用されていました。

作業計画書:131032_-1_-1_2_resource

この形式ではロケールはエンコードされず、APIは実質的に1つのリソース（通常はen-US）のみを公開します。

_新しいリソースID形式（多言語対応）_

新しい形式は次のとおりです。

```
jobAid:<jobAidId>_<version>_<localeCode>
```

例：

- 作業計画書:131032_2_en-US
- 作業計画書:131032_2_fr_FR
- 作業計画書:131032_2_es_ES

視覚的な内訳：

```
jobAid:131032_2_fr_FR

        │      │ │ │

        │      │ │ └──► Locale Code (fr_FR, en_US, es_ES, etc.)

        │      │ └────► Version (2)

        │      └──────► JobAid ID (131032)

        └─────────────► Resource Type Prefix ("jobAid:")
```

この構造体を使用すると、クライアントは次の操作を実行できます。

- リソースが属する作業計画書とバージョンをすばやく識別します。
- 必要に応じて、リソースIDから直接ロケールを推測します。

### 下位互換性： 

```/resources/{resourceId}```

従来のリソースエンドポイントは引き続き使用できます。

```GET /primeapi/v2/resources/{resourceId}

```

古いID形式と新しいID形式の両方で&#x200B;_下位互換性_&#x200B;があります。

- _古いID形式_ （例： jobAid:131032_-1_-1_2_resource）
   - 作業を続行します。
   - そのレガシID （通常は元のen-USリソース）に関連付けられた&#x200B;_最初に作成されたリソース_&#x200B;を返します。
- _新しいID形式_ （例： jobAid:131032_2_fr_FR）
   - そのIDに対応する&#x200B;_ロケール固有の正確なリソース_&#x200B;を返します。
   - これにより、ローカライズされた作業計画書のバリエーションを正確に取得および操作できます。

現在、古いリソースIDを保存または参照している統合は、変更なく機能し続けることができます。一方、新しい実装では、ロケール固有の操作に新しいID形式を採用することをお勧めします。

### 統合とUXに関する考慮事項

- _学習者/管理者UI_
   - 適切な言語でタイトルと説明を表示するには、learningObject.localizedMetadataおよびlearningObjectResource.localizedMetadataを使用します。
   - resource.attributes.localeを使用して、学習者のロケールに適したURL（場所/ downloadUrl）を選択します。
   - 学習者の正確なロケールが使用できない場合は、フォールバック動作（例：en-USにフォールバック）を実装します。
- _APIとストレージ_
   - 新しい統合の場合は、_新しい形式のリソースID_ (```jobAid:<jobAidId>_<version>_<localeCode>```)を保存して、ロケール固有の取得を明確にします。
   - 従来のIDは/resources/{resourceId}で引き続き使用できますが、ロケールは区別されません。

## 開始モジュールのタイムスロット制約

一部の学習体験は、定義された時間枠内でのみ利用できる必要があります。 このリリースでは、学習目標リソースのタイムスロット情報が表示され、学習者が現在の時間でリソースを開始できるかどうかをチェックする検証エンドポイントが導入されています。

タイムスロットメタデータは、エンドポイントを介して使用できます。

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

学習オブジェクトリソースレベルでは、timeSlotオブジェクトが属性に存在し、startTimeとendTimeの値がUTCになります。 リソースを起動する期間を指定します。

モジュールを起動する前に、統合は新しい検証エンドポイントを呼び出すことができます。

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

このエンドポイントは、学習者が読み取るシナリオ向けであり、設定された時間帯、配信タイプ、およびその他のバックエンドルールを考慮して、学習者が現在リソースを開始できるかどうかを返します。

カスタムプレーヤーとクライアントアプリケーションは、canStartを使用して時間ベースのアクセスを強制し、timeSlotメタデータを使用して、コンテンツが利用可能になった時期や期限切れになった時期に関する明確なメッセージを表示する必要があります。 canStartからの否定的な回答は、コンテンツをまだ開始できなくなった理由や終了した理由を学習者に知らせるために、明示的に処理する必要があります。

## 複数試行のコンテンツドリブンのクイズ

一部のコンテンツパッケージは、Adobe Learning Managerだけに依存するのではなく、独自の試行追跡を実装しています。 このリリースでは、試行がコンテンツ自体によって行われたことを示すフラグが導入されています。

スルー：

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

学習オブジェクトリソースは、ブール属性hasContentDrivenAttemptTrackingを公開できるようになりました。 この場合、クイズまたはモジュールは（SCORMやxAPIロジックなどを介して）試行を内部的に管理します。プラットフォームの標準試行カウンターは、学習者のエクスペリエンスを完全には反映していない場合があります。

試行回数を表示する統合、または再試行動作を制御する統合では、このフラグをチェックする必要があります。 有効な場合は、プラットフォームのメタデータのみから試行制限を推測するのではなく、コンテンツ側のレポート（例えば、xAPIステートメントを介して）またはビジネス固有のルールに依存できるようにする必要があります。

## 作業計画書リソースID形式の行動変更

このリリースでは、作業計画書のリソースIDの形式に重要な&#x200B;__動作の変更__&#x200B;が導入されています。 新しいエンドポイントは必要ありませんが、これは、これらのIDを保存または解析するシステムに直接影響を与えます。

以前は、作業計画書のリソースIDは次のような形式を使用していました。

```jobAid:<jobAidId>_-1_-1_2_resource```

2026年4月のリリースでは、これは簡略化されたより明確な形式に置き換えられました。

```jobAid:<jobAidId>_<version>_<localeCode>```

以下に例を示します。

作業計画書:131032_2_fr_FR

コンポーネントは次のとおりです。

- ```<jobAidId>```：数値の作業計画書ID （131032など）、
- ```<version>```：作業計画書のバージョン番号（例： 2）、
- ```<localeCode>```:ロケールコード（例： en_US、fr_FR、es_ES）。

リソースをインデックス化する、または作業計画書のリソースIDに保持する統合は、解析ロジックとストレージロジックを更新して、新しい形式を認識する必要があります。 ID自体が変更されるため、2026年4月のリリースにアップグレードした後で、作業計画書のリソースIDによってキー設定されたローカルインデックスを再構築することを強くお勧めします。

## 移行によるコースバナー画像の設定

標準の移行ワークフローの一環として、Adobe Learning Managerでコースバナー画像を設定または更新できるようになりました。 これにより、大きなカタログを起動したりクリーンアップしたりする際に、コースページの表示を手動で編集することなく、一貫した状態を保つことができます

### バナー画像の定義場所

バナー画像は&#x200B;_course.csv_&#x200B;移行ファイルで設定されます。このファイルは、次のようなコースメタデータを提供するために既に使用しています。

- id
- courseName
- courseCreationDate
- state（状態）
- author
- thumbnailUrl

この機能強化により、course.csv仕様にコースバナー画像の&#x200B;_オプション列_&#x200B;が追加されました。 正確なヘッダー名は、Learning ManagerアカウントからダウンロードしたCSV仕様で定義されます（例えば、bannerUrlやbannerImageUrlと表示される場合があります）。

バナー列：

- _コースバナー_&#x200B;として使用する画像ファイルを指します。
- thumbnailUrlと同様に、設定されたコンテンツリポジトリ(Box/FTP)で使用可能な画像を使用して機能します。

### 移行のためのバナー画像の準備

1. バナー画像のアップロード：既存のディレクトリ構造に従って、他の移行アセットで使用しているのと同じBoxまたはFTPの場所にバナー画像ファイルを配置します。
2. ファイル形式の確認：
必要システム構成の説明に従って、サポートされている画像形式（png、jpg、jpeg、gifなど）のいずれかを使用します。
   1. [*必要システム構成*](/help/migrated/system-requirements.md)
3. course.csvの更新：新しいバナー列で、バナー画像の相対パスまたは識別子を参照します。 概念の例：

```
id,courseName,courseCreationDate,state,author,thumbnailUrl,bannerUrl  
12345,DEMO1,2018-05-05T08:56:21.000Z,Published,Sudheer,pic1.png,banners/banner1.png  
45678,DEMO2,2018-05-05T08:56:21.000Z,Published,Sudheer,pic2.png,banners/banner2.png  
```

### 移行実行中のバナーの適用

course.csvが更新されると、フローは他の移行と同じになります。

1. _CSVのアップロード_
移行用に設定されたBox/FTPフォルダーに、更新されたcourse.csv（およびその他の関連ファイル）をアップロードします。 ファイル名は、csv_specifications.zipで指定された名前と正確に一致する必要があります（大文字と小文字が区別されます）。
2. _スプリントの実行を開始する_
Adobe Learning Managerで、統合管理者として、course.csvを含む移行_スプリントの実行_&#x200B;を開始します。\
   移行エンジンがバナー列を読み取り、バナー画像を各コースに適用します。
3. _結果とエラーログの確認_
スプリントの実行後：
   1. _作成者_&#x200B;および&#x200B;_学習者_&#x200B;アプリのバナーを確認します。
   2. ファイルパスが無効だったり、形式がサポートされていないなど、一部の行でエラーが発生した場合は、移行実行からエラーCSVをダウンロードし、データを修正します。

### 新規コースと既存コースの比較

バナーフィールドは、次の両方のシナリオで機能します。

- _移行によって作成された新しいコース_
course.csvからコースが初めて作成され、バナー列にデータが入力されると、そのバナーがすぐに設定されます。
- _既存のコース（後付/修正）_
同じコースIDと新しいバナー値で移行を再実行する場合：
   - Learning Managerは既存のコースを検索します。
   - バナー画像は、CSVで指定された新しい画像に&#x200B;_更新_&#x200B;されます。

実際の列名とパスは、_ダウンロードされたCSV仕様_&#x200B;とコンテンツリポジトリレイアウトと一致している必要があります。

## LearningProgramCourseの「順序」列を削除

Adobe Learning Managerでは、移行中の&#x200B;_学習パス（学習プログラム）内のコース順序_&#x200B;の簡略化されたモデルがサポートされるようになりました。 この変更の一部として、learning _program_ course.csv移行ファイルから_order列が削除されます_。

以前は、learning_program_course.csvファイルに、次の目的で使用する列（通常、orderまたは同様の列）が含まれていました。

- 学習プログラム内の各コースの&#x200B;_位置_&#x200B;を、その列の数値に基づいて明示的に設定します。
- 管理者やスクリプトは、この番号順序を手動で維持する必要があります。特に、コースの挿入や並べ替えを行う場合に必要です。

Adobe Learning Managerでは、learning_program_course.csvの「順序」列を使用して、コースの順序が決定されなくなりました。 移行CSVでは、数値順ではなく、_どのコースがどの学習プログラムに属しているかに_&#x200B;焦点が当てられます。

## 移行CSVへの影響

### learning_program_course.csv

従来の注文列は削除または無視されたものとして扱う必要があります。

- 移行中に学習プログラムのコースの順序を制御する必要はありません。
- 古いテンプレートの注文列が引き続き表示される場合：
   - Learning Managerでは、順序の設定は無視されます。
   - CSVからファイルを安全に削除し、時間の経過とともに移行ファイルを簡素化できます。
- 必要な主なマッピングは以下のとおりです。
   - 学習プログラムID ↔コースID （およびid、learningProgramId、courseId、日付など、その他の文書化された列）。

現在のヘッダーセットと要件を確認するには、常にLearning Managerアカウントから（csv _specifications.zipを介して）最新の[_ CSV仕様_](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/migration-manual)を参照します。

## コースインスタンスのtimeZoneCode

このリリース以降、コースインスタンスモデル(learningObjectInstance)には次のような新しい属性が公開されます。

timeZoneCode – アカウントで設定されているタイムゾーンに、コースインスタンスを明示的にリンクする文字列フィールド。

これにより、クライアントは次のことが可能になります。

- 一貫性のあるAPI方式で、コースインスタンスのタイムゾーンを解決します。
- ユーザー自身のタイムゾーンに関係なく、そのインスタンスのすべてのインスタンスレベルの日付/時刻を正しく解釈して表示します。

### timeZoneCodeの表示場所

フィールドはlearningObjectInstanceモデルの属性に追加されます
コースインスタンスのみ。

例：

```
{
  "id": "course:1262748_1359228",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2019-08-06T13:50:39.000Z",
    "isAET": false,
    "isDefault": true,
    "timeZoneCode": "356",
    "isFlexible": false,
    "state": "Active",
    "localizedMetadata": [
      {
        "locale": "en-US",
        "name": "Default instance"
      }
    ]
  }
}
```

### timeZoneCodeの解決方法

数値timeZoneCodeは、アカウントAPIを介して公開されるアカウントのタイムゾーンカタログへの参照キーです。

```http
GET /primeapi/v2/account
Authorization: Bearer <access_token>
```

応答の中で、タイムゾーンは次の場所にリストされます。

```
"data": {
  "attributes": {
    "timeZones": [
      {
        "name": "Etc/GMT+12",
        "timeZoneCode": "356",
        "utcOffset": -720,
        "utcOffsetCode": "UTC-12:00(Etc/GMT+12)",
        "zoneId": "Etc/GMT+12"
      },
      "..."
    ]
  }
}
```

### 推奨されるクライアントフロー：

1. GET /accountを1回呼び出し、テナントのattributes.timeZonesをキャッシュします。
2. コースインスタンスごとに、次の操作を行います。
   - attributes.timeZoneCodeを読み取ります。
   - timeZoneCodeが一致するtimeZones内の対応するエントリを検索します。
   - そのエントリのzoneId、utcOffset、およびutcOffsetCodeを表示およびスケジューリングロジックに使用します。

## ユーザーグループのメンバーシップ用の非同期パブリックAPI

### 概要

Adobe Learning Managerは、ユーザーグループ(UG)メンバーシップを管理するための2つの&#x200B;_admin async API_&#x200B;を公開しています。

- POST/async/userGroups/{userGroupId}/users – ユーザーを非同期でUGに追加します
- DELETE/async/userGroups/{userGroupId}/users - UGからユーザーを非同期に削除します

これらのAPIは、同じ要求でメンバーシップを更新するのではなく、バッチを受け入れ、_イベントID_&#x200B;を返します。 実際の結果は、後でWebhookを介して配信されます。

次の場合に使用します。

- 大規模なグループまたは頻繁な一括更新を管理している。
- レイテンシは、信頼性とスループットよりも重要ではありません。
- UIをクリックするのではなく、統合(HR、CRM、LXP)を構築します。

小規模で対話的な管理者アクションの場合は、引き続き同期`/userGroups/{id}/users` APIを使用できます。

### 認証とベースURL

これらのAPIは、標準の&#x200B;__v2 Admin API__&#x200B;サーフェスの一部です。

- [ベースURL (prod)](https://learningmanager.adobe.com/docs/primeapi/v2/)
- 認証： `admin:write`範囲のOAuth 2.0アクセストークン
- 必須ヘッダー：
   - Authorization: Bearer &lt;access_token>
   - Content-Type: application/json
   - Accept: application/json

一般的なAdmin APIの動作とスコープについては、次を参照してください。

- [デベロッパーマニュアル](/help/migrated/integration-admin/feature-summary/developer-manual.md)
- [APIリファレンスガイド](https://learningmanager.adobe.com/docs/primeapi/v2/)

### 形式をリクエスト

__add__&#x200B;と&#x200B;__remove__&#x200B;ではまったく同じボディの形状を使用しています。

#### 本文

```
{
  "metadata": {
    "event_id": "my-optional-correlation-id",
    "sourceSystem": "HRIS",
    "batchId": "hr_2026_03_30_0001"
  },
  "data": [
    { "type": "user", "id": "11101219" },
    { "type": "user", "id": "11101220" }
  ]
}
```

#### データ（必須）

dataは、このバッチのユーザー・リソース識別子のリストです。

- `type`は「user」である必要があります。
- `id`はALMの&#x200B;_数値ユーザーID_&#x200B;です（電子メールではありません。UUIDではありません）。

#### 制約

- `data`が存在し、空であってはなりません。
- 1人以上のユーザーが必要です。
- 最大ペイロードサイズは、リクエストごとに20ユーザーです。
- すべてのIDは数値で、有効なユーザーを参照する必要があります。

これらの条件のいずれかに失敗した場合、APIはエラーを返し、キューに何も格納されません。

#### メタデータ（オプション）

`metadata`は、Webhookにエコーバックする追加の相関データです。

一般的な使用方法：

- `event_id` – 生成する関連付けID。
- `sourceSystem` – アップストリームシステムの名前。
- `batchId` – バッチまたはジョブの識別子。

サービスは、Webhook応答でこのオブジェクトを変更せずに返すので、コールバックを内部ジョブと一致させることができます。

制約：

- オプション。完全に省略できます。
- すべてのキーと値を組み合わせた長さは1,000文字を超えることはできません。

### 応答形式

両方のエンドポイントが、イベントIDを使用して同期的に応答します。

```
{ "event_id": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5" }
```

動作：

- `metadata.event_id`が渡された場合、その値が使用されます。
- それ以外の場合、サービスはUUIDを生成します。

常に次のことを行う必要があります。

- この`event_id`をバッチのプライマリ識別子として保存します。
- Webhookコールバックで同じ値を受け取ることを想定します。

詳細については、[ユーザーグループメンバーシップを追加および削除するためのWebhook](/help/migrated/integration-admin/feature-summary/webhooks.md#webhooks-for-adding-and-removing-user-group-membership)を表示してください。

## よくある質問

_2026年4月のリリースでは、アダプティブ学習プログラム用のlearningObjects APIはどのように変更されますか？_

このリリースでは、学習プログラムにisAdaptiveフラグが追加され、セクションとサブLOが学習者に対応するようになりました。 適応プログラムでは、適応規則に基づいて表示されるセクションとサブ学習オブジェクトのみが学習者に対して表示され、ユーザーグループの基本的な適応設定は管理者が表示できます。

_すべてのセクションとサブLOが常に返されると想定される場合、統合を更新する必要がありますか？_

はい。 適応型学習プログラムの場合、APIは現在の学習者に表示されるセクションとサブLOのみを返すようになりました。 クライアントコードは、応答を完全なリストと見なすのではなく、信頼できる、場合によってはフィルタされたビューとして扱う必要があります。

_コースまたは学習プログラムに対する学習者の完了をプログラムでリセットするにはどうすればよいですか？_

新しいエンドポイントの使用：

```POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion```
これにより、アクセス許可と状態で許可されている場合、ターゲットのインスタンスの完了がリセットされます。

_学習者が別の学習目標または同等の学習目標で完了したかどうかを確認する方法を教えてください。_

学習目標のisAlternateComplete属性を確認します。 trueの場合、alternateCompletions関係に、その学習者の完了の代替手段として機能した学習目標がリストされます。

_特定の学習目標を満たす代替をすべて検索する方法を教えてください。_

次のエンドポイントを使用します。

```GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}```

また、データ配列（代替文字の場合）とmeta.count（代替文字の総数の場合）を使用します。

_現時点で学習者がモジュールの開始を許可されているかどうかを確認するにはどうすればよいですか？_

まず、次の場所からリソースのtimeSlotを取得します。

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```
その後、次のコマンドを使用します。

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

_hasContentDrivenAttemptTrackingはリソースについて何を意味しますか？_

これは、試行のトラッキングが、プラットフォームのカウンターのみではなく、コンテンツ自体（SCORM/xAPIロジックなど）によって制御されることを示します。 これが真実であれば、プラットフォームの試行回数や制限のみに頼ってUXとレポートを作成しないでください。

_ログインしていないユーザー（パブリックエクスペリエンス）に適したメニューを取得するにはどうすればよいですか？_

使用：

```GET /primeapi/v2/templates/menus?include=pages,subMenus.pages&isNonLoggedIn=true```

これにより、匿名ユーザー用にフィルターされたメニューおよびページの構造が返されます。これは、Experience Builderなどのヘッドレスサイトに適しています。

_effectiveModifiedDateを使用した作業計画書のフィルタリングで何が変更されましたか？_

filter.effectiveModifiedDateとfilter.loTypes=jobAidを組み合わせたリクエストで、指定された日付ウィンドウ内の作業計画書のみが正しく返されるようになりました。

_作業計画書のリソースID形式の変更点と対処方法_

ID形式が次のような値から変更されました。

```jobAid:<jobAidId>_-1_-1_2_resource```

宛先：

```jobAid:<jobAidId>_<version>_<localeCode>```

例： jobAid:131032_2_fr_FR。 作業計画書のリソースIDを保存または解析するシステムはすべて更新する必要があります。2026年4月のリリースにアップグレードした後、これらのIDによってキー設定されたローカルインデックスの再構築を計画する必要があります。
