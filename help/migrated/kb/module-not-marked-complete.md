---
jcr-language: en_us
title: Adobe Learning Manager のコース完了時に、モジュールが未完了とマークされる
description: 学習者が Adobe Learning Manager でコースを完了した後でも、モジュールが未完了としてマークされます。
contentowner: nluke
exl-id: c0f14f2e-733a-4b4f-a2c2-4c0b33a15fa1
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 53%

---

# Adobe Learning Manager のコース完了時に、モジュールが未完了とマークされる

## 問題

学習者が Adobe Learning Manager でコースを完了した後でも、モジュールが未完了としてマークされます。

## 原因

SCORM 2004では、合格および完了条件を定義し、両方のステートメントを別々に送信します。

例えば、**完了条件**&#x200B;が100%のスライド表示で、**合格条件**&#x200B;が「クイズに合格する」に設定されているコンテンツがあるとします。

学習者は、コースを完了しましたが、クイズに失敗しました。 この場合、進行状況は100%ですが、学習者が&#x200B;**合格条件**&#x200B;を満たしていないため、モジュールは未完了とマークされます。

## 解決策

この問題は、プロジェクトに設定されたレポート&#x200B;**設定**&#x200B;に関連しています。 作成者は、コースの完了および合格条件を確認する必要があります。

必要な変更がある場合、作成者はAdobe Captivate Classicなどのコンテンツオーサリングツールを使用して行うことができます。 その後、作成者はそれに応じてモジュールを更新できます。

![](assets/scorm.png)

*Captivateの従来のレポート設定を表示する*
