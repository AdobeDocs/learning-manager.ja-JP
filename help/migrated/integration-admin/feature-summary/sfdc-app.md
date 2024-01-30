---
jcr-language: en_us
title: Salesforce 用 Learning Manager アプリ
description: Salesforceは、営業およびマーケティングチームに最も人気のあるCRMソリューションの1つです。 Salesforce で Adobe Learning Manager アプリを用いることで、ユーザーは Salesforce インターフェイスからすべての学習コンテンツにアクセスすることができます。ユーザーは、コース、学習プログラム、ジョブエイドなど、割り当てられた学習コンテンツに Salesforce 内からアクセスすることが可能です。またユーザーは管理者から登録とアナウンスに関する通知を受信することができます。
contentowner: jayakarr
source-git-commit: 66dfaaaf723382eada39e2be29dfd49b795107a0
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 57%

---



# Salesforce 用 Learning Manager アプリ

## 概要 {#overview}

Salesforce™は、営業およびマーケティングチームに最も人気のあるCRMソリューションの1つです。 Salesforce で Adobe Learning Manager アプリを用いることで、ユーザーは Salesforce インターフェイスからすべての学習コンテンツにアクセスすることができます。ユーザーは、コース、学習プログラム、ジョブエイドなど、割り当てられた学習コンテンツに Salesforce 内からアクセスすることが可能です。またユーザーは管理者から登録とアナウンスに関する通知を受信することができます。

現在、Salesforce アプリは、Salesforce AppExchange からの承認が保留中のため使用できません。アプリのベータ版を確認したい場合は、アカウントマネージャーまたはLearning Managerサポートチームまでお問い合わせください。

## インストールとセットアップ {#installationandsetup}

以下の手順に従って、Salesforce 用 Learning Manager アプリをインストールおよび設定します。

### 前提条件 {#prerequisites}

1. 組織の統合管理者が Salesforce アプリを承認する必要があります。 このアプリは、統合管理者の役割向け Learning Manager アプリケーションの「主要アプリケーション」セクションに表示されています。
1. アプリのインストールが必要な組織の Salesforce アカウントにアクセスします。 通常このアプリのインストールを必要とするのは、組織の Salesforce 管理者です。 Learning Manager 統合管理者で Salesforce アカウントを持っていない場合は、組織の Salesforce 管理者までお問い合わせください。

### インストール手順 {#installationsteps}

1. アカウントマネージャーまたはカスタマーサクセスマネージャーに Learning Manager アカウント ID を提示し、アカウントでのアプリの使用を有効化するよう依頼します。また、Salesforce用Learning Manager学習者アプリのインストール可能なパッケージをCSMに申請します。

1. 統合管理者としてLearning Managerアカウントにログインし、アカウントでSalesforceアプリが有効化されていることを確認します。

1. Salesforce アカウントに Learning Manager アプリをインストールするには、アカウントマネージャーまたはカスタマーサクセスマネージャーが提供するインストール可能なパッケージを使用します。これには本アプリをインストールするSalesforceアカウントの管理者権限が必要です。

1. スナップショットに表示されているオプションを適宜選択し、をクリックします **[!UICONTROL インストール]**.

   ![](assets/install-options.png)

   *「管理者のみにインストール」オプションを選択します。*

   希望する場合 **特定のプロファイル用にインストール**&#x200B;リストからプロファイルを1つ以上選択します。

1. クリック **[!UICONTROL 続行]** ポップアップが表示され、サードパーティのアクセスを確認できます。

   アプリが正常にインストールされたことを確認するメッセージが表示されます。 **「完了」**&#x200B;をクリックします。

## ホームページへの通知コンポーネントの追加 {#addnotificationcomponenttothehomepage}

Learning Manager では、Salesforce 管理者がホームページレイアウトにも Learning Manager 通知コンポーネントを追加することを推奨します。このコンポーネントにより、Salesforce ユーザーは学習者アプリのコンテキスト外でも、Learning Manager から課題やその他の通知を受信できます。

ホームページレイアウトにLearning Manager通知コンポーネントを追加するには、次の手順に従います。

1. クリック **[!UICONTROL 設定]** をクリックします。 以下のスナップショットに示すように、左側のペインに「ホームページレイアウト」オプションが表示されます。

   ![](assets/homepage-component.png)

   *ホームページレイアウトを選択*

1. レイアウトを選択し、 **[!UICONTROL 編集]**.
1. ページに表示されるAdobeのLearning Manager通知オプションを選択し、 **[!UICONTROL Next]**.
1. 左ペインに表示されるコンポーネントの順序を選択し、プレビューしてクリックします **[!UICONTROL 保存]**.

Learning Managerアプリにログインし、学習者としてSalesforceで使用する方法については、 [Salesforceアプリのヘルプコンテンツ](../../learners/feature-summary/sfdc-app.md).
