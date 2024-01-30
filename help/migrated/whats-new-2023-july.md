---
title: このリリースの新機能（2023年7月）
description: Adobe Learning Manager の新機能と機能強化について説明します
hidefromtoc: true
source-git-commit: c55f9448082c9971c065eec95b59992db95e53dc
workflow-type: tm+mt
source-wordcount: '2052'
ht-degree: 67%

---

# このリリースの新機能（2023年7月）

## 推奨事項の改善

Adobe Learning Manager では、新しく改良されたコース推奨システムが導入されました。 このレコメンデーション機能では、AIアルゴリズムと、製品、役割、レベルなどのユーザーの関心事を使用して、パーソナライズされたコンテンツのレコメンデーションを提供します。

詳しくは、[Adobe Learning Manager の推奨機能](recommendations-adobe-learning-manager.md)を参照してください。

## 複数登録

Adobe Learning Manager のこのリリースでは、学習者向けに複数登録が導入されました。これにより学習者は、同一期間または異なる期間中に、複数のインスタンスに登録することができます。

詳しくは、[「複数登録」](/help/migrated/authors/feature-summary/courses.md)を参照してください。

### モバイルアプリまたは没入型での複数登録

学習者は、モバイルアプリや没入型から複数のインスタンスに登録することはできません。 モバイルアプリと没入型モバイルwebでは、複数登録はサポートされていません。

>[!NOTE]
>
>複数登録を有効にすると、各コースの学習者のトランスクリプトレポートに複数の行が追加されます（各インスタンスにつき 1 行）。
>
>コースごとに1行のみを見込むレポート自動処理を設定している場合は、複数登録機能を有効にする前に、レポート自動処理に必要な調整を行う必要があります。

### 複数登録インスタンスのバッジの形式

複数登録されたインスタンスでバッジをサポートするために、バッジの形式はに変更されています。 `userId_badgeId_COURSE_courseId_courseInstanceId`.

### 複数登録されているプレーヤーの起動（ヘッドレスモードを使用）

このリリースでは、ヘッドレスプレーヤーとの通信に使用するライブラリが変更されました。

複数登録では、オブジェクト内でラップされた引数を渡す必要があります。

```
{{startplayer(argument_object) ,
where
argument_object=
{ loId = <loId>, accountId = <accountId>, userId =<userId>, accessToken = <accessToken>, domId = <elementId>, onModuleLoaded = fn(), isMultiEnrolled=<boolean>, instanceId=<instanceId> }
}}
```

## exavaultコネクターの廃止

今回のAdobe Learning Manager のリリースには、AWS Transfer ファミリーの SFTP プロトコルを使用する新しいコネクタが含まれます。

この変更により、ExaVault コネクタも置き換えられ、新規ユーザは ExaVault コネクタを使用できなくなります。 ExaVault の代わりに、任意のオープンソース FTP クライアントを使用できます。 詳しくは、「 [Adobe FTPマネージャーからの移行](transition-from-ftp-manager.md).

## 教室およびバーチャルセッションのOutlookでのリマインダー

学習者のOutlookカレンダーに追加されたLearning ManagerAdobeが作成する教室およびバーチャルクラスルームセッションで、Outlookからのリマインダーが一貫してサポートされるようになりました（Outlookの会議リマインダーと同様）。

## コースへのスキルの割り当ての機能強化

作成者向けのスキル割り当てワークフローが強化されました。 コース設定ページの「スキル」候補リストに、先行入力検索機能が追加されました。 作成者は、最初の数文字を入力するだけでスキルを検索できるようになり、その入力に基づいて「スキル」ドロップダウンリストに候補が表示されるようになりました。 この機能強化により、作成者がコースにスキルを検索して割り当てるために、リスト全体をスクロールする必要がなくなりました。

## マネージャーが承認したコースワークフローの改善

マネージャーが承認したコースでは、マネージャーと学習者の両方に適切なエラー情報が提供されるようになりました。

![エラーメッセージ](assets/error-messages.png)

マネージャーがコース登録リクエストを承認できない場合に、関連するエラーメッセージと情報（登録期日の超過など）を表示できるようになりました。 学習者には、エラーと修復のためのアクションが表示されます。

## 新しい学習プランのレポート

管理者 / カスタム管理者は、アカウント内のすべての学習プランのリストと、ステータス、該当するユーザーグループ、トリガー情報、学習プランに含まれるコース / 学習パス、リマインダー情報などのメタデータを書き出すことができるようになりました。

## 今後の廃止インスタンスを追跡するためのレポート

トレーニングレポートには、コースまたは学習パスに存在するインスタンスの完了期日を表示する列が追加されています。これにより、管理者と作成者は、廃止されるインスタンスを把握し、必要なアクションを実行することができます。

## 学習者からコース評価をキャプチャするための機能強化

ユーザーがコースの最後のモジュールを完了するとすぐに、コースの星評価を促すポップアップが表示されます。

![評価](assets/ratings.png)

## 電子メールテンプレートのカスタマイズ

Learning Manager の電子メールテンプレートには、編集可能なセクションが含まれるようになり、電子メールによるコミュニケーションをメッセージングやブランディングの設定に基づいてより柔軟にカスタマイズできるようになりました。

詳しくは、[「電子メールテンプレートのカスタマイズ」](/help/migrated/administrators/feature-summary/email-templates.md#flexibility-in-customizing-the-templates)を参照してください。

## スケジューリングアシスタントの機能強化

教室やバーチャルセッションのインストラクターを選択するプロセスを細かく調整できます。 スケジュールアシスタントの[インストラクター]フィールドに[ユーザーグループ]フィルターが追加されました。 作成者は、「インストラクターのスキル」と、場所、言語、名称などの追加パラメーターに基づいて、インストラクターをフィルタリングできるようになりました。

詳しくは、[「スケジュール管理アシスタントのユーザーグループフィルター」](/help/migrated/authors/feature-summary/courses.md#user-group-filter)を参照してください。

## 学習目標の廃止ワークフローの強化

作成者が、コースの&#x200B;**「自動廃止」**&#x200B;の日付を指定できるようになりました。 これにより、時間の経過に伴ってカタログが増え続けることを防ぎ、戻ってコースを手動で廃止する必要がなくなります。

管理者は、アカウントレベルで「撤回済み」の学習オブジェクトへのアクセスの性質を決定することもできます。

トレーニングレポートには、新しい列、 **自動除・売却日**&#x200B;を選択すると、各学習目標の廃止日が表示されます（設定されている場合）。

## 作成者によるカタログラベル値

作成者は、コースの作成時または編集時にカタログラベルに自分の値を追加できるようになりました。 管理者は、この機能をアカウントレベルで有効にすることができます。 作成者が新しいカタログラベルの値を追加すると、その値は先行入力検索の対象となります。

![カタログを選択](assets/select-catalog.png)

## 管理者、作成者、マネージャーの役割のコース検索の機能強化

管理者、作成者、マネージャーの役割による検索機能が強化されました。 これにより、タイトルのキーワードで検索できるようになります。 これは、コース、学習パス、資格認定に適用されます。

## 移行エラーの通知

移行中、または PowerBI、FTP、Box などのデータコネクタの使用中に読み込み / 書き出し操作が失敗した場合、統合管理者は電子メールで通知を受け取れます。

## APIによるマルチマネージャー設定

マルチマネージャー構成をサポートするために、Managed Office の API セットに新しい API が追加されました。

## 登録APIの機能強化

大規模一括登録のサポートおよび最適化のために、登録 API の連携が強化されました。

## モバイルアプリ – オフラインコンテンツの表示

学習者は、オフラインモードでコンテンツをダウンロードして利用できます。 ネストされた柔軟な学習パスは、オフライン表示に対応していません。

*このリリースでは、オフラインコンテンツの表示は、英語のコンテンツでのみサポートされています。*

## アクセシビリティ

読みやすさを最適化するためのスクリーンリーダーを使用した機能強化などを含め、アクセシビリティの向上のために複数の機能強化が行われました。

## モバイルアプリのサポート

次のメジャーリリースで Adobe Learning Manager モバイルアプリに対応しているのは、モバイル OS の直近 3 つのバージョンのみです。

## LinkedIn のコンテンツ

Safari ブラウザーの没入型アプリでは、LinkedIn コンテンツを適切に読み込むことができません。 回避策として、次の操作を実行してください。

1. デバイスで、 **[!UICONTROL 設定]** > **[!UICONTROL Safari]**.
1. **サイト越えトラッキングを防ぐ**&#x200B;を無効化します。
1. **すべての Cookie をブロック**&#x200B;を無効化します。
1. 没入型アプリにログインします。
1. コンテンツを再生します。
1. ポップアップを許可します。

## その他の機能強化

### MS Teams でのインスタンスの切り替え

学習者は、完了するまで別のコースインスタンスに切り替えて、コースの進行状況を保持することができます。

### MS Teamsでの複数登録のサポート

学習者は、以前のインスタンスの完了ステータスに関係なく、別のコースインスタンスに登録できます。 そうすることにより、学習者は同じコースの複数のインスタンスに登録できます。

### MS Teams での複数登録をサポートするコースメモ

コースメモは、複数登録をサポートするためにコースインスタンスレベルで利用できます。

## API の変更

API の変更について詳しくは、[Adobe Learning Manager API のリファレンス](https://captivateprime.adobe.com/docs/primeapi/v2/)を参照してください。

### 新しい推奨事項のAPIサポート

**GET/アカウント**

prlRecommendation が有効な場合に返されます。

**リクエスト**

`https://learningmanagerstage1.adobe.com/primeapi/v2/account`

**GET /data?filter.recommendationCriteria=product**

製品 / トピックのリストを返します。 結果はアカウント設定によって異なり、学習者に対してすべての製品が表示されるか、製品 / トピックに対してカタログが表示されます。

**リクエスト**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=product&filter.showAllRecommenda`

**`GET /data?filter.recommendationCriteria=role`**

推奨される役割のリストを返します。

**リクエスト**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=role&filter.showAllRecommendationCriteria=false`

**`GET /data?filter.recommendationCriteria=level`**

推奨される役割のリストを返します。

**リクエスト**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=level&filter.showAllRecommendationCriteria=false`

**POST /search/query**

検索には、クエリの製品と役割のパラメータも含まれます。 クエリと本文に変更はありません。 新しい並べ替えオプションを追加します

**リクエスト**

`https://learningmanagerstage1.adobe.com/primeapi/v2/search/query?...`

**GET /learningObjects**

PRL 推奨事項が公開されている場合、学習目標モデルは、作成者タグ付きの推奨事項を返します。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects?sort=recommendationScore&filter.recommendationProducts=...&filter.recommendationRoles=...&filter.excludeIgnoredRecommendations=true`

POST /learningObjects/query

クエリ呼び出しの本文では、次の属性がサポートされています。

```javascript {line-numbers="true"}
{
  "filter.announcedGroups": [
    "string"
  ],
  "filter.bookmarks": true,
  "filter.catalogIds": [
    "string"
  ],
  "filter.cityName": [
    "string"
  ],
  "filter.duration.range": [
    "string"
  ],
  "filter.effectiveModifiedDate.fromDate": "string",
  "filter.effectiveModifiedDate.toDate": "string",
  "filter.excludeIgnoredRecommendations": true,
  "filter.ignoreEnhancedLP": true,
  "filter.ignoreHigherOrderLOEnrollment": true,
  "filter.lang.subLOs": true,
  "filter.lang.twoLetterCode": true,
  "filter.learnerState": [
    "string"
  ],
  "filter.loFormat": [
    "string"
  ],
  "filter.loTypes": [
    "string"
  ],
  "filter.price": "string",
  "filter.priceRange": [
    "string"
  ],
  "filter.recommendationLevels": [
    "string"
  ],
  "filter.skill.level": [
    "string"
  ],
  "filter.skillName": [
    "string"
  ],
  "filter.tagName": [
    "string"
  ],
  "language": [
    "string"
  ],
  "preferredSortPartitionOrder": [
    "string"
  ],
  "showLoContentSource": true,
  "useCache": true,
  "filter.recommendationProducts": [
    {
      "levels": [
        "string"
      ],
      "name": "string"
    }
  ],
  "filter.recommendationRoles": [
    {
      "levels": [
        "string"
      ],
      "name": "string"
    }
  ]
}
```

**GET /recommendationProducts**

recommendationProduct Id で PRL 製品を取得します。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationProducts`

GET /recommendationRoles

recommendationProduct Id で PRL 製品を取得します。 （学習目標）の表示可能な役割のみが返されます。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/prlRecommendations/roles`

`POST /users/{id}/recommendationPreferences`

PRL 推奨設定を作成 / 再作成（上書き）します。 サンプルペイロード：

```javascript {line-numbers="true"}
{
    "data": {
        "id": "userRecommendationPreferences:14755328",
        "type": "userRecommendationPreferences",
        "attributes": {
            "products": [
                {
                    "id": "recommendationProduct:1",
                    "dateCreated": "2023-05-07T20:00:00.000Z"
                },
                {
                    "id": "recommendationProduct:37",
                    "dateCreated": "2023-05-07T21:00:00.000Z"
                }
            ],
            "roles": [
                {
                    "id": "recommendationRole:23",
                    "dateCreated": "2023-05-07'T'21:00:00.000'Z'"
                },
                {
                    "id": "recommendationRole:1",
                    "dateCreated": "2023-05-07'T'20:01:00.000'Z'"
                },
                {
                    "id": "recommendationRole:2",
                    "dateCreated": "2023-05-07'T'19:02:00.000'Z'"
                },
                 {
                    "id": "recommendationRole:3",
                    "dateCreated": "2023-05-07'T'18:02:00.000'Z'"
                },
                {
                    "id": "recommendationRole:20",
                    "dateCreated": "2023-05-07'T'17:02:00.000'Z'",
                    "levels": [
                        "INTERMEDIATE"
                    ]
                }
            ]
        }
    }
}
```

**`GET /users/{id}/recommendationPreferences`**

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2//users/123/recommendationPreferences`

**`DELETE /users/{id}/recommendationPreferences`**

製品または役割の PRL 推奨ユーザー設定を削除します。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/users/123/recommendationPreferences?ids=recommendationRole:123,recommendationRole:234`

パラメーター：

Ids = 削除する ID のリスト

**PATCH /users/{id}/recommendationPreferences**

部分的な追加 / 更新。 サンプルペイロード：

```javascript {line-numbers="true"}
{
  "data": {
    "id": "userRecommendationPreferences:<USER_ID>",
    "type": "userRecommendationPreferences",
    "attributes": {
      "roles": [
        {
          "id": "recommendationRole:123",
          "type": "recommendationRole",
          "attributes": {
            "levels": [
              "INTERMEDIATE"
            ]
          }
        },
        {
          "id": "recommendationRole:123",
          "type": "recommendationRole",
          "attributes": {
            "levels": [
              "ADVANCED"
            ]
          }
        }
      ]
    }
  }
}
```

**POST /recommendationPreferences/learningObjects/{id}/ignore**

ブロックされた推奨事項に LO を追加します。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationPreferences/learningObjects/{id}/ignored`

**`DELETE /recommendationPreferences/learningObjects/{id}/ignore`**

ブロックされた推奨事項から LO を削除します。

**URLを要求**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationPreferences/learningObjects/{id}/ignored`

**`GET /users/{id}/recommendationStrips`**

prl 推奨事項の表示に使用するすべてのストリップを取得します

### APIの複数登録のサポート

**GET /primeapi/v2/account**

次の 2 つの新しい属性が追加されました。

* instanceSwitchEnabled
* multiEnrollmentEnabled

**GET /users/{userId}/userNotifications**

新しいメタデータ属性の通知に、コースインスタンス ID が追加されました。

**GET /learningObjects**

登録関係には、プライマリ登録（例：最初に登録済みまたは最初に完了済み）のみが表示されます。

**`GET /learningObjects/{id}`**

登録関係には、プライマリ登録（例：最初に登録済みまたは最初に完了済み）のみが表示されます。

**`GET /learningObjects/{loId}/instances/{loInstanceId}`**

新しい関係が LO インスタンスモデルに追加されます。

**`GET /enrollments/{id}`**

複数登録したコースの登録を取得します。

**`DELETE /enrollments/{id}`**

特定の学習目標インスタンスから登録解除します。

**POST/登録**

様々なインスタンスの登録をサポートします。

**GET/登録**

学習目標のプライマリ登録のみの登録を取得します。

**`GET /learningObjects/{id}/note`**

コースのメモのリストを取得します。

**`GET /learningObjects/{lo_id}/instances/{loi_id}/note`**

インスタンスおよびコースのメモのリストを取得します。

**`GET /learningObjects/{id}/resources/{loResourceId}/note`**

コース内のリソースのメモのリストを取得します。

**`POST /learningObjects/{id}/resources/{loResourceId}/note`**

特定のコースにおけるコースのモジュールにメモを追加します。

**`DELETE /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

特定のインスタンス（loResource Id の一部）に対する特定のモジュールから特定のメモを削除します。

**`GET /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

特定のインスタンス（loResourceId の一部）について、コース内のモジュールにある特定のメモを取得します。

**`PATCH /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

特定のインスタンス（loResource Id の一部）に対する特定のモジュールにある特定のメモを更新します。

**管理者APIの変更**

* GET /users/{id}/enrollments
* POST /users/{id}/enrollments
* DELETE /users/{id}/enrollments/{enrollmentId}
* PATCH /users/{id}/enrollments/{enrollmentId}

### エンドポイントのEnforcedfields

製品と役割は、強制的な場合のみ読み込まれます。

リクエストの例

* GET `https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects/course%3A7418798?enforcedFields[learningObject]=products`
* GET `https://learningmanagerstage1.adobe.com/primeapi/v2/users/11255638/userBadges?include=model&page[offset]=0&page[limit]=10&sort=dateAchieved&enforcedFields[learningObject]=products,roles`

### 実装に基づく検索APIの変更（英語ロケール）

語幹検索とは、単語を語幹形に変換する処理のことです。 これにより、検索時に用いる単語の活用形を一致させることができます。 例えば、「歩く」と「歩く」は同じ語根の単語である「歩く」と語根を変えることができます。 語幹検索では、どちらかの単語の出現箇所は他方の単語と一致します。

このリリースでは、英語のロケール用の語幹検索が追加されました。これには、en_US、en_AU、en_GBのバリエーションが含まれています。

stemmed 属性は、検索結果にステミングが必要かどうかを指定します。 デフォルトではFalseに設定されています

### V1 エンドポイントの削除

このリリースでは、V1 API は動作しなくなります。 詳しくは、[「デベロッパーマニュアル」](/help/migrated/integration-admin/feature-summary/developer-manual.md)を参照してください。

### コース登録または登録解除の通知

このリリースでは、新しいメタデータ属性に通知を使用したコースインスタンスIDのサポートが導入されました。

### L1フィードバックのサポート

学習者は、複数登録機能の各インスタンスレベルでフィードバックを提供できます。

**API:** `POST /enrollments/{id}/l1Feedback`

### LO 強制フィールドリスト

このリリースでは、section、prequisiteConstraints、prerequisiteLO、subLOs、supplementaryResources、supplementaryLOs、instances、catalogLabelsをlearningObjectに明示的に送信する必要があります。

以下に例を挙げます。

`enforcedFields[learningObject]=prerequisiteLOs,instances`

### 次のリリースの廃止通知

* 学習者 API の上書きフラグ。
* デフォルトを highlightResults=false に変更します。 また、snippetType=courseNameのデフォルトを変更します。
* 検索エンドポイントではmatchType=boolを廃止します。
* autoCompleteModeには [非推奨] タグを使用してautoCompleteMode =falseと同じ機能を提供するために、MatchというmatchTypeが追加されました。

### 複数登録でのバッジID形式

複数登録インスタンスバッジをサポートするために、コースバッジの形式を `userId_badgeId_COURSE_courseId to userId_badgeId_COURSE_courseId_courseInstanceId` バッジを一意に識別できます。

## リリースノート

Learning Manager Webアプリとデバイスアプリの現在および以前のリリースについて詳しくは、 [リリースノート](/help/migrated/release-note/release-notes.md).

## このリリースの既知の問題または制限事項

このリリースの制限事項は次のとおりです。

### モバイルアプリでのコンテンツのオフライン表示

アプリでコンテンツをオフライン表示している場合、次の要素には対応していません。

* Flex コース、学習プランまたは資格認定。
* 拡張コース、学習プラン、または資格認定。
* マルチクイズが有効になっているコース、学習プランまたは資格認定。
* Harvard Mentor、コンテンツマーケットプレイス、GetAbstract、またはLinkedInコース、学習プラン、または資格認定を管理します。
* 前提条件が有効になっている学習プランおよび資格認定。
* 廃止済みコース、学習プランまたは資格認定。
* 有効期限が切れているコース、学習プラン、または資格認定。
* 外部の資格認定。
* eコマース対応コース、学習プラン、または資格認定。

次の学習パス、コース、資格認定でオフライン同期を実施すると、いくつかのエラーが発生します。

* 学習パスすべて。
* 内部の資格認定すべて。
* POST 呼び出しを伴うコンテンツ。

### 推奨事項

次の要素は、新しい推奨システムでの製品 / 役割 / レベルに対応していません。

* Adobe Experience Manager、Teams、SFDC およびログインなし。
* モバイルアプリでは、推奨ページでの製品と役割の編集はサポｰﾄ対象外。
* 移行中はマッピング不可能。
* linkedIn、コンテンツマーケットプレイス、その他の外部コース、学習プラン、資格認定の自動タグ付け
* 本番環境移行後にスキルベースまたはクラシックに戻すこと。
* 学習者アプリの製品と役割の検索メニュー。
* 管理者アプリでコース、学習プラン、または資格認定、およびユーザーを一括マッピング

## 必要システム構成

[Learning Manager の必要システム構成](/help/migrated/system-requirements.md)
