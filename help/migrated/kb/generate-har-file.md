---
description: Google ChromeでHARファイルを生成する方法については、以下を参照してください。
jcr-language: en_us
title: HARファイルを生成する
contentowner: dvenkate
source-git-commit: ec79aa3dd6225cc424721afb50702963c1b125eb
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---



# HARファイルを生成する

Google ChromeでHARファイルを生成する方法については、以下を参照してください。

HARファイルを生成するには、次の手順に従います。

1. Google Chromeウィンドウを開き、新しいタブを開きます。
1. ページのデベロッパーツールを開き、右クリック/Inspectを選択します。
1. を開きます **[!UICONTROL ネットワーク]** タブをクリックします。 赤い録音ボタンがアクティブであることを確認します。 有効にする **[!UICONTROL ログを保持]** チェックボックスをオンにします。

   ![](assets/preserve-log-checkbox.png)

   *「ネットワーク」タブで「ログの保存」チェックボックスをオンにします*

1. ログイン先 [Learning Manager](https://learningmanager.adobe.com/acapindex.html) 認証情報を使用して、コースに参加します。 問題の原因となるすべての操作を実行します。
1. デベロッパーツールで、右クリックして **すべてをコンテンツ付きHARとして保存**.

   Google Chromeの一部のバージョンでは、次の操作が必要になる場合があります **[!UICONTROL コピー]** > **[!UICONTROL すべてをHARとしてコピー]**.

   ![](assets/copy-hra.png)

   *すべてのHARファイルをコピー*

1. コピーした内容をメモ帳ファイルに貼り付けます。 デスクトップに別名で保存 **logs.har** 電子メールでAdobeに送信します。
