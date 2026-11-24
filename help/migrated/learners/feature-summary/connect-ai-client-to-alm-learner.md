---
description: AIクライアントにAdobe Learning Managerへのアクセスを1回許可すると、コース、登録、学習パスについて自然言語で質問できるようになります。
jcr-language: en_us
title: AIクライアントをAdobe Learning Managerに接続
exl-id: dfb3d08d-405d-468c-9126-71a345815d5c
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---

# AIクライアントをAdobe Learning Managerに接続

## 概要

統合管理者は、まずコネクターを設定する必要があります。 Adobe Learning Manager コネクターが表示されない場合は、管理者に連絡してください。 **コネクターは、Adobe Learning Manager Ultimateレベルのアカウント**&#x200B;でのみ使用できます。 管理者は、[Adobe Learning ManagerをエンタープライズAIクライアントに追加](/help/migrated/administrators/feature-summary/add-alm-to-ai-client.md)を表示できます。

1. ClaudeやChatGPT Enterpriseなどの組織のAIクライアントを開きます。
2. コネクターのリストでAdobe Learning Manager コネクターを見つけます。
3. **Connect**&#x200B;を選択します。
4. 接続を認証し、メッセージが表示されたらAdobe Learning Managerアカウントの詳細を入力します。
5. 学習について質問します。 アイデアについては、[学習者へのサンプルプロンプト](/help/migrated/learners/feature-summary/sample-prompts-for-learners.md)をご覧ください。

>[!NOTE]
>
>1回認証します。 リクエストは独自の権限で実行されるので、Adobe Learning Managerでアクセスできる内容のみを確認できます。

## トラブルシューティング

**コネクターが見つかりません**
管理者に連絡して、コネクターを有効にしてもらってください。

**AIクライアントは以前の質問を記憶していません**
サーバは各要求を新しい要求として扱います。 会話が継続するかどうかは、AIクライアントによって異なります。 次の質問で、関連する詳細を再度述べます。

**AIクライアントはAdobe Learning Manager コネクターを呼び出しません**
登録やコーストピックなど、質問の内容に名前を付けます。
