---
jcr-language: en_us
title: Learning Manager でユーザーが自動的に削除される
description: 管理者が操作していないのに、Learning Manager からユーザーが削除されてしまいます。
contentowner: nluke
source-git-commit: 66dfaaaf723382eada39e2be29dfd49b795107a0
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 61%

---



# Learning Manager でユーザーが自動的に削除される {#user-gets-auto-deleted-in-learning-manager}

## 問題

管理者が操作していないのに、Learning Manager からユーザーが削除されてしまいます。

## 原因

Adobe Learning Manager には、一定期間システムにログインしていないユーザーを削除するオプションがあります。

## 設定を変更 / 適用する方法

### 社内学習者の場合

1. **管理者**&#x200B;としてログインします。
1. 未満 **設定**、をクリック **設定** > **一般**.
1. 「一般設定」ページで&#x200B;**「社内ユーザーの自動削除」**&#x200B;というオプションを見つけます。
1. クリック **[!UICONTROL 編集]** 学習者がシステムにアクセスしなかった場合に、自動削除されるまでの日数を入力します。

   ![](assets/cp-autodelete-internal.png)

   *日数を編集*

>[!NOTE]
>
>   ユーザーの自動削除を行わない場合、このフィールドは空白のままにします。


1. クリック **[!UICONTROL 保存]** 設定を保持します。

### 社外学習者の場合

1. **管理者**&#x200B;としてログインします。
1. 未満 **管理**、をクリック **[!UICONTROL ユーザー]** > **[!UICONTROL 外部]**.
1. 設定の適用が必要な社外ユーザーの名前をクリックします。

   すると、**「社外登録プロファイルを編集」**&#x200B;ウィンドウが開きます。

1. クリック **[!UICONTROL 詳細設定]** をクリックします。

   ![](assets/cp-autodelete-external.png)

   *「詳細設定」オプションを選択します。*

1. を **ログイン要件** フィールドに、学習者がシステムにアクセスしなかった場合に自動削除されるまでの日数を入力します。
1. クリック **[!UICONTROL 保存]** 設定を保持します。
