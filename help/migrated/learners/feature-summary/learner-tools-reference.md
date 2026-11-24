---
description: Adobe Learning Manager Model Context Protocolサーバーで学習者が実行できる作業と、各機能をサポートするツールについて説明します。
jcr-language: en_us
title: Model Context Protocolサーバーの学習者ツール
exl-id: 4509b984-d0ba-4b7e-a0bb-803aa235fd1e
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%
---

# Model Context Protocolサーバーの学習者ツール

## 概要

すべての機能は、学習者が接続すると、ログインした学習者として実行されます。 リクエストは、学習者がAdobe Learning Managerでアクセスできる内容のみを返します。 [AIクライアントの接続](/help/migrated/learners/feature-summary/connect-ai-client-to-alm-learner.md)に関する詳細情報。

## 学習者の機能

| **機能** | **学習者が実行できる操作** | **リクエストの例** |
|----|----|----|
| 学習コンテンツを検索 | コース、資格認定および学習パスの検索 | どのようなリーダーシップコースが利用できますか？ |
| 登録の表示 | 登録と学習期限の確認 | 期限切れになるコースはどれですか？ |
| 学習に関する質問 | 学習コンテンツから回答を得る | FedRAMPにおけるサプライチェーンのリスク管理とは何ですか？ |
| 学習パスの生成 | パーソナライズされた学習パスの作成 | プロジェクト管理のスキルアップに役立つコースを見つけるにはどうすればよいですか？ |
| 学習パスの保存 | 生成された学習パスの保存 | この学習パスを保存します。 |

## サポートされているMCPツール

Adobe Learning Manager MCPサーバーには、次の学習ツールが表示されます。

| **ツール名** | **説明** |
|----|----|
| search_learning_items | カタログで、コース、学習パス、資格認定、作業計画書、バッジ、スキル、カタログ、タグを検索します。 学習者の状態、スキル、タグ、カタログ、配信形式、価格、言語でフィルターします。 テーマ別の質問については、 answer_learning_content_questionを使用します。 例：「初級Pythonコース」 |
| list_my_learning_enrollments | 学習者の登録済み、進行中のコース、完了済みコース、学習パス、資格認定、作業計画書を、状態、進捗状況、期日とともに一覧表示します。 学習目標タイプまたは完了ステータスでフィルタリングします。 結果には、最新の登録が最初に表示されます。 例：「まもなく期限は何ですか？」 |
| get_learning_object | ID別にコース、学習パス、資格認定または作業計画書の詳細を確認します。必要に応じて、インスタンス、スキル、サブ学習オブジェクトも確認できます。 search_learning_itemsまたはlist_my_learning_enrollmentsからIDを取得します。 |
| get_my_learning_profile | アカウントとマネージャーの詳細を含む、学習者のプロファイルを取得します。 登録と進捗状況については、 list_my_learning_enrollmentsを使用します。 |
| answer_learning_content_question | ラーニングマテリアルに基づき、ソースの学習目標に引用されたラーニングコンテンツに関する質問に回答します。 1つの学習目標を要約するか、カバレッジ、深度、前提条件、オーディエンスを並べて比較します。 コンテンツを検索またはリスト表示するには、search_learning_itemsまたはlist_my_learning_enrollmentsを使用します。 例：「私のネットワークのコースで取り上げられているTCPとUDPの違いを説明する」 |
| personalized_learning_path | 学習者の目標、トピック、ニーズに合ったコースを推奨します。 学習者のアカウントに承認済みのパスを保存します。 保存されたパスを一覧表示するか、IDごとに1つのパスの詳細とコースを取得します。 |

>[!IMPORTANT]
>
>ツール名は参照用に表示されますが、クライアントの実装によって異なる場合があります。
