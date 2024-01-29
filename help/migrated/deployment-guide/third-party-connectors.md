---
description: コネクターを使用してSalesforceとLearning Managerを統合する方法と、FTPとLearning Managerを統合し、FTPコネクターを使用してCSVを自動的にアップロードする方法について説明します。
jcr-language: en_us
title: Learning Managerコネクタ
preview: true
source-git-commit: 2317aa899a82abe24d38c4e40a06df3646fde310
workflow-type: tm+mt
source-wordcount: '6293'
ht-degree: 0%

---



# Learning Managerコネクタ

コネクターを使用してSalesforceとLearning Managerを統合する方法と、FTPとLearning Managerを統合し、FTPコネクターを使用してCSVを自動的にアップロードする方法について説明します。

企業には、Learning Managerとの統合が必要な他のアプリケーションやシステムがあります。 コネクタは、外部システムからLearning Managerにデータを読み込んだり、Learning Managerから外部システムにデータを書き出したりするなど、データベースの統合を実行するのに役立つユーティリティです。 2016年7月のリリースでは、コネクタに、外部システムからLearning Managerのユーザーを一括読み込みする機能のみが用意されています。

Learning ManagerはSalesforceおよびFTPコネクタを提供します。 Salesforceコネクターを使用すると、組織の統合管理者はSalesforceアプリケーションとLearning Managerを統合できます。 統合者は、FTPコネクターを使用して、一連のユーザーをエンタープライズアプリケーションに自動読み込みすることもできます。

また、Learning ManagerにはLynda、getAbstractおよびHarvard Management Systemコネクターが用意されており、学習者はLynda.com、getAbstractおよびHarvard ManageMentorからコースにアクセスして使用できます。

これらのコネクターを設定し、Learning Managerで使用する方法については、以下の説明を参照してください。

![](assets/connectorslist.jpg)

## Salesforceコネクタ {#sfconnector}

SalesforceコネクターはLearning ManagerアカウントとSalesforceアカウントを接続して、データを自動的に同期します。 Salesforceコネクターの機能は次のとおりです。

### マップ属性

統合管理者はSalesforceの列を選択し、その列を対応するLearning Managerのグループ化可能属性にマッピングできます。 これは一度だけの作業です。 マッピングが完了すると、それ以降のユーザーの読み込みでは同じマッピングが使用されます。 管理者がユーザーを読み込むために別のマッピングを使用する場合は、再設定できます。

### 自動ユーザー読み込み

ユーザー読み込みプロセスにより、Learning Manager管理者はSalesforceから従業員の詳細を取得し、その情報をLearning Managerに自動的に読み込ませることができます。 この自動化により、CSVの作成とLearning Managerへのアップロードに伴う手作業を省略できます。

### 自動スケジュール

自動スケジュール機能と自動ユーザー読み込み機能を使用すると、効果的です。 Learning Manager管理者は、組織のニーズに応じてスケジュールを設定できます。 Learning Managerアプリケーションのユーザーは、スケジュールに従って最新の状態にすることができます。 Learning Managerアプリケーションで、同期を毎日実行できます。

### ユーザーのフィルタリング

Learning Manager管理者は、読み込む前にユーザーにフィルタリングを適用できます。 例えば、Learning Manager管理者は、階層内のすべてのユーザーを1人以上の特定のマネージャーの管理下に読み込むように選択できます。

## Salesforceコネクターの設定 {#configuresalesforceconnector}

Learning ManagerをSalesforceと統合するプロセスについて説明します。

### 前提条件 {#prerequisites}

Salesforce組織のURLが手元にあることを確認します。 例えば、組織名が **myorg** SalesforceのURLは次のようになります [https://myorg.salesforce.com](https://myorg.salesforce.com/). SalesforceアカウントをLearning Managerに接続するために入力が必要な項目は、組織名のみです。

また、アカウントにログインするための適切な資格情報があることを確認します。

## 接続を作成する {#createaconnection}

1. Learning Managerホームページで、Salesforceカード/サムネールにカーソルを合わせます。 メニューが表示されます。 クリック **[!UICONTROL Connect]** メニュー内のアイテムです。

   ![](assets/mouserover-salesforce.png)

1. 組織URLの入力を求めるダイアログが表示されます。 クリック **[!UICONTROL Connect]** urlの入力後
1. 接続が成功すると、概要ページが表示されます。

## マップ属性 {#mapattributes}

接続が正常に確立されたら、Salesforceの列をLearning Managerの対応する属性にマッピングできます。 この手順は必須です。

1. マッピングページの左側にはLearning Managerの列が表示され、右側にはSalesforceの列が表示されます。 Learning Managerの列名にマッピングする適切な列名を選択します。

   ![](assets/sfdc-map-columns.png)

   左側に表示されているLearning Managerの列データは、アクティブフィールドから取得されます。 この **支配人** フィールドは、必ず電子メールアドレスタイプのフィールドにマッピングする必要があります。 コネクタを使用するには、すべての列をマッピングする必要があります。

1. クリック **[!UICONTROL 保存]** マッピングの完了後。
1. これで、コネクタを使用する準備ができました。 現在設定されているアカウントは、管理者アプリ内のデータソースとして表示され、管理者が読み込みをスケジュールしたり、オンデマンドで同期したりできます。

## Salesforceコネクターの使用 {#usingsalesforceconnector}

SalesforceコネクターはSalesforce.comに接続して、設定どおりにユーザーを取得し、ユーザーをLearning Managerに追加します。

## Learning Manager FTPコネクタ {#ftpconnector}

FTPコネクターを使用すると、Learning Managerを任意の外部システムと統合して、データを自動的に同期できます。 外部システムがデータをCSV形式で書き出し、そのデータをLearning Manager FTPアカウントの適切なフォルダーに配置できることが期待されています。 FTPコネクタの機能は次のとおりです。

Boxコネクターを使用して、データの移行、ユーザーの読み込み、データの書き出しをおこなうこともできます。 詳しくは、「 [ボックスコネクタ。](third-party-connectors.md#main-pars_header_302653946)

## データのインポート {#dataimport}

ユーザー読み込みプロセスにより、Learning Manager管理者はLearning Manager FTPサービスから従業員の詳細を取得し、その情報をLearning Managerに自動的に読み込ませることができます。 この機能を使用すると、それらのシステムによって生成されたCSVをFTPアカウントの適切なフォルダーに配置することによって、複数のシステムを統合できます。 Learning ManagerはCSVファイルを取得し、ファイルを結合して、スケジュールに従ってデータを読み込みます。 詳細については「スケジュール機能」を参照してください。

**マップ属性**

統合管理者はCSVの列を選択し、その列をLearning Managerのグループ化可能属性にマッピングできます。 このマッピングは1回限りの作業です。 マッピングが完了すると、その後のユーザーのインポートでも同じマッピングが使用されます。管理者がユーザーのインポート用に別のマッピングを使用する場合は、マッピングを再構成できます。

## データの書き出し {#exportdata}

データの書き出しを使用すると、ユーザーはユーザースキルをFTPの場所に書き出して、サードパーティのシステムと統合することができます。

## スケジュール {#scheduling}

管理者は、組織の要件に応じてタスクをスケジュール設定できます。Learning Managerアプリケーション内のユーザーは、スケジュールに従って最新の状態になります。 同様に、統合管理者は、外部システムと統合されるようにスキルの書き出しをスケジュールすることができます。 Learning Managerアプリケーションで、同期を毎日実行できます。

## Learning Manager FTPコネクタの設定 {#configurecaptivateprimeftpconnector}

ここでは、Learning ManagerをFTPコネクターと統合するプロセスについて説明します。

### 接続を作成する {#Createaconnection-1}

1. Learning Managerホームページで、FTPカード/サムネールにカーソルを合わせます。 メニューが表示されます。 クリック **[!UICONTROL Connect]** メニュー内のアイテムです。

   ![](assets/mouseover-ftpconnector.png)

1. 電子メールIDの入力を求めるダイアログが表示されます。 組織のLearning Manager FTPアカウントの管理責任者の電子メールIDを入力します。 クリック **[!UICONTROL Connect]** 電子メールidの入力後
1. Learning Managerは、FTPに初めてアクセスする前にユーザーにパスワードの再設定を促す電子メールを送信します。 ユーザーはパスワードをリセットし、Learning Manager FTPアカウントへのアクセスにこのパスワードを使用する必要があります。

   特定のLearning Managerアカウントに作成できるLearning Manager FTPアカウントは1つだけです。

   概要ページでは、統合の接続名を指定できます。 次のオプションから、実行するアクションを選択します。

   * 社内ユーザーのインポート
   * ユーザースキルの書き出し – スケジュールの設定
   * ユーザースキルの書き出し – オンデマンド

   ![](assets/connectors-overview.png)

## 読み込み

・+++内ユーザー

社内ユーザーの読み込みオプションを使用すると、ユーザー読み込みレポートの生成を自動的にスケジュールできます。 生成されたレポートは、.CSVファイルとして送信されます。

+++

+++マップ属性

接続が正常に確立されたら、FTPフォルダーに配置されるCSVファイルの列をLearning Managerの対応する属性にマッピングできます。 この手順は必須です。

1. マップ属性ページの左側にはLearning Managerの予想される列が表示され、右側にはCSVの列名が表示されます。 最初は、右側に空の選択ボックスが表示されます。 任意のテンプレートCSVを読み込むには、次をクリックします **ファイルを選択**.
1. 上記の手順により、右側の選択ドロップダウンリストにすべてのCSV列名が表示されます。 Learning Managerの列名にマッピングする適切な列名を選択します。

   *マネージャーフィールドは、必ず電子メールアドレスタイプのフィールドにマッピングする必要があります。 コネクタを使用するには、すべての列をマッピングする必要があります。*

1. クリック **[!UICONTROL 保存]** マッピングの完了後。

   これで、コネクタを使用する準備ができました。 設定したばかりのアカウントは、管理者アプリ内でデータソースとして表示されるようになり、管理者が読み込みをスケジュールしたり、オンデマンドで同期したりできるようになります。



+++

+++Learning Manager FTPコネクタの使用

1. 外部システムからのCSVファイルは次のパスに配置する必要があります。

   `code $OPERATION$/$OBJECT_TYPE$/$SUB_OBJECT_TYPE$/data.csv`

   **注意：** 2016年7月リリースでは、ユーザーの読み込みのみが許可されています。 したがって、FTPコネクタを使用するには、CSVファイルが次のフォルダーにあることを確認する必要があります。

   `code Home/import/user/internal/*.csv`

1. FTPコネクタでは、CSVファイルからすべての行が取得されるため、あるCSV内のユーザーに対応する行が他のCSVに表示されないことが重要です。
1. すべてのCSVには、マッピングで指定された列が含まれている必要があります。
1. プロセスを開始する前に、必要なすべてのCSVがフォルダーに存在している必要があります。

ユーザーをLearning Managerに読み込む際、管理者はユーザーがLearning Managerで管理されている方法も把握しておく必要があります。 詳しくは、「 [ユーザー管理ヘルプ](../integration-admin/feature-summary/migration-manual.md#usermanagement) 詳細情報を参照してください。

+++

## エクスポート

+++スキル

ユーザーのスキルレポートを書き出すには、2つのオプションがあります。

**[!UICONTROL ユーザースキル – オンデマンド]**：開始日を指定し、オプションを使用してレポートを書き出すことができます。レポートは、入力された日付から現在までの間に抽出されます。

![](assets/user-skills-on-demand.png)

**[!UICONTROL ユーザースキル – 設定]**：このオプションでは、レポートの抽出をスケジュールできます。 「スケジュールを有効にする」チェックボックスをオンにし、開始日時を指定します。 レポートを生成および送信する間隔を指定することもできます。

![](assets/user-skills-configure.png)

+++

自分のFTPロケーションに書き出されたファイルが配置される書き出しフォルダーを開くには、次に示すように、ユーザースキルページで指定されたFTPフォルダーへのリンクを開きます。

![](assets/ftp-folder.png)

自動書き出しされたファイルは、この場所に存在します **Home/export/&#42;FTP_location&#42;**

自動書き出しされたファイルは、 **skill_achievements_&#42;開始日&#x200B;&#42;_から_&#42;終了日&#42;.csv**

![](assets/exported-csvs.png)

## Lyndaコネクタ {#lyndaconnector}

Lynda.comをご利用のエンタープライズのお客様は、Lyndaコネクターを使用することにより、お客様の学習者がLearning Manager内でLyndaコースを検索および使用できるようになります。 APIキーを使用してLynda.comからコースを定期的に取得するように、コネクタを設定できます。 Learning Manager内にコースが作成されると、ユーザーはコースを検索して使用できます。 これにより、学習者の進行状況をLearning Manager内で追跡できます。

### Lyndaコネクタの設定 {#configurethelyndaconnector}

1. 統合管理ダッシュボードから、「Lynda」をクリックします。

   タイルが表示されます。これには、「はじめに」、「接続」、「接続を管理」の3つのオプションがあります。

1. Lyndaコネクタを初めて設定する場合は、[接続]をクリックします。

   このコネクタを設定する前に、Exavault FTPアカウントを設定する必要があります。

1. 接続ページから、コネクタの名前を指定します。 接続のAppkeyとSecret keyを入力します。

   Appkeyと秘密鍵を取得するには、ベンダーに問い合わせる必要があります。

1. 「保存」をクリックします。

   設定が保存され、アカウントのLynda接続が追加されます。 ホームページで「接続の管理」をクリックして、いつでも設定を編集できるようになりました。

1. 既に接続が確立されている場合は、「接続の管理」をクリックしてすべての接続を表示します。

   このコネクタを設定する前に、アカウントで移行機能を有効にする必要があります。

1. 編集する接続をクリックします。
1. 左ペインで、[Configure]をクリックします。 次のいずれかの操作を行います。

   * このウィンドウで、アカウントの詳細と同期スケジュールを表示または編集します。 このアカウントを有効にするには、「接続を有効にする」チェックボックスをオンにする必要があります。
   * 「編集」をクリックして、資格情報を編集します。 このフィールドの更新を元に戻すには、[リセット]をクリックします。
   * 「スケジュールの有効化」をクリックして、同期をスケジュールします。 開始時刻と日付を入力し、同期スケジュールの頻度を日数で入力できます。 たとえば、同期を3日ごとに有効にします。

   「保存」をクリックして変更を保存します。

   ![](assets/lynda.png)

1. 左ペインで、「On Demand Execution」をクリックします。 このオプションを使用すると、Lyndaからユーザーフィードやその他の関連データを読み込むことができます。 オンデマンド実行の開始日を入力し、「実行」をクリックして同期を実行します。 開始日から現在までのすべてのデータが読み込まれます。

   * 同期中にアプリケーションのダウンタイムが発生する場合は、「実行中のLearning Managerへのアクセスを無効にする」をクリックします。
   * 「実行中のLearning Managerへのアクセスを有効にする」をクリックした場合でも、同期中にサービスが中断されることはありません。

   ![](assets/lynda-ondemand.png)

1. また、このコネクタのすべての実行の概要を時系列で表示するには、いつでも左ペインで「実行ステータス」をクリックできます。 同期の開始日と期間、同期の種類（オンデマンド同期かどうか）、および同期のステータス（同期が進行中か完了しているか）を表示できます。

   接続を削除して再作成すると、コネクタの前の配管が再び表示されます。 接続を削除する前に、すべての実行を表示できます。

   再実行は、最新の同期に対してのみ実行できます。

   ![](assets/lynda-executionstatus.png)

## getAbstractコネクタ {#getabstractconnector}

getAbstract.comのエンタープライズ版をご利用のお客様は、getAbstractコネクターを使用して、getAbstractサマリーの検出と使用を学習者に求めることができます。 コネクタは、Learning Manager内で作成された学習者の完了レコードに基づいて、使用データを定期的に取得するように設定できます。 Learning Managerでこのコネクターを設定する方法については、以下を参照してください。

### getAbstractコネクターの設定 {#configurethegetabstractconnector}

1. 統合管理ダッシュボードから、「getAbstract」をクリックします。

   タイルから、「はじめに」、「接続」、「接続を管理」の3つのオプションが表示されます。

1. getAbstractコネクタを初めて構成する場合は、「接続」をクリックします。

   このコネクタを設定する前に、Exavault FTPアカウントを設定する必要があります。

   フィードにアクセスするには、このFTP資格情報をコンテンツプロバイダーと共有してください。

1. 「接続名」フィールドに接続の名前を入力します。

   「クライアントID」および「クライアントシークレット」フィールドに適切なキーを入力します。 このコネクタの適切なキーを取得するには、ベンダーに問い合わせる必要がある場合があります。

   キーは、クライアントが使用するコースのコースメタデータを取得するために必要です。

1. 既に接続が確立されている場合は、ホームページから、 getAbstract /接続を管理をクリックして、既存の設定を表示および編集します。

   このコネクタを設定する前に、アカウントで移行機能を有効にする必要があります。

1. 構成を表示または編集する接続をクリックします。

   ![](assets/getabstractschedulepage.png)

1. 左ペインで、[Configure]をクリックします。 次のいずれかの操作を行います。

   * このウィンドウで、アカウントの詳細と同期スケジュールを表示または編集します。 このアカウントを有効にするには、「接続を有効にする」チェックボックスをオンにする必要があります。
   * 「編集」をクリックして、資格情報を編集します。 このフィールドの更新を元に戻すには、[リセット]をクリックします。
   * 「スケジュールの有効化」をクリックして、同期をスケジュールします。 開始時刻と日付を入力し、同期スケジュールの頻度を日数で入力できます。 たとえば、同期を3日ごとに有効にします。

1. 「保存」をクリックします。

   設定が保存され、アカウントのgetAbstract接続が追加されます。

1. 左ペインで、「On Demand Execution」をクリックします。 このオプションを使用すると、getAbstractからユーザーフィードやその他の関連データを読み込むことができます。 オンデマンド実行の開始日を入力し、「実行」をクリックして同期を実行します。 開始日から現在までのすべてのデータが読み込まれます。

   * 同期中にアプリケーションのダウンタイムが発生する場合は、「実行中のLearning Managerへのアクセスを無効にする」をクリックします。
   * 「実行中のLearning Managerへのアクセスを有効にする」をクリックした場合でも、同期中にサービスが中断されることはありません。

1. また、このコネクタのすべての実行の概要を時系列で表示するには、いつでも左ペインで「実行ステータス」をクリックできます。 同期の開始日と期間、同期の種類（オンデマンド同期かどうか）、および同期のステータス（同期が進行中か完了しているか）を表示できます。

   接続を削除して再作成すると、コネクタの前の配管が再び表示されます。 接続を削除する前に、すべての実行を表示できます。

   再実行は、最新の同期に対してのみ実行できます。

   どのような種類の同期を実行する場合でも、同期で指定した日付のgetAbstract FTPフォルダーにユーザーフィードが存在することを確認する必要があります。

   getAbstractのユーザー向けフィードファイルのサンプルである次のExcelシートを参照してください。 ファイル名は、** report_export_yyyy_MM_dd_HHmmss.xlsxの形式に従う必要があり**す。または、 **report_export_yyyy_MM_dd.xlsx**.
   [getAbstractユーザーフィードサンプルExcelシート](assets/report-export-20170401175342.xlsx)

## Harvard ManageMentorコネクタ {#hmmconnector}

Harvard ManageMentorコネクタは、Harvard ManageMentorのエンタープライズ版をご利用のお客様が使用できます。お客様は、Harvard ManageMentorのコースを学習者が検索および使用できるようになります。 コネクターはLearning Manager内でコースを作成するのに役立ち、学習者の進行状況データを定期的に取得するように設定できます。 このコネクタを設定するには、次の手順を実行します。

### Harvard ManagerMentorコネクタの設定 {#configuretheharvardmanagermentorconnector}

1. 統合管理ダッシュボードから、「 Harvard ManageMentor 」をクリックします。

   タイルから、「はじめに」、「接続」、「接続を管理」の3つのオプションが表示されます。

1. Harvard ManageMentorコネクタを初めて構成する場合は、「Connect」をクリックします。

   このコネクタを設定する前に、Exavault FTPアカウントも設定する必要があります。

   フィードにアクセスするには、このFTP資格情報をコンテンツプロバイダーと共有してください。

1. 「接続名」フィールドに、接続の名前を入力します。 [接続]をクリックして、この接続を保存します。
1. 既に接続が確立されている場合は、ホームページから、Harvard ManageMentor/接続の管理をクリックします。 既存の設定を編集するには、編集する接続をクリックします。

   このコネクタを設定する前に、アカウントで移行機能を有効にする必要があります。

   ![](assets/hmm.png)

1. 左ペインで、[Configure]をクリックします。 次のいずれかの操作を行います。

   * このウィンドウで、アカウントの詳細と同期スケジュールを表示または編集します。 このアカウントを有効にするには、「接続を有効にする」チェックボックスをオンにする必要があります。
   * 「スケジュールの有効化」をクリックして、同期をスケジュールします。 開始時刻と日付を入力し、同期スケジュールの頻度を日数で入力できます。 たとえば、同期を3日ごとに有効にします。

1. 左ペインで、「On Demand Execution」をクリックします。 このオプションを使用すると、Harvard ManageMentorからユーザーフィードやその他の関連データを読み込むことができます。 オンデマンド実行の開始日を入力し、「実行」をクリックして同期を実行します。 開始日から現在までのすべてのデータが、この接続にインポートされます。

   * 同期中にアプリケーションのダウンタイムが発生する場合は、「実行中のLearning Managerへのアクセスを無効にする」をクリックします。
   * 「実行中のLearning Managerへのアクセスを有効にする」をクリックした場合でも、同期中にサービスが中断されることはありません。

   数日ごとに同期を自動化する場合は、「繰り返し日数」フィールドに日数を指定します。 同期を行うと、アカウントが最新バージョンのHarvard ManageMentorからの要約と要約で更新されます。

1. また、このコネクタのすべての実行の概要を時系列で表示するには、いつでも左ペインで「実行ステータス」をクリックできます。 同期の開始日と期間、同期の種類（オンデマンド同期かどうか）、および同期のステータス（同期が進行中か完了しているか）を表示できます。

   接続を削除して再作成すると、コネクタの前の配管が再び表示されます。 接続を削除する前に、すべての実行を表示できます。

   再実行は、最新の同期に対してのみ実行できます。

   同期を正常に実行するには、Harvard ManageMentor FTPフォルダに少なくとも1つの以下のファイルが存在していることを確認する必要があります。

   hmm12_metadata.xlsx：このファイルは、Harvard ManageMentorコネクタのコースメタデータを提供します。 ファイルをアップロードするときには、命名規則に従ってください。

   client_hmm12_20150125.xlsx：これはHarvard ManageMentorコネクタのユーザーフィードです。 従う必要があるファイル命名規則は、次のとおりです。 **client_hmm12_yyyyMMdd.xlsx.**

   このコネクタの次の2つのユーザーフィードファイルとコースフィードファイルの例を参照してください。
   [Harvard ManageMentorコネクタのコースメタデータファイル](assets/hmm12-metadata.xlsx) [Harvard ManageMentorコネクタのユーザーフィード](assets/client-hmm12-20170304.xlsx)

## Workdayコネクタ {#workdayconnector}

Workdayコネクターを使用すると、Learning ManagerをWorkdayテナントと統合して、データを自動的に同期できます。

### 読み込み

#### マップ属性

統合管理者はWorkdayの列を選択し、その列を対応するLearning Managerのグループ化可能属性にマッピングできます。 これは1回限りの作業です。 マッピングが完了すると、それ以降のユーザーの読み込みでは同じマッピングが使用されます。 管理者がユーザーを読み込むために別のマッピングを使用する場合は、再設定できます。

#### 自動ユーザー読み込み

ユーザー読み込みプロセスにより、Learning Manager管理者はWorkdayから従業員の詳細を取得し、その情報をLearning Managerに自動的に読み込ませることができます。

#### ユーザーのフィルタリング

Learning Manager管理者は、読み込む前にユーザーにフィルタリングを適用できます。 例えば、Learning Manager管理者は、階層内のすべてのユーザーを1人以上の特定のマネージャーの管理下に読み込むように選択できます。

## エクスポート

ユーザーのスキルの書き出しを使用すると、ユーザーのスキルをWorkdayに自動的に書き出すことができます。

複数のLearning Managerアカウントのスキルを、同じWorkdayアカウントを使用して同時に書き出すことはできません。

## スケジュール {#Scheduling-1}

管理者は、組織の要件に応じてタスクをスケジュール設定できます。Learning Managerアプリケーション内のユーザーは、スケジュールに従って最新の状態になります。 同様に、統合管理者は、外部システムと統合されるようにスキルの書き出しをスケジュールすることができます。 Learning Managerアプリケーションで、同期を毎日実行できます。

## Workdayコネクタの設定 {#configureworkdayconnector}

**前提条件**:ISU_Permissionsドキュメントで定義された権限で統合システムユーザー(ISU)を作成するには、組織のWorkday管理者にリクエストしてください。 以下のリンクからコピーをダウンロードします。
[統合システムユーザー(ISU)のセキュリティのコピーをダウンロードします。](assets/isu-permissions-v1.pdf) Learning ManagerをWorkdayコネクタに統合するプロセスについて説明します。

1. Learning Managerホームページで、Workdayタイルにカーソルを合わせます。 メニューが表示されます。 クリック **[!UICONTROL Connect]** メニュー内のアイテムです。

   ![](assets/workday-tile.png)

1. 新しい接続の資格情報の入力を求めるダイアログが表示されます。 接続を行う前に入力する必要があるフィールドを次に示します。

   * 接続名：環境設定に従って接続名を指定します。
   * ホストURL：統合管理者は、対応するWorkday管理者からホストURLの詳細を取得できます。
   * テナント：テナントは会社の内部です。 Workday管理者に、テナントの詳細が表示されます。
   * ユーザー名とパスワード： Workday管理者は、必要なセキュリティ権限を持つ統合システムユーザー(ISU)を作成し、統合管理者と共有します。

   注意： Learning ManagerはWorkday APIのバージョン28.1を使用しています。

   ![](assets/configure-connector.png)

1. 関連するすべてのフィールドに情報を入力したら、「接続」をクリックします。

   複数のWorkday接続をLearning Managerアカウントに同期させることもできます。

概要ページでは、統合の接続名を指定できます。 次のオプションから、実行するアクションを選択します。

* 社内ユーザーのインポート
* ユーザースキルの書き出し – スケジュールの設定
* ユーザースキルの書き出し – オンデマンド

![](assets/overview.png)

## 読み込み

### マップ属性 {#MapAttributes-1}

Workdayコネクターを使用してLearning ManagerとWorkdayを連携し、データを自動的に同期できます。 すべてのアクティブユーザーをWorkdayからLearning Managerに読み込むことができます。 ユーザーは、FTPやSalesforceなど、様々なデータソースから読み込むことができます。

ユーザーを読み込む前に、Learning ManagerとWorkdayのユーザー属性をマッピングする必要があります。 概要ページで、「読み込み」の下の「社内ユーザー」オプションを使用してマップ属性を提供します。

「AdobeのLearning Manager」列に、AdobeのLearning Manager資格情報を入力します。 ドロップダウンを使用して、Workdayの列に対して正しい資格情報を選択します。

現在、Learning Managerは、Workdayから44のユーザー属性の読み込みをサポートしています。 Learning Managerのアクティブフィールドを使用して、属性を追加します。

![](assets/map-attributes.png)

Workdayには4つの階層レベルがありますが、Learning Managerには2つの階層レベルがあります。 Workdayの4つのレベルは、スキルプロファイルカテゴリ、スキルプロファイル、スキルアイテムカテゴリ、およびスキルアイテムです。 Learning Managerのスキル名とレベルは、Workdayのスキルアイテムにマッピングされます。

+++サポートされているWorkday属性のリスト

wd:User_ID\
wd:Worker_ID\
wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data@wd:Formatted_Name\
wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data@wd:Formatted_Name\
wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor\
wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor\
wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:First_Name\
wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Last_Name\
wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:First_Name\
wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Last_Name\
wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0@wd:Formatted_Address\
wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Postal_Code\
wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Country_Region_Descriptor\
wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0@wd:Formatted_Phone\
wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Country_ISO_Code\
wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:International_Phone_Code\
wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Phone_Number\
wd:Personal_Data.wd:Primary_Nationity_Reference.wd:ID.1.$\
wd:Personal_Data.wd:Gender_Reference.wd:ID.1.$\
wd:Personal_Data.wd:Identification_Data.wd:National_ID.0.wd:National_ID_Data.wd:ID\
wd:Personal_Data.wd:Identification_Data.wd:Custom_ID.0.wd:Custom_ID_Data.wd:ID\
wd:User_Account_Data.wd:Default_Display_Language_Reference.wd:ID.1.$\
wd:Role_Data.wd:Organization_Role_Data.wd:Organization_Role.0.wd:Organization_Role_Reference.wd:ID.1$\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Position_Title\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Title\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Name\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data@wd:Formatted_Address\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Classification_Reference.wd:ID.1$\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Group_Reference.wd:ID.1$\
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Work_Space__Reference.wd:ID.1$\
wd:Employment_Data.wd:Worker_Status_Data.wd:Active\
wd:Employment_Data.wd:Worker_Status_Data.wd:Active_Status_Date\
wd:Employment_Data.wd:Worker_Status_Data.wd:Hire_Date\
wd:Employment_Data.wd:Worker_Status_Data.wd:Original_Hire_Date\
wd:Employment_Data.wd:Worker_Status_Data.wd:Retired\
wd:Employment_Data.wd:Worker_Status_Data.wd:Retirement_Date\
wd:Employment_Data.wd:Worker_Status_Data.wd:Terminated\
wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Date\
wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Last_Day_of_Work\
wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Code\
wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Name\
wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Type_Reference.wd:ID.1$\
wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Subtype_Reference.wd:ID.1$\
wd:Qualification_Data.wd:Education.0.wd:School_Name\
wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Job_Title\
wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Company\
wd:Management_Chain_Data.wd:Worker_Supervisory_Management_Chain_Data.wd:Management_Chain_Data.0.wd:Manager.Employee_ID

+++

## エクスポート

ユーザーが達成したすべてのスキルをLearning ManagerからWorkdayに書き出すことができます。 Learning Managerはすべてのアクティブなユーザースキルのみを書き出し、廃止されたスキルは書き出さないことに注意してください。 複数のLearning Managerアカウントを同じWorkdayコネクタに接続することもできます。 2つのLearning Managerアカウントのスキル名が同じ場合、Workdayの同じスキルにマッピングされます。 2つのLearning Managerアカウントが同じWorkdayアカウントを使用している場合は、Workdayでスキルを更新する前に、すべてのLearning Managerアカウントでスキル名を更新することをお勧めします。

+++ユーザースキル – 設定

このオプションを使用すると、レポートの抽出をスケジュールできます。 「この接続を使用してユーザースキルの書き出しを有効にする」チェックボックスが有効になっていることを確認します。 「スケジュールを有効にする」チェックボックスをオンにし、開始日時を指定します。 レポートを生成および送信する間隔を指定することもできます。 「スケジュールを有効にする」チェックボックスをオンにし、開始日、時刻、およびn日後の繰り返しを入力します。 完了したら、「保存」をクリックします。

![](assets/configure-schedule.png)

+++

+++ユーザースキル – オンデマンド

オプションを使用して、開始日を指定し、レポートを書き出すことができます。 レポートは入力された日付から現在まで抽出されます。 レポートの生成を開始する日付を入力し、「実行」をクリックします。

![](assets/on-demand-report.png)

+++

+++ユーザースキル – 実行ステータス

ここでは、すべてのタスクの概要を表示し、その進捗レポートを取得できます。 エラーレポートのリンクをクリックして、エラーレポートをダウンロードできます。

![](assets/execution-status.png)

+++

## miniオレンジコネクタ {#miniorangeconnector}

miniOrangeコネクターを使用すると、Learning ManagerをminiOrangeのテナントと統合して、データを自動的に同期できます。

### 読み込み

#### マップ属性

統合管理者はminiOrange属性を選択し、対応するLearning Managerのグループ化可能属性にマッピングできます。 これは1回限りの作業です。 マッピングが完了すると、それ以降のユーザーの読み込みでは同じマッピングが使用されます。 管理者がユーザーを読み込むために別のマッピングを使用する場合は、再設定できます。

#### 自動ユーザー読み込み

ユーザー読み込みプロセスにより、Learning Manager管理者はminiOrangeから従業員の詳細を取得し、その情報をLearning Managerに自動的に読み込ませることができます。

#### ユーザーのフィルタリング

Learning Manager管理者は、読み込む前にユーザーにフィルタリングを適用できます。 例えば、Learning Manager管理者は、階層内のすべてのユーザーを1人以上の特定のマネージャーの管理下に読み込むように選択できます。

miniOrangeコネクターを設定するには、Learning Manager CSMチームにお問い合わせください。

## miniOrangeコネクタの構成 {#configureminiorangeconnector}

1. Learning Managerホームページで、miniOrangeカード/サムネールにカーソルを合わせます。 メニューが表示されます。 クリック  **[!UICONTROL Connect]** をクリックします。

   ![](assets/miniorange-tile.png)

1. 「接続」をクリックして、新しい接続を確立します。 miniOrangeコネクタページが表示されます。 マップするアカウントの詳細を入力します。

   ![](assets/establish-connection.png)

1. miniOrnageユーザーをLearning Manager社内ユーザーとして直接読み込む場合、 **[!UICONTROL 社内ユーザーのインポート]** オプションです。

   ![](assets/import-users.png)

1. マッピングページの左側にはLearning Managerの列が表示され、右側にはminiOrnageの列が表示されます。 Learning Managerの列名にマッピングする適切な列名を選択します。

   ![](assets/map-attributes.png)

1. データ・ソースを表示および編集するには、管理者として、 **[!UICONTROL 設定/データソース]**.

   確立されたminiOrangeソースがリストされます。 フィルターを編集する必要がある場合は、 **[!UICONTROL 編集]**.

   ![](assets/data-source.png)

1. 読み込みが完了すると、通知が届きます。 インポートログを表示または編集するには、 **[!UICONTROL ユーザー/ログを読み込み]**

### 接続を削除する {#deleteaconnection}

確立されたminiOrange接続を削除するには、次の手順に従います。

## BlueJeansコネクター {#bluejeansconnector}

Learning ManagerをBlueJeansコネクターと統合し、BlueJeansを使用してクラスをホストできるようになりました。 BlueJeansでは、オーディオおよびビデオ会議通話、ビデオチャット、ウェビナーを開始できます。

コネクタを設定して使用するには、次の手順に従います。

1. Learning Managerホームページで、BlueJeansカード/サムネールにマウスを合わせます。 メニューが表示されます。 クリック  **[!UICONTROL Connect]** をクリックします。

   ![](assets/miniorange.png)

1. BlueJeansコネクタページが開きます。 アカウントの詳細をそれぞれのフィールドに入力し、Learning ManagerとBlueJeansを統合してユーザーフィードを同期できるようにします。 詳細は、BlueJeansアカウントの管理者から取得できます。

   ![](assets/bluejeans-connecotrpage.png)

   コネクターを有効にしながら、学習者はLearning Managerアカウントで使用している電子メールIDを使用して、Learning Managerにフィードバックを送信できるようにします。

1. 接続が確立されたら、作成者は、会議システムとしてBlueJeansを使用してVCコースを作成します。

   ![](assets/conferencing-systems.png)

1. 管理者、マネージャー、学習者は、作成されたコースに学習者を登録できます。 登録時に、学習者は電子メールを受け取ります。 学習者は自分のLearning Managerアカウントにログインしてプログラムの詳細を表示し、コースを受講できます。
1. コースを完了すると、完了レポートがLearning Managerに送信されます。 管理者は完了レポートを表示して、学習者の出席とスコアを確認できます。

   ![](assets/-attendence-and-scoringreport.png)

## ボックスコネクタ {#boxconnector}

BOXコネクターを使用すると、Learning Managerを任意の外部システムと統合して、データを自動的に同期できます。 外部システムがデータをCSV形式で書き出し、そのデータをLearning ManagerのBoxアカウントの適切なフォルダーに配置できることが期待されています。 ボックスコネクタの機能は次のとおりです。

データ移行、ユーザー読み込み、およびデータ書き出しにFTPコネクターを使用することもできます。 詳しくは、 [Learning Manager FTPコネクタ。](third-party-connectors.md#main-pars_header_1427405935)

## データのインポート {#DataImport-1}

ユーザー読み込みプロセスにより、Learning Manager管理者はLearning Manager Boxサービスから従業員の詳細を取得し、その情報をLearning Managerに自動的に読み込ませることができます。 この機能を使用すると、それらのシステムによって生成されたCSVをBoxアカウントの適切なフォルダーに配置することで、複数のシステムを統合できます。 Learning ManagerはCSVファイルを取得し、ファイルを結合して、スケジュールに従ってデータを読み込みます。 詳細については「スケジュール機能」を参照してください。

**マップ属性**

統合管理者はCSVの列を選択し、その列をLearning Managerのグループ化可能属性にマッピングできます。 このマッピングは1回限りの作業です。 マッピングが完了すると、その後のユーザーのインポートでも同じマッピングが使用されます。管理者がユーザーのインポート用に別のマッピングを使用する場合は、マッピングを再構成できます。

## データの書き出し {#dataexport}

データの書き出しを使用すると、ユーザーはユーザースキルをBoxの場所に書き出して、サードパーティシステムと統合できます。

## スケジュールレポート {#schedulereports}

管理者は、組織の要件に応じてタスクをスケジュール設定できます。Learning Managerアプリケーション内のユーザーは、スケジュールに従って最新の状態になります。 同様に、統合管理者は、外部システムと統合されるようにスキルの書き出しをスケジュールすることができます。 Learning Managerアプリケーションで、同期を毎日実行できます。

## Boxコネクターの設定 {#configureboxconnector}

Learning ManagerをBoxコネクターと統合するプロセスについて説明します。

1. Learning Managerホームページで、Boxカード/サムネールにカーソルを合わせます。 メニューが表示されます。 メニューの接続項目をクリックします。

   ![](assets/screen-shot-2017-10-25at54426pm.png)

1. 電子メールIDの入力を求めるダイアログが表示されます。 組織のLearning Manager Boxアカウントの管理責任者の電子メールIDを入力します。 電子メールIDを入力した後、「接続」をクリックします。

1. Learning Managerは、Boxに初めてアクセスする前にユーザーにパスワードの再設定を促す電子メールを送信します。 ユーザーはパスワードをリセットし、Learning Manager Boxアカウントへのアクセスに使用する必要があります。

   特定のLearning Managerアカウントに作成できるLearning Manager Boxアカウントは1つだけです。

   概要ページでは、統合の接続名を指定できます。 次のオプションから、実行するアクションを選択します。

   * 社内ユーザーのインポート
   * ユーザースキルの書き出し – スケジュールの設定
   * ユーザースキルの書き出し – オンデマンド

## 読み込み

・+++内ユーザー

社内ユーザーの読み込みオプションを使用すると、ユーザー読み込みレポートの生成を自動的にスケジュールできます。 生成されたレポートは、.CSVファイルとして送信されます。

+++

+++マップ属性

接続が正常に確立されたら、Boxフォルダーに配置されるCSVファイルの列を、Learning Managerの対応する属性にマッピングできます。 この手順は必須です。

1. マップ属性ページの左側にはLearning Managerの予想される列が表示され、右側にはCSVの列名が表示されます。 最初は、右側に空の選択ボックスが表示されます。 「ファイルを選択」をクリックして、任意のテンプレートCSVを読み込みます。

1. 上記の手順により、右側の選択ドロップダウンリストにすべてのCSV列名が表示されます。 Learning Managerの列名にマッピングする適切な列名を選択します。

   *マネージャーフィールドは、必ず電子メールアドレスタイプのフィールドにマッピングする必要があります。 コネクタを使用するには、すべての列をマッピングする必要があります。*

1. マッピングが完了したら、「保存」をクリックします。

   これで、コネクタを使用する準備ができました。 設定したばかりのアカウントは、管理者アプリ内でデータソースとして表示されるようになり、管理者が読み込みをスケジュールしたり、オンデマンドで同期したりできるようになります。

+++

+++Learning Manager Boxコネクターの使用

1. 外部システムからのCSVファイルは次のパスに配置する必要があります。

   `code $OPERATION$/$OBJECT_TYPE$/$SUB_OBJECT_TYPE$/data.csv`

   **注意：** 2016年7月リリースでは、ユーザーの読み込みのみが許可されています。 したがって、Boxコネクタを使用するには、CSVファイルが次のフォルダーに配置されていることを確認する必要があります。\
   `code Home/import/user/internal/*.csv`

1. Boxコネクタは、CSVファイルからすべての行を取得するため、1つのCSV内のユーザーに対応する行が、他のCSVに表示されないことが重要です。
1. すべてのCSVには、マッピングで指定された列が含まれている必要があります。
1. プロセスを開始する前に、必要なすべてのCSVがフォルダーに存在している必要があります。

ユーザーをLearning Managerに読み込む際、管理者はユーザーがLearning Managerで管理されている方法も把握しておく必要があります。 詳しくは、「 [ユーザー管理ヘルプ](../integration-admin/feature-summary/migration-manual.md#usermanagement) 詳細情報を参照してください。

+++

## エクスポート

+++スキル

ユーザーのスキルレポートを書き出すには、2つのオプションがあります。

ユーザースキル – オンデマンド：開始日を指定し、オプションを使用してレポートを書き出すことができます。レポートは、入力された日付から現在までの間に抽出されます

**[!UICONTROL ユーザースキル – 設定]**：このオプションでは、レポートの抽出をスケジュールできます。 「スケジュールを有効にする」チェックボックスをオンにし、開始日時を指定します。 レポートを生成および送信する間隔を指定することもできます。

+++

Boxの場所に書き出されたファイルが配置される書き出しフォルダーを開くには、以下のように、ユーザースキルページで提供されているBoxフォルダーへのリンクを開きます。

自動書き出しされたファイルは、この場所に存在します **Home/export/&#42;Box_location&#42;**

自動書き出しされたファイルは、 **skill_achievements_&#42;開始日&#x200B;&#42;_から_&#42;終了日&#42;.csv**

Learning Managerチームが共有するBoxフォルダーのアクセス権限とコンテンツは、お客様が管理する必要があります。  また、フォルダー内のコンテンツはフランクフルト地域に物理的に保存されます。

## LinkedInLearningコネクター {#linkedinlearningconnector}

LinkedIn.comをご利用のエンタープライズのお客様は、LinkedInLearningコネクターを使用することにより、お客様の学習者がLearning Manager内でコースを検索および使用できるようになります。 APIキーを使用してコースを定期的に取得するようにコネクタを設定できます。 Learning Manager内にコースが作成されると、ユーザーはコースを検索して使用できます。 これにより、学習者の進行状況をLearning Manager内で追跡できます。

### linkedInコネクタの設定 {#configurelinkedinconnector}

1. 統合管理ダッシュボードから、「 LinkedInLearning 」をクリックします。

   タイルが表示されます。これには、「はじめに」、「接続」、「接続を管理」の3つのオプションがあります。

1. LinkedInLearningコネクターを初めて設定する場合は、「接続」をクリックします。

   このコネクタを設定する前に、Exavault FTPアカウントを設定する必要があります。

1. 接続ページから、コネクタの名前を指定します。 接続のAppkeyとSecret keyを入力します。

   Appkeyと秘密鍵を取得するには、ベンダーに連絡する必要があります。

1. 「保存」をクリックします。

   設定が保存され、アカウントのLinkedInLearning接続が追加されます。 ホームページで「接続の管理」をクリックして、いつでも設定を編集できるようになりました。

1. 既に接続が確立されている場合は、「接続の管理」をクリックしてすべての接続を表示します。

   このコネクタを設定する前に、アカウントで移行機能を有効にする必要があります。

1. 編集する接続をクリックします。
1. 左ペインで、[Configure]をクリックします。 次のいずれかの操作を行います。

   * このウィンドウで、アカウントの詳細と同期スケジュールを表示または編集します。 このアカウントを有効にするには、「接続を有効にする」チェックボックスをオンにする必要があります。
   * 「編集」をクリックして、資格情報を編集します。 このフィールドの更新を元に戻すには、[リセット]をクリックします。
   * 「スケジュールの有効化」をクリックして、同期をスケジュールします。 開始時刻と日付を入力し、同期スケジュールの頻度を日数で入力できます。 たとえば、同期を3日ごとに有効にします。

   「保存」をクリックして変更を保存します。

1. 左ペインで、「On Demand Execution」をクリックします。 linkedInからユーザーフィードやその他の関連データを読み込むことができます。 オンデマンド実行の開始日を入力し、「実行」をクリックして同期を実行します。 開始日から現在までのすべてのデータが読み込まれます。

   * 同期中にアプリケーションのダウンタイムが発生する場合は、「実行中のLearning Managerへのアクセスを無効にする」をクリックします。
   * 「実行中のLearning Managerへのアクセスを有効にする」をクリックした場合でも、同期中にサービスが中断されることはありません。

1. また、このコネクタのすべての実行の概要を時系列で表示するには、いつでも左ペインで「実行ステータス」をクリックできます。 同期の開始日と期間、同期の種類（オンデマンド同期かどうか）、および同期のステータス（同期が進行中か完了しているか）を表示できます。

   接続を削除して再作成すると、コネクタの前の配管が再び表示されます。 接続を削除する前に、すべての実行を表示できます。

   再実行は、最新の同期に対してのみ実行できます。

