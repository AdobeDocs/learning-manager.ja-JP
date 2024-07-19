---
jcr-language: en_us
title: Learning Manager の EU ドメインにパブリッシュできない
description: Adobe Learning Managerで、Adobe CaptivateからAdobe Learning ManagerのEUドメインに公開できない。
contentowner: nluke
exl-id: fb8ae1af-9902-4901-8263-fb3ebff98fbc
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 83%

---

# Learning Manager の EU ドメインにパブリッシュできない {#unable-to-publish-to-learning-manager-eu-domain}

## 問題

Adobe Captivate から Adobe Learning Manager の EU ドメインにパブリッシュできません。

## エラー

アカウントが見つかりません

## 説明

作成者が Adobe Captivate から Adobe Learning Manager にコースをパブリッシュしようとしても、「アカウントが見つかりません」というエラーメッセージが表示され、その操作ができないというシナリオがあります。

## 原因

Adobe Captivate では、Adobe Learning Manager の US ドメインにコンテンツをパブリッシュするようにデフォルトで設定されているため、この問題が発生します。

## 解決策:

注意点

* Adobe Captivate を開いている場合は、このアプリケーションを閉じます。
* 以下の手順を実行するには、マシンの管理者アクセス権が必要になります。 管理者アクセス権がない場合は、IT チームに連絡してサポートを受けてください。

解決までの手順

1. Adobe Captivate のインストールディレクトリに移動します。

   例： `kbd C:\\Program Files\\Adobe\\Adobe Captivate 2019 x64` (2019はCaptivate版です。 別バージョンの Adobe Captivate を使用していれば、この番号も異なります）

1. 設定ファイル **AdobeCaptivate.ini** をデスクトップにコピーします。

   ![](assets/cp-captivate.ini.png)
   *構成ファイルの表示*

1. デスクトップにコピーしたファイルをメモ帳で開きます。
1. LearningManagerBaseUrl = `https://learningmanager.adobe.com/inappstarter`の値をLearningManagerBaseUrl = `https://learningmanagereu.adobe.com/inappstarter`に変更

   ![](assets/cp-primebaseurl.png)
   *PrimeBaseURLの表示*

1. 変更したメモ帳を上書き保存します。
1. 編集した保存ファイルをコピーして、上記のファイルパスに貼り直します。 `kbd C:\\Program Files\\Adobe\\Adobe Captivate 2019 x64`の元のファイルを置き換える
1. 以上の手順が完了したら、Adobe Captivate を起動して、Adobe Learning Manager にパブリッシュします。
