---
description: コースの検索、登録の確認、学習パスの構築のためにCloudまたはChatGPT Enterpriseで学習者が要求できるサンプルプロンプトを検索します
jcr-language: en_us
title: Adobe Learning Manager学習者向けのサンプルプロンプト
exl-id: e5d64ac4-03e9-49bc-95d0-bb074d55987f
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%
---

# Adobe Learning Manager学習者向けのサンプルプロンプト

CloudまたはChatGPT Enterpriseで以下のプロンプトを使用して、コースの検索、登録の確認、学習パスの構築を行います。

まず、AIクライアントを接続します。 [AIクライアントをAdobe Learning Managerに接続](/help/migrated/learners/feature-summary/connect-ai-client-to-alm-learner.md)する方法の詳細をご覧ください。 各プロンプトは、[学習者ツール参照](/help/migrated/learners/feature-summary/learner-tools-reference.md)のツールにマップされます。

>[!TIP]
>
>トピック、コースのステータス、期限など、必要な名前を付けます。 特定のリクエストにより、AIクライアントは適切なツールを選択できます。

## 登録

| **プロンプト** | **ツール** |
|------------------------------------------|------------------------------|
| どのようなコースに登録できますか？ | list_my_learning_enrollments |
| 期限切れになるコースはどれですか？ | list_my_learning_enrollments |

## 検索

| **プロンプト** | **ツール** |
|-----------------------------------------|-----------------------|
| どのようなリーダーシップコースが利用できますか？ | search_learning_items |
| 利用可能なセキュリティトレーニングを表示します。 | search_learning_items |

## 知識

| **プロンプト** | **ツール** |
|----|----|
| FedRAMPにおけるサプライチェーンのリスク管理とは何ですか？ | answer_learning_content_question |
| コンプライアンスコースの要件を説明します。 | answer_learning_content_question |

## 学習パス

| **プロンプト** | **ツール** |
|----|----|
| プロジェクト管理のスキルアップに役立つ一連のコースを見つけましょう。 | personalized_learning_path |
| この学習パスを保存します。 | personalized_learning_path |
