---
jcr-language: en_us
title: Salesforce向けLearning Managerアプリ
description: Salesforceは、営業およびマーケティングチームに最も人気のあるCRMソリューションの1つです。 SalesforceでAdobeのLearning Managerアプリを使用することで、ユーザーはSalesforceインターフェイスからすべての学習コンテンツにアクセスできます。 ユーザーは、コース、学習プログラム、作業計画書などの割り当てられた学習コンテンツにSalesforce内からアクセスできます。 ユーザーは、管理者から登録とアナウンスに関する通知を受け取ることもできます。
contentowner: jayakarr
source-git-commit: 66dfaaaf723382eada39e2be29dfd49b795107a0
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---



# Salesforce向けLearning Managerアプリ

## 概要 {#overview}

Salesforce™は、営業およびマーケティングチームに最も人気のあるCRMソリューションの1つです。 SalesforceでAdobeのLearning Managerアプリを使用することで、ユーザーはSalesforceインターフェイスからすべての学習コンテンツにアクセスできます。 ユーザーは、コース、学習プログラム、作業計画書などの割り当てられた学習コンテンツにSalesforce内からアクセスできます。 ユーザーは、管理者から登録とアナウンスに関する通知を受け取ることもできます。

現時点では、Salesforce App Exchangeからの承認が保留中のため、Salesforceアプリは使用できません。 アプリのベータ版を確認したい場合は、アカウントマネージャーまたはLearning Managerサポートチームまでお問い合わせください。

## インストールとセットアップ {#installationandsetup}

以下の手順に従って、Salesforce用Learning Managerアプリをインストールおよび設定します。

### 前提条件 {#prerequisites}

1. 組織の統合管理者がSalesforceアプリを承認する必要があります。 このアプリは、統合管理者の役割向けLearning Managerアプリケーションの「主要アプリケーション」セクションに表示されています。
1. アプリのインストールが必要な組織のSalesforceアカウントにアクセスします。 通常、このようなアプリのインストールを行うのは、組織のSalesforce管理者です。 Learning Manager統合管理者でSalesforceアカウントを持っていない場合は、組織のSalesforce管理者までお問い合わせください。

### インストール手順 {#installationsteps}

1. アカウントマネージャーまたはカスタマーサクセスマネージャーにLearning ManagerのアカウントIDを提示し、アカウントでこのアプリを使用できるように依頼します。 また、Salesforce用Learning Manager学習者アプリのインストール可能なパッケージをCSMに申請します。

1. 統合管理者としてLearning Managerアカウントにログインし、アカウントでSalesforceアプリが有効化されていることを確認します。

1. SalesforceアカウントにLearning Managerアプリをインストールするには、アカウントマネージャーまたはカスタマーサクセスマネージャーが提供するインストール可能なパッケージを使用します。 これには本アプリをインストールするSalesforceアカウントの管理者権限が必要です。

1. スナップショットに表示されているオプションを適宜選択し、をクリックします **[!UICONTROL インストール]**.

   ![](assets/install-options.png)

   *「管理者のみにインストール」オプションを選択します。*

   希望する場合 **特定のプロファイル用にインストール**&#x200B;リストからプロファイルを1つ以上選択します。

1. クリック **[!UICONTROL 続行]** ポップアップが表示され、サードパーティのアクセスを確認できます。

   アプリが正常にインストールされたことを確認するメッセージが表示されます。 クリック **完了**.

## ホームページへの通知コンポーネントの追加 {#addnotificationcomponenttothehomepage}

Learning Managerでは、Salesforce管理者がホームページレイアウトにもLearning Manager通知コンポーネントを追加することをお勧めします。 このコンポーネントにより、Salesforceユーザーは学習者アプリのコンテキスト外でも、Learning Managerから課題やその他のアナウンスに関する通知を受け取ることができます。

ホームページレイアウトにLearning Manager通知コンポーネントを追加するには、次の手順に従います。

1. クリック **[!UICONTROL 設定]** をクリックします。 以下のスナップショットに示すように、左側のペインに「ホームページレイアウト」オプションが表示されます。

   ![](assets/homepage-component.png)

   *ホームページレイアウトを選択*

1. レイアウトを選択し、 **[!UICONTROL 編集]**.
1. ページに表示されるAdobeのLearning Manager通知オプションを選択し、 **[!UICONTROL Next]**.
1. 左ペインに表示されるコンポーネントの順序を選択し、プレビューしてクリックします **[!UICONTROL 保存]**.

Learning Managerアプリにログインし、学習者としてSalesforceで使用する方法については、 [Salesforceアプリのヘルプコンテンツ](../../learners/feature-summary/sfdc-app.md).
