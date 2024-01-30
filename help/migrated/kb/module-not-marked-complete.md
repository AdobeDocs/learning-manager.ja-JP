---
jcr-language: en_us
title: Adobe Learning Manager のコース完了時に、モジュールが未完了とマークされる
description: 学習者が Adobe Learning Manager でコースを完了した後でも、モジュールが未完了としてマークされます。
contentowner: nluke
source-git-commit: ec79aa3dd6225cc424721afb50702963c1b125eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 53%

---



# Adobe Learning Manager のコース完了時に、モジュールが未完了とマークされる

## 問題

学習者が Adobe Learning Manager でコースを完了した後でも、モジュールが未完了としてマークされます。

## 原因

SCORM 2004では、合格および完了条件を定義し、両方のステートメントを別々に送信します。

例えば、あるコンテンツに **完了条件** 100%のスライド表示および **合格条件** 「クイズに合格する」に設定します。

学習者は、コースを完了しましたが、クイズに失敗しました。 この場合、進行状況は100%ですが、学習者が **合格条件**.

## 解決策

この問題は、プロジェクトに設定されたレポート&#x200B;**設定**&#x200B;に関連しています。 作成者は、コースの完了および合格条件を確認する必要があります。

必要な変更がある場合、作成者はAdobe Captivate Classicなどのコンテンツオーサリングツールを使用して行うことができます。 その後、作成者はそれに応じてモジュールを更新できます。

![](assets/scorm.png)

*Captivateの従来のレポート設定を表示*
