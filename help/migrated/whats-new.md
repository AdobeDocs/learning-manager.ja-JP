---
description: Adobe Learning Manager の 2024 年 7 月リリースの新機能と機能強化について説明します。
jcr-language: en_us
title: 新機能の概要
source-git-commit: 7e3b19d29b9de23ea489c5651ef0aef1d4ec3005
workflow-type: tm+mt
source-wordcount: '2178'
ht-degree: 2%

---


# 新機能の概要 {#new-features-summary}

Adobe Learning Manager の 2024 年 7 月リリースの新機能と機能強化について説明します。

## コンプライアンスダッシュボードの機能強化

### コンプライアンスダッシュボードとは何ですか? {#whatiscompliancedashboard}

**Adobe Learning Manager**&#x200B;の&#x200B;**[!UICONTROL コンプライアンスダッシュボード]**&#x200B;を使用すると、マネージャーは学習者の学習目標に対する進捗状況を監視および監視できます。チームメンバーが締め切りを守り、学習プロセスに遅れずについていくかどうかを確認できるため、コンプライアンスを確保できます。 管理者はコンプライアンスダッシュボードを設定し、マネージャーと共有できます。

管理アプリのコンプライアンスダッシュボードにアクセスするには、 **[!UICONTROL レポート]** > **[!UICONTROL ラーニングの概要]** > **[!UICONTROL コンプライアンスダッシュボード]**&#x200B;を選択します。

### このリリースの変更点

強化されたコンプライアンス ダッシュボードを使用すると、管理者とマネージャーは、特定のカテゴリ (営業、マーケティング、法務など) に関連するコンプライアンス タイプのコース、ラーニング パス、または認定を表示できます。 管理者は、カスタムコンプライアンスコースを特定のカテゴリに分類できます。 カスタムコンプライアンスカテゴリは、カタログラベルを利用しています。  管理者はコースダッシュボードを作成し、マネージャと共有できます。 マネージャーは、それぞれのインスタンスで同じダッシュボードを表示できます。 コンプライアンスダッシュボードのユーザーインターフェイスとコンプライアンス電子メール通知も強化されました。![](assets/compliance-dashboard-admin.png)

#### ワークフロー

拡張コンプライアンスダッシュボードを使用する手順は次のとおりです。

| 役割 | タスク | 追加情報 |
|---|---|---|
| 管理者 | カスタムコンプライアンスラベルの作成 | 詳細については、この記事 [カスタムコンプライアンスラベルの作成](/help/migrated/administrators/feature-summary/reports.md#compliance-dashboard) を参照してください |
| 作成者 | これらのラベルをコースに追加する | 詳細については、この記事 [コース/ラーニング パス/認定資格にコンプライアンス ラベルを追加する](/help/migrated/authors/feature-summary/courses.md#add-compliance-labels-to-courselearning-pathcertification) を参照してください。 |
| 管理者 | コンプライアンスコースを含むダッシュボードを作成し、マネージャーと共有する | 詳細については、この記事 [コンプライアンスダッシュボードの作成と共有](/help/migrated/administrators/feature-summary/reports.md#create-and-share-a-compliance-dashboard) を参照してください。 |
| マネージャー | コンプライアンスダッシュボードを表示する | 詳細については、この記事 [コンプライアンス状況](/help/migrated/managers/feature-summary/manager-dashboard.md#compliance-status) を参照してください |

## 学習者のユーザーインターフェイスの刷新

>[!IMPORTANT]
>
>新しい学習者 UI は段階的にリリースされます。

**学習者UI**&#x200B;は、よりエレガントでモダンなデザインに更新されました。**[!UICONTROL 学習者ホーム]**、**[!UICONTROL マイラーニング]**、**[!UICONTROL カタログ]**、および&#x200B;**[!UICONTROL コースの概要]**&#x200B;のランディングページは、新しくモダンな外観になっています。コースカードには、詳細を現代的な方法で表示するための新しいデザインもあります。 コースカードにカーソルを合わせると、コースの説明と公開日が表示されます。

>[!NOTE]
>
>改良されたユーザーインターフェイスは、没入型レイアウトにのみ適用されます。 これらの変更は、モバイルウェブやアプリではまだサポートされておらず、今後のリリースで更新される予定です。

![](assets/old-ui.png)
_古いユーザー インターフェイス_

![](assets/new-ui.png)
_新しいユーザー インターフェイス_

### このリリースの変更点

**ルックアンドフィールのモダナイゼーション**

新しく更新されたビジュアル要素は、現代のデザイントレンドに合わせており、製品を直感的で魅力的に見せています。 これには、新しいマストヘッド、サイドパネル、およびモダンな外観のウィジェットが含まれます。

**ユーザー操作の向上**

学習者は、ホームページ、カタログ、マイラーニング、およびコースの概要ページで同様のカードビューを表示して、統一されたエクスペリエンスを提供します。

詳細については [学習者のホームページ](/help/migrated/learners/feature-summary/learner-home-page.md) を参照してください。

**コース公開日の変更**

この機能強化により、Adobe Learning Manager に読み込まれた LinkedIn および Go1 コースの公開日が、LinkedIn および Go1 での実際の公開日と同じになります。 LinkedInコースとGo1コースの実際の公開日もユーザーインターフェイスで確認できます。 詳細については [コースカード](/help/migrated/learners/feature-summary/learner-home-page.md#course-cards) を参照してください。

## ログインしていないエクスペリエンスの更新

ログインしていないエクスペリエンスを使用すると、ログインしていない顧客向けのリアルタイム エクスペリエンスを作成できます。 これは、マーケティングキャンペーンのランディングページとして機能し、サインアップを促すのに十分な情報を提供します。

### このリリースの変更点

お客様は、プレミアム プランを購入して、この高度にスケーラブルな非ログイン エクスペリエンスを構築できます。 [トレーニングデータアクセス](/help/migrated/integration-admin/feature-summary/connectors.md#training-data-access)を利用したこのログに記録されないエクスペリエンスでは、Adobe Learning Manager API を使用して、シート制限、占有シート、キャンセル待ちリストの制限、キャンセル待ちリストの数に関するリアルタイムデータを提供します。お客様はこれらの API を使用して、ログインしていない学習者に検索およびフィルター機能と完全なコースの概要を提供できます。 API について詳しくは、この記事 [非ログイン API](/help/migrated/integration-admin/feature-summary/non-logged-in-apis.md) を参照してください。

>[!NOTE]
>
>サポートチームまたはCSAMに連絡して、プレミアムプランを購入してください。

## 複数の在庫管理単位 (SKU) のサポート

学習者は、複数のコース、学習パス、または認定資格をカートに追加して、それらを一緒に購入できるようになりました。

### このリリースの変更点

以前は、学習者は一度に1つのコースしか購入できませんでした。 このリリースの **Adobe Learning Manager**&#x200B;では、カートを使用して複数のコース、ラーニングパスまたは認定資格を一度に購入できます。

この機能は、学習者アプリ (既存の UI、新しい学習者 UI、モバイル イマーシブ アプリ) でのみ使用できます。

ALMで [マルチアイテムカートを表示](/help/migrated/learners/feature-summary/multi-item-cart.md)

## Fluidic Player での HTML5 コンテンツのサポート

**Adobe Learning Manager** では、HTML5 コンテンツの.zipファイルとしてのコンテンツライブラリへのアップロードがサポートされるようになりました。 アップロードすると、これらのファイルをモジュールとしてコースに含めることができます。 また、作成者は自分のペースで進められる HTML5 モジュールの完了基準を定義して、学習者がマークした完了または起動時に自動的に完了することができます。

### このリリースの変更点

Adobe Learning Manager では、自分のペースで進められるコースで、HTML5 でサポートされているコンテンツがサポートされるようになりました。 作成者は、HTML5 コンテンツを.zipファイルとして、自分のペースで進められるコンテンツに追加できます。 学習者は HTML5 コンテンツを Fluidic Player で表示できます。 新機能により、学習者は自分のペースで進められるコースのFluidic Playerで直接コースを完了としてマークできるようになりました。 詳しくは [コンテンツライブラリに HTML5 ファイルタイプを追加](/help/migrated/authors/feature-summary/content-library.md#add-html5-file-type-in-the-content-library) を参照してください。

新しい機能強化により、作成者が新しいオプション **[!UICONTROL コンテンツの起動時]**&#x200B;に完了基準を設定している場合、外部リンクを含むコースはURLにアクセスすると自動的に完了としてマークされます。 新しいオプション **[!UICONTROL 完了基準]** がアクティビティモジュールページに追加され、作成者は外部リンクの完了基準を設定できます。 詳細については、 [アクティビティ モジュールに HTML リンクを追加](/help/migrated/authors/feature-summary/courses.md#add-html-link-in-the-activity-module) を参照してください。

![](assets/completion-criteria-activity-module.png)
_完了基準オプション-アクティビティモジュール_

## モバイルアプリでのコース期限切れプッシュ通知

学習者は、コースの締め切りに間に合わないたびにプッシュ通知を受け取ります。 この新しい機能強化により、学習者はリマインダーを24時間スヌーズするか、期限切れのリマインダーを受け取るたびに来週リマインダーを受け取るかを選択できるようになりました。 これは、期限超過通知にのみ適用されます。 表示 [プッシュ通知のスケジュール設定](/help/migrated/learners/feature-summary/user-notifications.md#schedule-the-push-notification)

## このリリースでの API の変更

### 検索 API

検索 API には、次の変更が含まれています。

学習者は、 ```GET /search``` API を使用してカタログフィルター内のタグを検索できます。 学習者は、パラメータの値として ```tag``` を選択することで、タグ ```filter.loTypes``` 検索できます。

**サンプルカール**

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 5a858f23924f4feafa38ae8d6c4d97b6' 'https://example.com/primeapi/v2/search?page[limit]=10&query=Business&autoCompleteMode=true&filter.loTypes=tag&sort=relevance&filter.ignoreEnhancedLP=true&matchType=phrase&persistSearchHistory=true&stemmed=false&highlightResults=true'
```

新しいフィルター、利用可能な座席、利用可能な順番待ちリスト、および時間範囲フィルターが、 ```GET /search``` と `GET /learningObjects` API に追加されました。

新しいフィルター `filter.session.includeEnrollmentDeadline` は、次の API ```GET /search```に追加されました。

### アカウント API

ユーザーエンドポイントのアカウントデータを取得するために、```GET /account``` API に新しい列`custom_injections`、`showComplianceLabel`、`complianceLabelDefaultID`が追加されました。

### 学習目標 API

このアップデートでラーニングオブジェクト API に加えられた変更点は次のとおりです。

`GET /learningObjects` API の [`authorDetails`] の下に追加された新しい応答レガシ作成者 ID とその他の詳細。さらに、 `filter.authors`という新しいフィルタが追加され、レガシー作成者とそのコースをフィルタできるようになりました。

`effectivenessIndex`という新しい属性は、コースの有効性データを取得するのに役立ちます。

**サンプルカール**

```
curl --location 'https://example.com/primeapi/v2/learningObjects/course%3A9790045?enforcedFields%5BlearningObject%5D=effectivenessData' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth 598665ab5c8a99bea0e774d9faf7f3ca'
```

このコースを受講する必要があるユーザーの詳細を示す新しい応答 `whoShouldTake`が、 `POST /learningObjects/query`、 `GET /learningObjects/{id}`、および `GET /learningObjects` API に追加されました。

**サンプルカール**

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 28a83fb8c87579af8ebc4434cc80f0c0' 'https://example.com/primeapi/v2/learningObjects/course%3A1131255' 
```

待機リストの制限に関する詳細を提供する新しい応答 `waitlistLimit`が `GET /learningObjects` API に追加されました。

学習オブジェクトの合計数を示す新しい応答 `count` が、API `GET/ learningObjects` と `POST/ learningObjects/query`に追加されました。

新しい応答、 `catalogFieldId` 、 `fieldValueId` が API の `catalogLabels` `GET/ learningObjects` に追加されました。

学習者は、API `GET /preview/learningObjects`でカタログラベル値を取得できます。

### マーケットプレイス数を取得するための新しい API

このリリースでは、新しい API `GET /search/marketplace/count` が追加されています。 これは、コンテンツマーケットプレイスで利用可能な学習オブジェクトの数を取得するのに役立ちます。

**サンプルカール**

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth d8631c7b0e3b5d2ae00422ef30aaecfc' 'https://example.com/primeapi/v2/search/marketplace/count?query=course'
```

**サンプル応答**

```
{
  "count": 54910
}
```

### ラーニングオブジェクトインスタンス API

このアップデートでラーニングオブジェクトインスタンス API に加えられた変更点は以下のとおりです。

このリリースでは、 `gamificationEnabled` という新しいキーがラーニングオブジェクトインスタンス API `GET /learningObjects/{loId}/instances/{loInstanceId}`に追加されました。

**サンプルカール**

```
curl --location 'http://example.com/acapapi/primeapi/v2/learningObjects/learningProgram:12756/instances/learningProgram:12756_15644' 
```

ゲーミフィケーション設定の詳細を取得するための上記のAPIへの新しい `gamificationSettings` 属性。 例: `GET /learningObjects/{loId}/instances/{loInstanceId}/gamificationSettings`。

**サンプルカール**

```
curl --location 'http://example.com/acapapi/primeapi/v2/learningObjects/learningProgram:103852/instances/learningProgram:103852_103526/gamificationSettings'
```

ゲーミフィケーション設定の詳細を取得するための上記のAPIへの新しい `leaderboard` 属性。 例: `GET /learningObjects/{loId}/instances/{loInstanceId}/leaderboard`。

**サンプルカール**

```
curl --location 'https://example.com/primeapi/v2/learningObjects/learningProgram:106339/instances/learningProgram:106339_105775/leaderboard' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth de4b5ee6efdd42375130db27ff503dd4'
```

### オフセット制限の変更

システムパフォーマンスを向上させ、リソース使用率をより効果的に管理するために、アドビでは、ADMIN スコープと LEARNER スコープの両方で GET /users エンドポイントの高いオフセット値を廃止しました。 ジョブ API を使用して、オフセット値を持つレコードを取得することをお勧めします。

### 廃止された API

製品 [Adobe Learning Manager での API の廃止](/help/migrated/api-deprecations-list.md) を参照して、製品で廃止されたすべての API の累積リストを確認してください。

## レポートの変更

### 準拠ダッシュボード

このリリースでは、コンプライアンス ダッシュボード レポートに 2 つの新しい列があります。

* ステータス
* コンプライアンスタイプ

これは、既存の列に追加されます。

* ユーザー名
* ユーザーの電子メール
* LP／資格認定／コース
* タイプ
* 登録日（UTC タイムゾーン）
* 期日 (UTC タイムゾーン)
* 完了日（UTC タイムゾーン）
* 進行状況 %

### トレーニングレポート

**管理者** > **レポート** > **カスタムレポート**&#x200B;および&#x200B;**ジョブAPI**&#x200B;のトレーニングレポートには、以前は&#x200B;**スキル**&#x200B;と&#x200B;**タグ**&#x200B;と呼ばれる列がありました。これらの列の名前が **スキル** と **タグ**&#x200B;に変更されました。

### コンテンツ監査レポート

このリリースでは、 **[!UICONTROL コンテンツ監査証跡]** レポートに「変更タイプ」列に次の新しい属性が含まれるようになりました。

* ユーザーグループ追加
* ユーザーグループの削除
* カスタムラベル 追加
* カスタムラベル 削除
* 共有カタログ 追加
* 共有カタログ 削除
* 共有カタログの更新

## このアップデートで修正されたバグ

**アクティビティの提出**

* アクティビティ送信モジュールにファイルを再アップロードしようとすると、ネットワーク呼び出しでエラー 500 で失敗します。

**API**

* 複数のインストラクターが同じメールアドレスを持っている場合、Connect VCミーティングの作成は失敗します。
* ラーニング パスに登録すると、MS Teams VC の [概要] ページに誤った URL が表示されます。
* ジョブ API 応答の一部として指定されたユーザーレポート署名付き URL は、6 時間後に期限切れになります。
* コースの登録レポートの生成中に、[コース名]列に誤ったコース名が表示されます。
* 移行ワーカーは、もちろん一括 API を呼び出すときに一意の lo id を送信できませんが、id は削除されます。
* ユーザーがアクセスできる特定のカタログにコースが含まれている場合(デフォルトのカタログが無効になっている場合)、未登録の学習者がコースを表示できないように設定されていても、learningobject/idエンドポイントを介してコースのメタデータを取得できます。
* スキル フィルターは、GET /learningObject API でスキル名の名前にコンマが含まれている場合、期待どおりに機能しません。
* SFTP のデータ保持ワーカー内のファイルのタイムスタンプ メタデータに不整合があります。
* いずれかのコネクタが削除されて再構成されると、プロジェクトの移行状態は閉じられたように見えます。
* トレーニングレポートには、列ヘッダーとして「タグ」ではなく「タグ」があります。
* カタログが無効になっていて、エクスポートされたコースのいずれかが無効になっているカタログの一部にすぎない場合、Commerce コネクタのエクスポートは失敗します。

**資格認定**

* 定期的な認定へのユーザーの再登録が失敗する場合があります。

**カスタムロール**

* 場合によっては、カスタム管理者が講師ロールに切り替えようとすると、エラー403禁止が表示されます。

**メールテンプレートと通知**

* セッションがキャンセルされた後の電子メール通知は、インストラクターがセッションから削除されても、最後のインストラクターセットに送信されません。
* 主催者は、仮想インストラクター主導のトレーニングを作成した後、MS Teamsの電子メール通知を受信しません。 コースが公開され、Eメールテンプレートが有効になって初めて、Eメールがトリガーされます。
* 電子メールテンプレートに誤った日付形式と翻訳が含まれている場合があります。

**学習者**

* 学習者がコースの複数のインスタンスに登録されている場合、出席レポートをダウンロードすると、レポートに誤った情報が含まれます。
* ユーザーは、別のユーザーの非公開投稿が公開ストーリーに追加されると、その投稿を表示できます。
* 場合によっては、認定資格から学習者の登録を解除できないことがあります。 登録を解除しようとすると、エラーメッセージが表示されます。
* 認定資格は、管理者がコースを 1 つだけ選択した後に完了とマークした後でも、完了としてマークされます。
* 管理者は、セッションの終了時刻が以前の日付に変更された場合、VC を完了としてマークできません。
* セッション出席レポートは、順番待ちリストに登録されている学習者に対して「未出席」として表示されます。

**学習者アプリ**

* コースノートをPDFとしてダウンロードすると、ノートがランダムに表示されます。 彼らは命令に従わない。

**ラーニング パス**

* ラーニング・パスでスキルを選択した後、テキスト・フィールドを選択してもドロップダウンが期待どおりに表示されません。
* 場合によっては、ラーニング パスからスキルを削除できません。

**学習プログラム**

* 柔軟な学習プログラムに多数のコースがある場合、管理者が完了とマークした後でも、学習計画は完了しません。
* 登録レポートの列last_modified_byは、学習者がインスタンスを変更しても更新されません。

**レポート**

* 場合によっては、管理者がトレーニング レポートをエクスポートできないことがあります。
* SCORMコンテンツに32,767文字を超える質問または回答が含まれている場合、Excelでコースクイズレポートをダウンロードすることはできません。
* [ゲーミフィケーションのリセット] を選択した後、[レベル達成日] はリセットされません。

**検索**

* 現在、すべてのユーザーグループをエクスポートした後、削除されたユーザーグループも出力に含まれます。
* 断続的な検索の問題により、認定資格を検索できません。

## このリリースの既知の問題

モバイルオフラインプレーヤーでは、HTML5 コンテンツは読み込まれません。

## 必要システム構成

[Adobe Learning Manager の必要システム構成](/help/migrated/system-requirements.md)を表示します。

## Adobe Learning Manager の過去のリリース

* [2024 年 3 月リリース](/help/migrated/whats-new-march-2024.md)
* [2023 年 11 月リリース](/help/migrated/whats-new-november-2023.md)
