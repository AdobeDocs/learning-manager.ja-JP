---
jcr-language: en_us
title: Salesforceパッケージのインストール
description: Learning ManagerはSalesforceアプリケーションパッケージを提供します。 SFDCにインストールして設定すると、セールス社員はSFDCポータル内でトレーニングアクティビティを実行できるようになります。 このアプリにより、SFDCユーザーは新しいトレーニングを調べ、推奨事項を表示し、SFDCポータル内ですぐに実行できます。 また、管理者からのアナウンスを、SFDCポータル内のアプリにマストヘッド形式で表示できます。
contentowner: saghosh
source-git-commit: ab6737e8b43222a6538921b0628a504a5f15859d
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 0%

---



# Salesforceパッケージのインストール

## 概要

Learning ManagerはSalesforceアプリケーションパッケージを提供します。 SFDCにインストールして設定すると、セールス社員はSFDCポータル内でトレーニングアクティビティを実行できるようになります。 このアプリにより、SFDCユーザーは新しいトレーニングを調べ、推奨事項を表示し、SFDCポータル内ですぐに実行できます。 また、管理者からのアナウンスを、SFDCポータル内のアプリにマストヘッド形式で表示できます。

### Learning Managerアプリで設定

1. 自分のLearning Manager管理者アカウントに、統合管理者としてログインします。
1. クリック **[!UICONTROL アプリケーション]** > **[!UICONTROL おすすめアプリ]**.
1. クリック **[!UICONTROL Salesforce]**.
1. Salesforceアプリケーションページで、説明に記載されているアプリケーションID（クライアントIDとも呼ばれます）とクライアントシークレットを確認します。
1. クリック **[!UICONTROL 承認]** また、アプリが正常に承認されている必要があります。
1. クリック **[!UICONTROL 開発者向けリソース]** > **[!UICONTROL テストおよび開発用のアクセストークン]**.
1. 「OAuthコードを取得」セクションで、クライアントIDとスコープを「admin:read,admin:write」に設定します。 クリック **[!UICONTROL 送信]**.
1. 「更新トークンの取得」に、クライアントIDとクライアントシークレットを入力します。 クリック **[!UICONTROL 送信]** 更新トークンを確認します。

### Salesforceアプリでのアカウントの作成

1. Salesforceサインアップページでアカウントを作成します。 Salesforceアカウントは、開発者版またはエンタープライズ版で作成する必要があります。  [開発者サインアップURL](https://developer.salesforce.com/signup). Salesforceへのサインアップには、Learning Managerで使用した電子メールIDを使用する必要があります。
1. 確認用メールでアカウントを確認します。
1. パスワードを作成し、Salesforceにログインします。
1. ログイン後にSalesforceのURLに注意してください(例：site.lightning.force.com)

### Learning Managerパッケージのインストール

パッケージをインストールする場合、まずSalesforceで既存のパッケージを削除する必要があります。 アンインストールする前に、次のように設定を有効にする必要があります。 これらの設定の適用は必須です。そうしないと、パッケージをインストールできなくなります。

![](assets/uninstall-package.png)

*Learning Managerパッケージのインストール*

>[!NOTE]
>
>AdobeのLearning Managerアプリは、Salesforce Lightningビューでのみサポートされています。

1. を起動  [Learning ManagerパッケージURL](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Ftest.salesforce.com%2Fpackaging%2FinstallPackage.apexp%3Fp0%3D04t1k0000008YWn&amp;data=04%7C01%7Ckillamse%40adobe.com%7Cf588f553fc694d2edee108d9a5c74711%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C637723097572585825%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&amp;sdata=mhYKVdwvS4F7WPruy0Kvw%2FsqgWxzTQpaZJyEACu8CNw%3D&amp;reserved=0).
1. を **ログイン** ページをクリック **[!UICONTROL カスタムドメインを使用]**.

1. パッケージURLを入力し、 **[!UICONTROL 続行]**. インストールページで「管理者のみにインストール」オプションを選択している必要があります。 このオプションは変更しないでください。
1. クリック **Ins背が高い**. パッケージがインストールされたら、 **[!UICONTROL 完了]**. インストール済みパッケージページが表示され、Learning Managerのインストール済みパッケージというAdobeが表示されます。

1. 設定の横にあるApp Launcherに移動して「Learning Manager Adobe」を検索します。
1. アプリを設定するには、 **[!UICONTROL 設定]**.
1. クリック **[!UICONTROL 新規]** 次の詳細を追加します。

   * **設定：** 任意の名前を入力します。
   * **ClientID**：最初のセクションで取得した値を入力します。
   * **ClientSecret:** 最初のセクションで取得した値を入力します。
   * **RefreshToken:** 最初のセクションで取得した値を入力します。
   * **LearningManagerBaseURL :** Learning ManagerがホストされているサイトのURL。
   * **リダイレクトの無効化：** Learning Managerの学習者ホームページへのリダイレクトを無効にします。

>[!NOTE]
>
>作成できる構成は1つだけです。 別の設定を追加しようとすると、エラーメッセージが表示されます。 この設定は、Salesforceアカウントを学習者アカウントにマッピングします。

### リモートサイト設定の追加

1. ページの右上隅にあるをクリックします。 **[!UICONTROL 設定]**.
1. イン **クイック検索**&#x200B;リモートサイトの設定を検索します。
1. クリック **[!UICONTROL 新しいリモートサイト]**.
1. 詳細を入力します。

   1. **リモートサイト名：** 任意の名前を入力します。
   1. **リモートサイトのURL:** Learning ManagerがホストされているサイトのURL。

1. Learning Managerを起動します。

### Learning Managerアプリの通知を有効にする

1. 右上隅のをクリックします。 **設定**.
1. カスタム通知を検索します。
1. クリック **[!UICONTROL 新規]**.
1. 次の詳細を入力します。

   1. **カスタム通知名：** LearningManagerNotification
   1. **API名：** LearningManagerNotification

1. 両方を選択 **デスクトップ** および **モバイル** をサポート対象チャンネルに設定します。

1. クリック **[!UICONTROL 保存]**.
1. モバイルデバイスのプッシュ通知を有効にするには、次の手順に従います。

   1. 携帯電話にSalesforceモバイルアプリをインストールします。
   1. 資格情報を使用してアプリにログインします。
   1. に移動 **設定** > **通知配信設定**.
   1. iOSおよびAndroid用のSalesforceを追加します。

### SalesforceからのLearning Managerのアンインストール

1. Salesforceアプリで「インストール済みパッケージ」に移動します。
1. クリック **[!UICONTROL アンインストール]**.

## Salesforceユーザー向けにLearning Managerを設定する

Learning Managerアプリは、Salesforceアカウント内のユーザーも利用できます。 Salesforce管理者は、プロファイルに基づいてユーザーを追加できます。 Salesforceプロファイルは、Learning Managerのプロファイルに似ています。 例えば、管理者、統合管理者、インストラクターなどです。 Salesforce管理者は、カスタムプロファイルも作成できます。

### プロフィール

Salesforce管理者は、ユーザーにプロファイルを割り当てるか、カスタムプロファイルを作成することができます。

>[!NOTE]
>
>SalesforceとLearning Managerの両方にユーザーが存在している必要があります。

![](assets/create-profile.png)

*学習者へのプロファイルの割り当て*

学習者を追加する場合、学習者に特定のプロファイルを割り当てる必要があります。 次に、そのプロファイルに移動して、必要なアクセス権を付与します。

学習者がLearning Managerアプリを表示できるようにするために、すべての学習者に対してアプリを有効にする必要があります。

次に、Learning Managerアプリにアクセス権を付与します。

![](assets/permission-set.png)

*Learning Managerアプリにアクセスするための権限を追加*

パッケージをインストールすると、新しい権限セットが作成され、 **Learning Manager Adobe**. 権限セットに移動し、ユーザーを追加します。

ユーザーを選択し、それに応じて権限を割り当てます。 これで、学習者がLearning Managerアプリにアクセスできるようになりました。

次に、プロファイル（ユーザーの標準プロファイルなど）を選択し、プロファイルをクリックします。 クリック **[!UICONTROL 編集]** そして **カスタムアプリ設定** セクションで、チェックボックスをオンにする **Learning ManagerのAdobe**. これにより、ユーザーがアプリにアクセスできるようになります。

を **カスタムタブ設定** セクション内の **学習者ホーム** ドロップダウンリストで、オプションを選択します **[!UICONTROL デフォルトをオン]**.

すべてのプロファイルに対して、アプリを表示可能にしておく必要があります。

クリック **[!UICONTROL 保存]** また、すべてのプロファイルに属する学習者がLearning Managerアプリにアクセスできます。
