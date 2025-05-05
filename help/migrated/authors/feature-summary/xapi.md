---
jcr-language: en_us
title: Learning Manager の xAPI
description: Experience API(xAPI)は、あらゆるタイプの学習体験を記録して追跡する方法で学習コンテンツと学習システムを相互に連携させることを可能にするeラーニングソフトウェア仕様です。
exl-id: 8e36b538-a451-448e-a65d-08d286adcfdb
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 49%

---

# Learning Manager の xAPI

## xAPI とは？ {#whatisxapi}

Experience API （xAPI）は、あらゆるタイプの学習経験を記録し、追跡しつつ、学習コンテンツと学習システムを相互に連携させることを可能にする e ラーニングのソフトウェア仕様です。 学習経験は、学習記録ストア（LRS）に記録されます。 LRS は、従来の学習管理システム（LMS）内、またはそれ自体で存在します。

xAPIの詳細については、[https://github.com/adlnet/xAPI-Spec](https://github.com/adlnet/xAPI-Spec)を参照してください。

## Learning Manager は xAPI にどのように対応していますか？ {#howdoescaptivateprimesupportxapi}

Learning Manager には学習記録ストアが組み込まれています。この LRS には、Learning Manager でホストされるコンテンツから xAPI ステートメントを受け入れる包括的な機能があります。サードパーティによって生成される xAPI ステートメントも受け入れます。 これらのxAPIステートメントはLearning Manager内に保存されます。ステートメントはその後、Learning Manager外に書き出して、サードパーティのデータウェアハウスシステムで視覚化することができます。

## xAPI を使用するタイミング {#whendoyouusexapi}

複数のシステムにまたがるエンドユーザーの学習体験をキャプチャする必要が高まっています。  また、学習者がトレーニングコンテンツに対して抱くエンゲージメントを正確に追跡する必要もあります。 開始時だけでなく、進行中も、完了時もそうする必要があります（これらは SCORM によってキャプチャされる唯一の属性です）。

## Learning ManagerでのxAPIの使用 {#usingxapiinprime}

## アプリケーションを設定する {#setupyourapplication}

1. 統合管理者としてログインします。**[!UICONTROL アプリケーション]** > **[!UICONTROL 登録]**&#x200B;を選択します。

   ![](assets/appregistration.png)

1. 新しいアプリケーションを登録します。

   ![](assets/appregistration.png)

1. アプリケーションの範囲を定義します。

   * **[!UICONTROL 「管理者役割 xAPI 読み取りおよび書き込みアクセス」]**&#x200B;を有効にすると、管理者は xAPI のステートメントとドキュメントの投稿と取得ができます。
   * **[!UICONTROL 「学習者役割 xAPI 読み取りおよび書き込みアクセス」]**&#x200B;を有効にすると、管理者は xAPI のステートメントとドキュメントの投稿と取得ができます。

1. 変更を保存します。デベロッパーの ID とシークレットを取得します。

**エンドポイント**:

下のリンクをクリックして、xAPI swagger ドキュメントを表示します。

[https://learningmanagereu.adobe.com/docs/primeapi/xapi/](https://learningmanagereu.adobe.com/docs/primeapi/xapi/)

注意： Learning ManagerでサポートされているxAPIのバージョンは1.0.3です。

## API 認証 {#apiauthentication}

Learning Manager xAPIでは、OAuth 2.0フレームワークを使用して、クライアントアプリケーションを認証および承認します。 アプリケーションを登録すると、clientIdとclientSecretを取得できます。 Get URLは、SSOやAdobe IDなどの事前設定されたアカウントを使用して、ブラウザーでLearning Managerユーザーを認証する際に使用されます。

```
GET https://learningmanager.adobe.com/oauth/o/authorize?client_id=<Enter your clientId>&redirect_uri=<Enter a url to redirect to>&state=<Any String data>&scope=<admin:xapi or learner:xapi>&response_type=CODE.
```

## Learning Manager LOとしてのxAPIステートメントのトラッキング {#trackingxapistatementsasprimelo}

これで作成者として、コースを作成する際に xAPI モジュールを選択し、Learning Manager の外でユーザーエクスペリエンスを監視できるようになりました。例えば、この機能を使用して、コースの受講に使用されるサードパーティーのプラットフォーム上のユーザーのアクティビティを評価できます。 

1. **[!UICONTROL アクティビティモジュール]**&#x200B;を作成するときに、&lbrack;**[!UICONTROL 型]**&#x200B;オプションで、ポップアップメニューを使用して&#x200B;**[!UICONTROL xAPIベースのモジュール]**&#x200B;を選択します。

   ![](assets/xapimodulecreation.png)

1. IRI を指定するように要求されます。 指定しなかった場合、Learning Managerは自動的に生成します。

   アクティビティの IRI は、アカウント全体で一意です。 つまり、Learning Managerの2つのモジュールで同じIRIを使用することはできません。 新しい IRI は、次の場合に生成されます。

   * xAPIモジュールを含むコースがアカウント間で共有されている場合。
   * xAPI モジュールを使用する資格認定が繰り返される場合



   指定のIRIを含むxAPIステートメントは上記のモジュールで追跡され、Learning Managerレポートに反映されます。

1. 自動生成された IRI をコピーするには、再度アクティビティモジュールページに移動します。
1. モジュールをパブリッシュします。

**注意点：**

* Learning Managerでは現在、識別子としてmboxのみをサポートしています。 mboz_sha1、openid、accountなどのその他の識別子はサポートされていません。

* stateIdとprofileIdは、Learning Managerで使用される際はUUIDになります。
* xAPIの担当者/プロファイル、アクティビティ/プロファイル、アクティビティ/ステートの文書は、PUTリクエストによって上書きされません
* アクターでは、不明なグループはサポートされていません。
* パラメーター「related_activities」は、GETステートメントではサポートされていません。
* パラメーター「format=ids」と「format=canonical」は、GET ステートメントでサポートされていません。
* xAPIステートメントを無効にしても、ステートメントの投稿時にLearning Managerで発生したアクションは取り消されません。

## レポートを生成する {#generatereports}

xAPIレポートは、Excelレポートとして生成できます。 管理者として、**[!UICONTROL レポート]** > **[!UICONTROL Excelレポート]** > **[!UICONTROL xAPIアクティビティレポート]**&#x200B;を開きます。

ダウンロードされたレポートでは、学習者と管理者がステートメントに関して投稿したすべての情報が取得されます。

同じレポートを、任意のサードパーティ統合用にFTPおよびBoxコネクタを使用して生成/スケジュールできます。 その場合、以下の手順を実行します。

統合管理者としてログインし、FTP/Box コネクタを開いて、左側のペインから xAPI アクティビティレポートを選択し、レポートのスケジュールまたは生成を選択します。

![](assets/xapischedule.png)

* xAPI ステートメントで未処理のスコアのみが送信され、最大スコアが送信されない場合、クイズスコアは LT に表示されません。

* Learning Manager でパーセンテージスコアを取得する場合、調整済みスコアが xAPI を介して送信されます。

## サンプルレポート {#samplereport}

[xAPI のサンプルレポートです。](assets/xapireport8842560559890766717csv.zip)
