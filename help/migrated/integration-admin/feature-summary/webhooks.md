---
jcr-language: en_us
title: Webhooks
description: コースの登録、コースの作成などの情報をリアルタイムで特定のURLに送信するためのWebhookについて説明します
contentowner: chandrum
exl-id: 472aaf2b-9c2f-4f43-a791-2b2d81e69471
source-git-commit: e4c3489db8207ead0416656161b918eba42f4582
workflow-type: tm+mt
source-wordcount: '765'
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
