---
description: AIクライアントをAdobe Learning Managerに連携し、一度ログインすればコース、登録、学習パスについて尋ねることができます
jcr-language: en_us
title: AIクライアントをAdobe Learning Managerに接続
exl-id: dfb3d08d-405d-468c-9126-71a345815d5c
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%
---

# AIクライアントをAdobe Learning Managerに接続

統合管理者は、まずコネクターを設定する必要があります。 Adobe Learning Manager コネクターが表示されない場合は、管理者に連絡してください。 **クライアントは、Adobe Learning Manager Ultimate Tier**&#x200B;でのみ使用できます。

管理者は、[AIクライアントへのAdobe Learning Managerの追加](/help/migrated/administrators/feature-summary/add-alm-to-ai-client.md)を参照できます。

1. ClaudeやChatGPT Enterpriseなどの組織のAIクライアントを開きます。
2. コネクターのリストでAdobe Learning Manager コネクターを見つけます。
3. **Connect**&#x200B;を選択します。
4. メッセージが表示されたら、企業IDを使用してログインします。
5. 学習について質問します。 アイデアについては、**学習者向けのサンプルプロンプト**&#x200B;をご覧ください。

>[!NOTE]
>
>一度ログインします。 リクエストは独自の権限で実行されるので、Adobe Learning Managerでアクセスできる内容のみを確認できます。

## トラブルシューティング

**コネクターが見つかりません**

管理者に連絡して、コネクターを有効にしてもらってください。

**AIクライアントは前の質問を記憶していません**

それぞれのリクエストは新規として扱われます。 会話が継続するかどうかは、AIクライアントによって異なります。 次の質問の詳細を繰り返します。

**AIクライアントはAdobe Learning Manager コネクターを呼び出しません**

登録やコーストピックなど、質問の内容に名前を付けます。
