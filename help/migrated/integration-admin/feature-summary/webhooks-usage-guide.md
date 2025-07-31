---
jcr-language: en_us
title: Webhook使用ガイド
description: Webhookの使用方法、ベストプラクティス、制限事項について説明します
contentowner: chandrum
exl-id: e6a63ffb-7fdd-46e4-b5e6-20ce36861cef
source-git-commit: 4c04757d78d599ca30e3cd26257a967d5b9e3fdc
workflow-type: tm+mt
source-wordcount: '3369'
ht-degree: 1%

---

# Webhook使用ガイド

Webhookは、webアプリケーションが自動的かつリアルタイムに相互に通信するための方法です。

ユーザーが情報を要求するのを待つ従来のAPIとは異なり、リアルタイムAPIはデータが発生した時点でデータを共有します。 WebhookはリアルタイムAPIとして機能し、指定されたイベントが発生するとすぐにデータを共有できます。

## エンティティ

Webhookイベントを理解するには、まず関与するエンティティと、これらのイベントのトリガー条件を認識する必要があります。

### 学習目標

学習目標（コース、学習パス、資格認定）でサポートされているイベントは次のとおりです。

#### 下書き

UIから学習オブジェクトを作成すると、常に&#x200B;**ドラフト**&#x200B;モードで開始します。 これは、学習目標がまだ公開されておらず、学習者が利用できないことを意味します。 **LEARNING_OBJECT_DRAFT**&#x200B;イベントは、学習目標が下書きである限りトリガーされます。 ドラフトを継続的に更新した場合にも、このイベントがトリガーされます。

#### アップデート

学習目標が公開されると、その状態が&#x200B;**ドラフト**&#x200B;から&#x200B;**公開済み**&#x200B;に変わります。 この移行中、学習オブジェクトが&#x200B;**ドラフト**&#x200B;から&#x200B;**公開済み**&#x200B;に変更されているため、Webhookは&#x200B;**LEARNING_OBJECT_MODIFICATION**&#x200B;イベントを生成します。 LOに対するその後の変更および更新もすべて、**LEARNING_OBJECT_MODIFICATION**&#x200B;イベントをトリガーします。

**LEARNING_OBJECT_MODIFICATION**&#x200B;イベントは、学習目標が廃止されたときにもトリガーされます。 親学習オブジェクトが廃止された状態でこれらのインスタンスが廃止されるため、この廃止操作により、基礎となるインスタンスに更新のマークが付けられます。

#### 削除

学習目標を削除すると、**LEARNING_OBJECT_DELETION**&#x200B;イベントが生成されます。 このイベントは、学習オブジェクトが削除されたため、学習者がアクセスできないことを示します。

学習目標イベントには、リアルタイムのイベントに加えて、**LEARNING_OBJECT_MODIFICATION_BATCH**&#x200B;イベントの一部としてトリガーされるバッチ（非リアルタイム）対応のイベントもあります。 このイベントは、移行ワークフローで学習目標を作成または変更しているときに発生します。 学習目標のドラフト操作と削除操作は移行ではサポートされていないため、これらのアクションに対応するドラフトまたは削除イベントはありません。

### 学習目標インスタンス

学習目標インスタンスでサポートされているイベントを以下に示します。

#### アップデート

インスタンスが作成されると、**LEARNING_OBJECT_INSTANCE_MODIFICATION**&#x200B;イベントが生成されます。 Adobe Learning Managerの学習目標インスタンスには&#x200B;**Draft**&#x200B;状態がないので、Adobe Learning Managerは&#x200B;**LEARNING_OBJECT_INSTANCE_DRAFTイベント**&#x200B;をサポートしていません。 このイベントは、インスタンスが作成、変更、または削除されるたびに生成されます。

インスタンスが作成、更新、または廃止されたときに生成されるだけでなく、このイベントは、親学習オブジェクトが&#x200B;**廃止**&#x200B;とマークされたときに自動生成されます。 これは、学習目標が廃止されたときに、基礎となるインスタンスも&#x200B;**廃止**&#x200B;とマークする必要があるためです。

#### 削除

インスタンスが削除されると、**LEARNING_OBJECT_INSTANCE_DELETION**&#x200B;イベントが生成されます。 このイベントは、セルフペースモジュールが含まれているコースインスタンスにのみ適用されます。Adobe Learning Managerでは、管理者はモジュールタイプがセルフペースモジュールであるコースインスタンスのみを削除できます。 Adobe Learning Managerでは、学習パスインスタンスまたは資格認定インスタンス以外の他の種類のコースモジュールに対する明示的な削除はサポートされていません。

学習目標インスタンスには非リアルタイム対応の機能もあり、**LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH**&#x200B;イベントの一部として公開されます。 このイベントは、移行ワークフローによる学習オブジェクトインスタンスの作成または変更中にトリガーされます。 移行では学習オブジェクトインスタンスのドラフトまたは削除操作がサポートされていないため、対応するドラフトまたは削除イベントは使用できません。

### 登録

学習者が登録アクションを実行すると、リアルタイムの登録イベントがトリガーされます。 学習目標タイプに応じて、リアルタイム登録イベントは次のいずれかのカテゴリに分類されます。

* COURSE_ENROLLMENT
* LEARNING_PATH_ENROLLMENT
* CERTIFICATION_ENROLLMENT

登録イベントには、これらのリアルタイムイベントに加えてバッチ対応があります。 管理者、マネージャー、またはプラットフォームによって登録がトリガーされるたびに、非リアルタイム登録イベントがトリガーされます。 学習目標タイプに基づいて、バッチ登録イベントは次のいずれかになります。

* COURSE_ENROLLMENT_BATCH
* LEARNING_PATH_ENROLLMENT_BATCH
* CERTIFICATION_ENROLLMENT_BATCH

### 登録解除

学習者が登録解除アクションを実行すると、リアルタイムの登録解除イベントがトリガーされます。 学習目標のタイプに応じて、リアルタイム登録解除イベントは次のいずれかのカテゴリに分類されます。

* COURSE_UNENROLLMENT
* LEARNING_PATH_UNENROLLMENT
* CERTIFICATION_UNENROLLMENT

これらのイベントに加えて、バッチ登録解除イベントもあります。 登録解除が管理者、マネージャー、またはプラットフォームによってマークされるたびに、非リアルタイム登録解除イベントがトリガーされます。 学習目標タイプに基づいて、バッチ登録解除イベントは次のいずれかになります。

* COURSE_UNENROLLMENT_BATCH
* LEARNING_PATH_UNENROLLMENT_BATCH
* CERTIFICATION_UNENROLLMENT_BATCH

### 完了

リアルタイム完了イベントは、学習者が学習目標を完了するたびにトリガーされます。 学習目標タイプに基づいて、リアルタイム完了イベントは次のいずれかのカテゴリに分類されます。

* COURSE_COMPLETED
* LEARNING_PATH_COMPLETE
* CERTIFICATION_COMPLETED

これらのリアルタイムイベントに加えて、バッチ完了イベントもあります。 例えば、管理者、マネージャー、またはプラットフォームが学習オブジェクトを完了とマークすると、非リアルタイム完了イベントがトリガーされます。 学習目標タイプに基づいて、バッチ完了イベントは次のいずれかのカテゴリに分類されます。

* COURSE_COMPLETED_BATCH
* LEARNING_PATH_COMPLETED_BATCH
* CERTIFICATION_COMPLETED_BATCH

### 学習者の進行状況

学習者が学習目標に登録してモジュールを開始するたびに、その進行状況が追跡されます。 このデータは、**LEARNER_PROGRESS**&#x200B;イベントに含まれます。 進捗状況の追跡はリアルタイムではない複雑な集計ロジックに依存しているため、イベントは最大15分遅れる可能性があります。

### 構成項目の統計

**CI_STATS**&#x200B;リアルタイムイベントは、コースインスタンスの座席またはキャンセル待ちの利用可能時間に変更があった場合にトリガーされます。 このデータは、インスタンスレベルでのみ取得されます。 また、座席とキャンセル待ちの有無はコースとそのインスタンスに固有の属性であるため、このイベントはコースに対してトリガーされ、他の学習パスや資格認定にはトリガーされません。

## イベントの順序

Adobe Learning Managerでは、イベントがアカウントごとに注文されます。 ただし、登録または完了イベントと進捗イベントの間でメッセージを関連付ける際に相違が生じることがあります。 これは、学習者の進行状況イベントが最大で15分遅れる可能性があるためです。進行状況の追跡は、リアルタイムではない複雑な集計ロジックに依存します。 また、進捗イベントは様々なデータソースから取得されるため、登録イベントや完了イベントに関して進捗イベントの順序を保証することはできません。 そのため、Adobe Learning Managerは、これらのイベントをリッスンする際にクライアントにベストプラクティスを提供します。

完了イベントが学習者の進行状況イベントよりも前に発生した場合、クライアントは学習者の進行状況イベントを無視できます。 これは、学習者の進行状況イベントは最大15分遅延する可能性がありますが、完了イベントは進行状況イベントを受信する前にトリガーされる可能性があるためです。 完了イベントを受け取ると、学習目標が完了したことを示すため、進行状況が100%に達したことを意味します。

まれに、学習者の進行状況イベントの後に登録イベントが発生する場合があります。クライアントは登録イベントを無視できます。 これは、学習者が学習目標に登録した場合にのみ、進捗状況を追跡できるためです。 つまり、progressイベントを受け取った場合は、学習目標が開始されたことを示します。これは、登録が成功した後にのみ発生します。

## リアルタイムイベントとバッチイベント

特定のイベントには、上記のようにリアルタイムと非リアルタイムの対応があります。 リアルタイムイベントをサブスクライブする場合と、リアルタイムイベント以外のイベントをサブスクライブする場合は、いくつかの質問が考えられます。 以下は、上記のエンティティに基づいて従うことができるガイドラインです。

### リアルタイムイベント

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

### 非リアルタイムイベント

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

### 学習目標とそのインスタンス

* 管理者、作成者などの役割によるUIアクションを介して行われた学習オブジェクトへの変更をリッスンする場合は、いつでもリアルタイムイベントをサブスクライブできます。
* 移行ワークフローで行われた学習目標の変更を確認する必要がある場合は、非リアルタイムまたはバッチ処理されたイベントを購読します。

### 登録、登録解除および完了

* 学習者が実行した登録、登録解除または完了をリスニングする場合は、いつでもリアルタイム・イベントに登録できます。
* 管理者、マネージャー、プラットフォームなどによってマークされた登録、登録解除または完了をリッスンする場合は、非リアルタイムまたはバッチ処理イベントをサブスクライブします。

### 学習者の進行状況

* 学習者の進捗状況の変更を確認する場合は、必ずイベントに登録します。

>[!NOTE]
>
>上記のシナリオ（登録、登録解除、完了および進行状況）では、userIdとloInstanceIdで構成される属性合成によってレコードを一意に識別できます。

### コースインスタンス統計

* 空席やキャンセル待ちの有無の変化を確認したい場合は、いつでもリアルタイムの&#x200B;**CI_STATS**&#x200B;イベントに登録できます。

## Webhookイベントのペイロード

Webhook応答ペイロードの一部として、Adobe Learning Managerはエンティティを一意に識別するために必要な属性を生成します。 これらは同じ形式で、パブリックAPIで使用される標準に従って生成されるため、webhookデータがパブリックAPIデータと同期するようになります。 [サンプルペイロード](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#sample-payloads-for-the-events)を表示して、各種イベントのペイロードを確認します。

## Webhookを使用した外部DBまたは通知サービスの構築

Webhookが役立つと聞いたユースケースの1つは、お客様側でデータベースを構築する場合です。 Adobe Learning Managerには独自のデータベースとスキーマがありますが、お客様はこのデータベースにアクセスできません。

問題は、顧客がwebhookのイベントを使用してデータベースを構築する方法を教えてください。

Adobe Learning Managerはテーブルレコードとスキーマを直接公開しないため、お客様は、イベントを使用してデータを入力することで、Webhooksソリューションを使用して外部データベースを構築できます。 このリリースでは、学習目標、学習目標インスタンス、登録、登録解除、完了、進捗状況、コースインスタンス統計に関するイベントが提供されています。

### 学習目標イベントからのデータベースの構築

学習目標イベントは、エンティティを識別するために`loId`と`loType`を公開します。 ただし、これらの属性だけでは外部学習目標データベースを構築するには不十分です。 学習目標を詳しく説明するために、お客様は追加のフィールドを必要とします。
追加データを取得するには、次の2つの方法があります。

#### トレーニングデータレポートを生成してすべてのデータを取得する

このアプローチは、移行などのワークフローを使用して学習目標を一括で作成する場合に使用する必要があります。 ここでの目標は、移行ワークフローの一部として取り込まれたすべての学習目標を含む&#x200B;**[!UICONTROL トレーニングデータ]**&#x200B;レポートを生成することです。 読み込みプロセスを最適化するには、書き出し開始時間を移行がトリガーされた時間に設定することをお勧めします。 これにより、履歴データがお客様のデータベースで既に使用可能になるため、移行によって取り込まれた学習目標のみがレポートに書き出されます。

#### パブリックAPI GET /learningObjects - Adminスコープからの情報の照会

この方法は、学習目標をリアルタイムワークフローで作成する場合に使用する必要があります。 お客様は、イベントを介して生成された学習オブジェクトをバッチ処理し、これらの学習オブジェクトIDを渡して`GET /learningObjects` APIをクエリするための独自のキャッシュレイヤーを用意する必要があります。 キャッシュ層を持つ理由は、パブリックAPIレートの制限を超えないようにするためです。 現在、` GET /learningObject`個のAPIに対して、1時間あたり500件のリクエストに設定されている管理者レート制限があります。 この制限を超えると、パブリックAPIサービスは&#x200B;**HTTP 429 Too Many Requestsメッセージ**&#x200B;で応答します。

### 学習オブジェクトインスタンスおよびCI_STATSイベントからのデータベースの構築

学習目標インスタンスイベントは、コースおよび学習パスの`loInstanceId`、`loId`および`loType`属性を生成します。 同様に、**CI_STATS**&#x200B;イベントはコースにのみ適用されます。`seatLimit`、`seatAvailability`、`waitListLimit`、`waitlistAvailability`などはコースにのみ適用されます。

特定の使用例では、インスタンス名、状態などの追加のインスタンスデータが必要です。 追加のインスタンスデータを取得するには、次のアプローチに従います。

#### public-api GET /learningobjectsから情報を照会する – 管理者スコープ

お客様は、上記のように`GET /learningObjects` APIを、含まれるインスタンスと共に使用して、インスタンスに関する情報を取得できます。 レート制限が違反しないように、[セクション](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#query-the-information-from-the-public-api-get-learningobjects-admin-scope)で説明されているアプローチに従う必要があります。


>[!NOTE]
>
>1. 資格認定には、ALMのインスタンスの概念がありません。
>2. CI_STATSの追加データを取得する必要はありません。同じ情報が学習目標のインスタンスイベントの一部としてすでに取得されているからです。

### 登録、登録解除、完了、進捗状況のイベントからのデータベースの構築

Adobe Learning Managerでは、学習者の登録、登録解除、完了および進捗状況が、個別のイベントとして表示されます。 学習者は`userId`属性で識別されます。 ただし、顧客側の下流のワークフローで、名前、電子メールなどの追加の学習者情報が必要となるシナリオが存在する場合があります。 このデータを取得するには、次に示す方法に従います。

#### 管理者またはコネクタからのユーザーレポートの書き出し

このアプローチは、一括登録、一括登録解除など、一括ワークフローが関与する場合は常に実行する必要があります。 Adobe Learning Managerのユーザーレポートには、ユーザーに関するすべての情報が含まれています。 Webhookイベントから取得された`userId`を関連付けることによって、お客様はこのレポートを検索し（データベース、キャッシュ、またはAPIエンドポイントとして顧客側で公開される場合があります）、名前、メール、UUIDなどの追加の詳細を取得できます。 この方法を使用して、ユーザーを週単位または日単位で同期できます。

#### パブリックAPI GET /usersからの情報の照会 – 管理者範囲

このアプローチは、上記のレポートでユーザーが使用できない場合に適用されます。 アプローチ1と2を組み合わせることで、過去に作成されたすべての既存のユーザーが&#x200B;**[!UICONTROL ユーザーレポート]**&#x200B;の対象となり、新しく作成されたユーザーは引き続きAPIから取得できます。 **[!UICONTROL ユーザーレポート]**&#x200B;にデータがない場合、ユーザー情報を取得するために、ユーザーIDを入力引数として`GET /users` APIに送信できます。 この情報は、同じユーザーセットに対して繰り返しパブリックAPIを呼び出さないように、顧客側でキャッシュする必要があります。 現在、GET/ユーザーAPIの管理者レートの制限は、1時間あたり500リクエストに設定されています。 この制限を超える要求があると、**HTTP 429 Too Many Requests**&#x200B;応答が発生します。

## フォールトトレランス

ALM Webhookシステムのフォールトトレラントは、サブスクライバーがイベントの損失、重複イベント、順不同の配信などの潜在的な問題を処理するための推奨事項を提供します。

ALMでは、接続タイムアウトが10秒に、ソケットタイムアウトが5秒に設定されています。 クライアントは、メッセージを受信するとすぐに確認することを想定しています。 これは、メッセージの処理中にクライアントの遅延が発生しないようにするためです。 時間のかかるダウンストリーム処理がある場合でも、クライアントは即座にイベントを確認し、最後にダウンストリーム処理を処理する必要があります。

### データの保持

イベントは7日間開催されます。 この時間内に処理されなかった場合、それらは永久に失われます。 最終日にリカバリが行われ、より多くの時間が必要になった場合、システムは保存期間を延長しません。
消費されるよりも早くイベントが生成されると、一部のイベントが失われる可能性があります。 これは一般的ではありませんが、長期的問題にならないように監視する必要があります。

### Webhookを無効にする

加入者がwebhookイベントに応答できない場合、ALMシステムは指数バックオフを使用してwebhookを再試行し、加入者を圧倒するのを防ぎます。

再試行プロセスは、5秒の初期間隔で開始されます。 サブスクライバーが応答しない場合、待ち時間が10秒、20秒、40秒と80秒の2倍になり、最終的には最大5分に増えます。 5分に達すると、7日間の保持期間が終了するまで、システムは5分ごとに再試行を続けます。 サブスクライバーがこの期間内にまだ応答しない場合、webhookは自動的に無効になります。 リマインダーメールは定期的にサブスクライバーに送信されます。

### イベントの複製

サブスクライバーがイベントの処理後に応答に5秒以上かかる場合、システムは同じイベントの処理を再試行する可能性があります。 処理済みのイベントを追跡するために、イベントIDを使用することをお勧めします。 また、イベントを送信した後、処理されたことを保存する前にwebhookがクラッシュした場合、同じグループのイベントが再試行されることがあります。 重複を認識して無視するには、バッチIDまたは個々のイベントIDを使用することをお勧めします。

### フォールトトレランスの推奨事項

これらの障害を防ぐために、サブスクライバーはwebhookイベントをアクティブに監視し、イベントの欠落、配信の重複、順序が正しくないシーケンスなどの問題に対するアラートを設定する必要があります。

## Webhookイベントに関する特定のガイドライン

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

## Webhookイベントの消費のベストプラクティス

* Webhookソリューションは、速度と低レイテンシーが不可欠な高スループットのシステムを処理するために使用されます。 したがって、お客様は、イベントが受信されるとすぐに、そのイベントが確認されるようにする必要があります。 お客様側で追加の処理（レポートからのデータの取得、API、その他のアクションの実行など）が必要な場合でも、イベントが受信されるとすぐに確認を送信する必要があります。確認の処理は後でクライアントが行います。
* イベントをできる限り早く確認しないと、後続のイベントは前の確認が受信された後にのみ発生するため、イベントのリアルタイム性に影響を与える可能性があります。
* クライアントは、HTTP 202 Acceptedステータス・コードを使用して応答し、イベントが受け入れられたことを確認できます。

## 制限

* 作業計画書は、通常、学習者が他の学習目標を完了する際に使用されるため、LOのカテゴリに属するWebhookイベントには考慮されません。
* 学習目標インスタンスの廃止は、更新イベントと見なされます。 インスタンスには削除イベントはありません。削除ではなく削除することのみが可能です。
* セッションの変更は、インスタンス更新イベントの一部としてキャプチャされます。 これはコースにのみ適用されます。 学習パスインスタンスまたは資格認定インスタンスに対して、下位レベルのエンティティから上位に伝播されることはありません。
* 学習パスにコースが含まれており、学習者が学習パスを介してコースを完了すると、2つの&#x200B;**LearnerProgress**&#x200B;イベント（コース用と学習パス用）が生成されます。
* 一部のワークフローでは、期間や配信タイプなど、学習オブジェクトの属性が非同期で計算されます。 そのため、cronジョブの処理が完了すると、これらの学習目標のイベントが生成されます。
* コースが親学習プログラムまたは認定資格を通じて登録されている場合、登録、登録解除、完了のイベントは、親学習プログラムまたは認定資格に対してのみトリガーされます。 登録は間接的に行われたため、これらのイベントは子コースではトリガーされません。
* Webhookは、状態が&#x200B;**[!UICONTROL ACTIVE]**&#x200B;のアカウントでのみサポートされます。 **[!UICONTROL TRIAL]**&#x200B;または&#x200B;**[!UICONTROL INACTIVE]**&#x200B;アカウントでは使用できません。

## イベントのサンプルペイロード

+++CI_STATS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345-0458-4450-b5dd-6bc1ef4f8b50",
      "eventName": "CI_STATS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456785-LoSt",
      "data": {
        "loInstanceId": "course:12345678_14448475",
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
      "eventId": "12345c1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "1234ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "c2345c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12345823000-040363-12018-0",
      "data": {
        "userId": 11080928,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
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
      "eventId": "c23458c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456823000-040363-12018-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
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
      "eventId": "1234791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234567",
        "loInstanceId": "learningProgram:1234567_109139",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "12340791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234557",
        "loInstanceId": "learningProgram:1234557_109139",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "123404e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
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
      "eventId": "12344e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
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
      "eventId": "1234e776-148e-4128-80e9-b896a460b655",
      "eventName": "CERTIFICATION_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12344672000-040654-559128-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "123472ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "CERTIFICATION_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234524713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:123456798",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
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
      "eventId": "1234bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123454768000-040654-756257-0",
      "data": {
        "userId": 123456728,
        "loId": "certification:123418",
        "loInstanceId": "certification:134518_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
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
      "eventId": "123453bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604768000-040654-756257-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
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
      "eventId": "d1234d3a4-c3df-44fa-a1cf-7edd6e3d2075",
      "eventName": "LEARNER_PROGRESS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235604551000-297002-5823-0",
      "data": {
        "loId": "course:7542090",
        "loType": "course",
        "userId": 12380928,
        "loInstanceId": "course:7232090_10423047",
        "dateStarted": "2024-11-08T03:49:52.000Z",
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
      "eventId": "f3237817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1345506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
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
      "eventId": "f2317817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "17235506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
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
      "eventId": "823df878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
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
      "eventId": "8e23f878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
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
      "eventId": "7232766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235507900000-040304-1065-0",
      "data": {
        "userId": 12311591,
        "loId": "certification:123199",
        "loInstanceId": "certification:123199_162078",
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
      "eventId": "7202766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1735507900000-040304-1065-0",
      "data": {
        "userId": 12511591,
        "loId": "certification:139199",
        "loInstanceId": "certification:139199_162078",
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
      "eventId": "12345da9f-26ec-453c-b56a-cdf18a841948",
      "eventName": "LEARNING_OBJECT_DRAFT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234519188000-040344-48604-0",
      "data": {
        "loId": "course:1234091",
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
      "eventId": "1234a690-5517-4c09-9cde-d953cdd8582c",
      "eventName": "LEARNING_OBJECT_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605296000-040656-662792-0",
      "data": {
        "loId": "course:12319716",
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
  "accountId": 8308,
  "events": [
    {
      "eventId": "223e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
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
  "accountId": 8308,
  "events": [
    {
      "eventId": "1234e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
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
      "eventId": "121da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
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
      "eventId": "1231da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
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
      "eventId": "12d16e90-d73a-457b-83f3-666ba9654edb",
      "eventName": "LEARNING_OBJECT_INSTANCE_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605491000-040657-236307-0",
      "data": {
        "loInstanceId": "course:12319674_14453849",
        "loId": "course:12319674",
        "loType": "course"
      }
    }
  ]
}
```

+++
