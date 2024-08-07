---
jcr-language: en_us
title: コースに学習者を表示できない
description: コースの「学習者」タブに、Adobe Learning Managerに登録されている学習者が表示されません。 ただし、レポートを生成すると、登録済みの学習者がレポートに表示されます。
contentowner: saghosh
exl-id: 2ea54347-fa6b-493e-b73c-d350efb2aaaf
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 58%

---

# コースに学習者を表示できない

## 問題

登録済みの学習者をコースに表示できません。

## 説明

コースの「学習者」タブに、登録済みの学習者が表示されません。 ただし、レポートを生成すると、登録済みの学習者がレポートに表示されます。

![](assets/no-learners.png)

*学習者が表示されていません*

## 原因

学習者が上位の学習オブジェクト（学習プログラムまたは資格認定）から登録されている場合、上位の学習オブジェクトの「学習者」タブに学習者が表示されます。 学習者は、コースの「学習者」タブで検索することはできません。

**学習者が登録している上位学習オブジェクトを表示する方法を教えてください。**

この情報は、学習トランスクリプトレポートで確認できます。 学習者トランスクリプトを生成するには、次の手順を実行します。

1. 管理者としてログインします。
1. **[!UICONTROL レポート]** > **[!UICONTROL カスタムレポート]** > **[!UICONTROL Excelレポート]** > **[!UICONTROL 学習者トランスクリプト]**&#x200B;をクリックします。

1. **[!UICONTROL 学習者]**&#x200B;の名前を入力し、**[!UICONTROL 日付]**&#x200B;の範囲を指定してください。
1. **[!UICONTROL 「詳細オプション」]**&#x200B;セクションを展開し、**[!UICONTROL 「モジュールレベル情報を有効にする」]**&#x200B;オプションを選択します。
1. **[!UICONTROL 「生成」]**&#x200B;をクリックします。

   学習者トランスクリプトで、学習者が登録している上位学習オブジェクトを確認できます。
