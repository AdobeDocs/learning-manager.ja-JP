---
description: このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、データとコンテンツを既存の LMS から Learning Manager に移行する際に発生する可能性のある一般的な問題のいくつかを解決できます。
jcr-language: en_us
title: 移行の問題のトラブルシューティング
contentowner: jayakarr
exl-id: b9f17644-f237-4701-86e9-8496db941920
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 43%

---

# 移行の問題のトラブルシューティング

このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、データとコンテンツを既存の LMS から Learning Manager に移行する際に発生する可能性のある一般的な問題のいくつかを解決できます。

## 一般的な移行の問題 {#genericmigrationissues}

### FTP フォルダーまたはコンテンツフォルダーにログインできない {#unabletologintoftpfolderorcontentfolder}

ご使用のアカウントを FTP サービスおよび Box サービスで作成したことを確認してください。移行プロジェクトの作成時に、この 2 つのサービスの設定を依頼します。サービスを作成すると、Exavault および Box からパスワードをリセットまたは設定する電子メールが届きます。パスワードを忘れた場合は、ExavaultおよびBoxのwebサイトにアクセスしてパスワードをリセットできます。

### 「更新」ボタンをクリックしてもジョブが反映されない {#jobsarenotreflectedevenafterclickingrefreshbutton}

* CSV ファイルが Exavault FTP の正しいフォルダーにアップロードされていることを確認します。パス構造は次のようになります。

`code Account>Project>Sprint location`

* CSV ファイルのファイル名が CSV 仕様名に従っていることを確認してください。

   * course.csv
   * course_instance.csv
   * course_module.csv
   * enrollment.csv
   * module.csv
   * module_version.csv
   * user_course_grade.csv

### ジョブのエラーがエラーレコードと共に表示される {#failuresareshownforjobswitherrorrecords}

1. **エラーレコードのダウンロード**&#x200B;リンクをクリックしてエラーログをダウンロードします。
1. 報告されたエラーに基づいて元の CSV を修正し、
1. 変更したCSVを使用して、スプリントを再実行します。

変更の数がレコードの総数と比較して少ないときには、変更したCSVを新しいSprintで実行することがベストプラクティスです。

### Sprint の移行を停止しても Learning Manager アプリケーションにログインできない {#unabletologintocaptivateprimeapplicationevenafterstoppingthesprintmigration}

Sprint の実行が停止または完了すると、アカウントのロック解除に 10 〜 15 分かかります。15分後にアプリケーションにアクセスしてみてください。

### 一部の移行ジョブでは、「停止」がトリガーされた後でも「進行中」ステータスが表示されます。 {#someofthemigrationjobsdisplayinprogressstatusevenafterstopistriggered}

「処理中」状態になると、すべてのジョブの実行を停止するまでに10～15分かかる場合があります。 10分後にステータスを再確認してください。

### ボタンが無効になっているため、スプリントを作成できない {#unabletocreateasprintasthebuttonisdisabled}

スプリントを作成する前に、現在のスプリントが「完了」とマークされていることを確認します。 ページの上部にある「**[!UICONTROL スプリントを完了とマークする]**」をクリックして、スプリントの移行を完了します。

### ボタンが無効になっているため、移行プロジェクトに完全とマークすることができない {#unabletomarkamigrationprojectascompleteasthebuttonisdisabled}

移行プロジェクトを完了とマークする前に、現在のスプリントが「完了」とマークされていることを確認します。 ページの上部にある「**[!UICONTROL スプリントを完了とマークする]**」をクリックして、スプリントの移行を完了します。

## CSVの問題 {#csvissues}

### module_version.csv ファイルの移行に失敗したため、コンテンツがまだ移行されていない {#moduleversioncsvfilemigrationisfailingandcontentisnotmigratedyet}

コンテンツがコンテンツフォルダー（指定された移行プロジェクト、スプリントパスのBoxアカウント）で利用可能であることを確認します。 また、**このスプリントのコンテンツを移行しますか？**&#x200B;はい&#x200B;**のオプションを選択していることを確認してください。スプリントの作成ページの**&#x200B;質問。

「**はい**」の選択を忘れても、このスプリントで続行する場合は、このスプリントを完了するまで待つ必要があります。別のスプリントを作成し、「**[!UICONTROL はい]**」をクリックします。

### enrollment.csvまたはuser_course_grade.csvレコードで「有効なLearning Manager IDではありません」というエラーメッセージが表示されて失敗する {#enrollmentcsvorusercoursegradecsvrecordsfailwithanerrormessagenotavalidprimeid}

電子メール ID が userId の一部として入力されていること、assignedByUserID フィールドが有効な Learning Manager ユーザーに属していることを確認します。そうでない場合は、「**ユーザーの同期化**」オプションを選択た状態で、ユーザーを追加して新しいスプリントを作成してください。ユーザーが組織に属していない場合は、ユーザーCSV仕様の「ユーザーを追加」を使用して、そのユーザーをLearning Managerの削除済みユーザーとして追加します。 削除されたユーザーを追加するためのサンプルCSV仕様は、参照用に以下のとおりです。

[Users.csv](assets/users.zip) CSVの仕様とサンプルCSVファイルの完全なセットをダウンロードするには、[移行マニュアル](../integration-admin/feature-summary/migration-manual.md)の&#x200B;**CSVの仕様とサンプルCSV**&#x200B;セクションを参照してください。

### 移行したコースで、コースが空白で表示されるか、正しくないモジュールが再生される {#coursesappearblankorincorrectmodulesplayforamigratedcourse}

コースの&#x200B;**moduleOrderInCourse**&#x200B;キー値が&#x200B;**0**&#x200B;で始まり、連続していることを確認してください。 courseModuleTypeに関する順序は、PRETEST、TESTOUT、CONTENTでなければなりません

また、2つのバージョンのアクティビティ、クラスルーム、VCが、既存のコースにリンクされていないことを確認してください。

### 「モジュールは既存のコースに既にリンクされています」というメッセージを受信 {#receivingamessageasmoduleisalreadylinkedwithanexistingcourse}

Learning Manager では、アクティビティ / VC / クラスルームモジュールを複数のコースにリンクすることはできません。モジュールが他のコースにリンクされていないことを確認します。

### コースは別々のモジュールバージョンにリンクされているが、すべてのコースで Activity/VC/Classroom モジュールの最新バージョンが表示される {#allthecoursesshowthelatestversionofactivityvcclassroommoduleseventhoughthecoursesarelinkedwithdifferentmoduleversions}

アクティビティ、クラスルーム、バーチャルクラスルームのモジュールのバージョン管理は、Learning Manager ではサポートされていません。moduleVersion.csvファイルを使用してバージョンを提供する場合、新しいバージョンを作成する代わりに、既存のファイルが更新されます。

### 移行されたアクティビティ/VC/教室モジュールに対して目的の期間が表示されない {#desireddurationdoesnotappearforamigratedactivityvcclassroommodule}

アクティビティ/ VC /クラスルームモジュールに対して、希望期間が有効なエントリではありません。

### Learning ManagerでハイパーリンクURLが開かない {#hyperlinkurldoesntopenupincaptivateprime}

提供されたリンクに「http://&#39;」または「https://&#39;」が付いていることを確認します。

### moduleVersionの移行が「ファイルが見つかりません」というエラーで失敗する {#moduleversionmigrationfailswithfilenotfounderrors}

参照先ファイルがコンテンツフォルダーに存在し、正常に移行されていることを確認します。

### moduleVersionの移行が失敗し、エラーメッセージ「内部エラーが発生しました – モジュール: xおよびモジュールのバージョン: y」が表示されます。 {#moduleversionmigrationfailswithanerrormessageasaninternalerrorhasoccurredformodulexandmoduleversiony}

スプリントを再実行して問題を解決します。
