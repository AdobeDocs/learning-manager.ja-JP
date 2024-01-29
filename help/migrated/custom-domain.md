---
jcr-language: en_us
title: カスタムドメインのサポート
description: カスタムドメインは、Learning ManagerのAzureインスタンスではサポートされていません。
contentowner: saghosh
source-git-commit: 8635072782253cbac3f913953797cae7c0bc5ef4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---



# カスタムドメインのサポート

カスタムドメインは、Learning ManagerのAzureインスタンスではサポートされていません。

## 概要 {#overview}

カスタムドメインのサポートにより、お客様はLearning Managerのアカウントで使用できるドメイン名を完全に制御できます。 お客様は、カスタムドメインを別途購入し、Adobeチームと協力して学習プラットフォームのログインURLとして設定する必要があります。

これにより、お客様はログインとアクセスのエクスペリエンスにホワイトラベルを付けて、Learning ManagerにAdobeやAdobeが表示されないように設定できます。

例えば、ユーザーがAdobeドメインにいる場合と同じエクスペリエンスを得られるように、ドメインをカスタマイズすることができます。 ABC社が顧客のトレーニングを希望する場合は、 `abc.com/mylearning`の代わりに `learningmanager.adobe.com/abc-inc/mylearning`.

>[!NOTE]
>
>前提条件として、ドメインを登録する必要があります。登録すると、AdobeがURLのカスタマイズについて説明します。


カスタムドメイン機能は、追加料金で利用できます。 詳細については、カスタマーサクセスマネージャーにお問い合わせください。

* 学習者の役割の場合、ドメインは次で始まります `https://cdn.<customer_custom_domain>/` 例えば、 `https://cdn.elearningstage1.cpdomaintest.in/`
* その他の役割の場合、ドメインは `https://<customer_custom_domain>/`. 例えば、 `https://elearningstage1.cpdomaintest.in/`

`<customer_custom_domain>` カスタマイズ可能なパーツです。

## アカウントにカスタムドメインを設定する方法 {#howtosetupacustomdomainonanaccount}

前提条件として、お客様はドメイン名を所有し、プロバイダーからドメインを購入する必要があります。

例えば、お客様が架空のドメインを所有していると考えてみましょう。 **acme.com**. お客様は、Learning Managerコンテンツの提供元を希望しています **learning.acme.com**.

カスタムドメインを設定するには、次の手順に従います。

1. お客様は次のことを行う必要があります。 **3つのCNAMEを追加** ドメイン内のレコード：

   * **learning.acme.com:** Adobeが共有するLearning ManagerのALBパブリックエンドポイント
   * **lrs.learning.acme.com:** learning.acme.comが指すALBパブリックエンドポイント
   * **cdn.learning.acme.com:** Adobeによって共有されているCDNエンドポイント

1. お客様は、次のドメインのSSL証明書を提供する必要があります。

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. AdobeはこれらのSSL証明書をAWS ALBにアップロードし、ドメインにリクエストを提供します。
1. Adobeは、SAN証明書にlearning.acme.comを追加します。
1. メタデータにはカスタムドメインURLが含まれるため、Adobeはお客様のSPメタデータを生成します。

   * お客様がソーシャルログインを希望している場合は、AdobeできるURLのリストにソーシャルサイトのリダイレクトURLパターンを含める必要があります。
   * お客様がSSOを有効にしている場合は、IDPを使用してリダイレクトURLにドメインを含める必要があります。 お客様は、IDPメタデータXMLをAdobeに提供する必要があります。 Adobeは、お客様のアカウントのSSO設定を更新する必要があります。

1. その後、Adobeはお客様のドメインを含めるようにS3 CORSルールを変更します。
