---
jcr-language: en_us
title: Learning Managerのソーシャルログイン
description: Learning Managerのソーシャルログイン
contentowner: saghosh
preview: true
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%
---


# Learning Managerのソーシャルログイン

facebook、LinkedIn、またはTwitterの資格情報を使用して、Learning Managerにログインできます。

## ソーシャルログインの設定 {#setupsociallogin}

1. アカウントの設定については、カスタマーサクセスマネージャーにお問い合わせください。

   それ以外の場合は、次の手順に従います。

1. ソーシャルログインを設定するアカウントを検索します。
1. ログインをSSOに変更します。
1. 「詳細」をクリックします。 次のJSONを指定します。

   ```
   \{"linkedIn":true,"microsoft":true,"twitter":true,"facebook":true,"editingAllowed":true
   ```

   不正なJSONである場合は、例外が発生します。

   このソーシャルログイン機能は、社内ユーザーにのみ使用されます。

