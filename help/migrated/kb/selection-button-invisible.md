---
jcr-language: en_us
title: Learning Manager で選択ボタンが表示されない
description: ラジオボタンがないため、管理者は役割の割り当てや削除、ウェルカムメールの送信、ユーザーの削除を行うことができません。
contentowner: nluke
exl-id: d2c86f9f-3e79-4f1f-992e-f92873940061
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 55%

---

# Learning Manager で選択ボタンが表示されない

## 問題

ラジオボタンが表示されないため、管理者は次の操作を実行できません（すべてを網羅しているわけではありません）。

* 役割の割り当てや削除
* ウェルカムメールの送信
* ユーザーの削除

## 原因

この問題は、アカウントのテーマが正しくないために発生します。

![](assets/radio-buttons.png)

*ラジオボタンが表示されません*

## 解決策

テーマを再読み込みして、ラジオボタンの外観を修正します。 次の手順を実行します。

1. 管理者として&#x200B;**[!UICONTROL 「ブランディング」]**&#x200B;を選択します。
1. **テーマ**&#x200B;セクションで、**[!UICONTROL 編集]をクリックします。**
1. 任意のテーマを選択し、変更を保存します。

   ![](assets/set-themes.png)

   *任意のテーマを選択*

1. 前のテーマに戻し、変更を保存します。
1. Adobe Learning Manager からログアウトし、再度サインインします。
