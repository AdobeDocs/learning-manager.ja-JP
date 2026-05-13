---
description: WorkdayコネクタとAdobe Learning Managerを統合する方法について説明します。
jcr-language: en_us
title: Workday コネクタ
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 1%

---


# Adobe Learning ManagerのWorkdayコネクタ

## 概要

**Workday**&#x200B;は、社員や財務データの管理を支援するクラウドベースのシステムです。 主に採用、給与、業績追跡などの人事タスクに使用されます。 Adobe Learning Managerに接続すると、2つのプラットフォーム間でユーザーデータとスキルデータを自動的に同期できます。

Workdayコネクタを使用すると、Adobe Learning Managerを組織のWorkdayテナントとシームレスに統合できます。 この統合により、2つのシステム間でユーザーデータとスキルを自動的に同期し、データの正確性を向上させ、手作業を減らすことができます。

## 主な利点

- WorkdayからAdobe Learning Managerにユーザーを読み込みます。
- WorkdayとAdobe Learning Managerの間で属性をマッピングします。
- Adobe Learning ManagerからWorkdayにユーザースキルを書き出します。
- データ同期タスクを自動的に実行するようにスケジュールします。

## 前提条件

Workdayコネクタを設定する前に、Workday管理者から次の詳細情報を取得します。

- ホストURL
- テナントID
- ユーザー名
- パスワード

## Workdayコネクタを設定する

Adobe Learning ManagerでWorkdayコネクタを設定して、Workdayからユーザーデータを読み込み、ユーザースキルをWorkdayに書き出し、両方のシステムを最新の状態に保つための自動同期をスケジュールできます。

Workdayコネクタを設定するには：

1. Adobe Learning Managerに統合管理者としてログインします。
2. **Workday**&#x200B;タイルにカーソルを合わせ、**Connect**&#x200B;を選択します。

   ![](assets/workday-connector1.png)
   _データをインポートおよびエクスポートするようにWorkdayコネクタを構成する_

3. 次の接続詳細を入力します。
   - **接続名**：接続に使用する名前です。
   - **ホストUrl**: Workday管理者から提供されました。
   - **テナント**: Workday管理者からの内部識別子。
   - **ユーザー名とパスワード**: Workday管理者は、必要なセキュリティ特権を持つ統合システムユーザー(ISU)を作成し、統合管理者と共有します。

   ![](assets/workday-connector2.png)
   _Workdayコネクタを構成するために必要な詳細を追加します_

4. **接続**&#x200B;を選択して、セットアップを完了します。

>[!NOTE]
>
>アカウントで複数のWorkday接続を設定できます。

## Workdayからのユーザーの読み込み

### マップ属性

Workdayコネクタを使用して、WorkdayテナントからAdobe Learning Managerにアクティブユーザーを読み込むことができます。 この統合により、従業員の記録を同期させてユーザー管理を合理化できます。 Adobe Learning Managerでは、Workdayに加えて、FTPやSalesforceなどの他のデータソースからのユーザーインポートもサポートしています。

ユーザーを読み込む前に、WorkdayとLearning Manager間でユーザー属性をマッピングする必要があります。

1. Workdayコネクタの&#x200B;**概要**&#x200B;ページに移動します。
2. 「**インポート**」セクションで「**社内ユーザー**」を選択します。

   ![](assets/workday-connector3.png)
   _ユーザー属性をマップする内部ユーザーを選択してください_

3. **マップ属性**&#x200B;オプションを使用して、2つのシステム間でフィールドをリンクします：
   - **Adobe Learning Manager**&#x200B;列で、対応するAdobe Learning Manager属性を選択します。
   - **Workday**&#x200B;列で、ドロップダウンメニューを使用して、一致するWorkday属性を選択します。

   ![](assets/workday-connector4.png)
   _Adobe Learning Managerフィールドを使用してWorkday属性をマッピングしています_

   >[!NOTE]
   >
   >Adobe Learning Managerでは現在、Workdayから最大&#x200B;**69個のユーザー属性**&#x200B;の読み込みをサポートしています。 Adobe Learning Managerの&#x200B;**アクティブフィールド**&#x200B;機能を使用して、追加のフィールドを有効にすることができます。 カスタムのWorkday属性を追加するには、カスタマーサクセスアカウントマネージャー(CSAM)に連絡してください。

4. 派遣社員をインポートしないようにするには、**[派遣社員を除外]**&#x200B;チェックボックスをオンにします。
5. 必要に応じてフィルターを適用します。例えば、特定のマネージャーの下にあるユーザーを読み込みます。

>[!IMPORTANT]
>
>UUID、電子メールアドレス、従業員名が一意であることを確認します。 値が正しくないか重複している場合は、統合エラーが発生する可能性があります。

## サポートされているWorkday属性

サポートされているWorkday属性のリスト：

```
wd:User_ID wd:Worker_ID manager wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Postal_Code wd:Personal_Data.wd:Contact_Data.wd:Email_Address_Data.0.wd:Email_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.@wd:Formatted_Phone wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Country_ISO_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:International_Phone_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Phone_Number wd:Personal_Data.wd:Primary_Nationality_Reference.wd:ID.1.$ wd:Personal_Data.wd:Gender_Reference.wd:ID.1.$ wd:Personal_Data.wd:Identification_Data.wd:National_ID.0.wd:National_ID_Data.wd:ID wd:Personal_Data.wd:Identification_Data.wd:Custom_ID.0.wd:Custom_ID_Data.wd:ID wd:User_Account_Data.wd:Default_Display_Language_Reference.wd:ID.1.$ wd:Role_Data.wd:Organization_Role_Data.wd:Organization_Role.0.wd:Organization_Role_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Position_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.@wd:Formatted_Address
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Classification_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Group_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Work_Space__Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Family_Reference.0.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Reference.wd:ID.2.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Worker_Type_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Management_Level_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Status_Data.wd:Active wd:Employment_Data.wd:Worker_Status_Data.wd:Active_Status_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Original_Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Retired wd:Employment_Data.wd:Worker_Status_Data.wd:Retirement_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Terminated wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Last_Day_of_Work wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Code wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Name wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Type_Reference.wd:ID.1.$ wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Subtype_Reference.wd:ID.1.$ wd:Qualification_Data.wd:Education.0.wd:School_Name wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Job_Title wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Company wd:Management_Chain_Data.wd:Worker_Supervisory_Management_Chain_Data.wd:Management_Chain_Data.0.wd:Manager.Employee_ID Primary Work Email wd:Organization_Type_Reference_Cost_Center_ID wd:Organization_Type_Reference_Cost_Center_Name wd:Organization_Type_Reference_Company wd:Organization_Subtype_Reference_Department
wd:Organization_Subtype_Reference_Division wd:Universal_ID wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Reference.wd:ID.2.$ wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Municipality
```

## ユーザースキルのWorkdayへの書き出し

すべてのアクティブなユーザースキルをAdobe Learning ManagerからWorkdayに書き出すことができます。 撤回したスキルは書き出されません。

>[!IMPORTANT]
>
>- 複数のWorkdayアカウントから同じAdobe Learning Managerアカウントにスキルを同時に書き出そうとしないでください。
>- 複数のAdobe Learning Managerアカウントで同じWorkdayアカウントを使用している場合は、スキル名がアカウント間で一貫していることを確認して、競合を避けてください。

### スケジュールされた書き出しの設定

スケジュールされたエクスポートを構成するには、次の手順に従います。

1. **ユーザースキル**&#x200B;を選択し、**Workdayの概要**&#x200B;ページで&#x200B;**スケジュールの構成**&#x200B;を選択します。

   ![](assets/workday-connector5.png)
   _ユーザースキルを選択して書き出しをスケジュールする_

2. 「**この接続を使用してユーザースキルの書き出しを有効にする**」チェックボックスをオンにします。
3. 「**スケジュールを有効にする**」を選択します。
4. 開始日、時刻、および定期的なアイテムの間隔を設定します。

   ![](assets/workday-connector6.png)
   _Workdayコネクタでスケジュールの書き出しを構成する_

5. [**保存**]を選択して、スケジュールを適用します。

### オンデマンド書き出し

オンデマンド書き出しを作成するには：

1. 「**Workdayの概要**」ページで「**オンデマンド**」を選択します。
2. レポートを開始する開始日を入力します。
3. **実行**&#x200B;を選択してレポートを実行します。

### 実行ステータスの表示

1. **実行ステータス**&#x200B;に移動します。
2. すべてのタスクのステータスを表示し、必要に応じてエラーレポートをダウンロードします。

## 同期タスクのスケジュール

データ同期タスクを自動的に実行するようにコネクタを設定できます。

- WorkdayからLearning Managerへのユーザーの毎日の読み込みをスケジュールします。
- ユーザースキルのWorkdayへの定期的な書き出しをスケジュールします。

>[!NOTE]
>
>スケジューリングにより、ユーザーレコードとスキルデータが両方のシステムで常に最新の状態になります。

## 注意事項

- Workdayから入力されたUUIDフィールドは、クライアント対応のLMS管理者が削除することはできません。
- **ユーザーの消去**&#x200B;関数は、1回の実行で最大50人のユーザーのみをサポートします。 UUIDを持つユーザーを読み込む場合は注意してください。
- スキルは、Adobe Learning Managerのスキル名とレベルを使用して、Workdayのスキル項目レベルにマッピングされます。
