---
jcr-language: en_us
title: カスタムドメインのサポート
description: カスタムドメインは、Learning Manager の Azure インスタンスではサポートされていません。
contentowner: saghosh
source-git-commit: 8635072782253cbac3f913953797cae7c0bc5ef4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 67%

---



# カスタムドメインのサポート

カスタムドメインは、Learning Manager の Azure インスタンスではサポートされていません。

## 概要 {#overview}

カスタムドメインのサポートにより、お客様は Learning Manager のアカウントで使用できるドメイン名を包括的に管理できます。お客様は、カスタムドメインを別途購入し、Adobe チームと連携して、カスタムドメインを学習プラットフォームのログイン URL として設定する必要があります。

これにより、お客様はログインとアクセスのエクスペリエンスにホワイトラベルを付けて、アドビや Adobe Learning Manager がユーザーに表示されないように設定できます。

例えば、ユーザーがAdobeドメインにいる場合と同じエクスペリエンスを得られるように、ドメインをカスタマイズすることができます。 ABC社が顧客のトレーニングを希望する場合は、 `abc.com/mylearning`の代わりに `learningmanager.adobe.com/abc-inc/mylearning`.

>[!NOTE]
>
>前提条件として、ドメインを登録する必要があります。登録すると、AdobeがURLのカスタマイズについて説明します。


カスタムドメイン機能は、追加料金で利用できます。 詳細については、カスタマーサクセスマネージャーにお問い合わせください。

* 学習者の役割の場合、ドメインは次で始まります `https://cdn.<customer_custom_domain>/` 例えば、 `https://cdn.elearningstage1.cpdomaintest.in/`
* その他の役割の場合、ドメインは `https://<customer_custom_domain>/`. 例：`https://elearningstage1.cpdomaintest.in/`

`<customer_custom_domain>` カスタマイズ可能なパーツです。

## アカウントのカスタムドメインを設定する方法 {#howtosetupacustomdomainonanaccount}

前提条件として、お客様はドメイン名を所有し、プロバイダーからドメインを購入する必要があります。

例えば、お客様が架空のドメイン **acme.com** を所有しているとします。 お客様は、**learning.acme.com** から Learning Manager コンテンツが配信されることを希望しています。

次の手順に従って、カスタムドメインを設定します。

1. お客様は、次の **3 つの CNAME** レコードをドメインに追加する必要があります。

   * **learning.acme.com:** Adobeが共有するLearning ManagerのALBパブリックエンドポイント
   * **lrs.learning.acme.com:** learning.acme.comが指すALBパブリックエンドポイント
   * **cdn.learning.acme.com:** Adobeによって共有されているCDNエンドポイント

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
