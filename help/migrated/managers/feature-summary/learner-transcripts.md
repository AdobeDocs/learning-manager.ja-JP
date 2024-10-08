---
description: Learning Manager のユーザー、学習目標、スキルに基づいて、学習者のトランスクリプトをダウンロードする方法について説明します。
jcr-language: en_us
title: 学習者のトランスクリプト
exl-id: 8204aa1e-0e0d-4d9e-9dc0-6260667bf4e7
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 85%

---

# 学習者のトランスクリプト

Learning Manager のユーザー、学習目標、スキルに基づいて、学習者のトランスクリプトをダウンロードする方法について説明します。

組織のマネージャーは、Adobe Learning Manager で学習者に関連付けてトランスクリプトを生成できます。

## 学習者のトランスクリプトの生成 {#generatelearnertranscripts}

1. 学習者のトランスクリプトを生成するには、マネージャーのログイン画面の左ペインで「**[!UICONTROL レポート]**」をクリックします。
1. ページの[**[!UICONTROL マイレポート]**]タブをクリックします。
1. **[!UICONTROL 「学習者のトランスクリプト」]**&#x200B;リンクをクリックします。

   ![](assets/learner-transcripts.png)

   *学習者のトランスクリプトのレポートの作成*

1. 学習者のトランスクリプトダイアログが表示されます。生成するトランスクリプトの日付範囲を選択します。

   >[!NOTE]
   >
   >デフォルトでは、「開始日：自」は学習者の登録日で、「終了日」は常に現在の日付です。 データが必要な場合は、「開始日」のみを変更できます。

1. 「学習者を選択」フィールドから学習者名を選択し、「**[!UICONTROL 生成]**」をクリックします。

単一の学習者または学習者のグループを選択できます。複数の学習者を追加するには、「他の学習者を追加」をクリックします。

トランスクリプトが生成され、コンピューター上に .xls ファイルとしてダウンロードされます。各.xls Excelファイルには7つのシートがあり、詳細は次の通りです。

## タイムゾーンに基づく学習者のトランスクリプトのダウンロード {#lt-timezone}

管理者と同様に、マネージャーも列を選択して書き出すことができます。 また、マネージャーは、プロファイル設定で選択したタイムゾーンに基づいて、学習者のトランスクリプトをダウンロードすることもできます。

マネージャーがこのオプションを有効にした場合、以下に示すように、プロファイル設定ページで設定したタイムゾーンが選択されます。

>[!NOTE]
>
>新しいマネージャーの場合は、「タイムゾーン」チェックボックスがオフになっています。

![](assets/image030.png)

*一定期間の学習者のトランスクリプトをダウンロードする*

## 学習者のトランスクリプトファイルのコンテンツ {#learnertranscriptfilecontent}

学習者のトランスクリプトファイルは通常、6 つの Excel シートで構成されている単一ファイルです。学習者のトランスクリプトシートには、コースごとの学習者数、学習者のスキル、コースまたは学習者に基づいた達成度のパーセンテージ、準拠ダッシュボードなど、概要データが表示されます。次に学習者のトランスクリプトで使用可能なダッシュボードを示します。

**学習者のトランスクリプト**

学習者のトランスクリプトの Excel シートには、学習者のプロフィールの詳細に加えて、学習目標の使用状況の詳細（登録日、開始日、獲得したグレード、獲得したクイズスコアなど）が表示されます。学習プログラムにコースが含まれている場合は、各コースの使用状況の詳細とは別にコースの一覧が表示されます。

**1 - 学習活動ダッシュボード**

この LO 固有のダッシュボードでは、個々のコース、学習プログラム、または資格認定の学習者数を表示できます。特定の学習目標に対する学習者の進行状況シートを表示できます。このシートにはコースまたは学習プログラムを完了した学習者数、進行中の学習者、学習者の期日といったデータが表示されます。

特定のコースに関するユーザーの進行状況は、入力フィールドに指定する期日と進行状況 % のしきい値に基づいて計算されます。例えば、入力フィールドに 7 日、70% とそれぞれ指定した場合、7 日以内に期日を迎えるコースのうち、進行状況が 70% を超えているコースの進行状況が表示されます。このシートの期間は変更することもできます。変更されたデータはこのダッシュボードに自動的に表示されます。

**2 - 学習活動ダッシュボード**

この学習ダッシュボードには特定のユーザーのデータが表示されます。このダッシュボードでは、特定のユーザーが登録しているコース、学習プログラム、または資格認定を表示できます。テーブルにはユーザーが完了した学習目標に関するデータ、進行中の学習目標、ユーザーに予定されている期日も表示されます。

各コースに関するユーザーの進行状況は指定する出力に基づいて計算されます。つまり、期日と進行状況 % 値を指定します。 例えば、入力フィールドに 7 日、70% とそれぞれ指定した場合、7 日以内に期日を迎える各種コースのうち、進行状況が 70% を超えているコースの進行状況が表示されます。

**スキル**

スキルシートには、スキル名、スキルレベル、必要な単位、獲得した単位、達成度（パーセンテージ）、その他のプロフィールの詳細が表示されます。スキル Excel シートのサンプルスナップショットを次に示します。

**スキルダッシュボード**

このダッシュボードでは、組織が各種スキルに対応しているかどうかを確認できます。特定のスキルに関して、組織内でそのスキルを取得する必要のあるユーザーの数と、そのスキルを実際に取得しているユーザーの数を確認できます。このダッシュボードではスキルを更新する必要のあるユーザーも指定できます。この値は入力フィールドに指定する値に基づいて計算されます。例えば、50 日と入力した場合、ダッシュボードには 50 日後にスキルを更新する必要のあるユーザーのデータが表示されます。

このスキルダッシュボードはよりユーザーに特化したデータを表示します。特定のユーザーまたは複数のユーザーへの絞り込みを行って、ユーザーのスキルレベルをダッシュボードに表示できます。このシートを使用すると、マネージャーや管理者は各学習者のスキルを追跡し、各学習者のスキルの期待値と比較できます。スキルダッシュボードは学習者が更新する必要のあるスキルを特定する際にも役立ちます。学習者の更新に関するリストは、入力フィールドに指定する日数に基づいて計算されます。

**準拠ダッシュボード**

準拠ダッシュボードは、ユーザーごとの準拠レポート、トレーニングごとの準拠レポートの 2 つから構成されます。ユーザーベースのレポートでは、準拠ダッシュボードを使用して、準拠する必要のある重要な取り組みの期日が予定されているユーザーを追跡できます。トレーニングベースのレポートでは、学習プログラムまたは資格認定を使用して絞り込みを行うことができます。

適切な日付を表示するには、どちらの準拠レポートにおいても期日を使用して絞り込みを行ってください。
