---
jcr-language: en_us
title: Webhooks
description: コースの登録、コースの作成などの情報をリアルタイムで特定のURLに送信するためのWebhookについて説明します
contentowner: chandrum
exl-id: 472aaf2b-9c2f-4f43-a791-2b2d81e69471
source-git-commit: 3b35c16d74c83329cee24ee9ad007a53ccbd8cf3
workflow-type: tm+mt
source-wordcount: '1633'
ht-degree: 0%

---

# Webhooks

Webhookを使用すると、特定のイベントが発生したときに、1つのエンティティから別のエンティティにリアルタイムのデータまたは通知を自動的に送信できます。 これにより、アプリケーションは常に情報を要求することなく、他のアプリケーションに情報を提供することができます。 例えば、ユーザーが学習管理システム(LMS)コースを完了すると、webhookはその情報をCRMやレポートツールなどの別のプラットフォームに自動的に送信できます。 Webhookは、プロセスを自動化し、システム間の手動アップデートの必要性を減らすために、統合でよく使用されます。 データの送信先となるコールバックURLを指定して、webhookを設定します。

## WebhookとAPIの比較

WebhookとAPIはどちらもシステムが相互に通信するのに役立ちますが、動作の方法は異なります。 APIを使用すると、ユーザーが要求した場合にのみ情報が共有されます。 例えば、学習者がコースの進捗状況に関するデータを必要とする場合、学習者はAPIにリクエストを送信し、APIがその情報を提供します。 一方、Webhookでは、イベントが発生するとすぐにデータが自動的に送信されます。 例えば、学習者がコースを完了すると、手動リクエストなしでデータがリスナーURLにすぐに送信されます。

## リアルタイムAPIとは

リアルタイムAPIを使用すると、イベントが発生したときにアプリケーションでデータを即座に交換できます。 ユーザーが情報を要求するのを待つ従来のAPIとは異なり、リアルタイムAPIはデータが発生した時点でデータを共有します。 WebhookはリアルタイムAPIとして機能し、指定されたイベントが発生するとすぐにデータを共有できます。 リアルタイムAPIにより、手動リクエストを行うことなく、このデータ転送が即座に行われるため、システムが即座に更新されます。

## Webhookイベント

Webhookイベントは、リスナーURLにデータを自動的に送信するシステムで発生する特定のアクションです。 例えば、学習者がコースに登録すると、webhookイベントがトリガーされ、登録の詳細がリスナーURLに送信されます。

Webhookイベントは、次の2つのカテゴリに分類されます。

* **リアルタイムイベント**:イベントはリアルタイムで処理され、ターゲットURLに送信されます
* **非リアルタイムイベント**:イベントはバッチで処理され、リアルタイムではなく指定された時間に送信されます

## リスナーURL

リスナーURLは、イベントが発生したときにデータ情報を受信するエンドポイントまたは宛先です。 コースへのユーザー登録など、特定のイベントが発生すると、システムは手動で要求することなく、このURLに詳細を自動的に送信します。 リスナーURLは、これらすべてのアップデートが配信されるアドレスです。
Webhookは、関連する情報をJSON形式で送信します。 Adobe Learning Managerでトリガーされるイベントのペイロードの例を次に示します。

```
{
  "accountId": 1010,
  "events": [
    {
      "eventId": "d5fb7071-10a9-46b2-9f9e-79dde346c052",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": 1727414643000,
      "eventInfo": "1727414643000-047210-84242-0",
      "data": {
        "userId": 4279332,
        "loId": "course:7374992",
        "loInstanceId": "course:7376092_10250977",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1727414643
      }
    }
  ]
}
```

## Webhookの作成と管理 – 統合管理者

Adobe Learning ManagerでWebhook統合を作成するには、次の手順を実行します。

1. **[!UICONTROL 統合管理者]**&#x200B;としてログインします。
2. ホームページで、**[!UICONTROL Webhook]**/**[!UICONTROL Webhookを追加]**&#x200B;を選択します。

   ![](assets/create-webhook.png)
   _Webhookを追加_

3. Webhookの&#x200B;**[!UICONTROL 名前]**&#x200B;と&#x200B;**[!UICONTROL 説明]**&#x200B;を入力します。
4. イベントデータを渡すリスナーURLを&#x200B;**[!UICONTROL ターゲットURL]**&#x200B;として入力します。
5. 次のいずれかの認証方法を選択します。
Webhooksの認証は、リスナーURLに送信されるデータが信頼できるソースから来ていることを確認するためのセキュリティ方法です。
   * **[!UICONTROL なし]**：認証は不要です。
   * **[!UICONTROL 基本]**：これは資格情報ベースの認証です。 ユーザー名とパスワードを入力します。
   * **[!UICONTROL 署名]**:システムは特別な署名を作成し、Webhookデータに追加します。 受信側のサーバーはこのコードをチェックして、データが実際のものであり、変更されていないことを確認します。 署名を生成し、認証に使用します。 署名をJSONとしてダウンロードします。
6. **[!UICONTROL トリガーイベント]**&#x200B;ドロップダウンからWebhookイベントを選択します。

   >[!NOTE]
   >
   >「 Webhookを追加」ページから「 Webhookをテスト」オプションを選択して、webhookをテストすることもできます。

7. **[!UICONTROL アクティベーションステータス]**&#x200B;の切り替えを選択して、Webhookを有効にします。 有効にすると、選択したイベントが発生するたびにデータが渡されます。

>[!NOTE]
>
>最大5つのWebhookを作成および管理できます。

### Webhookを編集 – 統合管理者

Adobe Learning ManagerからWebhookを編集するには、次の手順に従います。

1. **[!UICONTROL 統合管理者]**&#x200B;としてログインします。
2. ホームページで&#x200B;**[!UICONTROL Webhook]**&#x200B;を選択します。
3. 編集するwebhookを選択します。

   ![](assets/edit-webhook.png)
   _Webhookを編集_
4. 「**[!UICONTROL 編集]**」を選択してwebhookの詳細を変更し、「**[!UICONTROL 保存]**」を選択します。

### Webhookを削除 – 統合管理者

Adobe Learning ManagerからWebhookを編集するには、次の手順に従います。

1. **[!UICONTROL 統合管理者]**&#x200B;としてログインします。
2. ホームページで&#x200B;**[!UICONTROL Webhook]**&#x200B;を選択します。
3. 削除するwebhookを選択します。
4. Webhookを削除するには、**[!UICONTROL 削除]**&#x200B;を選択します。

![](assets/delete-webhooks.png)
_Webhookを削除_

### Webhookの廃止 – 統合管理者

Webhookを廃止するには、次の手順に従います。

1. **[!UICONTROL 統合管理者]**&#x200B;としてログインします。
2. ホームページで&#x200B;**[!UICONTROL Webhook]**&#x200B;を選択します。
3. 編集するwebhookを選択します。
4. **[!UICONTROL 編集]**&#x200B;を選択し、**[!UICONTROL アクティベーションステータス]**&#x200B;を無効にして、Webhookを廃止します。

![](assets/retire-webhook.png)
_Webhookを廃止_

## 代替用のWebhook {#webhooks-for-alternates}

ALMは、代替完了用の専用のwebhookイベントを提供して、自動化、統合、外部システムとの同期をサポートします。

これらのイベントにより、外部のコンシューマーは、別の関係を介して付与された直接完了と完了を確実に区別できます。

### 概要

学習者が代替または関係を介してコースを完了すると、ALMは、標準のコース完了webhookとは別にwebhookイベントをトリガーします。 これにより、必要に応じて別の完了に対して統合が異なる応答を返すことができます。

また、Webhookイベントは、遡及的な完了または遡及的な未完了が発生した場合にもトリガーされ、履歴更新と関係の変更が対象となります。

### Webhookイベントの動作

* 個別のwebhookイベントは、学習者がターゲットコースの代替ステータスを介して「完了」を受信した場合にトリガーされます。
* このイベントは、学習者が代替関係を通じてターゲットを満たす設定されたソースコースを完了したときに生成されます。
* このWebhookは、直接コースの完了にはトリガーされません。
* 「遡及完了」または「遡及未完了」が有効になっている場合は、影響を受ける学習者およびターゲット・コースごとにWebhookイベントが発行されます。

### Webhookペイロードの詳細

代替完了Webhookペイロードには、次のキー属性が含まれます。

* **学習者ID**
代替完了を受け取った学習者を識別します。
* **ソースコース**
学習者が直接完了したコースまたは学習パス。
* **対象コース**
代替関係を介して完了とマークされたコース。
* **完了方法**
補完方式が代替であることを示します。
* **完了日**
ソースコースの完了日から取得されます。
* **リレーションシップの種類**
リレーションシップが代替かどうかを指定します。

遡及的完了取消シナリオの場合、webhookイベントは、既存の代替完了が取り消されたことを示します。

### 統合に関する考慮事項

外部システムは、次のWebhookイベントを使用できます。

* 学習者レコードの更新
* 完了ステータスの同期
* 通知またはダウンストリームワークフローのトリガー
* コンプライアンスの目的で監査証跡を維持

Webhookコンシューマーは、直接完了と代替完了を明示的に区別する必要があります。

代替完了では、スキル、バッジ、およびゲーミフィケーション報酬は付与されません。 下流のシステムでは、フィードバックを適切に処理する必要があります。

## アダプティブ学習パスのWebhook

### 概要

Adobe Learning Managerは、**学習パス（学習プログラム）**&#x200B;の完了ステータスが更新されるたびに外部システムに通知する&#x200B;**webhookイベント**&#x200B;を提供します。 これにより、学習者の完了レコードがロールバックまたは再計算されるたびに、下流システム（人事、レポート作成、分析プラットフォームなど）を同期できます。

2つの新しいWebhookイベントタイプを使用できます。

**LEARNING_PATH_COMPLETION_ROLLBACK** - **学習者**&#x200B;が自分の学習パスの完了ステータスを更新するとトリガーされます。

**LEARNING_PATH_COMPLETION_ROLLBACK_BATCH** - **管理者**&#x200B;が&#x200B;**1人以上の学習者**&#x200B;の学習パスの完了ステータスを更新したときにトリガーされます（一括操作など）。

これらのイベントは、**共通のペイロード構造**&#x200B;を使用し、webhookエンドポイントが使用して、サイドで完了データを更新または再処理できます。

### 共通のペイロード構造

各Webhookリクエストには、次のトップレベル構造が含まれています。

```
{
  "accountId": 69735,
  "events": [
    {
      "eventId": "757b9d58-048c-4ae2-9fff-35f9def7ef29",
      "eventName": "LEARNING_PATH_COMPLETION_ROLLBACK",
      "timestamp": "2026-01-20T05:48:10.000Z",
      "eventInfo": "1768888090000-197513-137581-0",
      "data": {
        "userId": 13446697,
        "loId": "learningProgram:157165",
        "loInstanceId": "learningProgram:157165_148769",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2026-01-20T05:44:05.000Z"
      }
    }
  ]
}
```

**同じ構造**&#x200B;は、両方のイベントの種類で使用されます。eventNameとデータ内の値（userId、loId、enrollmentSourceなど）のみが異なります。

#### 例：学習者が開始する更新

学習者が自分の学習パスの完了ステータスを更新すると、WebhookはLEARNING_PATH_COMPLETION_ROLLBACKイベントを送信します。

```
{
  "accountId": 69735,
  "events": [
    {
      "eventId": "757b9d58-048c-4ae2-9fff-35f9def7ef29",
      "eventName": "LEARNING_PATH_COMPLETION_ROLLBACK",
      "timestamp": "2026-01-20T05:48:10.000Z",
      "eventInfo": "1768888090000-197513-137581-0",
      "data": {
        "userId": 13446697,
        "loId": "learningProgram:157165",
        "loInstanceId": "learningProgram:157165_148769",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2026-01-20T05:44:05.000Z"
      }
    }
  ]
}
```

学習者が明示的に更新を要求した場合に、外部システムで&#x200B;**学習者の完了データを再計算またはリセット**&#x200B;するには、このイベントを使用します。

#### 例：管理者が開始するバッチリフレッシュ

管理者が1人以上の学習者の完了の更新（グループの過去の完了数の修正など）を実行すると、WebhookからLEARNING_PATH_COMPLETION_ROLLBACK_BATCHイベントが発生します。

```
{
  "accountId": 69735,
  "events": [
    {
      "eventId": "757b9d58-048c-4ae2-9fff-35f9def7ef29",
      "eventName": "LEARNING_PATH_COMPLETION_ROLLBACK_BATCH",
      "timestamp": "2026-01-20T05:48:10.000Z",
      "eventInfo": "1768888090000-197513-137581-0",
      "data": {
        "userId": 13446698,
        "loId": "learningProgram:157166",
        "loInstanceId": "learningProgram:157166_148770",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2026-01-21T05:44:05.000Z"
      }
    }
  ]
}
```

バッチ操作では、webhookエンドポイントは、完了が更新された学習者ごとに1つ、1つのリクエストで&#x200B;**複数のイベントオブジェクト**&#x200B;を受信する場合があります。 統合では、イベント配列を反復処理し、各イベントを個別に処理する必要があります。

### これらのイベントを統合で使用する方法

これらのwebhookイベントは、次の場合に使用できます。

**完了レコードを外部のLMS/LRS、HR、またはレポートシステムと同期します**&#x200B;完了がロールバックまたは再計算されたとき。

**ダウンストリームワークフローのトリガー** （証明書やバッジの再割り当て、通知、再計算など）。

eventId、タイムスタンプ、eventInfoを、学習者および学習パスIDと共にログに記録することで、**監査証跡を維持**&#x200B;します。

少なくとも、webhookハンドラーは次のことを行う必要があります。

ペイロードを検証し、イベントを解析します[]。
eventNameを使用して、変更が**learnerinitiated**&#x200B;か&#x200B;**admin/batchinitiated**&#x200B;かを特定します。

userId、loId、およびloInstanceIdを使用して、システム内の対応するレコードを検索し、更新します。
同じイベントが複数回配信される場合に、重複した処理を防ぐには、eventIdを使用します。

## ユーザーグループのメンバーシップを追加および削除するためのWebhook

2つの新しいWebhookイベントタイプに最終ステータスが反映されます。

* 応答:ASYNCAPI_USERGROUP_USER_ADDED
* 応答:ASYNCAPI_USERGROUP_USER_REMOVED

### サンプルペイロード

```
{
  "accountId": 69735,
  "events": [
    {
      "eventId": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5",
      "eventName": "RESPONSE:ASYNCAPI_USERGROUP_USER_REMOVED",
      "timestamp": "2026-03-18T13:38:12.000Z",
      "eventInfo": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5",
      "data": {
        "status": "SUCCESS",
        "request": {
          "metadata": { "event_id": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5" },
          "data": [ { "type": "user", "id": "13446641" } ]
        }
      }
    }
  ]
}
```

### 主な要素

* `accountId`はALMアカウントを識別します。
* `events`はイベントオブジェクトの配列です。
* `eventId`は元の非同期要求識別子と一致します。
* `eventName`は追加操作または削除操作を示します。
* `timestamp`は完了時間を表示します。
* `data.status`は現在、成功したバッチの「SUCCESS」を報告しています。
* `data.request`には、送信した正確な要求が含まれています。

統合では、主に`eventId` （または`metadata.event_id`）と`status`をキーオフする必要があります。

### 例

#### ユーザーの非同期追加

**手順1. 非同期呼び出しを行う**

POST/primeapi/v2/async/userGroups/12345/users

```
{
  "metadata": {
    "event_id": "sync-2026-03-30T10:15:00Z-ug-12345",
    "sourceSystem": "HRIS",
    "batchId": "hr_2026_03_30_0001"
  },
  "data": [
    { "type": "user", "id": "11101219" },
    { "type": "user", "id": "11101220" }
  ]
}
```

**手順2. 即時応答を読み取ります**

```
{ "event_id": "sync-2026-03-30T10:15:00Z-ug-12345" }
```

このジョブをシステムで送信済みとしてマークできるようになりました。

**手順3. Webhook**&#x200B;を処理します

Webhookコールバックの例：

```
{
  "accountId": 69735,
  "events": [
    {
      "eventId": "sync-2026-03-30T10:15:00Z-ug-12345",
      "eventName": "RESPONSE:ASYNCAPI_USERGROUP_USER_ADDED",
      "timestamp": "2026-03-30T10:15:43.000Z",
      "data": {
        "status": "SUCCESS",
        "request": {
          "metadata": {
            "event_id": "sync-2026-03-30T10:15:00Z-ug-12345",
            "sourceSystem": "HRIS",
            "batchId": "hr_2026_03_30_0001"
          },
          "data": [
            { "type": "user", "id": "11101219" },
            { "type": "user", "id": "11101220" }
          ]
        }
      }
    }
  ]
}
```

一般的なコンシューマーは次のことを行います。

* 内部ジョブを見つけます。
* オプションで、GET /userGroups/{id}/usersを使用してメンバーシップを確認します。
* ジョブを完了としてマークします。

#### ユーザーの非同期的な削除

同じ身体構造のDELETEを用いて、切除は対称性である。

```
{
  "metadata": {
    "event_id": "sync-2026-03-30T11:00:00Z-ug-12345",
    "sourceSystem": "HRIS",
    "batchId": "hr_2026_03_30_0002"
  },
  "data": [ { "type": "user", "id": "11101219" } ]
}
```

速やかな対応：

```
{ "event_id": "sync-2026-03-30T11:00:00Z-ug-12345" }
```

その後、同じeventIdでRESPONSE:ASYNCAPI_USERGROUP_USER_REMOVED Webhookが受信されます。

詳細については、[ユーザーグループメンバーシップの非同期パブリックAPI](/help/migrated/api-changes-alm.md#asynchronous-public-apis-for-user-group-membership)を参照してください。
