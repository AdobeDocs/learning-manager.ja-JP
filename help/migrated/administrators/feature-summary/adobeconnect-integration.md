---
jcr-language: en_us
title: Adobe Connectとの連携
description: 作成者は、コースの作成プロセスでAdobe Connectを使用してバーチャルクラスルームコースを作成できます。 Learning ManagerアカウントでAdobe Connectを有効にするには、組織の管理者に連絡する必要があります。
contentowner: jayakarr
source-git-commit: 0052ccb2f5a8f9617bca2c7bad91c0cd18338b66
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---



# Adobe Connectとの連携

組織の管理者は、Learning Managerアカウントを設定してAdobe Connectとの連携を有効にすることができます。

## Adobe Connectの設定 {#configureadobeconnect}

1. 管理者ログインで、 **[!UICONTROL 設定]** をクリックすると、会社に関する基本的な情報が表示されます。 クリック **[!UICONTROL Adobe Connect]** をクリックします。

   ![](assets/left-pane.png)

   *左側のパネルで「 Adobe Connect 」を選択します*

1. クリック **[!UICONTROL 設定する]** リンクする **[!UICONTROL Adobe Connectの設定]** セクションに追加します。

   <!--![](assets/configure-now-connect.png)-->

1. 会社のAdobe Connectドメイン名とログイン資格情報を入力します。

   ![](assets/adobeconnect-config.png)

   *ドメイン名と資格情報の追加*

   Adobe Connect URLの例：mycompany.adobeconnect.com\
   Adobe接続アカウントの管理者の電子メールIDを入力する必要があります。

   Learning Managerでは、AdobeがホストするConnectアカウントのみがサポートされています。 例：「.adobeconnect.com」

1. クリック **[!UICONTROL 統合].**

   電子メールIDの認証後、Connectが正常に統合されたというメッセージがLearning Managerに表示されます。 Adobe Connectを使用して、バーチャルクラスルームコースを自動的に表示できるようになります。

   Adobe Connectアカウント管理者は、Adobe Connect利用条件に同意する必要があります。 これを受け入れない場合、ログイン認証に失敗する可能性があります。 Adobe Connectアカウントを作成したら、アカウントに1回ログインします。 初回ログイン時には、利用条件ページが表示されます。

   <!--![](assets/mail-confirmation.png)-->

## バーチャルクラスルームセッション情報を追加 {#addvirtualclassroomsessioninformation}

バーチャルクラスルームコースの作成者がセッション情報を提供していない場合、管理者はセッションの詳細を含めることができます。

管理者ログインで、VCコース名をクリックします。 クリック **[!UICONTROL インスタンス]** をクリックします。 **[!UICONTROL セッションの詳細]**.  「セッションの詳細」ページの右隅にある「編集」アイコンをクリックして、セッション情報を追加します。

![](assets/session-creation-admin.png)

*バーチャルクラスルームセッション情報を追加*

バーチャルクラスルームモジュールまたはセッションを作成するためにAdobeのLearning ManagerとAdobe Connectが統合されている場合、Connectアカウントでは、ユースケースに十分な数の会議室と同時ユーザーを持つ会議室がサポートされます。 これらの会議室は、Learning Managerのバーチャルクラスルームモジュールをホストするために使用されます。 Learning Manager内のバーチャルクラスルームモジュールまたはセッションごとに、新しいConnectの会議室がLearning Managerによって動的に作成されます。

AdobeのLearning Managerとは別に、Adobe Connectを別途購入する必要があります。

## 学習者の出席 {#learnersattendance}

バーチャルクラスルームコースのホストがセッションに出席しない場合、セッションに出席した学習者の出席は自動的に登録されません。 このような場合、管理者は出席を手動で記録できます。

バーチャルクラスルームコースをクリックし、次のページの左ペインで「出席」をクリックして出席を記録します。
