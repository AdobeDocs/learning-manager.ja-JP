---
jcr-language: en_us
title: ユーザーの一括追加
description: 一度に複数のユーザーを追加する方法を説明します。
contentowner: saghosh
source-git-commit: 0534bd52c80b77d985cfe715f74054f3aabac9a2
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 24%

---



# ユーザーの一括追加

このトレーニングでは、CSVを使用してユーザーを一括で追加する方法を説明します。

[![ボタン](feature-summary/assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&amp;sdid=51TC8QS1&amp;mv=display&amp;mv2=display#/course/7555555)

トレーニングを起動できない場合は、にメッセージを送信してください。 <almacademy@adobe.com>.

## 複数のユーザーを追加する方法

次の手順に従って、一度に複数のユーザーを追加できます。

1. クリック **[!UICONTROL ユーザー]** 管理者ログインの左側のペインで、次に「 **[!UICONTROL 追加]** > **[!UICONTROL CSVをアップロード]**. ポップアップダイアログが表示されます。

1. .CSV ファイルを使用して、複数のユーザーを追加できます。 クリック **[!UICONTROL 読み込み]** コンピューターで.csvファイルを選択して開きます。

1. ファイルを読み込んだ後、最初に.csv ファイルをアップロードするときに、.csv ファイルの内容をアプリケーションラベルにマッピングします。

   それ以降のすべてのアップロードでは、以前のラベルの設定が考慮されます。 クリック **[!UICONTROL 保存]** データのマッピングが完了したら、「 **[!UICONTROL 追加]** マッピングされた.csvファイルをアップロードします。

1. クリック **[!UICONTROL 保存]** データのマッピングが完了したら、「 **[!UICONTROL 追加]** マッピングされた.csvファイルをアップロードします。

## 必須フィールドを含む CSV アップロード {#csvuploadwithmandatoryfields}

CSVにユーザーのプロファイルとマネージャーの電子メールIDを追加する必要はありません。 ユーザー名とユーザーのemail-idのみが必須フィールドです。

この場合、デフォルトでは、会社の管理者がユーザーのマネージャーとして扱われます。 デフォルトでは、従業員はユーザーのプロファイルと見なされます。

**サンプルCSV**

Learning ManagerのサンプルCSVは、以下の必須フィールドで利用できます。
[Sample-CSV-name-email.zip](assets/sample-csv-name-email.zip)

## すべてのフィールドを含む CSV アップロード {#csvuploadwithallthefields}

従業員にマネージャーの電子メールIDを含める前に、必ずマネージャーを従業員としてCSVに追加してください。 例えば、以下のスナップショットの従業員名 Howard Walters を参照してください。

![](assets/csv-example.png)

*アップロード用のCSVテンプレート*

また、組織の管理者は、自分自身を従業員として追加し、マネージャーの電子メールIDをルートとして指定できます。

**サンプルCSV**

Learning ManagerのサンプルCSVには、以下のすべてのフィールドが含まれています。
[learning-manager-sample-csv.zip](assets/learning-manager-sample-csv.zip).

詳しくは、「  [CSVアップロードの使用](/help/migrated/administrators/feature-summary/add-users-user-groups.md) 詳細については、機能のヘルプコンテンツを参照してください。
