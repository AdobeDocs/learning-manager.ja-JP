---
jcr-language: en_us
title: Learning Manager と AEM の統合
description: Learning Managerは、学習コンテンツ管理システムが組み込まれた学習管理システムです。 ユーザーは、学習コンテンツを Learning Manager にアップロードして管理します。これにより Learning Manager で、バージョン管理、コースへの割り当て、学習者への表示の定義、使用状況の追跡、管理者への報告を行うことができます。
contentowner: saghosh
exl-id: 61fae7bd-1703-4ed1-9bd9-07387d67a91c
source-git-commit: 447a4e041d74cf086afada3794ac08a04e70c2ca
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 45%

---

# Learning Manager と AEM の統合

Learning Managerは、学習コンテンツ管理システムが組み込まれた学習管理システムです。 ユーザーは、学習コンテンツを Learning Manager にアップロードして管理します。これにより Learning Manager で、バージョン管理、コースへの割り当て、学習者への表示の定義、使用状況の追跡、管理者への報告を行うことができます。

一方、ユーザーはアセット管理システムにコンテンツを保存して管理することもできます。 この方法でも、コンテンツを他のさまざまな機能で再利用できます。

学習者アプリにあるさまざまなストリップは、AEM サイトに埋め込むことができます。 AEM サイトにサインインする学習者は、これらのストリップ内で自身の特定のトレーニングデータを参照できます。

## コンテンツパッケージのダウンロード {#downloadthecontentpackage}

インストーラーは AEM コンテンツパッケージに付属しています。 [***パッケージのダウンロード***](https://github.com/adobe/adobe-learning-manager-reference-site).

コンテンツパッケージはzipファイルとして利用可能であり、AEM 6.4およびAEM 6.5と互換性があります。

## Learning Manager コンポーネントのインストール {#installcaptivateprimecomponent}

AEM Package Manager を使用して、Learning Manager コンテンツパッケージをインストールします。

>[!NOTE]
>
>パッケージのインストールについては、を参照してください。  [***パッケージを使用する方法***](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#how-to-work-with-packages).

1. AEM 作成者として、AEM Package Manager を開きます。
1. **[!UICONTROL 「パッケージのアップロード」]**&#x200B;ボタンをクリックします。
1. クリック **[!UICONTROL 参照]** コンテンツパッケージをアップロードします。
1. **[!UICONTROL 「アップロード」]**&#x200B;をクリックします。
1. パッケージのアップロード後に、コンテンツパッケージを選択し、**[!UICONTROL 「インストール」]**&#x200B;をクリックして、コンテンツパッケージをインストールします。

   ![](assets/install-package.jpg)

   *コンテンツパッケージのインストール*

## 更新トークンの生成 {#generatetherefreshtoken}

AEM 管理者は、Learning Manager アカウントからの更新トークンを必要とします。Learning Manager統合管理者は更新トークンを生成します。

1. AEM サイトのおすすめアプリを承認します。

   クリック **[!UICONTROL アプリケーション]** > **[!UICONTROL おすすめアプリ]** > **[!UICONTROL Adobe Experience Manager - Sites]**.

   ![](assets/launch-aem.jpg)

   *アプリを承認*

1. クリック **[!UICONTROL アプリケーション]** > **[!UICONTROL おすすめアプリ]** AEMサイトのアプリケーションを開きます。

   アプリケーションの ID と説明をコピーします。

1. クリック **[!UICONTROL 開発者向けリソース]** > **[!UICONTROL アクセストークン]**.

   ![](assets/click-tokens.jpg)

   *アクセストークンの生成*

1. 次の情報を入力します。

   * アプリケーション ID であるクライアント ID。
   * 説明に記されているクライアントシークレット。

1. OAuthコードを取得します。 リダイレクト URL で V2 API を使用する必要があります。
1. クリック **[!UICONTROL 送信]** 更新トークンを取得します。

## AEM でのウィジェットの設定 {#configurethewidgetinaem}

ウィジェット設定の場合、AEM作成者はLearning Manager統合管理者が提供する更新トークンのみを必要とします。

複数のページに複数のアカウント構成を設定することもできます。

1. クリック **[!UICONTROL ツール]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Learning Managerウィジェットの設定]**.
1. **[!UICONTROL 「作成」]**&#x200B;をクリックします。
1. 更新トークンを入力します。 その他の設定を行います。
1. EU地域の場合、ホスト名は「learningmanagereu」に変更する必要があります。
1. 設定を保存して閉じます。
1. 設定を選択してから公開します。

## AEM 作成者 {#aemauthor}

AEM 作成者は、まずコンポーネントを AEM テンプレートに追加する必要があります。

AEM 作成者は、Adobe Learning Manager コンポーネントをドラッグ＆ドロップすることで設定を進めることができます。

Learning Managerコンポーネントを使用するには、上記の手順で作成した構成をページにマッピングする必要があります。  作成者は、「ページプロパティ」の下で「編集」を選択して、設定をマッピングできます **[!UICONTROL 詳細]** > **[!UICONTROL 設定]** > **[!UICONTROL クラウド設定]** 設定のパスを指定します。 作成者は、このようにして、複数の Learning Manager アカウントの構成を作成し、各構成を個々のサイトページにマップできます。構成がページにマップされていない場合、コンポーネントは、構成が見つかるまで、親ページから構成を再帰的に読み取ります。

## 学習者 {#learner}

学習者は、ページ内からコースを受講できます。

Learning Manager ウィジェットにアクセスする場合、学習者は AEM ユーザーとしてログインしている必要があります。プロパティ **電子メール** 学習者のrep:Userノードの/profileノードに存在する必要があります。 この電子メールは、Learning Manager アカウントに存在する電子メールとまったく同じにする必要があります。

学習者は、ページ内からコースを受講できます。

コースの進行状況も保存されます。

次のウィジェットが用意されています。

1. ゲーミフィケーション
1. 学習カレンダー
1. ソーシャルウィジェット
1. カタログウィジェット
1. 学習状況
1. ピアの学習に基づいて推奨
1. 管理者による推奨
1. 学習者の関心に基づいて推奨

推奨がない場合は、ウィジェットは空白で表示されます。

## Skyline のサポート

Skylineは、AEMのクラウド版です。 まず、パッケージマネージャーからSkylineをインストールする必要があります。 AEMでSkylineコンポーネントを使用するには、Learning Managerアカウントにログインしている必要があります。 つまり、ユーザーの電子メールアドレスがアカウントに存在している必要があります。

### Skyline をデプロイする

Skylineの設定手順については、  [GitHubリポジトリ](https://github.com/adobe/captivate-prime-aem-components).

## カタログウィジェット

カタログウィジェットには、特定のカタログまたはカタログのセットに由来するトレーニングがユーザーに表示されます。 ページプロパティの「プロパティ」セクションで、オプションの一覧から「カタログ」を選択します。

<!--![](assets/catalog-widget.png)-->

カタログウィジェットには、次のオプションが含まれます。

* **[!UICONTROL カタログID]:** 表示が必要なトレーニングを示す、コンマで区切られたカタログのID。
* **[!UICONTROL 並べ替え]:** トレーニングの並べ替え順序。 名前、日付、作成日、登録日などのオプションがあります。
* **[!UICONTROL 学習者の状態]:** enrolled（登録済み）、started（開始）、completed（完了）、not enrolled（未登録）というフィルターを使用している、すべてのトレーニングを返します。 ソートオプションがdateEnrolled、dueDate、またはdateEnrolledの場合、検索結果は表示されません。
* **[!UICONTROL スキル名]:** トレーニングを正確にフィルタリングするのに使用するスキル。
* **[!UICONTROL タグ名]:** 結果を正確にフィルタリングするのに使用するタグ。

カスタマイズ可能な追加コンポーネントをいくつか紹介します。

**[!UICONTROL 学習目標タイプ]:** 学習目標のタイプに従ってフィルターします。 サポートされているタイプは、course（コース）、certification（資格認定）、jobAid（作業計画書）、learningProgram（学習プログラム）です。

AEMでは、ストリップ内のカードのタイトルは最初は空白になります。 プロパティで、widgets.htmlにタイトル名を入力します。

**カスタマイズ**

widgets.htmlを使用して、レイアウトの外観をカスタマイズできます。 表示されるカードの見た目を変更し、テーマをカスタマイズできます。

を **[!UICONTROL 一般設定]** ここでは、カードのメインカラーとサブカラーを選択したり、プロパティを指定したりして、テーマをカスタマイズできます。

```
{ 
 "globalCssText":"@import url('https://fonts.googleapis.com/css2?family=Grandstander:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Montserrat:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');", 
 "fontNames":"Grandstander", 
 "cardLayout":{ 
 "cardLayoutName":"compact", 
 "cardPrimaryColor":"#376BA4", 
 "cardSecondaryColor":"#F98EB0", 
 "startedStateTextColor":"#ffffff", 
 "continueStateTextColor":"#ffffff", 
 "revisitStateTextColor":"#ffffff", 
 "startedStateColor":"#a0a0a0", 
 "continueStateColor":"#f9a122", 
 "revisitedStateColor":"#7fbc64", 
 "textPrimaryColor":"#ffffff", 
 "textSecondaryColor":"#d93f3f", 
 "navIconColor":"#a0a0a0" 
 } 
}
```

### 上位のLO登録を無視

もし **上位のLO登録を無視** このチェックボックスがオンであり、ユーザーが学習プログラムまたは資格認定に直接登録されている場合、その資格認定または学習プログラムに関するコースがウィジェットでユーザーに表示されます。

このチェックボックスがオフの場合、ユーザーが直接登録されていない学習プログラムまたは資格認定に含まれるコースは表示されません。

![](assets/higher-order-lo.png)

*上位のLO登録を無視するチェックボックスを選択します。

設定がウィジェットに適用されます。

### セキュリティ

「クライアント ID」と「クライアントシークレット」というフィールドが追加されます。また、更新トークンがマスクされます。ユーザーが設定全体を作成した後、ユーザーが設定を編集するために再度開いた場合、または他のユーザーがこの設定を開いた場合、更新トークンはマスクされます。
