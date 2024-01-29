---
jcr-language: en_us
title: Learning Managerでユーザーが自動削除される
description: ユーザーがLearning Managerから削除されても、管理者がそのようなアクションを実行することはありません。
contentowner: nluke
source-git-commit: 66dfaaaf723382eada39e2be29dfd49b795107a0
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---



# Learning Managerでユーザーが自動削除される {#user-gets-auto-deleted-in-learning-manager}

## 問題

ユーザーがLearning Managerから削除されても、管理者がそのようなアクションを実行することはありません。

## 原因

一定期間システムにログインしていないユーザーは、AdobeのLearning Managerで削除できます。

## 設定を変更/適用するにはどうすればよいですか？

### 社内学習者の場合

1. ログインする **Administrator**.
1. 未満 **設定**、をクリック **設定** > **一般**.
1. [一般設定]ページで、オプションについては「 」を参照してください **社内ユーザーの自動削除**.
1. クリック **[!UICONTROL 編集]** 学習者がシステムにアクセスしなかった場合に、自動削除されるまでの日数を入力します。

   ![](assets/cp-autodelete-internal.png)

   *日数を編集*

>[!NOTE]
>
>   ユーザーを自動的に削除しない場合は、このフィールドを空白のままにします。


1. クリック **[!UICONTROL 保存]** 設定を保持します。

### 社外学習者の場合：

1. ログインする **Administrator**.
1. 未満 **管理**、をクリック **[!UICONTROL ユーザー]** > **[!UICONTROL 外部]**.
1. 設定の適用が必要な社外ユーザーの名前をクリックします。

   これにより、 **社外登録プロファイルを編集** ウィンドウ：

1. クリック **[!UICONTROL 詳細設定]** をクリックします。

   ![](assets/cp-autodelete-external.png)

   *「詳細設定」オプションを選択します。*

1. を **ログイン要件** フィールドに、学習者がシステムにアクセスしなかった場合に自動削除されるまでの日数を入力します。
1. クリック **[!UICONTROL 保存]** 設定を保持します。
