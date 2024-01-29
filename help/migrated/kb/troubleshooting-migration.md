---
description: このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、データとコンテンツを既存のLMSからLearning Managerに移行する際に発生する可能性のある一般的な問題のいくつかを解決できます。
jcr-language: en_us
title: 移行に関する問題のトラブルシューティング
contentowner: jayakarr
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---



# 移行に関する問題のトラブルシューティング

このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、データとコンテンツを既存のLMSからLearning Managerに移行する際に発生する可能性のある一般的な問題のいくつかを解決できます。

## 一般的な移行の問題 {#genericmigrationissues}

### FTPフォルダーまたはコンテンツフォルダーにログインできない {#unabletologintoftpfolderorcontentfolder}

FTPサービスとBoxサービスでアカウントが作成されていることを確認します。 移行プロジェクトを作成するときは、これら2つのサービスの設定を要求します。 サービスを作成すると、ExavaultとBoxからパスワードをリセットまたは設定する電子メールが届きます。 パスワードを忘れた場合は、ExavaultおよびBoxのwebサイトにアクセスしてパスワードをリセットできます。

### 「更新」ボタンをクリックしてもジョブが反映されない {#jobsarenotreflectedevenafterclickingrefreshbutton}

* CSVファイルがExavault FTPの正しいフォルダーにアップロードされていることを確認します。 パス構造は次のようになります。

`code Account>Project>Sprint location`

* CSVファイルのファイル名がCSV仕様名に従っていることを確認してください。

   * course.csv
   * course_instance.csv
   * course_module.csv
   * enrollment.csv
   * module.csv
   * module_version.csv
   * user_course_grade.csv

### ジョブのエラーがエラーレコードとともに表示されます {#failuresareshownforjobswitherrorrecords}

1. をクリックしてエラーログをダウンロードします。 **エラーレコードのダウンロード** リンク
1. 報告されたエラーに基づいて元のCSVを修正し、
1. 変更したCSVを使用して、スプリントを再実行します。

変更の数がレコードの総数と比較して少ないときには、変更したCSVを新しいSprintで実行することがベストプラクティスです。

### スプリントの移行を停止してもLearning Managerアプリケーションにログインできない {#unabletologintocaptivateprimeapplicationevenafterstoppingthesprintmigration}

Sprintの実行が停止または完了すると、アカウントのロック解除に10 ～ 15分かかります。 15分後にアプリケーションにアクセスしてみてください。

### 一部の移行ジョブでは、「停止」がトリガーされた後でも「進行中」ステータスが表示されます。 {#someofthemigrationjobsdisplayinprogressstatusevenafterstopistriggered}

「処理中」状態になると、すべてのジョブの実行を停止するまでに10～15分かかる場合があります。 10分後にステータスを再確認してください。

### ボタンが無効になっているため、スプリントを作成できない {#unabletocreateasprintasthebuttonisdisabled}

スプリントを作成する前に、現在のスプリントが「完了」とマークされていることを確認します。 クリック **[!UICONTROL スプリントの完了をマーク]** をクリックして、スプリントの移行を完了します。

### ボタンが無効になっているため、移行プロジェクトに完了とマークすることができない {#unabletomarkamigrationprojectascompleteasthebuttonisdisabled}

移行プロジェクトを完了とマークする前に、現在のスプリントが「完了」とマークされていることを確認します。 クリック **[!UICONTROL スプリントの完了をマーク]** をクリックして、スプリントの移行を完了します。

## CSVの問題 {#csvissues}

### module_version.csvファイルの移行に失敗したため、コンテンツがまだ移行されていません {#moduleversioncsvfilemigrationisfailingandcontentisnotmigratedyet}

コンテンツがコンテンツフォルダー（指定された移行プロジェクト、スプリントパスのBoxアカウント）で利用可能であることを確認します。 また、オプションが選択されていることを確認します **はい** 対象 **このスプリントのコンテンツを移行しますか？** スプリントの作成ページで質問します。

選択し忘れた場合 **はい**&#x200B;次に、このスプリントで先に進みます。このスプリントを完了するまで待つ必要があります。 別のスプリントを作成し、をクリックします **[!UICONTROL はい]**.

### enrollment.csvまたはuser_course_grade.csvレコードで「有効なLearning Manager IDではありません」というエラーメッセージが表示されて失敗する {#enrollmentcsvorusercoursegradecsvrecordsfailwithanerrormessagenotavalidprimeid}

電子メールIDがuserIdの一部として入力されていること、assignedByUserIDフィールドが有効なLearning Managerユーザーに属していることを確認します。 そうでない場合は、ユーザーを追加して、で新しいスプリントを作成してください。 **ユーザーを同期** オプションが選択されました。 ユーザーが組織に属していない場合は、ユーザーCSV仕様の「ユーザーを追加」を使用して、そのユーザーをLearning Managerの削除済みユーザーとして追加します。 削除されたユーザーを追加するためのサンプルCSV仕様は、参照用に以下のとおりです。

[Users.csv](assets/users.zip) 詳しくは、「 **CSVの仕様とサンプルCSV** のセクション [移行マニュアル](../integration-admin/feature-summary/migration-manual.md) csv仕様の完全なセットとサンプルCSVファイルをダウンロードできます。

### 移行したコースで、コースが空白で表示されるか、正しくないモジュールが再生される {#coursesappearblankorincorrectmodulesplayforamigratedcourse}

次のことを確認します **moduleOrderInCourse** コースのキー値は次で始まります **0** 連続順序です。 courseModuleTypeに関する順序は、PRETEST、TESTOUT、CONTENTでなければなりません

また、2つのバージョンのアクティビティ、クラスルーム、VCが、既存のコースにリンクされていないことを確認してください。

### 「モジュールは既存のコースに既にリンクされています」というメッセージを受信 {#receivingamessageasmoduleisalreadylinkedwithanexistingcourse}

Learning Managerでは、アクティビティ/ VC /クラスルームモジュールを複数のコースにリンクすることはできません。 モジュールが他のコースにリンクされていないことを確認します。

### コースは別々のモジュールバージョンにリンクされているが、すべてのコースでActivity/VC/Classroomモジュールの最新バージョンが表示される {#allthecoursesshowthelatestversionofactivityvcclassroommoduleseventhoughthecoursesarelinkedwithdifferentmoduleversions}

アクティビティ、クラスルーム、バーチャルクラスルームのモジュールのバージョン管理は、Learning Managerではサポートされていません。 moduleVersion.csvファイルを使用してバージョンを提供する場合、新しいバージョンを作成する代わりに、既存のファイルが更新されます。

### 移行されたアクティビティ/VC/教室モジュールに対して目的の期間が表示されない {#desireddurationdoesnotappearforamigratedactivityvcclassroommodule}

アクティビティ/ VC /クラスルームモジュールに対して、希望期間が有効なエントリではありません。

### Learning ManagerでハイパーリンクURLが開かない {#hyperlinkurldoesntopenupincaptivateprime}

提供されたリンクに「http://&#39;」または「https://&#39;」が付いていることを確認します。

### moduleVersionの移行が「ファイルが見つかりません」というエラーで失敗する {#moduleversionmigrationfailswithfilenotfounderrors}

参照先ファイルがコンテンツフォルダーに存在し、正常に移行されていることを確認します。

### moduleVersionの移行が失敗し、エラーメッセージ「内部エラーが発生しました – モジュール: xおよびモジュールのバージョン: y」が表示されます。 {#moduleversionmigrationfailswithanerrormessageasaninternalerrorhasoccurredformodulexandmoduleversiony}

スプリントを再実行して問題を解決します。
