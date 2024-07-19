---
jcr-language: en_us
title: Salesforce パッケージのインストール
description: Learning ManagerはSalesforceアプリケーションパッケージを提供します。 SFDC にインストールして設定すると、セールス社員は SFDC ポータル内でトレーニングアクティビティを実行できるようになります。 このアプリから、SFDC ユーザーは新しいトレーニングを調べ、推奨事項を表示し、SFDC ポータル内ですぐに実行できます。 また、管理者からのアナウンスを、SFDCポータル内のアプリにマストヘッド形式で表示できます。
contentowner: saghosh
exl-id: 2b1c32e7-81af-4c13-a2bd-66684cde084e
source-git-commit: fb946ae98dce45156e2f4c1cf992319405403ea9
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 47%

---

# Salesforce パッケージのインストール

## 概要

Learning ManagerはSalesforceアプリケーションパッケージを提供します。 SFDC にインストールして設定すると、セールス社員は SFDC ポータル内でトレーニングアクティビティを実行できるようになります。 このアプリから、SFDC ユーザーは新しいトレーニングを調べ、推奨事項を表示し、SFDC ポータル内ですぐに実行できます。 また、管理者からのアナウンスを、SFDCポータル内のアプリにマストヘッド形式で表示できます。

### Learning Manager アプリケーションで設定

1. 自分の Learning Manager 管理者アカウントに、統合管理者としてログインします。
1. **[!UICONTROL アプリケーション]** > **[!UICONTROL おすすめアプリ]**&#x200B;をクリックします。
1. **[!UICONTROL Salesforce]**&#x200B;をクリックします。
1. Salesforceアプリケーションページで、説明に記載されているアプリケーションID（クライアントIDとも呼ばれます）とクライアントシークレットを確認します。
1. 「**[!UICONTROL 承認]**」をクリックすると、アプリが正常に承認されます。
1. **[!UICONTROL 開発者向けリソース]** > **[!UICONTROL テストおよび開発用のアクセストークン]**&#x200B;をクリックします。
1. 「OAuthコードを取得」セクションで、クライアントIDとスコープを「admin:read,admin:write」に設定します。 「**[!UICONTROL 送信]**」をクリックします。
1. 「更新トークンを取得」で、クライアント ID とクライアントシークレットを入力します。 **[!UICONTROL [送信]]**&#x200B;をクリックして、更新トークンを確認します。

### Salesforce アプリでのアカウントの作成

1. Salesforce のサインアップページでアカウントを作成します。 Salesforceアカウントは、開発者版またはエンタープライズ版で作成する必要があります。  [開発者サインアップURL](https://developer.salesforce.com/signup)。 Salesforceへのサインアップには、Learning Managerで使用した電子メールIDを使用する必要があります。
1. 確認用の電子メールからアカウントを確認します。
1. パスワードを作成し、Salesforce にサインインします。
1. ログイン後にSalesforceのURLに注意してください(例：site.lightning.force.com)

### Learning Manager パッケージのインストール

パッケージをインストールする場合、まず Salesforce で既存のパッケージを削除する必要があります。 アンインストールする前に、次のように設定を有効にする必要があります。 パッケージのインストールには、これらの設定の適用が必須です。

![](assets/uninstall-package.png)

*Learning Managerパッケージをインストール*

>[!NOTE]
>
>Adobe Learning Managerアプリは、Salesforce Lightningビューでのみサポートされています。

1. [Learning ManagerパッケージのURL](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tDb000000LRvP)を起動します。
1. **ログイン**&#x200B;ページで、[**[!UICONTROL カスタムドメインを使用]**]をクリックします。

1. パッケージのURLを入力し、**[!UICONTROL [続行]]**&#x200B;をクリックします。 インストールページで「管理者のみにインストール」オプションを選択している必要があります。 このオプションは変更しないでください。
1. **InsTall**&#x200B;をクリックします。 パッケージがインストールされたら、[**[!UICONTROL 完了]**]をクリックします。 インストール済みパッケージページが表示され、Adobe Learning Manager のインストール済みパッケージが表示されます。

1. 設定の横にある App Launcher に移動して「Adobe Learning Manager」を検索します。
1. アプリを構成するには、[**[!UICONTROL 構成]**]をクリックします。
1. **[!UICONTROL 新規]**&#x200B;をクリックして、次の詳細を追加します：

   * **Config：**&#x200B;任意の名前を入力します。
   * **ClientID**：最初のセクションで取得した値を入力します。
   * **ClientSecret:**&#x200B;最初のセクションで取得した値を入力します。
   * **RefreshToken:**&#x200B;最初のセクションで取得した値を入力します。
   * **LearningManagerBaseURL:** Learning ManagerがホストされているサイトのURLです。
   * **リダイレクトの無効化：** Learning Manager の学習者ホームページへのリダイレクトを無効にします。

>[!NOTE]
>
>作成できる構成は1つだけです。 構成をさらに追加しようとすると、エラーメッセージが表示されます。 この構成は、Salesforce アカウントを学習者アカウントにマッピングします。

### リモートサイトの設定の追加

1. ページの右上隅で、[**[!UICONTROL セットアップ]**]をクリックします。
1. **クイック検索**&#x200B;で、リモートサイトの設定を検索します。
1. **[!UICONTROL 新しいリモートサイト]**&#x200B;をクリックします。
1. 詳細を入力します：

   1. **リモートサイト名：**&#x200B;任意の名前を入力します。
   1. **リモートサイトの URL：** Learning Manager がホストされているサイトの URL です。

1. Learning Manager を起動します。

### Salesforceの信頼済みURLにAdobeドメインを追加する

信頼済みURLにAdobeドメインを追加するには、次の手順に従います。

1. Salesforceコンソールで、**[!UICONTROL 設定]**/**[!UICONTROL 簡易検索]**&#x200B;に移動します。
1. **[!UICONTROL 信頼済みURL]**&#x200B;を検索し、**[!UICONTROL 新しい信頼済みURL]**&#x200B;を選択します。
1. 「**[!UICONTROL API名]**」フィールドに名前を入力します。
1. URLフィールドに`*.adobe.com`を入力します。
1. **CSPディレクティブ**&#x200B;のすべてのチェックボックスをオンにして、変更を保存します。
1. Salesforceアプリの更新トークンを編集して保存します。
1. Salesforceアプリを再起動します。

### Learning Manager アプリケーションの通知を有効にする

1. 右上隅の[**セットアップ**]をクリックします。
1. カスタム通知を検索します。
1. [**[!UICONTROL 新規]**]をクリックします。
1. 次の情報を入力します。

   1. **カスタム通知名：** LearningManagerNotification
   1. **API名：** LearningManagerNotification

1. **デスクトップ**&#x200B;と&#x200B;**モバイル**&#x200B;の両方を、サポートされているチャネルとして選択してください。

1. **[!UICONTROL 「保存」]**&#x200B;をクリックします。
1. モバイルデバイスのプッシュ通知を有効にするには、次の手順に従います：

   1. 携帯電話に Salesforce モバイルアプリをインストールします。
   1. 資格情報を使用してアプリにログインします。
   1. **セットアップ**/**通知配信設定**&#x200B;に移動します。
   1. iOS および Android 用の Salesforce を追加します。

### Salesforce からの Learning Manager のアンインストール

1. Salesforceアプリで「インストール済みパッケージ」に移動します。
1. 「**[!UICONTROL アンインストール]**」をクリックします。

## Salesforce ユーザー用の学習マネージャーの設定

Learning Manager アプリは、Salesforce アカウント内のユーザーも利用できます。Salesforce 管理者は、プロファイルに基づいてユーザーを追加できます。 Salesforce プロファイルは、Learning Manager のプロファイルと類似しています。たとえば、管理者、統合管理者、インストラクターなどです。 Salesforce 管理者は、カスタムのプロファイルも作成できます。

### プロファイル

Salesforce 管理者は、ユーザーにプロファイルを割り当てるか、カスタムのプロファイルを作成することができます。

>[!NOTE]
>
>SalesforceとLearning Managerの両方にユーザーが存在している必要があります。

![](assets/create-profile.png)

*学習者にプロファイルを割り当てる*

学習者を追加する場合、学習者に特定のプロファイルを割り当てる必要があります。 次に、そのプロファイルに移動して、必要なアクセス権を付与します。

学習者がLearning Managerアプリを表示できるようにするために、すべての学習者に対してアプリを有効にする必要があります。

次に、Learning Manager アプリにアクセス権を付与します。

![](assets/permission-set.png)

*Learning Managerアプリにアクセスするための権限を追加*

パッケージをインストールすると、新しいアクセス許可セット&#x200B;**Adobe Learning Managerユーザー**&#x200B;が作成されます。 権限セットに移動し、ユーザーを追加します。

ユーザーを選択し、アクセス権を割り当てます。 これで、学習者が Learning Manager アプリにアクセスできるようになりました。

次に、プロファイル（ユーザーの標準プロファイルなど）を選択し、そのプロファイルをクリックします。 **[!UICONTROL [編集]]**&#x200B;をクリックし、**[カスタムアプリ設定]**&#x200B;セクションで&#x200B;**[Adobe Learning Manager]**&#x200B;のチェックボックスをオンにします。 これにより、ユーザーがアプリにアクセスできるようになりました。

**カスタムタブ設定**&#x200B;セクションの&#x200B;**「学習者ホーム」**&#x200B;ドロップダウンリストで、**[!UICONTROL 「デフォルトでオン」]**&#x200B;オプションを選択します。

すべてのプロファイルに対して、アプリを表示可能にすることが必要です。

**[!UICONTROL 「保存」]**&#x200B;をクリックすると、すべてのプロファイルに属する学習者がLearning Managerアプリにアクセスできます。
