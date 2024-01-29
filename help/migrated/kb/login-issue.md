---
jcr-language: en_us
title: Learning Managerのログインに関する問題
description: Learning Manager Adobeのログインに関する問題
contentowner: nluke
source-git-commit: ec79aa3dd6225cc424721afb50702963c1b125eb
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---



# Learning Managerのログインに関する問題

## 問題

AdobeのLearning Managerにログインできません。

## エラー

AdobeのLearning Managerにログインしようとすると、以下のエラーメッセージが表示されます。

![](assets/cp-error.png)

*期限切れのセッションのエラーメッセージ*

## 理由

ユーザーがSSOでログインすると、ブラウザーに保存されるセッションクッキーが作成されます。 また、ユーザーは他のアプリケーションにログインすることもできます。 ほとんどのSSOは、24時間後にログアウトするように設定されています。 新しいセッションでは、ユーザーは再度認証を受ける必要があります。

場合によっては、古いSSOクッキーが原因で、ユーザーがシステムにアクセスできないことがあります。 これらのCookieは、認証用にAdobeのLearning Managerに転送されます。 ユーザーが長時間ブラウザーを閉じなかった場合や、ログアウトしていない場合、セッションは終了しません。

AdobeのLearning Managerではこのような古いCookieが拒否されるため、エラーが発生します。

## 解決策

古いCookieがAdobeのLearning Managerに拒否される場合は、次のオプションを試してください。

1. ブラウザーのCookieとキャッシュをクリアします。 詳しくは、こちらを参照してください。 [文書](unable-log-in-learning-manager.md).

   また、IDP管理者は、特定の時間が経過したら強制的にログアウトするように定義することもできます。 この手順では、新しいセッションを開始するためにユーザーを再度認証します。

このエラーが発生する理由は他にもありますが、一般的なシナリオは上記のとおりです。

## 参照リンク：

[Microsoft：有効期間の条件付きアクセスセッション](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)
