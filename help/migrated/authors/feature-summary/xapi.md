---
jcr-language: en_us
title: Learning ManagerのxAPI
description: Experience API(xAPI)は、あらゆるタイプの学習体験を記録して追跡する方法で学習コンテンツと学習システムを相互に連携させることを可能にするeラーニングソフトウェア仕様です。
source-git-commit: 0fabd369e70e15ba22fead0177a24aafd851d88d
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---



# Learning ManagerのxAPI

## xAPIとは？ {#whatisxapi}

Experience API(xAPI)は、あらゆるタイプの学習体験を記録して追跡する方法で学習コンテンツと学習システムを相互に連携させることを可能にするeラーニングソフトウェア仕様です。 学習体験は、学習記録ストア(LRS)に記録されます。 LRSは、従来の学習管理システム(LMS)内または独自に存在できます。

xAPIについて詳しくは、以下を参照してください。  [https://github.com/adlnet/xAPI-Spec](https://github.com/adlnet/xAPI-Spec).

## Learning ManagerはxAPIをどのようにサポートしていますか？ {#howdoescaptivateprimesupportxapi}

Learning Managerには学習記録ストアが組み込まれています。 このLRSには、Learning Manager内でホストされるコンテンツからxAPIステートメントを受け入れる完全な機能があります。 サードパーティが生成するxAPIステートメントも受け入れます。 これらのxAPIステートメントはLearning Manager内に保存されます。ステートメントはその後、Learning Manager外に書き出して、サードパーティのデータウェアハウスシステムで視覚化することができます。

## xAPIを使用するタイミング {#whendoyouusexapi}

複数のシステムにまたがるエンドユーザーの学習体験をキャプチャする必要が高まっています。  また、学習者がトレーニングコンテンツに対して抱くエンゲージメントを正確に追跡する必要もあります。 開始、進行中、完了を超えます（これらはSCORMによってキャプチャされる唯一の属性です）。

## Learning ManagerでのxAPIの使用 {#usingxapiinprime}

## アプリケーションの設定 {#setupyourapplication}

1. 統合管理者としてログインします。 選択 **[!UICONTROL アプリケーション]** > **[!UICONTROL 登録]**.

   ![](assets/appregistration.png)

1. 新しいアプリケーションを登録します。

   ![](assets/appregistration.png)

1. アプリケーションの範囲を定義します。

   * If **[!UICONTROL 管理者役割xAPI読み取りおよび書き込みアクセス]** が有効になっている場合、管理者はxAPIのステートメントとドキュメントの投稿と取得を行うことができます。
   * If **[!UICONTROL 学習者役割xAPI読み取りおよび書き込みアクセス]** が有効になっている場合、管理者はxAPIのステートメントとドキュメントの投稿と取得を行うことができます。

1. 変更を保存します。 開発者IDとシークレットを取得します。

**終点**:

以下のリンクをクリックして、xAPI swaggerドキュメントを表示します。

[https://learningmanagereu.adobe.com/docs/primeapi/xapi/](https://learningmanagereu.adobe.com/docs/primeapi/xapi/)

注意： Learning ManagerでサポートされているxAPIのバージョンは1.0.3です。

## API認証 {#apiauthentication}

Learning Manager xAPIでは、OAuth 2.0フレームワークを使用して、クライアントアプリケーションを認証および承認します。 アプリケーションを登録すると、clientIdとclientSecretを取得できます。 Get URLは、SSOやAdobe IDなどの事前設定されたアカウントを使用して、ブラウザーでLearning Managerユーザーを認証する際に使用されます。

```
GET https://learningmanager.adobe.com/oauth/o/authorize?client_id=<Enter your clientId>&redirect_uri=<Enter a url to redirect to>&state=<Any String data>&scope=<admin:xapi or learner:xapi>&response_type=CODE.
```

## Learning Manager LOとしてのxAPIステートメントのトラッキング {#trackingxapistatementsasprimelo}

作成者は、コースの作成中にxAPIモジュールを選択し、Learning Managerの外部でユーザーエクスペリエンスを監視できるようになりました。 例えば、この機能を使用して、コースの受講に使用されるサードパーティプラットフォーム上のユーザーのアクティビティを評価できます。

1. の作成中 **[!UICONTROL アクティビティモジュール]****内の[!UICONTROL 種類]**オプションを選択する場合は、ポップアップメニューで  **[!UICONTROL xAPIベースモジュール。]**

   ![](assets/xapimodulecreation.png)

1. IRIを指定する必要があります。 指定しなかった場合、Learning Managerは自動的に生成します。

   アクティビティのIRIは、アカウント全体で一意です。 つまり、Learning Managerの2つのモジュールで同じIRIを使用することはできません。 新しいIRIは、次の場合に生成されます。

   * xAPIモジュールを含むコースがアカウント間で共有されている場合。
   * xAPIモジュールを使用する資格認定が繰り返される場合



   指定のIRIを含むxAPIステートメントは上記のモジュールで追跡され、Learning Managerレポートに反映されます。

1. 自動生成されたIRIをコピーするには、再度アクティビティモジュールページに移動します。
1. モジュールをパブリッシュします。

**注意事項：**

* Learning Managerでは現在、識別子としてmboxのみをサポートしています。 mboz_sha1、openid、accountなどのその他の識別子はサポートされていません。

* stateIdとprofileIdは、Learning Managerで使用される際はUUIDになります。
* xAPIの担当者/プロファイル、アクティビティ/プロファイル、アクティビティ/ステートの文書は、PUTリクエストによって上書きされません
* アクターでは、不明なグループはサポートされていません。
* パラメーター「related_activities」は、GETステートメントではサポートされていません。
* パラメーター&#39;format=ids&#39;および&#39;format=canonical&#39;は、GETステートメントではサポートされていません。
* xAPIステートメントを無効にしても、ステートメントの投稿時にLearning Managerで発生したアクションは取り消されません。

## レポートの生成 {#generatereports}

xAPIレポートは、Excelレポートとして生成できます。 管理者として、以下を開きます。 **[!UICONTROL レポート]** > **[!UICONTROL Excelレポート]** > **[!UICONTROL xAPIアクティビティレポート]**.

ダウンロードされたレポートでは、学習者と管理者がステートメントに関して投稿したすべての情報が取得されます。

同じレポートを、任意のサードパーティ統合用にFTPおよびBoxコネクタを使用して生成/スケジュールできます。 次の手順に従います。

統合管理者としてログインし、FTP/Boxコネクターを開いて、左ペインから「xAPIアクティビティレポート」を選択し、レポートのスケジュールまたは生成を選択します。

![](assets/xapischedule.png)

* xAPIステートメントで生スコアのみが送信され、最大スコアが送信されない場合、クイズスコアはLTに表示されません。

* Learning Managerでパーセンテージスコアを取得するには、スケールスコアがxAPIを介して送信されます。

## サンプルレポート {#samplereport}

[xAPIレポートのサンプル。](assets/xapireport8842560559890766717csv.zip)
