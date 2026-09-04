---
jcr-language: en_us
title: Adobe Learning Manager Content ComposerのCreative Cloudストレージを設定する
description: Adobe Learning Manager Content ComposerのCreative Cloudストレージを設定する方法について説明します。 このガイドでは、Creative Cloudストレージが必要な理由、管理者がAdobe Admin Consoleで無料メンバーシップのオファーを割り当てる方法、ストレージ関連のアクセス問題をトラブルシューティングする方法について説明します。
contentowner: saghosh
source-git-commit: 15e1f5c383442fb93706acdf68eb889c16511859
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Adobe Learning Manager Content ComposerのCreative Cloudストレージを設定する

>[!IMPORTANT]
>
>この文書の対象：管理者は、Adobe Learning Managerユーザーがコンテンツコンポーザーにアクセスして使用できるように、Creative Cloudストレージを有効にする必要があります。 管理者がストレージ関連のログインやアクセスエラーのトラブルシューティングを行い、Adobe Admin Consoleから無料メンバーシップのオファーを割り当てる場合に特に便利です。


Adobe Learning Manager(ALM)Content Composerを使用するには、Adobeアカウントに関連付けられたCreative Cloudストレージが必要です。 Creative Cloudストレージがない場合は、Content Composerにアクセスできない可能性があり、ログイン時やアクセス時にエラーが発生することがあります。

Adobeでは、影響を受けるユーザーに対するストレージのプロビジョニングを支援するために、管理者がAdobe Admin Consoleを通じて割り当てることができる無料メンバーシップのオファーを提供しています。 このオファーにはCreative Cloudストレージが含まれ、ストレージの使用権限を提供するプランをまだ持っていない場合に使用できます。

## 始める前に

次のことを確認します。

* Adobe Admin Console管理者権限があります。
* Content Composerのアクセスを必要とするユーザが特定されます。
* Creative Cloudストレージを含むプランをユーザーが既に持っているかどうかを確認しました。

## ユーザーがCreative Cloudストレージを必要とする理由

Content Composerは、Creative Cloudストレージを使用してコースを保存します。 Adobeプロファイルにストレージが割り当てられていない場合、コンテンツコンポーザーを使用しようとするとエラーが発生することがあります。

![コンテンツコンポーザーの記憶域エラー](../assets/coco-storage1.png)

多くのAdobeのお客様は、既存のAdobe製品を使用して既にCreative Cloudストレージを所有しており、影響を受けません。 ただし、Adobe Learning Managerをご利用の場合は、デフォルトでストレージがプロビジョニングされていない可能性があり、有効にするには管理者が必要になることがあります。

## ユーザーに無料のCreative Cloudストレージを有効にする

ユーザーがCreative Cloudストレージを持っていない場合は、Adobe Admin Consoleから無料メンバーシップのオファーを割り当てます。

1. 管理者権限を持つアカウントを使用して[Adobe Admin Console](https://adminconsole.adobe.com/)にサインインします。 製品やオファーをユーザーに割り当てることができるのは、管理者のみです。
2. Admin Consoleから、製品/体験版および特典を選択します。

   ![Admin Consoleでの体験版と特別提供](../assets/coco-storage2.png)

3. 体験版および特別オファーで利用できる無料メンバーシップオファーを見つけます。 これは、まだストレージの使用権限を持っていないユーザーがCreative Cloudストレージを有効にする推奨方法として説明されているオファーです。

   ![無料メンバーシップのオファー](../assets/coco-storage3.png)

4. 必要なユーザーに無料メンバーシップの特典を割り当てます。 割り当てを完了できるのは、適切なAdmin Console権限を持つ管理者のみです。
5. 割り当て後に、Creative Cloudストレージが使用可能であることを確認し、Content Composerに再度ログインするように依頼します。

## 無料メンバーシップで提供されるストレージ

無償メンバーシップを利用すると、約2 GBのCreative Cloudストレージを利用できます。このストレージを使用して、Content Composerを使用できます。

## トラブルシューティング

**ユーザーがコンテンツコンポーザーにアクセスするときにエラーを受信しました**

Adobeプロファイルで使用可能なCreative Cloudストレージがユーザーにあるかどうかを確認します。

**ユーザーに無料メンバーシップの特典を表示できません**

次のことを確認します。

* 管理者としてログインしています。
* Adobe Admin Consoleの「製品」エリアが表示されています。
* 組織はオファーにアクセスする資格があります。

## よくある質問

**すべてのAdobe Learning ManagerユーザーがCreative Cloudストレージを自動的に受け取りますか？**

掲示板で 一部のALMユーザーにはデフォルトでストレージがプロビジョニングされていない場合があり、無料メンバーシップのオファーを通じて追加の使用権限が必要になる場合があります。

**ユーザーは自分でストレージを有効にできますか？**

掲示板で ストレージの使用権限は、Adobe管理者がAdmin Consoleを通じて割り当てる必要があります。

**Content ComposerにCreative Cloudストレージは必要ですか？**

はい。 Content Composerは、Adobeアカウントに関連付けられたCreative Cloudストレージを持つユーザーに依存します。

**ストレージ関連のエラーが発生した場合、管理者はどうすればよいですか？**

ユーザーがCreative Cloudストレージの使用権限を持っていることを確認します。 そうでない場合は、Adobe Admin Consoleから無料メンバーシップのオファーを割り当て、ユーザーに再試行してもらいます。

**アクセス権または使用権限の問題が解決しない場合、管理者はどうすればよいですか？**

Adobe Admin Console administratorでCreative Cloudストレージの割り当て時やアクセス関連の問題のデバッグ時に問題が面された場合は、エンタープライズアカウントレベルのサポートが必要になる場合があります。 このような場合は、Admin Consoleで利用可能なサポートオプションを通じて、Adobeエンタープライズサポートにお問い合わせください。

詳しくは、[Adobeエンタープライズサポートオプション](https://helpx.adobe.com/business/enterprise/get-help/support-options/support-for-enterprise.html)をご覧ください。
