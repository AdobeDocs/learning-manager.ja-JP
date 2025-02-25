---
description: Adobe Learning Managerの2024年11月リリースの新機能と強化機能について説明します
jcr-language: en_us
title: 新機能の概要
exl-id: 4dfe0e31-d202-4a6e-8c4f-43851218699f
source-git-commit: e11a51273d27e6c871a45a52ddb2536baccc57be
workflow-type: tm+mt
source-wordcount: '3255'
ht-degree: 2%

---

# 新機能の概要 {#new-features-summary}

Adobe Learning Managerの2024年11月リリースの新機能と強化機能について説明します。

* **AIを活用した検索：**&#x200B;字句的および意味的な検索を組み合わせて、よりスマートでコンテキストに応じた結果を得られます。
* **Webhooks**: Webhooksと統合して、特定のURLにリアルタイムの情報を送信します。
* **学習ツールの相互運用性(LTI)**：他のLMSプラットフォームとの相互運用性を確保するために、LTIをサポートします。
* **Credly統合** : Credlyで外部バッジを管理および共有します。
* **準拠ダッシュボードの機能強化** ：他の管理者とダッシュボードを共有し、学習者のホームページにデフォルトの準拠ウィジェットを設定します。
* **複数言語のサポート**：教室およびバーチャル教室モジュールの言語固有のインスタンスを作成します。
* **カスタムの役割**:ユーザーの役割とアクセス許可に対する制御が強化されました。
* **完了コメント** ：学習者を完了としてマークするときにコメントを追加します。
* **ユーザーグループレポート**：詳細レポートを使用してユーザーグループを管理します。
* **キャンセル待ちレポート**:コースインスタンスのキャンセル待ち学習者リストをダウンロードします。
* **アクセシビリティの強化** :マストヘッドおよび会社のロゴの代替テキストをサポートします。
* **ヒンディー語のサポート**:ヒンディー語のインターフェイス言語サポート。
* **不敬のチェック**：禁止単語を含むソーシャル投稿をブロックします。
* **電子メールテンプレートの最適化** ：インストラクターの割り当てとセッションのキャンセル用に、電子メールテンプレートを組み合わせて最適化しました。
* **MSチームの完了条件**: VILTセッションの最小出席時間を設定します。
* **新しい移行ワークフロー** ：移行の変更には、コースとモジュールの完了条件およびフォルダーへのモジュールの移行が含まれます。

>[!NOTE]
>
>このリリースの新機能について詳しくは、この[ウェビナー](https://cdn.content.adobelearningmanageracademy.com/public/newlearner/newlearner_0dc0f1e8.html#/overviewPage?instanceId=11932477&amp;loId=11231360&amp;loType=course)をご覧ください。

## Adobe Learning ManagerでのAIを活用した検索

Adobe Learning Managerは、学習者がコースやトレーニングを検索する方法を刷新しています。 AIを活用した検索機能を導入し、語彙検索と意味検索を組み合わせています。 特定の用語を検索し、その背景にある文脈と意図を理解することで、検索が高速化されました。 詳細検索では、クエリの意味が理解され、関連する結果が提供されます。 これにより、検索の主要なフォーカスが識別され、最も完全な結果セットが表示されます。

>[!NOTE]
>
>AIを利用した検索は、学習者のみが利用できます。

詳細については、この記事[高度な検索](/help/migrated/learners/feature-summary/advanced-search.md)を参照してください。

## Webhooks

Adobe Learning Managerを使用すると、Webhooksと統合して、コースの登録、コースの作成などの情報をリアルタイムで特定のURLに送信できます。

ALMのwebhookを使用すると、あるエンティティがHTTPを介して別のアプリケーションにデータを自動的に送信できます。 これにより、アプリケーションは常に情報を要求することなく、他のアプリケーションに情報を提供することができます。 例えば、ユーザーが学習管理システム(LMS)コースを完了すると、webhookはその情報をCRMやレポートツールなどの別のプラットフォームに自動的に送信できます。 Webhookは、プロセスを自動化し、システム間の手動アップデートの必要性を減らすために、統合でよく使用されます。 データの送信先となるコールバックURLを指定して、webhookを設定します。

詳細については、この記事[Webhook](/help/migrated/integration-admin/feature-summary/webhooks.md)を参照してください。

## 学習ツールの相互運用性

Adobe Learning Managerは、LTIをサポートするようになり、Adobe Learning Managerとその他のLearning Management Systems(LMS)との相互運用性が向上しました。

### LTIとは何ですか？

LTI(Learning Tools Interoperability)は、サードパーティのツールおよびコンテンツプロバイダーが学習管理システム(LMS)と接続できるようにする標準です。 ユーザーは、ログインしたり別のLMSに移動したりしなくても、LMS内で外部コンテンツプロバイダーの外部学習コンテンツに直接アクセスできます。

**ツールプロバイダーとしてのLTI**:ツールプロバイダーとしてのLTIにより、外部システムをLMSと統合できます。 Adobe Learning ManagerはLTIツールプロバイダーとして機能し、他のLMSプラットフォームが、自身のLMS内でAdobe Learning Managerから直接、コース、証明書、または学習パスにアクセスできるようにします。

**ツールコンシューマーとしてのLTI**:ツールコンシューマーとしてのLTIを使用すると、LMSはLearning Tools Interoperability(LTI)を介して外部ツールを統合できます。 このシナリオでは、LMSは外部ツールによって提供されるサービスの消費者です。 Adobe Learning ManagerはLTI Tool Consumerの役割を果たし、サードパーティの学習ツールとの連携を可能にします。 これにより、Adobe Learning Managerの学習者は、Adobe Learning Manager内のサードパーティツールからコース、資格認定、または学習パスを利用できます。

詳細については、この記事[学習ツールの相互運用性](/help/migrated/integration-admin/feature-summary/learning-tools-interoperability.md)を参照してください。

## 信心深く

ALMの管理者はCredlyを使用して、学習者がプラットフォームから様々なソーシャルメディアチャネルにわたって外部バッジを管理および共有できるようにします。

### Credlyとは何ですか？

Credlyは、学習者や組織がバッジや資格認定などの専門的な成果を獲得、共有、検証できるようにするデジタル資格情報プラットフォームです。 学習者は、ソーシャルメディアやその他の場所にあるCredlyプロファイルを通じてバッジを管理および共有できます。

### CredlyをAdobe Learning Managerと統合

まず、Adobe Learning Manager(ALM)にCredlyコネクタを追加します。 次に、学習者の達成が継続できるように、既存のバッジをCredlyから移行します。 最後に、Adobe Learning Managerで適切な学習パスに沿ってスキルを構築し、学習者の育成と認知度を高めます。

詳細については、この記事[信頼性](/help/migrated/integration-admin/feature-summary/credly-integration.md)を参照してください

## 準拠ダッシュボード

このリリースでは、管理者が他の管理者、カスタム管理者、ストアマネージャーとダッシュボードを共有できるようになり、準拠ダッシュボードに即座にアクセスできるようになりました。 学習者のホームページでデフォルトの準拠ウィジェットを設定できるようになり、学習者は準拠に関する要件を追跡できるようになりました。 詳細については、この記事[準拠ダッシュボード](/help/migrated/administrators/feature-summary/reports.md#share-compliance-dashboard-with-admins-and-custom-admins)を参照してください。

## 多言語サポート

Adobe Learning Manager(ALM)を使用すると、作成者は教室およびバーチャルクラスルームモジュールの言語タグを使用して言語固有のインスタンスを作成できるようになりました。 学習者は、希望する言語でCR/VCモジュールにアクセスできます。 例えば、作成者は2つのインスタンス（英語とフランス語）を持つCR/VCモジュールを作成できます。 学習者は、希望する言語でインスタンスを選択できます。

詳細については、この記事[別のロケールで学習目標を追加](/help/migrated/authors/feature-summary/add-new-language-learning-objects.md#multi-language-support-for-crvc-instances-with-language-tagging)を参照してください。

## カスタム役割

カスタムの役割を使用すると、管理者はユーザーグループごとに特定の役割と責任を定義できるため、管理と制御を強化できます。 このリリースでは、ALMにより、次のセクションをより詳細に制御してカスタムの役割を強化します。

* ユーザー
* コース
* 学習パス
* 資格認定
* 作業計画書
* カタログ

管理者は、ユーザーの責任に基づいて正確な権限を割り当てることができ、各グループが関連する機能とコンテンツにのみアクセスできるようになります。 これらの機能強化されたコントロールにより、主要なセクションをより詳細に管理できます。

管理者としてログインし、**[!UICONTROL ユーザー]**/**[!UICONTROL カスタムの役割]**&#x200B;に移動して、カスタムの役割を作成および管理します。

詳細については、この記事[カスタムの役割](/help/migrated/administrators/feature-summary/custom-role.md)を参照してください。

## 完了コメント

管理者は、コース、学習パス、資格認定で学習者を完了としてマークするときにコメントを追加できるようになりました。 管理者は、1人または複数の学習者のコメントを同時に追加でき、それらのコメントが[学習者のトランスクリプト](/help/migrated/administrators/feature-summary/reports.md#learner-transcripts)レポートに表示されます。

詳細については、この記事[完了のコメント](/help/migrated/administrators/feature-summary/courses.md#completion-comments)を参照してください。

## ユーザーグループレポート

Adobe Learning Managerの新しい&#x200B;**[!UICONTROL ユーザーグループレポート]**&#x200B;では、管理者が退出したときに管理されていないグループを表示できるため、ユーザーグループを管理しやすくなります。 管理者は、**[!UICONTROL ユーザー]** > **[!UICONTROL ユーザーグループ]**&#x200B;セクションのレポートにアクセスできます。 各グループについて、次のような詳細情報が提供されます。

* ユーザーグループタイプ
* グループ名
* 説明
* 作成者（名前）
* 作成者（電子メール）
* 作成日（UTCタイムゾーン）
* ユーザー数

詳細については、この記事[ユーザーグループレポート](/help/migrated/administrators/feature-summary/add-users-user-groups.md#user-group-report)を参照してください。

## キャンセル待ちレポート

Adobe Learning Managerの新しい&#x200B;**[!UICONTROL キャンセル待ちレポート]**&#x200B;を使用すると、管理者は、コースのすべてのインスタンスについて、キャンセル待ちの学習者リストをダウンロードできます。 管理者とインストラクターは、**[!UICONTROL コース]**&#x200B;または&#x200B;**[!UICONTROL セッションの概要]**&#x200B;ページの&#x200B;**[!UICONTROL キャンセル待ち]**&#x200B;セクションからこのレポートにアクセスできます。 キャンセル待ちレポートは、「管理者」セクションおよび「インストラクター」セクションからダウンロードできます。

キャンセル待ちレポートで使用できる列は次のとおりです。

* コース名
* インスタンス名
* インスタンス ID
* インスタンスのステータス
* ユーザー名
* 電子メール
* ユーザーの一意の ID
* 登録日 (UTC タイムゾーン)
* ステータス
* キャンセル待ち番号
* キャンセル待ちの制限
* 人数制限

この記事[キャンセル待ちレポート（管理者）](/help/migrated/administrators/feature-summary/courses.md#waitlist-report)と[キャンセル待ちレポート（インストラクター）](/help/migrated/instructors/feature-summary/learners.md#waitlist-report)を参照して、管理者およびインストラクターのセクションからレポートをダウンロードしてください。

## 学習者ホームページのアクセシビリティ

Adobe Learning Managerでは、すべてのマストヘッドの代替テキストをサポートするようになり、学習者が利用しやすくなりました。 これにより、スクリーンリーダーを使用して代替テキストを読み、画像を理解する必要のある特別な学習者が学習できます。 複数の言語を選択し、各言語の代替テキストを指定できます。 それぞれの言語で代替テキストを追加してください。 アカウント内の会社のロゴに、会社名の付いた代替テキストも含まれていることを確認します。
詳細については、この記事[発表](/help/migrated/administrators/feature-summary/announcements.md#masthead)を参照してください。

## ヒンディー語のサポート

Adobe Learning Managerは、プラットフォームのインターフェイス言語の1つとしてヒンディー語を導入し、インドでのプラットフォームの成長をサポートするようになりました。 ヒンディー語ネイティブスピーカーがサポートされているので、すべての機能、レポート、全体的なユーザーエクスペリエンスにユーザーが完全にアクセスできます。

>[!NOTE]
>
>PDF形式でシステムによって生成されたバッジ証明書は、ヒンディー語をサポートしません。

インターフェイス言語を変更するには、次の手順に従います。

1. **[!UICONTROL 管理者]**&#x200B;としてログインします。
2. **[!UICONTROL プロファイル設定]** > **[!UICONTROL インターフェイス言語]**&#x200B;に移動します。
3. インターフェイス言語として&#x200B;**[!UICONTROL ヒンディー語]**&#x200B;を選択します。


## SNSへの投稿の不敬チェック

Adobe Learning Managerで、禁止されている単語を含む学習者アプリでのソーシャル投稿がブロックされるようになりました。 これにより、特に医療などの敏感な分野で、専門性とコンプライアンスを保つことができます。

## 電子メールテンプレートの最適化

### インストラクターが割り当てられたときに学習者に電子メールを送信

**[!UICONTROL インストラクターとして追加された]**&#x200B;既存の電子メールと&#x200B;**[!UICONTROL VCProviderセッションの詳細]**&#x200B;が1通の電子メール&#x200B;**[!UICONTROL にまとめられ、UserTypeとして追加されました]**。 **[!UICONTROL UserType]**&#x200B;は、ユーザーの役割に基づいて、**[!UICONTROL インストラクター]**&#x200B;または&#x200B;**[!UICONTROL 主催者]**&#x200B;のいずれかになります。 これらの電子メールは、以前はUIで使用できませんでした。 これらは1つの電子メールに結合され、UIに追加されました。 管理者は、**[!UICONTROL 電子メールテンプレート]**&#x200B;セクションでこのテンプレートにアクセスできます。 デフォルトでは、新規および既存のすべてのアカウントで有効になっていますが、管理者は同じセクションで無効または有効にすることができます。 このメールは、セッションが作成され、インストラクターが割り当てられた際に、Zoom、Teams、Connect、その他のサービスなどのセッション用に送信されます。

### セッションのキャンセル時に学習者に電子メールを送信

セッションから削除されたインストラクターには、セッションのキャンセル通知メールのみが送信されるようになりました。 以前は、キャンセルと更新メールの両方が届いていました。 セッションに残っているインストラクターには、セッションの更新メールが送信されます。また、セッションの新しい招待状も送信されます。

## MS Teamsの完了条件

現在、わずか数秒のバーチャルインストラクター主導のトレーニング(VILT)セッションに参加した場合でも、学習者は出席としてマークされています。 今回のリリースでは、より正確な出席を保証するために、チームモジュールの完了条件が導入されました。 作成者は、学習者が出席をカウントするためにVILTセッションに費やす必要がある最小時間を設定できるようになりました。

これは、デフォルトで無効になっているバックエンド機能です。 CSMに連絡して有効にしてください。

## 電子メール配信用の新しいIPアドレスを更新しています

メール配信の信頼性を向上させるために、既存のプールに新しいIPアドレスを追加しています。 電子メール通信が中断されないようにするには、必要に応じて組織の電子メール設定を更新します。

現在、電子メール配信には次のIPアドレスを使用しています。

* 149.72.162.66
* 167.89.5.155

次のIPアドレスがメール配信プールに追加されます：

* 159.183.228.93
* 159.183.225.26
* 159.183.218.22
* 168.245.57.144

>[!NOTE]
>
>必要に応じて、ITチームと協力して新しいIPアドレスをホワイトリストに登録することをお勧めします。

## 移行の変更

移行ワークフローでは、次の変更が行われます。

* モジュールを特定のフォルダーに移行します。
* モジュールの完了条件を追加。
* コースの完了条件の追加

### モジュール移行の変更点

モジュールをALMに移行すると、デフォルトでパブリックフォルダーに保存されます。 このリリースでは、[module_version.csv](assets/module_version.csv)ファイルに`folder`という新しい列が追加されました。 管理者はこの列を使用して、移行後にモジュールを配置するフォルダーの名前を指定できます。 管理者は、フォルダー名をコンマで区切ってリストすることで、1つのモジュールを複数のフォルダーに配置することもできます。

folder列は文字列データ型を使用し、オプションの列です。 folder列の条件は次のとおりです。

* 追加するフォルダー名は、ALMアカウントの既存のコンテンツフォルダーである必要があります。
* 値はコンマ区切りの文字列である必要があります。
* 別のフォルダーに既に存在するモジュールに対して新しいフォルダー名を追加しても、割り当てられたフォルダーが新しい値で上書きされたり、置き換えられたりすることはありません。 モジュールは新しいフォルダーに追加され、既存のフォルダーでも使用できます。
* 値が空白の場合、フォルダーは既定で&#x200B;**[!UICONTROL Public]**&#x200B;になります。

詳細については、[module_version csv spec](assets/4-module_version.xlsx)ファイルを参照してください。

### モジュールの移行の変更 – 完了条件

管理者は、モジュールの移行中にモジュールの完了条件を指定できます。 このリリースでは、[module_version.csv](assets/module_version.csv)に新しい列`completionCriteria`、`viewPercent`および`quizData`が追加されました。

新しい列の条件は次のとおりです。

1. `completionCriteria`：

   * データ型は文字列値である必要があり、サポートされている値は次のとおりです。
      * `LAUNCH_CONTENT`
      * `VIEW_PERCENT`
      * `QUIZ`
      * `MARK_COMPLETE`
   * セルフペースモジュールタイプの場合にのみ、モジュールレベルで完了条件を追加します。
   * 静的コンテンツでサポートされている値は`LAUNCH_CONTENT`および`VIEW_PERCENT`です。
   * インタラクティブコンテンツでサポートされている値は、`LAUNCH_CONTENT`、`VIEW_PERCENT`、および`QUIZ`です。
   * HTML5コンテンツでサポートされている値は`LAUNCH_CONTENT`および`MARK_COMPLETE`です。

2. `viewPercent`：

   * この列のデータ型は整数にする必要があり、値は0 ～ 100の範囲にする必要があります。
   * completionCriteriaが`VIEW_PERCENT`に設定されている場合、この列に必要なビューの割合を入力するか、空白のままにします。

3. `quizData`：

   * データ型は文字列値である必要があり、サポートされている値は`QUIZ_ATTEMPTED`、`QUIZ_PASSED`、および`QUIZPASSED_OR_LIMITREACHED`です。
   * `completionCriteria`が`QUIZ`に設定されている場合は、`quizData`列に適切なクイズ値を入力します。

詳細については、[module_version csv spec](assets/4-module_version.xlsx)ファイルを参照してください。

### コース移行の変更点 – 完了条件

管理者は、コースの移行中に、コースの完了条件を指定できます。 このリリースでは、[course.csv](assets/course.csv)に`completionCriteria`という新しい列が追加されました。

`completionCriteria`列の条件は次のとおりです。

* データ型はstringまたはnumberのいずれかである必要があり、これはオプションのフィールドです。
* 値は`ALL`、`X`、および`SELECTEDMODULES`である必要があります。
* Xは、0より大きく、モジュールの総数より小さい整数値です。
* `completionCriteria`を`SELECTEDMODULES`に設定した場合、[course_module.csv](assets/course_module.csv)ファイルで必須モジュールをマークする必要があります。
* `optionalCriteria`列に、`TRUE`または`FALSE`を入力します。 値を`TRUE`に設定すると、モジュールは必須になります。

詳細については、[course csv spec](assets/3-course.xlsx)および[course_module csv spec](assets/6-course_module.xlsx)ファイルを参照してください。

## API の変更

APIの変更点は次のとおりです。

* **APIの検索**:
   * classicSearchとadvanceSearchのオプションを持つ新しいモードフィルター。
   * snippetTypesの新しいloMetadataオプション。
* **アナウンスAPI**:
   * マストヘッドの説明にaltText属性が含まれます。
* **インスタンスAPI**:
   * ロケールの詳細を取得するための新しいlocale属性。
* **冒涜的なチェック**:
   * APIを更新し、ソーシャル投稿へのコメントや返信で禁止されている単語を確認できるようになりました。
* **RPMおよびバーストの制限**:
   * すべてのAPIのRPM(Requests Per Minute)とバースト制限を追加しました。
* **バッジAPI**:
   * 外部バッジに関する情報を取得する新しい属性externalProvider。
* **ジョブAPI**:
   * ジョブAPIを使用してユーザーグループレポートとカスタム役割監査レポートをダウンロードします。

### 検索APIの変更点

検索APIに、次の2つのオプションを持つ新しいモードフィルターが追加されました： `classicSearch`と`advanceSearch`。 `snippetTypes`の新しい`loMetadata`オプションもあります。 最適な結果を得るには、`advanceSearch`モードを使用する場合は、`snippetTypes`に`loMetadata`を含めてください。

### アナウンスAPIの変更点

`GET /announcements API`に`altText`属性が追加され、マストヘッドの説明が提供されるようになりました。

#### cURLを使用したサンプルリクエスト：

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' 'https://abcd.adobe.com/primeapi/v2/announcements/123456'
```

#### 応答の例：

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/announcements/123456"
  },
  "data": {
    "id": "12345",
    "type": "adminAnnouncement",
    "attributes": {
      "actionUrl": "google.com",
      "announcementType": "MASTHEAD",
      "expiryDate": "2038-01-19T03:14:07.000Z",
      "liveDate": "2024-07-31T11:11:30.000Z",
      "contentMetaData": [
        {
          "contentType": "IMAGE",
          "contentUrl": "https://abcd.adobe.com",
          "locale": "en-US",
          "altText": "Moonlight - english changed new",
          "thumbnailUrl": "https://abcd.adobe.com/"
        },      ]
    }
  }
}
```

### インスタンスAPIの変更

ロケールの詳細を取得するために、新しい`locale`属性が次のAPIに追加されました。

* `GET /learningObjects/{loId}/instances/{loInstanceId}`
* `GET /learningObjects/{id}?include=instances,enrollment.loInstance`
* `GET /learningObjects?include=instances,enrollment.loInstance`
* `GET /learningObjects/{id}/relatedLOs?include=instances,enrollment.loInstance`
* `POST /learningObjects/query?include=instances,enrollment.loInstance`
* `POST /search/query?include=model.instances`
* `GET /search?include=model.instances`

#### cURLを使用したサンプルリクエスト：

```
curl --location 'http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567' \
```

#### サンプルリクエスト：

```
{
    "links": {
        "self": "http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567"
    },
    "data": {
        "id": "course:1234567_1234567",
        "type": "learningObjectInstance",
        "attributes": {
            "dateCreated": "2024-02-27T09:21:25.000Z",
            "isAET": false,
            "isDefault": true,
            "isFlexible": false,
            "locale": "en-US",
            "state": "Active",
            "localizedMetadata": [
                {
                    "locale": "en-US",
                    "name": "Default instance"
                }
            ]
        },
        "relationships": {
            "learningObject": {
                "data": {
                    "id": "course:1234567",
                    "type": "learningObject"
                }
            },
            "loResources": {
                "data": [
                    {
                        "id": "course:123456_1234567_1234567_1",
                        "type": "learningObjectResource"
                    }
                ]
            }
        }
    }
}
```

### 冒涜性チェックのためのパブリックAPIの変更

次のAPIが更新され、ソーシャル投稿に対するコメントや返信の不公平なチェックが実行されるようになりました。

* `POST /boards/{id}/posts `
* `PATCH /posts/{id}`
* `POST /posts/{id}/comments`
* `PATCH /comments/{id}`
* `POST /comments/{id}/replies`
* `PATCH /replies/{id}`

投稿内に制限された単語が見つかった場合、次の応答が送信されます。

#### 応答の例：

```
{
  "status": "FORBIDDEN",
  "title": "BAD_WORD_FOUND",
  "source": {
    "info": "Unacceptable word found in post"
  }
}
```

### RPMおよびバースト制限の変更

このリリースでは、すべてのAPIに対してRPM(Requests Per Minute)とバースト制限が追加されています。 各APIの最大RPMは、Swaggerページで確認できます。

RPMは、1分間にAPIサーバーに送信できる要求の数です。 バースト制限では、通常のレート制限を超えて、短い時間でより多くの要求が許可されます。 たとえば、`learningObject` APIでは、1分あたり最大15件の要求を許可します。 この制限を超えると、APIはエラーメッセージを返します。

### バッジAPIの変更点

バッジIDとプロバイダー名を含む外部バッジに関する情報を取得するために、新しい属性`externalProvider`が次のAPIに追加されました。

* `GET /badges `
* `GET /badges/{id}`
* `GET /skills?include=levels.badge`
* `GET /skills/{id}?include=levels.badge`
* `GET /learningObjects/{loId}/instances/{loInstanceId}?include=badge`
* `GET /users/{userId}/userBadges`
* `GET /users/{userId}/userBadges/{id}`

#### cURLを使用したサンプルリクエスト：

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 123456789' 'https://abcd.adobe.com/primeapi/v2/badges/44'
```

#### 応答の例：

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/badges/44"
  },
  "data": {
    "id": "44",
    "type": "badge",
    "attributes": {
      "imageUrl": "https://abcd.com/accountassets/1/badges/download.png",
      "name": "external badge",
      "state": "Active",
      "externalProvider": {
        "id": "1234sjd-b272-4de1-9b60-1234567",
        "provider": "credly"
      }
    }
  }
}
```

### ジョブAPIを介したユーザーグループおよびカスタムの役割の監査レポートのダウンロード

ユーザーは、`Job API`を使用して&#x200B;**[!UICONTROL ユーザーグループレポート]**&#x200B;と&#x200B;**[!UICONTROL カスタムロール監査レポート]**&#x200B;をダウンロードできます。

#### ユーザーグループレポートのダウンロードのサンプルリクエスト：

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' -d '{ \ 
     "data": { \ 
         "type": "job", \ 
         "attributes": { \ 
             "jobType": "generateUserGroupReport" \ 
         } \ 
    } \ 
 }' 'https://abcd.adobe.com/primeapi/v2/jobs'
```

#### カスタム役割監査レポートのダウンロードのサンプルリクエスト：

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 1234567' -d '{
    "data": {
        "type": "job",
        "attributes": {
            "description": "description of your choice",
            "jobType": "generateCustomRoleAuditReport",
            "payload":{
                 "fromDate": "2020-01-01T18:30:00.000Z",
                 "toDate": "2024-09-31T18:30:00.000Z",
                 "locale":  "en-US"
            }
        }
   }
}
```

### リクエスト本文なしのエラーメッセージ

リクエスト本文が必須であるが、APIに提供されていない場合の特定のエラーメッセージを導入しました。

#### エラーメッセージの例：

```
{
    "status": "BAD_REQUEST",
    "title": "Generic Error"
}
```

## レポートの機能強化

管理者は、**管理者** > **レポート**&#x200B;セクションで、これらのレポートの変更を確認できます。

### 学習トランスクリプトレポート

**[!UICONTROL 学習トランスクリプト]**&#x200B;レポートには、次の2つの新しい列が含まれます：

* **[!UICONTROL モジュールID]**：各モジュールの一意の識別子を表示します。 この新しい列は、既存の&#x200B;**[!UICONTROL モジュール]**&#x200B;列の後に追加されました。
* **[!UICONTROL コースインスタンスID]**：各コースインスタンスの一意のIDを表示します。この新しい列は、既存の&#x200B;**[!UICONTROL インスタンス]**&#x200B;列の後に追加されました。
* **[!UICONTROL 完了コメント]**：この列には、ユーザーの完了を記録するときに管理者が入力したコメントが記録されます。 この新しい列は、レポートの最後に追加されました。


### セッションの概要レポート

**[!UICONTROL セッションの概要]**&#x200B;レポートには、次の3つの新しい列が含まれます。

* **[!UICONTROL モジュールID]**&#x200B;列が&#x200B;**[!UICONTROL セッション名]**&#x200B;列の前に追加されました。
* **[!UICONTROL セッションID]**&#x200B;列が&#x200B;**[!UICONTROL セッション名]**&#x200B;列の前に追加されました。
* **[!UICONTROL コースインスタンスID]**&#x200B;列が&#x200B;**[!UICONTROL インスタンス名]**&#x200B;列の後に追加されました。
* **[!UICONTROL 完了数]**&#x200B;列が&#x200B;**[!UICONTROL 登録数]**&#x200B;列の後に追加されました。

## このアップデートで修正されたバグ

* AndroidデバイスおよびiOSデバイスでのファイル送信中に、アクティビティモジュールからビデオをアップロードする際に発生したエラーを修正しました。
* モバイルアプリでコースを開く際に、webバージョンが正しく機能していましたが、この問題を修正しました。
* Safariで作業計画書やその他のリソースを表示する際の問題を修正しました。
* ユーザーがモバイルアプリで作業計画書をダウンロードできない問題を修正しました。
* パッチユーザーAPIのドキュメントのエラーを修正しました。
* コースからセッションが削除されたときに、主催者がメール通知を受け取れない問題を修正しました。
* モジュールがコースから削除されて再パブリッシュされた場合、主催者がセッションのキャンセルを知らせるメールを受信しない問題を修正しました。
* 外部ユーザーの作成時に電子メールアドレスに特殊文字「+」および「 – 」を含める機能がサポートされました。
* ユーザーのスキルレポートのCSVレコード値に二重引用符が含まれていると、Marketoコネクタの統合レポートの同期が失敗する問題を修正しました
* `/skills`エンドポイントがAdmin APIの正しい状態を返すが、学習者APIが常に正しくないデータまたはキャッシュされたデータを表示する問題を修正しました。
* アカウントにGo1コネクタが設定されていない場合、フリーミアムコースのGo1オンボーディングが失敗する問題を修正しました。
* 学習者が学習パス(LP)を既に完了している場合、移行を介して学習パス(LP)のコースにアクセスできない問題を修正しました。
* ユーザーのマネージャーとスキップレベルマネージャーの両方が管理者ではなくSU（スーパーユーザー）として設定され、CSVに含まれていないと、インクリメンタルユーザーのCSVが失敗する問題を修正しました。
* ダッシュボードレポートのストアマネージャーのスコープの問題を修正しました。
* ドラフトコースが削除されたときにxapi_iriが削除されない問題を修正しました。
* 特定のシナリオで一意のLO IDを追加できない問題を修正しました。
* 学習プランのIsEmbeddableプロパティが共有学習プランで正しく更新されない問題を修正しました。
* 学習者ビューの学習パスの合計表示時間に影響する問題を修正しました。
* アカウントが削除された後でも、学習者が自己登録リンクを介して登録または新規登録できる問題を修正しました。
* コースの作成中にコースの説明にリンクを追加すると`www`が削除される問題を修正しました。
* 非表示情報と作業計画書のダウンロードが正しく機能しない問題を修正しました。
* IP IDを使用したセルフ登録リンクを介して追加された新しいユーザーに対してシングルサインオン(SSO)が機能しない問題を修正しました。
* アナウンスが削除された後、通知メッセージデータが取得されない問題を修正しました。
* 電子メールでユーザーを検索する際に、検索結果が不十分になる問題を修正しました。

## 必要システム構成

[Adobe Learning Managerの必要システム構成](/help/migrated/system-requirements.md)を確認してください。

## リリースノート

最新のリリースアップデートについては、[リリースノート](/help/migrated/release-note/release-notes.md)を参照してください。

## Adobe Learning Manager の過去のリリース

* [2024年7月リリース](/help/migrated/whats-new-july-2024.md)
* [2024年3月リリース](/help/migrated/whats-new-march-2024.md)
