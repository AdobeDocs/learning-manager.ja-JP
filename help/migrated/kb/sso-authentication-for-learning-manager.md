---
description: SSO 認証を設定して Learning Manager アカウントにログインする際に、このドキュメントが役立ちます。
jcr-language: en_us
title: SSO 認証を使用して Learning Manager にログイン
contentowner: dvenkate
exl-id: ef5ab232-0a87-4f76-8dfd-b2497f360cbe
source-git-commit: 1529039e35d4190864e96826bfbea25dcad17c73
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 68%
---
# SSO 認証を使用して Learning Manager にログイン

SSO 認証を設定して Learning Manager アカウントにログインする際に、このドキュメントが役立ちます。

SSO 認証を設定するには、次の手順を実行します。

1. **[!UICONTROL 設定]**／**[!UICONTROL ログインメソッド]**&#x200B;を開きます。

   ![](assets/login-methods.png)

1. 要件に応じて、「**[!UICONTROL 内部ユーザー]**」または「**[!UICONTROL 外部ユーザー]**」を選択します。
1. [**[!UICONTROL ログイン]**]オプションの横のドロップダウンをクリックし、[**[!UICONTROL シングルサインオン]**]を選択します。

   ![](assets/single-sign-on.png)

1. シングルサインオン(SSO)の設定を調整するには、**[!UICONTROL [変更]]**&#x200B;をクリックしてください。

   ![](assets/change.png)

1. サービスプロバイダーから提供された&#x200B;**[!UICONTROL IDPによる認証URL]**&#x200B;を入力し、**[!UICONTROL IDPメタデータXMLファイル]**&#x200B;をクリックしてXMLファイルをアップロードしてください。

   ![](assets/sso-configuration.png)

   Learning Manager に設定する SSO は、SAML 2.0 に対応している必要があります。

   これで、SSO 認証を使用して Learning Manager にログインできるようになりました。
