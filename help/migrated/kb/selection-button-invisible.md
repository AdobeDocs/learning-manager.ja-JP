---
jcr-language: en_us
title: Learning Managerで選択ボタンが表示されない
description: ラジオボタンがないため、管理者は役割の割り当てや削除、ウェルカムメールの送信、ユーザーの削除を行うことができません。
contentowner: nluke
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---



# Learning Managerで選択ボタンが表示されない

## 問題

ラジオボタンが表示されないため、管理者は次の操作を実行できません（すべてを網羅しているわけではありません）。

* ロールの割り当てまたは削除
* ウェルカムメールを送信します。
* ユーザーを削除します。

## 原因

この問題は、アカウントのテーマが正しくないために発生します。

![](assets/radio-buttons.png)

*ラジオボタンが表示されない*

## 解決策

テーマを再読み込みして、ラジオボタンの外観を修正します。 次の手順を実行します。

1. 管理者として、次をクリックします。 **[!UICONTROL ブランディング]**.
1. を **テーマ** セクションをクリック **[!UICONTROL 編集].**
1. 任意のテーマを選択し、変更を保存します。

   ![](assets/set-themes.png)

   *任意のテーマを選択*

1. 前のテーマに戻し、変更を保存します。
1. AdobeのLearning Managerからログアウトし、再度ログインします。
