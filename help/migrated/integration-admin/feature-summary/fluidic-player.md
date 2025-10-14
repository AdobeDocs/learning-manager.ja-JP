---
description: この記事では、カスタムアプリケーションに Fluidic プレーヤーを埋め込む方法について説明します。
jcr-language: en_us
title: 埋め込み型 Fluidic プレーヤー
contentowner: dvenkate
preview: true
source-git-commit: fba5e5ddc1964b485be473bf356806f234688cf4
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 24%

---



# 埋め込み型 Fluidic プレーヤー

この記事では、カスタムアプリケーションに Fluidic プレーヤーを埋め込む方法について説明します。

企業は Learning Manager の外部でも、学習者にカスタムエクスペリエンスを提供できるようになりました。パブリックAPIを使用して、学習目標、学習者の登録および学習の進捗状況に関連するすべての情報を取得し、webサイトに表示できます。 さらに重要な点として、Learning Manager の Fluidic プレーヤーを web サイトに埋め込めるようになりました。これにより、学習者は、コンテンツを web サイト内で利用できるようになります。Fluidic プレーヤーは、Learning Manager がサポートするあらゆるコンテンツを再生できます。他のWebサイトに埋め込んだ場合も、Learning Manager内で使用するときとまったく同じ機能を利用できます。

**eラーニングコンテンツを再生[&#128279;](../../learners/feature-summary/fluidic-player.md#main-pars_text_779047019)**

Fluidic プレーヤーは、プラグインやダウンロードを必要とせずに、ほぼすべてのタイプの e ラーニングコンテンツを、一貫した直感的な方法で再生できます。 コンテンツファイルの種類に関わらず、学習者がコンテンツを起動すると再生が始まります。

**メモとブックマーク**

ファイルの種類に関わらず、任意のコンテンツにメモしたり、ブックマークしたりすることができます。 長いファイルまたはビデオから特定の選択を行う場合、ニーズに関連する情報を見つけた場所にポイントをブックマークできます。 ノートとブックマークは、検索したり、メールとして送信したりできます。 ノートとブックマークをクリックすると、Fluidic プレーヤーでビデオやドキュメントページの該当する部分に移動します。

Fluidicプレーヤーの詳細については、[Fluidicプレーヤー](../../learners/feature-summary/fluidic-player.md)を参照してください。

埋め込み型Fluidicプレーヤーを使用できる例を次に示します。

* **webサイトに埋め込み型Fluidicプレーヤーを使用して**&#x200B;従業員の登録コースをリストアウトしたり、同じページでトレーニングを開始するためのリンクを提供したりできます。 これは、学習者がイントラネットwebサイトでトレーニングを利用できることを意味します。

* トレーニングをビジネスとして行っている方たちの中には、自分たちの顧客がサイト上でコースを購入できるような web サイトを運営している場合があります。 埋め込み型プレーヤーを同じwebサイトに統合して、顧客がwebサイト内で購入したコンテンツを利用できるようにすることができます。

## web サイトに埋め込み型 Fluidic プレーヤーを埋め込む手順 {#stepstoembedfluidicplayerinyourwebsite}

web サイトに Fluidic プレーヤーを埋め込むためのカスタムアプリケーションを構築するには、次の 3 つの基本的な手順が必要です。

1. Learning Manager の統合管理アプリでアプリケーションを作成します。
1. アクセストークンを取得します。
1. パブリックAPIを使用してLearning Managerからリソースを取得するために、アクセストークンを使用します。

### 1. 統合管理者としてのアプリケーションの作成 {#1createanapplicationinintegrationadmin}

この手順は、更新トークンとアクセストークンの取得に使用する、アプリケーション／クライアント ID とアプリケーション／クライアントシークレットを作成する場合に必要です。 アプリケーション作成の詳細については、[アプリケーション開発プロセス](developer-manual.md#main-pars_header_994876235)を参照してください。

1. **[!UICONTROL 統合管理]**&#x200B;アプリに移動して&#x200B;**[!UICONTROL アプリケーション]**&#x200B;を開きます。

1. ページの右上隅から&#x200B;**[!UICONTROL 「登録」]**&#x200B;を選択します。
1. **[!UICONTROL 新規アプリケーションを登録]**&#x200B;ウィンドウが開きます。 必須フィールドに入力します。
1. カスタムアプリケーションを複数のアカウントで共有する必要がある場合は、オプションフィールド&#x200B;**[!UICONTROL このアカウントのみですか？]**&#x200B;で&#x200B;**[!UICONTROL いいえ]**&#x200B;を選択してください。
1. アプリケーションを保存して、アプリケーション ID とシークレットを生成するには&#x200B;**[!UICONTROL 「保存」]**&#x200B;をクリックします。

### 2. アクセストークンの取得 {#2retrievingaccesstoken}

Learning ManagerはOAUTH2.0を使用しています。パブリックAPIを使用してリソースを取得するには、アクセストークンが必要です。 アクセストークンは、更新トークン、クライアント ID またはクライアントシークレットを使用して取得できます。

**2.1更新トークン**

* OAuth コードの取得

更新トークンを取得するには、OAuth コードが必要です。 次のURLを使用してサインインすると、Learning ManagerはOAuthコードを使用してリダイレクトURLにユーザーをリダイレクトします（サンプルアプリケーションの「oauthredirect.html」ファイルでは、OAuthコードの抽出が例示されています）。

```
code https://learningmanager.adobe.com/oauth/o/authorize  
client_id= <application_id>  
&redirect_uri=<redirect_uri>  
&state=<dummy_data>  
&scope=learner:read,learner:write  
&response_type=CODE  
&account=<account_id>  
&email=<email_id>
```

ここで、**[!UICONTROL クライアントID]**&#x200B;は、手順1で取得したアプリケーションIDです。
**[!UICONTROL redirect_url]**&#x200B;は、手順1で設定されたredirect_urlです。
**[!UICONTROL state]**&#x200B;は、任意のダミーデータです。OAuthコードを取得するためのリダイレクトURLをフィルター処理する必要があります。 範囲は、手順1で設定した学習者の範囲です。
**[!UICONTROL response_typ]**&#x200B;eは常に「CODE」です。\
**[!UICONTROL account]**&#x200B;はオプションのフィールドです\
**[!UICONTROL email]**&#x200B;はオプションのフィールドです\
&#42;アカウントIDと電子メールの両方を指定した場合、上のURLを使用して同じアカウントにログインできます。 このエンドポイントの例は、サンプルアプリケーションの「index.html」ファイルに表示されています。

* 更新トークンの取得

OAuthコードを受信した後、受信したOAuthコード、クライアントID、およびクライアントシークレットを使用して、次のエンドポイントから更新トークンを取得できます。

**https://learningmanager.adobe.com/oauth/token**

POST リクエストへの応答として、次の情報が提供されます。

i. refresh_token\
ii. access_token\
iii. user_id\
iv. expires_in\
v. user_role\
vi.  account_id

**2.2更新トークンからアクセストークンを取得しています**

アクセストークンを取得するには、refresh_token、client_idおよびclient_secretをPOST本文とした別のリクエストを次のURLに送信します。

**https://learningmanager.adobe.com/oauth/token/refresh**

POST リクエストへの応答として、次の情報が提供されます。\
i. refresh_token\
ii. access_token\
iii. user_id\
iv. expires_in\
v. user_role\
vi.  account_id

### 3. パブリック API を使用したリソースの取得 {#3retrieveresourcesusingpublicapi}

3番目の手順として、アクセストークンを使用する必要があります。パブリックAPIを使用して、Learning Managerからリソースを取得します。  アクセストークンは、公開api呼び出しを行うために必要であり、サンプルアプリケーションで示されているように、ヘッダーに追加する必要があります。

## 埋め込み型プレーヤー {#embeddableplayer}

サードパーティのアプリケーションでも、埋め込み型プレーヤーを使用して、学習目標のコンテンツを再生できます。

**埋め込み型プレーヤーでコースを開く**

1. 埋め込み URL の作成

   埋め込み型プレーヤーを使用してコースを開くには、次のように埋め込みURLを作成する必要があります。

   `https://learningmanager.adobe.com/app/player?lo_id=<v2-api course id>&access_token=<access_token>`

   ここで、lo_id は V2 API のコース ID 形式に適合している必要があります。

   例： `https://learningmanager.adobe.com/app/player?lo_id=course:123456&access_token=45b269b75ac65d6696d53617f512450f`

   埋め込み型プレーヤーでは、資格認定、学習プログラム、作業計画書も再生できます。

   例： `https://learningmanager.adobe.com/app/player?lo_id=certification:12345&access_token=c1a4847dfbf4007826a027d481b93c1e`

   `https://learningmanager.adobe.com/app/player?lo_id=learningProgram:12345&access_token=c1a4847dfbf4007826a027d481b93c1e`

   `https://learningmanager.adobe.com/app/player?lo_id=jobAid:1234&access_token=c1a4847dfbf4007826a027d481b93c1e`

1. このURLをiframeの「src」属性に設定します。

**埋め込みプレーヤーを閉じています**

```
code window.addEventListener("message", function closePlayer(){  
   if(event.data === "status:close"){  
     //handle closing event  
   }  
});
```

## サンプルアプリケーションチュートリアル {#sampleapplicationtutorial}

添付のpdf文書には、サンプルアプリケーションチュートリアルが含まれています。
[Fluidicプレーヤーを埋め込むためのサンプルチュートリアルとチュートリアルソース。](assets/sample-applicationtutorial.zip)代替コンテンツ

管理者は、Fluidicプレーヤー内で学習者に代替コンテンツを提供できるように、コースの内容を設定できます。 例えば、複数の地域の学習者が複数の言語を使用する場合は、複数の言語で同じコンテンツを作成できます。 Fluidicプレーヤーは設定されている言語を学習者に提供しますが、学習者はプレーヤー内から別の言語に切り替えることもできます。

ビデオ固有のコントロール

Learning Manager Fluidicプレーヤーで使用されているストリーミングテクノロジーは、ビデオの開始を遅らせることなく、また、どのデバイスでもディスク容量を必要とせずに、ビデオ再生エクスペリエンスを学習者に提供します。 また、Fluidicプレーヤーは再生スピード（1倍、1.5倍）、スキップ+ -10秒などのスマートコントロールを提供します。これは、学習速度に合わせて必要な正確なレベルのコントロールを学習者に提供するように設計されています。

これは、ITチームの誰かまたは外部コンサルタントが行う必要のある作業です。外部コンサルタントは、アプリケーションを構築し、サイトでホストします。

1. 取得する必要がある正確な学習オブジェクトを指すパラメーターを使用して、Learning Managerの埋め込みプレーヤーのURLを変更します。

   URL: [https://learningmanager.adobe.com/app/player](https://cpcontents.adobe.com/public/embedplayer/index22fa615ec2baa034a22090c8cd4289fa.html)

1. 次のいずれかのパラメーターを使用して、コースを起動します。

   * course_id ：起動するコースのIDです
   * learning_program_id ：起動する学習プログラムのIDです
   * certification_id ：起動する資格認定のIDです
   * lo_id ：再生する学習目標（コース/学習プログラム/資格認定/作業計画書）のID


1. アクセストークンを必須パラメーターとして使用します。

   * access_token ：これはセキュリティパラメーターで、パブリックAPI oauthを使用します   アクセストークン

   トークンは、統合管理者で埋め込み型Fluidicプレーヤーを設定することで取得できます。 アクセストークンとして使用できる認証トークンを取得できます。

   作成されたURLの例； https://learningmanager.adobe.com/app/player?lo_id=&quot;+lo_id+&quot;&access_token=&quot;+accToken

   ここで、 lo_idはコースのID、学習プログラム、資格認定および作業計画書になります。

   lo_idの例 – course:21324、learningProgram:2143、certification:23432、jobAid:237

1. 上記のパラメーターを取得するために、Learning Manager API呼び出しを作成します。

   これらのAPI呼び出しは、ITチーム/コンサルタントがサイトで作成およびホストするアプリケーションによって行われます。

   APIの使用について詳しくは、次を参照してください。

   Learning Manager V1 API - [https://learningmanager.adobe.com/docs/primeapi/v1/](https://learningmanager.adobe.com/docs/primeapi/v1/)



   Learning Manager V2 API - [https://learningmanager.adobe.com/docs/primeapi/v2/](https://learningmanager.adobe.com/docs/primeapi/v2/)

   オブジェクトのIDは、V1およびV2 APIとは異なります。 埋め込み型プレーヤーでは、v2形式のIDが必要です。 V2でIDマッピングAPIを使用して、V1 IDからV2 IDに変換します。

   URLを作成した後、アプリケーションで学習者に表示する方法の1つとして、iFrame内にURLを入れることが挙げられます。 このリンクをクリックすると、コンテキスト内の特定のコースを使用してFluidicプレーヤーが起動されます。

   ![](assets/salesforce-player.png)

   進捗状況と完了レポートを確認するには、Learning Managerにログインします。

   学習者がプレーヤーを閉じると、html5 postMessageを使用して、Fluidicプレーヤーは親要素に「閉じる」メッセージを送信します。 ロードコントローラはこのメッセージを処理して続行する必要があります。

取得する必要がある正確な学習オブジェクトを指すパラメーターを使用して、Learning Managerの埋め込みプレーヤーのURLを変更します。

URL: [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player)

コースの起動には、次のいずれかのパラメーターを使用できます。

* course_id ：起動するコースのIDです
* learning_program_id ：起動する学習プログラムのIDです
* certification_id ：起動する資格認定のIDです
* lo_id ：再生する学習目標（コース/学習プログラム/資格認定/作業計画書）のID

必須パラメーター：

* access_token ：これはセキュリティパラメーターで、パブリックAPI oauthを使用します   アクセストークン

上記のパラメーターを取得するために、Learning Manager API呼び出しを作成します。 これらのAPI呼び出しは、ITチーム/コンサルタントがサイトで作成およびホストするアプリケーションによって行われます。

APIの使用について詳しくは、次を参照してください。

Learning Manager V1 API - [https://learningmanager.adobe.com/docs/primeapi/v1/](https://learningmanager.adobe.com/docs/primeapi/v1/)



Learning Manager V2 API - [https://learningmanager.adobe.com/docs/primeapi/v2/](https://learningmanager.adobe.com/docs/primeapi/v2/)


