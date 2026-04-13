---
description: 統合設定を使用してAdobe Learning Managerとサードパーティソリューションを連携する方法の詳細
jcr-language: en_us
title: Adobe Learning Managerの統合設定
source-git-commit: 03123dcd8d9066cdfcb0fe97e61acb3df625a23e
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 4%

---


# Adobe Learning Managerの統合設定

## ログイン方法

Adobe Learning Managerには複数のログイン方式が用意されており、内部ユーザーと外部ユーザーのアクセスを安全かつ柔軟に行うことができます。 管理者は、組織の要件に基づいてこれらのログイン方法を設定できます。

使用できるログイン方法は次のとおりです。

* Adobe Learning Manager ID
* Adobe ID
* シングルサインオン

### 社内ユーザー

「内部ユーザー」セクションでは、内部ユーザー専用のログインオプションを設定できます。 社内ユーザーは、Adobe IDまたはシングルサインオン(SSO)を使用してアカウントにアクセスできます。

**Adobe ID:**

* 社内ユーザーは、Adobe IDの資格情報を使用してログインできます。
* アドビのサービスを既に使用している組織に適しています。

**シングルサインオン(SSO):**

* 内部ユーザーが組織のIDプロバイダー(IdP)を使用するためのSSOを許可します。
* シームレスなログインエクスペリエンスを実現するSAML 2.0ベースの認証をサポートします。

社内ユーザーのSSOログインを許可するには、「ログインに複数のシングルサインオン(SSO)を有効にする」を選択して、SSOの構成を開始します。

Adobe Learning Managerの&#x200B;**[!UICONTROL SSOアクティブフィールド]**&#x200B;は、シングルサインオン(SSO)構成を特定のユーザー属性またはグループにマップするために使用されます。 このフィールドを設定して、組織、場所、またはその他の条件に基づいて、内部ユーザーに対して複数のSSO設定を有効にできます。

### 外部ユーザー

Adobe Learning Managerの「社外ユーザー」セクションで、Adobe Learning Managerアカウントへの制限付きアクセスを必要とする社外学習者（パートナーやエージェンシーなど）を管理できます。 このセクションでは、登録プロファイルの作成、社外ユーザーグループの管理、および社外学習者に固有の設定を行うためのツールが用意されています。

社外ユーザーは、次の方法でログインできます。

* Adobe ID：外部ユーザーは、Adobe IDの資格情報を使用してログインできます。
* シングルサインオン(SSO)：管理者が設定した場合は、外部ユーザーがSSOでログインできます。
* Adobe Learning Manager ID：社外ユーザーは、プラットフォームにアクセスするためのLearning Managerのユーザー名とパスワードを作成できます。

**キーポイント：**

* 社外ユーザーに対して1つ以上のログイン方法を有効にすることができます。
* 「Adobe Learning Manager ID」を選択した場合、外部ユーザーは自分の資格情報を作成する必要があります。
* 組織のニーズに応じて、社外ユーザーに対してSSOを構成できます。

### Adobe Learning ManagerでのSSO設定

Adobe Learning Managerはシングルサインオン(SSO)をサポートしているため、認証を1回行えば、複数のアプリケーションにアクセスできます。 管理者は、SAML 2.0ベースのプロバイダーを使用して、社内ユーザーと社外ユーザーの両方にSSOを構成できます。

詳細については、[Adobe Learning ManagerでのSSOログイン](/help/migrated/administrators/feature-summary/multiple-sso-logins.md)を参照してください。

>[!NOTE]
>
>* 1 つのアカウントに SSO 設定を 20 件まで追加できます。
>* SAML 2.0ベースのSSOプロバイダーに関するサポートについては、Adobeサポートにお問い合わせください。

## データソース

データソースを使用すると、または統合管理者は、ユーザーや学習データを読み込んで同期するために、外部システムを統合することができます。 この機能により、HRMS、Salesforce、FTPなどのシステムとのシームレスなデータ管理と同期が可能になります。

**データソースの種類の例**

* **FTPコネクタ**: FTPベースのデータソースを使用すると、セキュリティで保護されたファイル転送プロトコルを介してユーザーのデータファイルをAdobe Learning Managerに直接アップロードできます。 これらの接続は、ユーザー情報、コース登録、およびその他のバルクデータ操作をバッチで読み込む場合に特に便利です。
* **サードパーティとの統合** : Adobe Learning Managerは、事前定義済みのコネクタを介したさまざまなエンタープライズシステムとの統合をサポートしています。 これらの統合には、人事管理システム、顧客関係管理プラットフォーム、およびその他の学習管理システムが含まれます。
*** Salesforceとの統合**: Salesforceコネクターを使用すると、SalesforceとAdobe Learning Managerの間でユーザーデータ、コース情報、学習記録を直接同期できます。

詳細については、[Adobe Learning Managerのコネクタ](/help/migrated/integration-admin/feature-summary/connectors.md)を参照してください。

## ピアアカウント

Adobe Learning Managerのピアアカウントでは、購入した席を共有し、関連するアカウント間でレポートを表示できます。 この機能は、組織が異なるアカウント間で共同作業やリソースの共有を行う場合に便利です。

詳しくは、Adobe Learning Managerの[ピアアカウント](/help/migrated/administrators/feature-summary/peer-account.md)を参照してください。





