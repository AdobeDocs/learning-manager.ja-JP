---
jcr-language: en_us
title: カスタムドメインのサポート
description: カスタムドメインは、Learning Manager の Azure インスタンスではサポートされていません。
contentowner: saghosh
exl-id: 162ce268-48e3-4c7e-acb1-5181cebbb18d
source-git-commit: a09c81a6dacbfc4bb55db39e64820ba87ce53d09
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 66%

---

# カスタムドメインのサポート

カスタムドメインは、Learning Manager の Azure インスタンスではサポートされていません。

## 概要 {#overview}

カスタムドメインのサポートにより、お客様は Learning Manager のアカウントで使用できるドメイン名を包括的に管理できます。お客様は、カスタムドメインを別途購入し、Adobe チームと連携して、カスタムドメインを学習プラットフォームのログイン URL として設定する必要があります。

これにより、お客様はログインとアクセスのエクスペリエンスにホワイトラベルを付けて、アドビや Adobe Learning Manager がユーザーに表示されないように設定できます。

例えば、ユーザーがAdobeドメインにいる場合と同じエクスペリエンスを得られるように、ドメインをカスタマイズすることができます。 ABC社が顧客のトレーニングを希望している場合、`abc.com/mylearning`ではなく`learningmanager.adobe.com/abc-inc/mylearning`というドメインへの登録を希望しています。

>[!NOTE]
>
>前提条件として、ドメインを登録する必要があります。登録すると、AdobeがURLのカスタマイズについて説明します。


カスタムドメイン機能は、追加料金で利用できます。 詳細については、カスタマーサクセスマネージャーにお問い合わせください。

* 学習者の役割の場合、ドメインは`https://cdn.<customer_custom_domain>/`で始まります（例： `https://cdn.elearningstage1.cpdomaintest.in/`）
* その他の役割の場合、ドメインは`https://<customer_custom_domain>/`で始まります。 例：`https://elearningstage1.cpdomaintest.in/`
* 実際のログインURLは`https://<customer_custom_domain>/acapindex`または`https://<customer_custom_domain>/login`です。

>[!NOTE]
>
>`<customer_custom_domain>`を組織の実際のドメインに置き換えます。

## アカウントのカスタムドメインを設定する方法 {#howtosetupacustomdomainonanaccount}

前提条件として、お客様はドメイン名を所有し、プロバイダーからドメインを購入する必要があります。

例えば、お客様が架空のドメイン **acme.com** を所有しているとします。 お客様は、**learning.acme.com** から Learning Manager コンテンツが配信されることを希望しています。

次の手順に従って、カスタムドメインを設定します。

1. お客様は、次の **3 つの CNAME** レコードをドメインに追加する必要があります。

   * **learning.acme.com:** Adobeが共有するLearning ManagerのALBパブリックエンドポイント
   * **lrs.learning.acme.com:** learning.acme.comが指すALBパブリックエンドポイント
   * **cdn.learning.acme.com:** CDNエンドポイントがAdobeによって共有されました

1. お客様は、次のドメインの SSL 証明書を提供する必要があります。

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. Adobe は、リクエストをドメインに送信するために、これらの SSL 証明書を AWS ALB にアップロードします。
1. Adobe は、SAN 証明書に learning.acme.com を追加します。
1. Adobe はお客様向けの SP メタデータを生成します。そのメタデータにはカスタムドメイン URL が含まれます。

   * お客様がソーシャルログインを希望する場合、Adobe は、許可される URL のリストにソーシャルサイトのリダイレクト URL パターンを含める必要があります。
   * お客様が SSO を有効にしている場合、お客様は IDP と連携して、ドメインをリダイレクト URL に含める必要があります。 お客様は、IDP メタデータ XML を Adobe と共有する必要があります。 Adobe は、お客様のアカウントの SSO 設定を更新する必要があります。

1. その後、S3 CORS ルールを変更して、お客様のドメインを追加します。
