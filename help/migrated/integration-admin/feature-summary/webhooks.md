---
jcr-language: en_us
title: Webhooks
description: コースの登録、コースの作成などの情報をリアルタイムで特定のURLに送信するためのWebhookについて説明します
contentowner: chandrum
source-git-commit: e4b0526e11083d116bf4ca4b0816892e0e8f0f9d
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 1%

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

## リアルタイムイベント

| S.No | Webhookイベント | 説明 |
|---|---|---|
| 1 | CI_STATS | コースインスタンスの空席またはキャンセル待ちの有無に変更があった場合にトリガーされます。 |
| 2 | COURSE_ENROLLMENT | 学習者がコースに登録するとトリガーされます。 |
| 3 | COURSE_COMPLETED | 学習者がコースを完了するとトリガーされます。 |
| 4 | LEARNING_PATH_ENROLLMENT | 学習者が学習パスに登録するとトリガーされます。 |
| 5 | LEARNING_PATH_COMPLETE | 学習者が学習パスを完了するとトリガーされます。 |
| 6 | CERTIFICATION_ENROLLMENT | 学習者が資格認定に登録するとトリガーされます。 |
| 7 | CERTIFICATION_COMPLETED | 学習者が資格認定を完了するとトリガーされます。 |
| 8 | COURSE_UNENROLLMENT | 学習者がコースから登録解除するとトリガーされます。 |
| 9 | LEARNING_PATH_UNENROLLMENT | 学習者が学習パスから登録解除するとトリガーされます。 |
| 10 | CERTIFICATION_UNENROLLMENT | 学習者が資格認定から登録解除するとトリガーされます。 |
| 11 | LEARNING_OBJECT_DRAFT | ドラフト状態の学習オブジェクトの作成中にトリガーされます。 |
| 12 | LEARNING_OBJECT_DELETION | 学習目標の削除中にトリガーされます。 |
| 13 | LEARNING_OBJECT_MODIFICATION | 学習目標の変更時にトリガーされます。 |
| 14 | LEARNING_OBJECT_INSTANCE_MODIFICATION | 学習目標インスタンスの作成時または変更時にトリガーされます。<div><b>注意：</b>コースの公開後にのみコースインスタンスを使用することをお勧めします。</div> |
| 15 | LEARNING_OBJECT_INSTANCE_DELETION | 学習オブジェクトインスタンスの削除中にトリガーされます。 |

## 非リアルタイムイベント

| S.No | Webhookイベント | 説明 |
|---|---|---|
| 1 | COURSE_ENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームが学習者をコースに登録するとトリガーされます。 |
| 2 | COURSE_COMPLETED_BATCH | 管理者/マネージャー/プラットフォームがコースを完了としてマークするとトリガーされます。 |
| 3 | LEARNING_PATH_ENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームが学習パスに学習者を登録するとトリガーされます。 |
| 4 | LEARNING_PATH_COMPLETED_BATCH | 管理者/マネージャーが学習パスを完了とマークするとトリガーされます。 |
| 5 | CERTIFICATION_ENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームが学習者を資格認定に登録するとトリガーされます。 |
| 6 | CERTIFICATION_COMPLETED_BATCH | 管理者/マネージャー/プラットフォームが資格認定を完了としてマークしたときにトリガーされます。 |
| 7 | LEARNER_PROGRESS | モジュールが完了したときの学習者の進行状況を追跡します。 |
| 8 | COURSE_UNENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームがコースから学習者を登録解除するとトリガーされます。 |
| 9 | LEARNING_PATH_UNENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームが学習パスから学習者を登録解除するとトリガーされます。 |
| 10 | CERTIFICATION_UNENROLLMENT_BATCH | 管理者/マネージャー/プラットフォームが資格認定から学習者を登録解除するとトリガーされます。 |
| 11 | LEARNING_OBJECT_MODIFICATION_BATCH | 移行ワークフローを介した学習目標の変更中にトリガーされます。 |
| 12 | LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH | 移行ワークフローを介した学習オブジェクトインスタンスの作成または変更中にトリガーされます。 |

## Webhookのベストプラクティス

Webhookにより、サービス間でリアルタイムのイベント駆動型通信が可能になります。 ただし、不適切な実装は、イベントの損失、システムパフォーマンスの低下、またはセキュリティリスクを引き起こす可能性があります。 以下は、フォールトトレランス、信頼性、およびセキュリティに重点を置いた、Webhookを実装するためのベストプラクティスです。

### フォールトトレランス

ALM Webhookシステムのフォールトトレラントは、サブスクライバーがイベントの損失、重複イベント、順不同の配信などの潜在的な問題を処理するための推奨事項を提供します。

ALMでは、接続タイムアウトが10秒に、ソケットタイムアウトが5秒に設定されています。 クライアントは、メッセージを受信するとすぐに確認することを想定しています。 これは、メッセージの処理中にクライアントの遅延が発生しないようにするためです。 時間のかかるダウンストリーム処理がある場合でも、クライアントは即座にイベントを確認し、最後にダウンストリーム処理を処理する必要があります。

#### データの保持

イベントは7日間開催されます。 この時間内に処理されなかった場合、それらは永久に失われます。 最終日にリカバリが行われ、より多くの時間が必要になった場合、システムは保存期間を延長しません。
消費されるよりも早くイベントが生成されると、一部のイベントが失われる可能性があります。 これは一般的ではありませんが、長期的問題にならないように監視する必要があります。

#### Webhookを無効にする

加入者がwebhookイベントに応答できない場合、ALMシステムは指数バックオフを使用してwebhookを再試行し、加入者を圧倒するのを防ぎます。

再試行プロセスは、5秒の初期間隔で開始されます。 サブスクライバーが応答しない場合、待ち時間が10秒、20秒、40秒と80秒の2倍になり、最終的には最大5分に増えます。 5分に達すると、7日間の保持期間が終了するまで、システムは5分ごとに再試行を続けます。 サブスクライバーがこの期間内にまだ応答しない場合、webhookは自動的に無効になります。 リマインダーメールは定期的にサブスクライバーに送信されます。

#### イベントの複製

サブスクライバーがイベントの処理後に応答に5秒以上かかる場合、システムは同じイベントの処理を再試行する可能性があります。 処理済みのイベントを追跡するために、イベントIDを使用することをお勧めします。 また、イベントを送信した後、処理されたことを保存する前にwebhookがクラッシュした場合、同じグループのイベントが再試行されることがあります。 重複を認識して無視するには、バッチIDまたは個々のイベントIDを使用することをお勧めします。

#### 順不同イベント

ALMでは、イベントを正しい順序に維持しようとしますが、特にリアルタイムイベントと非リアルタイムイベントの間で、イベントが順番どおりに配信されない場合があります。

管理者が一度に複数の学習者をコースに登録する場合、登録イベントは非リアルタイムとしてマークされます。 ただし、学習者がコースをすばやく完了すると、完了イベントがリアルタイムとしてマークされ、登録イベントの前に配信される場合があります。

#### フォールトトレランスの推奨事項

これらの障害を防ぐために、サブスクライバーはwebhookイベントをアクティブに監視し、イベントの欠落、配信の重複、順序が正しくないシーケンスなどの問題に対するアラートを設定する必要があります。

## Webhookイベントに固有のガイドライン

1. 最初にLEARNER_PROGRESSイベントが発生した場合は、以下のイベントを無視します。

   * COURSE_ENROLLMENT
   * COURSE_ENROLLMENT_BATCH
   * LEARNING_PATH_ENROLLMENT
   * LEARNING_PATH_ENROLLMENT_BATCH
   * CERTIFICATION_ENROLLMENT
   * CERTIFICATION_ENROLLMENT_BATCH

2. LEARNER_PROGRESSイベントが次のイベントの後にある場合は無視します。

   * COURSE_COMPLETED
   * COURSE_COMPLETED_BATCH
   * LEARNING_PATH_COMPLETE
   * LEARNING_PATH_COMPLETED_BATCH
   * CERTIFICATION_COMPLETED
   * CERTIFICATION_COMPLETED_BATCH

3. タイムスタンプフィールドを使用して、LEARNER_PROGRESSイベントを除いて、イベントを無視するか処理するかを指定します。


## イベントのサンプルペイロード

+++CI_STATS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "01234567-0458-4450-b5dd-6bc1edr4560",
      "eventName": "CI_STATS",
      "timestamp": 1725604147,
      "eventInfo": "1725604145-LoSt",
      "data": {
        "loInstanceId": "course:1234567_123456775",
        "waitlistCount": 0,
        "enrollmentCount": 10,
        "seatLimit": 30
      }
    }
  ]
}
```

+++

+++COURSE_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "29123ec1-4576-4ec5-a057-3a6dr45t9d6",
      "eventName": "COURSE_ENROLLMENT",
      "timestamp": 1725524713,
      "eventInfo": "1725524713000-040366-10488-0",
      "data": {
        "userId": 1234567,
        "loId": "course:1234567",
        "loInstanceId": "course:1234567_1234567",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": 1725524713
      }
    }
  ]
  }
```

+++

+++COURSE_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "29572ec1-4576-4ec5-a057-3wsd43r59d6",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": 1725524713,
      "eventInfo": "1725524713000-040366-10488-0",
      "data": {
        "userId": 1234567,
        "loId": "course:1234567",
        "loInstanceId": "course:12345678_123456788",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1725524713
      }
    }
  ]
  }
```

+++

+++COURSE_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c1a3168c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED",
      "timestamp": 1725523823,
      "eventInfo": "1725523823000-040363-12018-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345671",
        "loInstanceId": "course:1234567_12345674",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": 1725523818,
        "hasPassed": true
      }
    }
  ]
}
```

+++

+++COURSE_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c1a3168c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED_BATCH",
      "timestamp": 1725523823,
      "eventInfo": "1725523823000-040363-12018-0",
      "data": {
        "userId": 112345678,
        "loId": "course:12345678",
        "loInstanceId": "course:1234567_12345678",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": 1725523818,
        "hasPassed": true
      }
    }
  ]
}
```

+++

+++LEARNING_PATH_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "96ed0791-338f-4c4c-83bc-9fwfr4564965",
      "eventName": "LEARNING_PATH_ENROLLMENT",
      "timestamp": 1725604249,
      "eventInfo": "1725604248000-040653-71396-0",
      "data": {
        "userId": 11234567,
        "loId": "learningProgram:123456",
        "loInstanceId": "learningProgram:12345_134567",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": 1725604248
      }
    }
  ]
}
```

+++

+++LEARNING_PATH_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "96edft791-338f-4c4c-83bc-9f7erf94965",
      "eventName": "LEARNING_PATH_ENROLLMENT",
      "timestamp": 1725604249,
      "eventInfo": "1725604248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:12347",
        "loInstanceId": "learningProgram:12345_12345",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1725604248
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "e207104e-d554-4027-944b-08fty6fdddf",
      "eventName": "LEARNING_PATH_COMPLETED",
      "timestamp": 1725604392,
      "eventInfo": "1725604391000-040653-314618-0",
      "data": {
        "userId": 11080928,
        "loId": "learningProgram:12345",
        "loInstanceId": "learningProgram:12345_95662",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": 1725604380,
        "hasPassed": true
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "e207104e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED",
      "timestamp": 1725604392,
      "eventInfo": "1725604391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:12345",
        "loInstanceId": "learningProgram:12345_95662",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": 1725604380,
        "hasPassed": true
      }
    } 
    ]
    }
```

+++

+++CERTIFICATION_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8bdfr76-148e-4128-80e9-b89123456755",
      "eventName": "CERTIFICATION_ENROLLMENT",
      "timestamp": 1725604672,
      "eventInfo": "1725604672000-040654-559128-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:1234567",
        "loInstanceId": "certification:123456_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": 1725604672
      }
    }
  ]
}
```

+++

+++CERTIFICATION_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8b2ee776-148e-4128-80e9-12345678",
      "eventName": "CERTIFICATION_ENROLLMENT_BATCH",
      "timestamp": 1725604672,
      "eventInfo": "1725604672000-040654-559128-0",
      "data": {
        "userId": 123456788,
        "loId": "certification:1234567",
        "loInstanceId": "certification:12345678_160299",
        "loType": "certification",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1725604672
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "b8b63bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED",
      "timestamp": 1725604769,
      "eventInfo": "1725604768000-040654-756257-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:1245678",
        "loInstanceId": "certification:1234567_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": 1725604740
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "b8b63bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED_BATCH",
      "timestamp": 1725604769,
      "eventInfo": "1725604768000-040654-756257-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:134567",
        "loInstanceId": "certification:1234567_160299",
        "loType": "certification",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": 1725604740
      }
    }
  ]
  }
```

+++

+++LEARNER_PROGRESS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "dd04d3a4-c3df-44fa-a1cf-7edd6e3d2075",
      "eventName": "LEARNER_PROGRESS",
      "timestamp": 1725604552,
      "eventInfo": "1725604551000-297002-5823-0",
      "data": {
        "loId": "course:7542090",
        "loType": "course",
        "userId": 12345678,
        "loInstanceId": "course:1234567_11234567",
        "dateStarted": 1725604380,
        "progressPercent": 50
      }
}
]
}
```

+++

+++COURSE_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f3417817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT",
      "timestamp": 1725515824,
      "eventInfo": "1725506253000-040298-24078-0",
      "data": {
        "userId": 12345671,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
      }
    }
  ]
}
```

+++

+++COURSE_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f3417817-8cb8-40ea-a441-8123e45724",
      "eventName": "COURSE_UNENROLLMENT_BATCH",
      "timestamp": 1725515824,
      "eventInfo": "1725506253000-040298-24078-0",
      "data": {
        "userId": 123456781,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL"
    }
   }
  ]
}
```

+++

+++LEARNING_PATH_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8e5df878-1dfd-47ac-9bfe-7d123456d1",
      "eventName": "LEARNING_PATH_UNENROLLMENT",
      "timestamp": 1725516573,
      "eventInfo": "1725506667000-040299-28209-0",
      "data": {
        "userId": 12345678,
        "loId": "learning_program:1234567",
        "loInstanceId": "learning_program:1234567_109139",
        "loType": "learning_program",
        "enrollmentSource": "SELF_ENROLL",
       
      }
    }
]
}
```

+++

+++LEARNING_PATH_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8e5df878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT",
      "timestamp": 1725516573,
      "eventInfo": "1725506667000-040299-28209-0",
      "data": {
        "userId": 1234567,
        "loId": "learning_program:1234567",
        "loInstanceId": "learning_program:1234567_109139",
        "loType": "learning_program",
        "enrollmentSource": "ADMIN_ENROLL"
      }
    }
]
}
```

+++

+++CERTIFICATION_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7902766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT",
      "timestamp": 1725517341,
      "eventInfo": "1725507900000-040304-1065-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:1234567",
        "loInstanceId": "certification:12345678_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++CERTIFICATION_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7902766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT_BATCH",
      "timestamp": 1725517341,
      "eventInfo": "1725507900000-040304-1065-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:1234567",
        "loInstanceId": "certification:1234567_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DRAFT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1712349f-26ec-453c-b56a-cdf18a841948",
      "eventName": "LEARNING_OBJECT_DRAFT",
      "timestamp": 1725519188,
      "eventInfo": "1725519188000-040344-48604-0",
      "data": {
        "loId": "course:12345671",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "023456-5517-4c09-9cde-d953cdd8582c",
      "eventName": "LEARNING_OBJECT_DELETION",
      "timestamp": 1725605296,
      "eventInfo": "1234567800-040656-662792-0",
      "data": {
        "loId": "course:1234567",
        "loType": "course"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "22345668-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION_BATCH",
      "timestamp": 1725523081,
      "eventInfo": "123456000-039736-54153-0",
      "data": {
        "loId": "learningProgram:1234567",
        "loType": "learningProgram"

      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "2234567068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION_BATCH",
      "timestamp": 1725523081,
      "eventInfo": "123456700-039736-54153-0",
      "data": {
        "loId": "learningProgram:1234567",
        "loType": "learningProgram"

      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "b131da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION",
      "timestamp": 1725603298,
      "eventInfo": "1723456000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12345678_14453691",
        "loId": "course:12345678",
        "loType": "course"
        
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "b23458-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH",
      "timestamp": 1725603298,
      "eventInfo": "112345000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12345678_14453691",
        "loId": "course:1234568",
        "loType": "course"

      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234560-d73a-457b-83f3-666ba9654edb",
      "eventName": "LEARNING_OBJECT_INSTANCE_DELETION",
      "timestamp": 1725605491,
      "eventInfo": "17223456700-040657-236307-0",
      "data": {
        "loInstanceId": "course:1234567_14453849",
        "loId": "course:1234567",
        "loType": "course"

      }
    }
  ]
}
```

+++

