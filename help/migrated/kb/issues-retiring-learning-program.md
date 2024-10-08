---
jcr-language: en_us
title: 学習プログラムの廃止に関する問題
description: Adobe Learning Managerでの学習プログラムの廃止に関する問題
contentowner: nluke
exl-id: 706cafe3-2650-4837-9dee-e381a4a711f9
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 55%

---

# 学習プログラムの廃止に関する問題

## 問題

学習プログラムが自動的に廃止されます。

## 原因

管理者や作成者が LP を明示的に廃止していないにも関わらず、学習プログラムが廃止される場合があります。

この問題が発生するのは、学習プログラムがコースの集合体であるためです。 上位のトレーニングに、廃止されたインスタンスを含むコースがあるか、コースインスタンスが廃止された場合、トレーニングも廃止されます。

## 解決策

廃止されたインスタンスを含むコースを確認するには、次の手順に従います：

1. 管理者としてログインし、関連する学習プログラムを起動します。

1. **[!UICONTROL インスタンス]** > **コースをクリックします。** このページには、この学習プログラムに含まれるすべてのコースが一覧表示されます。 廃止されたインスタンスを含むコースを確認できます。

   ![](assets/retired-instance.png)

   *すべてのコースの一覧を表示*

1. 廃止されたコースインスタンスを見つけたら、**[!UICONTROL コース]**/**[!UICONTROL コースを開く]**&#x200B;をクリックします。

1. **[!UICONTROL [インスタンス]]**&#x200B;をクリックします。 廃止されたインスタンスで、**[!UICONTROL 編集]**&#x200B;をクリックし、完了日を、インスタンスを廃止する将来の日付に編集します。

   ![](assets/completion-date.png)

   *コースの完了日を編集する*

1. 完了したら、下の画像のようにドロップダウンをクリックします。 次に、**[!UICONTROL 「インスタンスを再度開く」]**&#x200B;をクリックします。

   ![](assets/re-open-instance.png)

   *コースのインスタンスを読み込む*

1. 関連する学習プログラムにアクセスします。 **[!UICONTROL 「インスタンス」]**&#x200B;をクリックして前の手順を実行し、学習プログラムのインスタンスを再び開きます。
