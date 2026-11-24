---
description: Adobe Learning Manager MCPサーバーをEnterprise AIクライアントのコネクターとして登録すると、組織内の学習者が学習内容に接続して照会できるようになります。
jcr-language: en_us
title: エンタープライズAIクライアントへのAdobe Learning Managerの追加
exl-id: d893efb7-dc0d-4a3a-88d6-b315340e5daa
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%
---

# エンタープライズAIクライアントへのAdobe Learning Managerの追加

## 概要

AIクライアントの管理者権限が必要です。 始める前に、Adobe Learning Manager管理者からMCPエンドポイントURL、クライアントID、秘密鍵を取得します。 [モデルコンテキストプロトコルサーバーの構成](/help/migrated/administrators/feature-summary/configure-mcp-admin.md)に関する詳細情報をご覧ください。

## コネクターを追加

1. エンタープライズAIクライアントに管理者としてログインします。
2. コネクターのAdministrator設定を開きます。
3. モデルコンテキストプロトコルを使用するカスタムコネクターを追加します。
4. Adobe Learning Manager MCPエンドポイントのURLを入力します。
5. Adobe Learning Manager Administratorで取得したクライアントIDと秘密鍵を入力します。
6. コネクターを保存します。
7. 学習者がコネクターを使用できるようにします。

>[!NOTE]
>
>AIクライアントインターフェイスは頻繁に変更されます。 これらの手順がクライアントの仕様と一致しない場合は、AIクライアントベンダーのドキュメントでリモートコネクターの追加を確認してください。

## トラブルシューティング

**学習者にコネクターが表示されません。**
学習者のワークスペースまたはグループに対してコネクターが有効になっていることを確認します。

**学習者が「接続」を選択すると、認証に失敗します。**
クライアントIDとシークレットキーが、Adobe Learning Managerのサーバーの&#x200B;**クライアント資格情報**&#x200B;ページの値と一致することを確認してください。
