---
jcr-language: en_us
title: ユーザーの一括追加
description: 一度に複数のユーザーを追加する方法を説明します。
contentowner: saghosh
exl-id: c3309ce5-8764-452e-82d5-5637c23c661b
source-git-commit: f964dd3f1adeadb76f4843c9af229ce5f09afde1
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 22%

---

# ユーザーの一括追加

このトレーニングでは、CSVを使用してユーザーを一括で追加する方法を説明します。

[![ボタン](feature-summary/assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&amp;sdid=51TC8QS1&amp;mv=display&amp;mv2=display#/course/7555555)

トレーニングを起動できない場合は、<almacademy@adobe.com>に書き込んでください。

## 複数のユーザーを追加する方法

次の手順に従って、一度に複数のユーザーを追加できます。

1. 管理者ログインの左ペインで&#x200B;**[!UICONTROL ユーザー]**&#x200B;をクリックしてから、**[!UICONTROL 追加]** > **[!UICONTROL CSVをアップロード]**&#x200B;をクリックします。 ポップアップダイアログが表示されます。

1. .CSV ファイルを使用して、複数のユーザーを追加できます。 「**[!UICONTROL 読み込み]**」をクリックし、コンピューターで.csvファイルを選択して開きます。

1. ファイルを読み込んだ後、最初に.csv ファイルをアップロードするときに、.csv ファイルの内容をアプリケーションラベルにマッピングします。

   それ以降のすべてのアップロードでは、以前のラベルの設定が考慮されます。 データのマッピングが完了したら「**[!UICONTROL 保存]**」をクリックし、「**[!UICONTROL 追加]**」をクリックして、マップされた.csvファイルをアップロードします。

1. データのマッピングが完了したら「**[!UICONTROL 保存]**」をクリックし、「**[!UICONTROL 追加]**」をクリックして、マップされた.csvファイルをアップロードします。

## 必須フィールドを含む CSV アップロード {#csvuploadwithmandatoryfields}

CSVにユーザーのプロファイルとマネージャーの電子メールIDを追加する必要はありません。 ユーザー名とユーザーのemail-idのみが必須フィールドです。

この場合、デフォルトでは、会社の管理者がユーザーのマネージャーとして扱われます。 デフォルトでは、従業員はユーザーのプロファイルと見なされます。

>[!NOTE]
>
>新しいユーザーを追加するには、詳細情報を記載した新しいCSVファイルを作成してアップロードします。 既存のCSVファイルの更新と再アップロードはサポートされていません。

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
[learning-manager-sample-csv.zip](assets/learning-manager-sample-csv.zip)。

詳細については、[CSVアップロードの使用](/help/migrated/administrators/feature-summary/add-users-user-groups.md)機能のヘルプコンテンツを参照してください。
