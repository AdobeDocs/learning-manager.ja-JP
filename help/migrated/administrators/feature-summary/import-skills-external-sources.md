---
jcr-language: en_us
title: 外部ソースからのスキルの読み込み
description: それぞれのコネクタを使用して、LinkedInやGo1などのコンテンツプロバイダーからスキルを読み込みます。  読み込まれたスキルは、Learning Managerで管理者が定義したスキルに追加され、コースの作成ワークフローで作成者が利用できるようになります。
contentowner: saghosh
source-git-commit: fc77dad8f39d6d29c8ec74eb5ba137bf12ab7f8c
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# 外部ソースからのスキルの読み込み

それぞれのコネクタを使用して、LinkedInやGo1などのコンテンツプロバイダーからスキルを読み込みます。 この機能強化は、Learning Managerが外部のSkills CloudおよびTalent Managementシステムと統合できるようにするための目標の一部です。 読み込まれたスキルは、Learning Managerで管理者が定義したスキルに追加され、コースの作成ワークフローで作成者が利用できるようになります。 また、プラットフォーム全体のスキル検索機能が強化され、アカウントに多数のスキルが含まれている場合の検索機能が向上しました。

## スキルインポートを設定

アカウントでスキルインポートを有効にするには、手順に従います。

1. 管理アプリで、 **設定** をクリックします。
1. 選択 **一般**.
1. を **スキルのインポート** セクション、選択 **有効にする**. 有効にすると、読み込む外部ソースを選択できます **スキル**. 既存の学習リソースのスキルは、最初の実行時に1回、スキルリポジトリに読み込まれます。 それ以降に学習リソースを読み込んだ場合、スキルは新しく読み込まれた項目のスキルリポジトリにのみ読み込まれます。
1. ドロップダウンからコンテンツプロバイダーを選択します。

## 統合管理ワークフロー

統合管理者はCSV（スキル、スキルレベル、コース）をアップロードし、コースをアカウントに移行します。 例えば、管理者がLinkedIn Learningを選択した後、統合管理者はスキルとレベルの両方がAdobeのLearning Managerに読み込まれるアクティビティをスケジュールできます。

## スキルの書き出し

管理者は、

1. 選択 **スキル** をクリックします。
1. 任意のスキルのソースを選択します。 コース、作業計画書、登録済み学習者、およびコースのインストラクターを表示できます。

### スキルの編集

スキルを選択します。 を **スキルの編集** ポップアップでスキルの名前と説明を編集することはできません。 ただし、スキルドメインやスキルのバッジを追加することはできます。