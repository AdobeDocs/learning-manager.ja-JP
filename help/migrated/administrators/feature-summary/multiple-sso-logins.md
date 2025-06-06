---
description: Adobe Learning Managerでは、社内ユーザーと社外ユーザーの両方に対して複数のSSO構成で複数のログイン方式をサポートしています。
title: 複数の SSO ログイン
contentowner: saghosh
exl-id: 398816e8-a144-459b-8c39-6517ce4573b4
source-git-commit: f964dd3f1adeadb76f4843c9af229ce5f09afde1
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 38%

---

# 複数の SSO ログイン {#multiple-sso-logins}

管理者は、社内ユーザーと社外ユーザーの両方に対して複数のログイン方式を設定できます。 Adobe Learning Manager では複数の SSO ログインがサポートされているため、管理者はニーズやユースケースに基づいてログイン方式を設定できます。

管理者は、場所や組織などに基づいて、ユーザーグループ別に SSO を構成できます。

1 つのアカウントに SSO 設定を 20 件まで追加できます。 社内と社外の両方のユーザーに対して SSO を設定するために、この設定を使用できます。

>[!NOTE]
>
>複数のSSOを有効にすると、セルフ登録プロファイルで値またはユーザーグループを選択できます。 値を選択すると、ユーザー数が0のユーザーグループが作成されます。 このようなユーザーグループにはユーザーが存在しません。 次のCSVが読み込まれると、このユーザーグループは削除されます。

## 複数の SSO を有効にする

複数のSSOを有効にするには、**設定** > **ログイン方式**&#x200B;を選択します。

セットアップページで、内部ユーザーまたは外部ユーザーに対して[複数のシングルサインオン(SSO)を有効にする]チェックボックス&#39;**&#x200B;**&#39;をオンにします。

複数のSSOを有効にすると、「デフォルトのログイン方法」で選択したログイン方法が、どのSSO構成にもリンクされていないユーザーグループ/プロファイルのデフォルトのログインタイプになります。 デフォルトのログインは、Adobe ID、SSO、ALM ID（社外ユーザー）です。

>[!NOTE]
>
>管理者と必要な権限を持つカスタム管理者は、次の手順を実行できます。

SSOを構成するには、次の手順に従います。

1. 「シングルサインオン(SSO)を構成」をクリックします。
1. 「新しいSSO構成の追加」をクリックします。\
   ![](assets/sso.png)
1. SSO 構成ダイアログで、以下の内容を追加します。

   * SSO の名前を入力します。
   * SSO のタイプ（IDP から開始、または SP から開始）を選択します。

      * 「IDPから開始」を選択した場合は、IDP URLを入力します。 この URL は、アプリケーションで一意の ID で、IDP サービスプロバイダーから提供される情報です。 すべてのAdobe Learning Managerユーザーは、ログイン後にこのURLにリダイレクトされます。
      * IDP プロバイダーから IDP メタデータ XML をアップロードします。 このファイルには、IDP に関する情報が含まれます。この情報を使用すると、Adobe Learning Manager で SAML アサーションを認証できます。
      * 「SPから開始」を選択した場合は、エンティティIDを入力します。 エンティティ ID は、サービスプロバイダー（SP）が提供する URL です。
      * SP のログイン URL を入力します。 ユーザーはこの URL を使用してアプリケーションにログインします。

1. SSO構成がリストに追加されます。

## 社内ユーザーの SSO の設定

### CSV からのユーザー

以下の手順を実行します。

1. アクティブフィールドとその値を含むCSVを読み込みます。
1. 設定/ログイン方式をクリックします。
1. **[!UICONTROL [ログインに複数のシングルサインオン(SSO)を有効にする]]**&#x200B;チェックボックスをオンにします。
1. アクティブフィールドの値にSSO構成をマッピングします。
1. 設定を保存します。CSV を再度インポートします。

### 1 人のユーザー

以下の手順を実行します。

1. 設定/ログイン方式をクリックします。
1. **[!UICONTROL [ログインに複数のシングルサインオン(SSO)を有効にする]]**&#x200B;チェックボックスをオンにします。
1. SSOのアクティブフィールドを選択します。
1. フィールドの値にSSO構成をリンクします。
1. 設定を保存します。1人のユーザーを追加し、アクティブフィールドに値を割り当てます。

### セルフ登録ユーザー

以下の手順を実行します。

1. 設定/ログイン方式をクリックします。
1. **[!UICONTROL [ログインに複数のシングルサインオン(SSO)を有効にする]]**&#x200B;チェックボックスをオンにします。
1. フィールドの値にSSO構成をリンクします。
1. 設定を保存します。1人のユーザーを追加し、アクティブフィールドに値を割り当てます。
1. セルフ登録プロファイルを追加します。
1. 設定したSSOフィールドの値を選択します。

プロファイル設定を保存すると、コピーされたURLから、プロファイルで選択された値にリンクされたSSOにリダイレクトされます。

### 社外ユーザーの SSO の設定

以下の手順を実行します。

1. 社外プロファイルを作成します。
1. 設定/ログイン方式をクリックします。
1. **[!UICONTROL [ログインに複数のシングルサインオン(SSO)を有効にする]]**&#x200B;チェックボックスをオンにします。
1. 作成した社外プロファイルにSSO構成をリンクします。
1. 設定を保存します。

プロファイルの設定を保存すると、コピーされた外部プロファイルのURLは、プロファイルにリンクされたSSOにリダイレクトされます。

## よくある質問

+++ ユーザーに対して複数のSSOを有効にできるのは誰ですか？

管理者とカスタム管理者の両方が、複数の SSO を有効化できます。
+++

+++値が1つの既存または新規のアクティブフィールドを使用できますか。

はい。値が 1 つの既存または新規のアクティブフィールドを使用して、複数の SSO を設定できます。
+++

+++CSVに無効なフィールドがある場合、複数のSSOを設定できないことはありますか？

いいえ、SSO の設定には影響がありません。 構成済みの SSO にユーザーがリダイレクトされます。
+++

+++複数のSSOを設定している場合、管理者がページのアクティブフィールドに新しい値を追加できますか？

はい、管理者はアクティブなフィールドに新しい値を追加できます。
+++

+++SSOにリンクされたフィールドを無効にしたり、削除したりできますか？

はい、SSOにリンクされているフィールドは、SSO設定ページからリンクを解除するまで、無効化または削除できます。
+++
