---
jcr-language: en_us
title: Learning Manager とSlack
description: Learning Manager とSlack
contentowner: dvenkate
source-git-commit: 864b1796f1ca99ae7b5643e8c58d1756ff2461a1
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 44%

---



# Learning Manager とSlack

Learning Managerのコネクタとして、**削除済み** **Slack**&#x200B;です。 Slackコネクタにアクセスできなくなります。

Slack ユーザーは、Slack App ディレクトリの Adobe Learning Manager アプリを Slack チームにインストールして、Slack で Learning Manager のコンテンツを検索できます。Primebotを操作して、Learning Managerで新しいコースを検索したり、推奨事項を表示したり、今後の締め切りに関する通知を受信したりできます。 Slack 内で登録を行って学習内容に直接ジャンプできます。

Learning ManagerアプリSlack版は、Learning ManagerのAzureインスタンスではサポートされていません。

## Learning ManagerAdobeアプリケーションのインストール {#installingadobecaptivateprimeapp}

学習者は、Slack アカウントで CP Prime アプリをインストールできます。 アプリをインストールするには、Slack アカウントで App ディレクトリを開き、Learning Manager を検索します。アプリをダウンロードしてインストールします。 アカウントでアプリが承認されない場合は、統合管理者に連絡して承認を受けてください。 既に承認されている場合は、サインインできます。

## 統合管理者としての学習者のログインを承認する方法 {#approvinglearnersigninasanintegrationadmin}

統合管理者として、SlackでPrimeアプリケーションを使用するための権限を学習者に付与するには、次の手順に従います。

1. 左ペインで&#x200B;**[!UICONTROL 「アプリケーション」]**&#x200B;を選択し&#x200B;**[!UICONTROL 「おすすめアプリ」]**&#x200B;タブをクリックします。

   ![](assets/featuredapps.jpg)

1. **[!UICONTROL Slack]**&#x200B;タイルをクリックし、Slack との統合ページを開きます。 右上隅の&#x200B;**[!UICONTROL 承認]**&#x200B;をクリックして、アプリケーションを承認します。

   ![](assets/approval.png)

1. **[!UICONTROL アプリケーション]**&#x200B;ページに戻ります。 承認されると「**[!UICONTROL 外部アプリ]**」タブに「Slack」が表示されます。
1. 学習者は、Slack を使用して Prime アカウントにサインインできるようになりました。

## Primebot の機能 {#primebotfunctionalities}

これで、Primebotを操作できるようになりました。 Primebot の機能を次に示します。

1 – コマンド

&#42;/prime&#42;は、Adobe Learning Managerアカウントに関する1回限りのポイントクエリに使用できます。

使用できるサブコマンドは以下のとおりです：

/prime find `<query>` – コース、資格認定などを検索します。

/prime recommend - 推奨事項の表示

/prime deadlines - 期限切れと期限切れ予定の表示

/prime enrollments - 登録の表示

/prime skills - スキルの表示

/prime notifications - 通知の表示

/prime catalogs - カタログの表示

/prime invite - [管理者のみ]現在のグループのSlackユーザーにprimebotを試すよう招待します

/prime profile - プロファイルの表示

/prime logout - この Slack チームの Prime アカウントからのログアウト

/prime help - ヘルプメッセージの表示

2 – 推奨

`show my recommendations`のようなフレーズを試して、Adobe Learning Managerアカウントから推奨コース、資格認定および学習プログラムのパーソナライズされたリストを取得できます。

3 – 検索

`search for machine learning`や`search for artificial intelligence`などのフレーズを試すことができます。 `search for machine learning certifications`、`search for artificial intelligence courses`、`search for adobe photoshop job aids`などのフレーズを使用して、学習目標の種類を指定できます。 `search for machine learning in Lynda catalog`などのフレーズを使用して、カタログ内で検索することもできます。

4 – 期限

Adobe Learning Managerアカウントから期限切れおよび期限切れ予定のリストを取得するには、`show my deadlines`などのフレーズを使用します。 `show my overdue deadlines`や`show my upcoming deadlines`などのフレーズを使用して、期限切れや期限切れ予定をフィルター処理できます。
