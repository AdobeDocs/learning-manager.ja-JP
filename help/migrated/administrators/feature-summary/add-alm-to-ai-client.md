---
description: Adobe Learning Manager MCPサーバーをClaudeやChatGPT Enterpriseなどの大規模法人AIクライアントに追加して、学習者が接続できるようにします
jcr-language: en_us
title: エンタープライズAIクライアントへのAdobe Learning Managerの追加
exl-id: d893efb7-dc0d-4a3a-88d6-b315340e5daa
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%
---

# エンタープライズAIクライアントへのAdobe Learning Managerの追加

AIクライアントの管理者権限が必要です。 まず、Adobe Learning Manager管理者からMCPエンドポイントURL、クライアントID、秘密鍵を取得します。 詳細については、**モデルコンテキストプロトコルサーバーの構成**&#x200B;を参照してください。

## コネクターを追加

1. 企業のAIクライアントに管理者としてログインします。
2. コネクターの管理者設定を開きます。
3. モデルコンテキストプロトコルを使用するカスタムコネクターを追加します。
4. Adobe Learning Manager MCPエンドポイントのURLを入力します。
5. Adobe Learning Manager管理者から提供されたクライアントIDと秘密鍵を入力します。
6. コネクターを保存します。
7. 学習者がコネクターを使用できるようにします。

>[!NOTE]
>
>AIクライアントインターフェイスは頻繁に変更されます。 これらの手順がクライアントと一致しない場合は、AIクライアントベンダーのドキュメントでリモートコネクターを追加する方法を確認してください。

## トラブルシューティング

**学習者にコネクターが表示されません。** 学習者のワークスペースまたはグループに対してコネクターが有効になっていることを確認します。

**学習者が「接続」を選択すると、認証に失敗します。** クライアントIDとシークレットキーが、Adobe Learning Managerのサーバーの&#x200B;**クライアント資格情報**&#x200B;ページの値と一致することを確認してください。
