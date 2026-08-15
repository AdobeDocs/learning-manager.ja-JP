---
description: 公開後の配信、トラッキング、レポートにおいて、Content Composerでオーサリングを、Adobe Learning Managerで処理する方法について説明します。
jcr-language: en_us
title: コンテンツコンポーザーとAdobe Learning Managerの連携
source-git-commit: 68d15fa96588b2569c9b1cdb480e2ba9f31a1cf6
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Adobe Learning ManagerコンテンツコンポーザーとAdobe Learning Managerの連携

コンテンツコンポーザーはオーサリングを処理します。 Adobe Learning Managerは、配信、登録、トラッキング、レポートを処理します。 2つの製品は、公開ステップを介して接続されます。 コンテンツコンポーザーからパブリッシュすると、コースはALMコンテンツライブラリ内のモジュールになり、コースに組み込んで学習者に割り当てることができます。

## コンテンツコンポーザーが制御する内容

- レッスンとトピックの構造

- コースコンテンツ – テキスト、画像、ビデオ、コンポーネント、ナレッジチェック

- 質問タイプと解答オプションを含む、レッスンの終わりのクイズ

- 視覚テーマ

- 完了条件と合格条件

- レポートに使用されるSCORMバージョン

## Adobe Learning Managerが制御するもの

- 学習者の登録とアクセス

- モジュールメタデータ – 期間、タグ、一意のID、有効期限

- コースアセンブリ – コンテンツコンポーザーモジュールと他の学習コンテンツの組み合わせ

- 学習者のトラッキング、レポート作成、トランスクリプト

- コースのバージョン管理

- 通知とリマインダー

## コースの作成から学習者の完了まで

1. **コンテンツコンポーザーでコースを作成します**:コンテンツコンポーザーでコースを作成します。レッスン、トピック、テーマ、クイズ、完了設定などを作成できます。 パブリッシュ前に、コース設定（完了条件、合格条件、クイズスコア付け）を構成します。
詳細については、[コース設定の構成](#settings)を参照してください。

2. **PublishからAdobe Learning Managerへの書き出し：**&#x200B;オーサリングが完了したら、**書き出し**&#x200B;設定でコンテンツコンポーザーをALMアカウントに接続し、コースを公開します。 コンテンツコンポーザーは、コースをSCORM準拠モジュールとしてALMコンテンツライブラリに送信します。
   ![カスタムヘッダー、ロゴ、およびフォントテーマが適用された公開済みのコース](../assets/49_published_course_custom_branding_header_updated.png)

3. **ALMでモジュールを構成する：**&#x200B;公開されると、コースはALMコンテンツライブラリにモジュールとして表示されます。 ALM作成者は、期間、タグ、一意のID、有効期限の設定などのモジュールメタデータを設定し、その他の学習コンテンツと共に、モジュールをALMコースに追加します。
   ![モジュールのメタデータと完了条件のフィールド](../assets/50_alm_add_content_composer_module_metadata_updated.png)

>[!NOTE]
>
>Adobe Learning Manager(ALM)で完了条件および合格条件を設定した場合、これらの設定はコンテンツコンポーザーで定義されたものよりも優先されます。

4.**ALMコースをPublishする：** ALM作成者がモジュールをALMコースにまとめ、コースの画像と設定を追加してパブリッシュします。 この手順を実行した後にのみ、学習者を登録できます。

詳細については、[Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/get-started/getting-started-author)を参照してください。
![&#x200B; Adobe Learning Managerのコンテンツライブラリ。公開されたモジュールと処理モジュールが表示されます](../assets/51_alm_content_library_list_view_updated.png)

詳細については、[ALMでの作成者としてのコースの作成](https://experienceleague.adobe.com/en/docs/learning-manager/using/authors/courses)を参照してください。

5.**学習者がコースを完了する：**&#x200B;学習者は、Adobe Learning Managerからコースにアクセスし、コンテンツコンポーザーモジュールを起動して、レッスンとクイズを完了し、手順1で設定した完了条件と合格条件に基づいてスコアを受け取ります。

詳細については、「[学習者としてコースにアクセス](https://experienceleague.adobe.com/en/docs/learning-manager/using/get-started/getting-started-learner)」を参照してください。

6.ALMは学習者の進行状況を記録します。完了ステータス、クイズスコア、学習者データがALMに記録され、学習者のトランスクリプトおよび管理者レポートを通じて使用できます。

7.**バージョン管理を使用してコースを更新** :コンテンツコンポーザーのコンテンツを更新して再公開すると、ALMによりモジュールの新しいバージョンが作成されます。 ALMの作成者は、既存のコースを更新して最新バージョンを使用できます。
