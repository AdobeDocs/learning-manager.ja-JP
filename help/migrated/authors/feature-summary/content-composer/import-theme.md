---
description: カスタマイズしたテーマのJSONファイルをContent Composerに読み込む方法、およびコーステーマパネルで使用できる新しいカスタムテーマとして保存する方法について説明します。
jcr-language: en_us
title: テーマを読み込む
source-git-commit: f8687710f5b73e8b7cf8d56057cac25483f38cdc
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# テーマを読み込む

カスタマイズしたJSONファイルを読み込み、変更を新しいテーマとしてコンテンツコンポーザーに適用します。

1. ツールバーから&#x200B;**テーマ**&#x200B;を選択します。

2. 「**コーステーマ**」オプションから「**読み込み**」を選択します。
   ![](../assets/48_course_themes_import_button_updated.png)

3. カスタマイズしたJSONファイルをコンピューターから選択します。

4. **新規として保存**&#x200B;を選択して、新しいカスタムテーマを作成します。

## テーマJSON構造の概要

テーマのJSONファイルには、次の5つの主な領域があります。

| セクション | コントロール |
|----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| メタデータ（ID、名前、バージョン、説明、作成者、ソース、isDefault） | テーマIDと表示情報 |
| foundation.palette | テーマ全体でvar(—tokenName)を介して参照される7つのコアカラートークン（前景、背景、アクセント、背景Subtle、セカンダリ、textPrimary、textInverse） |
| foundation.fonts | 見出しと本文のフォントスタック |
| foundation.spacingおよびfoundation.radius | 水平/垂直方向の間隔スケールと角丸の半径トークン |
| エレメント | すべてのテキストロール(lessonTitle、topicTitle、blockHeading、subheading、question、caption、paragraph、buttonLabel)およびすべてのコンポーネント(paragraphBlock、imageBlock、videoBlock、imageGrid、accordion、carousel、flipCard、tabs、timeline、assessment)のタイポグラフィと構造スタイル |

ほとんどの値はvar(—tokenName)を使用するパレットトークンを参照するため、アクセントなどの1つのトークンを更新すると、そのトークンを参照するすべての要素に対して変更が自動的にカスケードされます。 個々のカラー値を検索する必要はありません。

