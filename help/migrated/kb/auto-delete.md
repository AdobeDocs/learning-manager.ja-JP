---
jcr-language: en_us
title: Learning Manager でユーザーが自動的に削除される
description: 管理者が操作していないのに、Learning Manager からユーザーが削除されてしまいます。
contentowner: nluke
exl-id: 9e293da3-bcbf-4798-b391-aef53ef8d946
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
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
1. **構成**&#x200B;で、**設定** > **一般**&#x200B;をクリックします。
1. 「一般設定」ページで&#x200B;**「社内ユーザーの自動削除」**&#x200B;というオプションを見つけます。
1. 学習者がシステムにアクセスしなかった場合に自動削除するには、**[!UICONTROL 「編集」]**&#x200B;をクリックして、フィールドに日数を入力します。

   ![](assets/cp-autodelete-internal.png)

   *日数を編集する*

>[!NOTE]
>
>   ユーザーの自動削除を行わない場合、このフィールドは空白のままにします。


1. **[!UICONTROL [保存]]**&#x200B;をクリックして、設定を保持します。

### 社外学習者の場合

1. **管理者**&#x200B;としてログインします。
1. **管理**&#x200B;で、**[!UICONTROL ユーザー]** > **[!UICONTROL 外部]**&#x200B;をクリックします。
1. 設定の適用が必要な社外ユーザーの名前をクリックします。

   すると、**「社外登録プロファイルを編集」**&#x200B;ウィンドウが開きます。

1. 左下隅の&#x200B;**[!UICONTROL 詳細設定]**&#x200B;をクリックします。

   ![](assets/cp-autodelete-external.png)

   *[詳細設定]オプションを選択します*

1. **ログイン要件**&#x200B;フィールドに、学習者がシステムにアクセスしなかった場合に自動削除されるまでの日数を入力します。
1. **[!UICONTROL [保存]]**&#x200B;をクリックして、設定を保持します。
