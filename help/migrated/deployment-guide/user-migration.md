---
jcr-language: en_us
title: Learning Managerデプロイメントガイド – セクション2
contentowner: sanm
preview: true
source-git-commit: fba5e5ddc1964b485be473bf356806f234688cf4
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 0%

---



# Learning Managerデプロイメントガイド – セクション2

## 技術的セットアップ {#technicalsetup}

Learning Managerアカウントの技術的な設定は、主にエンタープライズユーザーの場合に必要となります。 このドキュメントでは、組織のシングルサインオンの設定と、Learning Managerとサードパーティコネクタの統合について説明します。

### シングルサインオンの設定 {#configuresinglesignon}

Admin Consoleのシステム管理者は、まず、エンドユーザーの認証を行うIDシステムを定義して設定する必要があります。 組織でLearning Managerのライセンスを購入する場合、それらのライセンスをエンドユーザーにプロビジョニングする必要があります。 そのためには、これらのユーザーを認証する方法が必要です。 ユーザーのSSOを構成するには、次の手順を実行します。

1. Learning Managerホームページで、次をクリックします。 **[!UICONTROL **&#x200B;設定&#x200B;**>**&#x200B;ログインメソッド&#x200B;**.]**

   ![](assets/configure-sso-step1.png)

1. ユーザーのタイプに応じて、次のいずれかを選択します。 **[!UICONTROL **&#x200B;社内ユーザー&#x200B;**または**&#x200B;社外ユーザー&#x200B;**.]**



1. **から&#x200B;[!UICONTROL **ログイン**]**ドロップダウンフィールド、選択 **[!UICONTROL **&#x200B;シングルサインオン&#x200B;**.]**

   ![](assets/configure-sso-step3.png)

1. シングルサインオンの設定を行うには、 **[!UICONTROL **&#x200B;変更&#x200B;**.]**

   ![](assets/configure-sso-step4.png)

1. を ****[!UICONTROL IDPによる認証URL]**** フィールドに、サービスプロバイダーから提供された認証URLを入力します。



   ![](assets/configure-sso-step5.png)

1. **をクリック&#x200B;[!UICONTROL **アップロード&#x200B;**]**横に**[!UICONTROL  **IDPメタデータXMLファイル&#x200B;**]******フィールドに入力し、XMLファイルをアップロードします。
1. クリック **[!UICONTROL **&#x200B;保存&#x200B;**.]**
1. アカウントにSSO認証が正常に設定されました。 SSOを使用してLearning Managerアカウントにログインできます。

   ***Learning Managerで設定するSSOは、SAML 2.0に対応している必要があります。***

## ユーザーデータの移行 {#migrationofuserdata}

管理者がLearning Managerを購入した場合、重要な手順の1つとして移行を実行する必要があります。 既存のトレーニングコンテンツとユーザーデータをLearning Managerに移行することが不可欠です。 次の移行ワークフローにより、直感的に使用できる最新のLMSのメリットを活用できます。組織のレガシーデータが失われることはありません。

Learning Managerでは、ステップバイステップのウィザードを使用して、反復スプリントで既存のLMSから移行できます。 レガシーデータをAdobeのLearning Managerに移行する際、各スプリントのステータスを完全に把握して、学習者のダウンタイムを確実にゼロにすることができます。

移行ワークフローを実行するには、統合管理者権限が必要です。 管理者は、統合管理者の役割を引き受けるか、統合管理者の役割を別のユーザーに割り当てることができます。

**ここでは、Shaleenの助けを借りて、ビジュアルを作成できます。**

1. 前提条件
1. 既存のコンテンツとユーザーデータの評価
1. 既存のLMSからのデータの書き出しとマッピング
1. 移行用のFTPフォルダーとBOXフォルダーの設定
1. 学習者をLearning Managerに転送する
1. Learning Managerへの学習コンテンツの転送
1. 残りのデータをLearning Managerに転送



### 前提条件 {#prerequisite}

移行プロセスを開始する前に、次の前提条件を実行する必要があります。

* 既存のLMSからデータとコンテンツを抽出し、そのデータをLearning Managerで定義されているファイル形式に変換します。
* FTPコネクタとBOXコネクタを使用してユーザーを読み込みます。 統合管理者は、移行プロセスの前にコネクタが設定されていることを確認する必要があります。



***管理者は、データとコンテンツをLearning Managerの実稼働環境に移行する前に、体験版アカウントで移行プロセスをお試しいただくことをお勧めします。 ***

### データの評価と書き出し {#evaluatingandexportingdata}

統合管理者は、まず現在のLMSで使用可能なデータを確認する必要があります。 統合管理者は、次の学習目標のみを移行できます。

* モジュール
* コース
* モジュールバージョン
* コースインスタンス
* コースモジュール
* スキル
* スキルレベル
* スキルコース
* 資格認定
* 資格認定コース
* 保証のコミット
* 学習プログラム
* 学習プログラムコース
* 学習プログラムインスタンス
* 学習プログラムコースインスタンス
* 登録
* 資格認定の登録
* 学習プログラムの登録
* ユーザーのコース成績



既存データの評価後、Learning Managerの標準のCSV仕様を使用して、このデータをマッピングする必要があります。 次のサンプルをダウンロードします ***csv-specifications.zip*** この移行に必要な7つのexcelシートを含むファイル。 これらのExcelシートには、仕様と、既存のデータを.csvファイル内のフィールドにマップする方法を理解するための説明が含まれています。

<!--
<Download link to the zip file>
-->

各.csvファイルに、各フィールドのデータが所定の形式で含まれていることを確認します。

<table> 
 <tbody> 
  <tr> 
   <th width="7%" valign="top"><p><strong>いいえ。</strong></p></th> 
   <th width="29%" valign="top"><p><strong>Excelシート名</strong></p></th> 
   <th width="31%" valign="top"><p><strong>コンテンツの説明</strong></p></th> 
   <th width="31%" valign="top"><p><strong>注意</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>1</p></td> 
   <td><p>module.xlsx</p></td> 
   <td><p>module.csvのメタデータ</p></td> 
   <td><p> </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>course.xlsx</p></td> 
   <td><p>course.csvのメタデータ</p></td> 
   <td><p>移行後は複数の作成者名がアプリケーションで正確に表示されない場合があるため、特定のコースに対して1つの作成者名を指定するようにします。 </p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>module_version.xlsx </p></td> 
   <td><p>module_version.csvのメタデータ</p></td> 
   <td><p>コンテンツをアップロードしたBoxアカウントフォルダーのURLパスを指定します。 </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>course_instance.xlsx</p></td> 
   <td><p>course_instance.csvのメタデータ </p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>course_module.xlsx</p></td> 
   <td><p>course_module.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>6</p></td> 
   <td><p>skill.xlsx</p></td> 
   <td><p>skill.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>7</p></td> 
   <td><p>skill_level.xlsx</p></td> 
   <td><p>skill_level.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>8</p></td> 
   <td><p>skill_course.xlsx</p></td> 
   <td><p>skill_course.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>9</p></td> 
   <td><p>Certification.xlsx</p></td> 
   <td><p>Certification.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>10</p></td> 
   <td><p>certification_course.xlsx</p></td> 
   <td><p>certification_course.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>11</p></td> 
   <td><p>certification_commit.xlsx</p></td> 
   <td><p>certification_commit.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>12</p></td> 
   <td><p>learning_program.xlsx</p></td> 
   <td><p>learning_program.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>13</p></td> 
   <td><p>learning_program_course.xls </p></td> 
   <td><p>learning_program_course.csvのメタデータ </p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>14</p></td> 
   <td><p>learning_program_instance.xlsx </p></td> 
   <td><p>learning_program_instance.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>15</p></td> 
   <td><p>learning_program_instance_course_instance.xlsx </p></td> 
   <td><p>learning_program_instance_course_instance.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>16</p></td> 
   <td><p>enrollments.xlsx</p></td> 
   <td><p>登録.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>17</p></td> 
   <td><p>certification_enrollment.xlsx</p></td> 
   <td><p>certification_enrollment.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>18</p></td> 
   <td><p>learning_program_enrollment.xlsx</p></td> 
   <td><p>learning_program_enrollment.csvのメタデータ</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>19</p></td> 
   <td><p>User_course_grade.xlsx</p></td> 
   <td><p>User_course_grade.csvのメタデータ</p></td> 
   <td><p>必須ではない学習者のレコードデータを.csvファイルに入力します。 この情報がない場合、.csvファイルを移行対象として処理しても、Learning Managerアプリケーションでデータが反映されない可能性があります。 </p></td> 
  </tr> 
 </tbody> 
</table>

***Learning Managerでは、UTF 8および32ビット形式の日付と時刻の値のみをサポートしています。 CSVファイルで2038-07-17T08などの範囲外の日付を指定すると、移行中にエラーが発生することがあります:53:21.000Zまたは1980-04-17T08:13:25.322Z。***

### CSVファイルへのデータ読み込み時の依存関係 {#dependencieswhileimportingdatatocsvfiles}

既存のデータを標準のcsv形式に読み込む際は、次の依存関係に注意してください。

* module_version.csvはmodule.csvに依存している
* course_instance.csvはcourse.csvに依存している
* course_module.csvはcourse.csv、module.csvおよびmodule_version.csvに依存している
* course_instance.csvはcourse.csvに依存している
* enrollment.csvはcourse.csvに依存している
* user_course_grade.csvはcourse.csvおよびmodule.csvに依存している
* skill_course.csvはcourse.csvに依存している
* skill_level.csvはskill.csvに依存している
* learning_program_instance.csvはlearning_programおよびlearning_program_course.csvに依存している
* learning_program_course.csvはlearning_program.csvに依存している
* learning_program_enrollment.csvはlearning_programおよびlearning_program_instance.csvに依存している
* learning_program_instance_course_instance.csvはlearning_program.csv、learning_program_instance.csvおよびcourse_instance.csvに依存している
* certification_course.csvはcertification.csvおよびcourse.csvに依存している
* certification_commit.csvはcertification.csvおよびcertification_course.csvに依存している
* certification_enrollment.csvは、certification.csv、certification_course.csv、certification_enrollment.csvに依存している



データを書き出したら、.csvファイルをローカルコンピューターに保存します。 これで、ファイルをFTPフォルダーまたはBOXフォルダーにドロップする準備ができました。

## 移行用のFTPフォルダーとBOXフォルダーの設定 {#setupftpandboxfoldersforthemigration}

すべてのコンテンツの実際の移行を計画して開始する前に、まずFTPフォルダーとBOXフォルダーを設定する必要があります。 これらのフォルダーに.csvファイルをドロップするには、これらのフォルダーが必要です。 FTPフォルダーとBOXフォルダーで.csvファイル形式のレガシーコンテンツが利用可能になると、Learning Managerでデータを使用できるようになります。

### FTPアカウントの設定 {#setupanftpaccount}

統合管理ホームページで、 **[!UICONTROL ** CSV FTPフォルダーの要求&#x200B;**.]** 表示されるポップアップダイアログボックスで、電子メールIDを入力します。 オンラインウィザードでExavault FTPアカウントを作成します。 アカウントを作成するとすぐに、Exavault FTPで移行プロジェクトとスプリントプロジェクトのフォルダーを表示できます。

ExaVaultのプロジェクトファイルとフォルダーのサンプルスナップショットについては、以下を参照してください。

![](assets/set-up-an-ftp-account.png)

FTPフォルダーのセットアップが正常に完了すると、「FTPフォルダーのセットアップが完了しました」というメッセージが表示されます。

## BOXアカウントの設定 {#setupaboxaccount}

BOXアカウントを作成し、BOXフォルダーを設定するには、次の手順を実行します。

統合管理ホームページで、「移行」を選択します。

「設定」セクションで、「Request for a Box folder」をクリックします。

![](assets/set-up-a-box-account.png)

を ****[!UICONTROL 電子メールを入力]**** フィールドに、Boxに接続するためのログイン手順を受け取るメールIDを入力します。

クリック **[!UICONTROL ** Connect **.]**

共有フォルダーへのリンクが記載されたメールがBoxから届きます。 Boxアカウントをお持ちでない場合は、「新規登録」をクリックしてアカウントを作成します。 ログインの手順が、統合管理者の電子メールIDに送信されます。

接続を保存すると、移行ページに「Boxフォルダーの設定が完了しました」というメッセージが表示されます。

## Learning Managerへのコンテンツの移行 {#migratingthecontenttocaptivateprime}

移行を開始する前に、次の点に注意する必要があります。

* 1つのアカウント内で同時にアクティブにできる移行プロジェクトは1つのみです。 プロジェクト内で同時にアクティブにできるスプリントは1つだけです。
* 既に進行中の実行は元に戻せません。 ただし、Learning Managerの各機能にある既存の削除オプションを使用すると、データやコンテンツの移行を取り消すことができます。

移行プロジェクトが開始されるとすぐに、プロジェクトは「移行中」の状態になります。 この状態では、統合管理者以外のユーザーはLearning Managerにログインできません。

コンテンツフォルダーへのトレーニングコンテンツのアップロード：

統合管理ホームページで、 **[!UICONTROL 移行：]**

移行ホームページに、組織内で既に作成されている移行プロジェクトが表示されます。

**をクリック&#x200B;[!UICONTROL **新規**]**ページの右上隅に、移行プロジェクトを作成するためのタブがあります。

***FTPフォルダーをまだ作成していない場合は、FTPフォルダーのExavaultアカウントを作成するように求められます。 これは、移行プロジェクトの作成を開始する前に行う必須の手順です。 ***

を ****[!UICONTROL 新しい移行プロジェクトの作成]**** ページで、プロジェクトの名前を指定します。

![](assets/migrating-the-content-1.png)

プロジェクトのタグとコースカタログを指定し、移行プロジェクトの説明を入力します。 移行データ項目は、移行プロジェクトタグを使用して識別されます。 特定のコースカタログが存在しない場合は、ドロップダウンからデフォルトのカタログを選択します。移行プロジェクトを使用して移行するすべてのコースが、ここで選択するカタログに含まれます。 カタログを選択しない場合、移行したすべてのコースがデフォルトのカタログに含まれます。

クリック **[!UICONTROL 作成。]**

スプリントの構成ページで、移行プロジェクトのスプリントを作成します。 Learning Managerの移行プロセスで、スプリントは既存のLMSから移行するように選択した一連の移行項目を定義します。

![](assets/migrating-the-content-2.png)

スプリントの名前を指定し、スプリントの説明を入力します。

を選択します ****[!UICONTROL 「前回の実行後に追加または変更されたユーザー」チェックボックス]****&#x200B;をクリックして、Learning Managerアプリケーションとユーザーリストを同期します。 コンテンツとデータをLearning Managerアプリケーションに移行する場合、この操作は不要な場合があります。 ただし、前回のスプリントを移行してから最新のスプリントを移行するまでに長時間経過している場合は、ユーザーリストを同期することをお勧めします。 この手順により、Learning ManagerデータベースをLMSユーザーと同期させることができます。

***enrollment.csvとuser_course_grade.csvを移行する場合は、同期手順を実行することをお勧めします。 この手順により、Learning Managerデータベースを移行データベースと同期させることができます。また、レコードがスプリントに移行されるすべてのユーザーが移行データベース上で利用可能になります。***

クリック **[!UICONTROL ** Next **.]**

**をクリック&#x200B;[!UICONTROL **開始**]**アップロードされたデータとコンテンツを使用して、スプリントの移行を開始します。 クリック ****[!UICONTROL 更新]**** learning Managerでスプリントを実行して、FTPフォルダーとコンテンツフォルダーを同期する前に行います。

![](assets/migrating-the-content-3.png)

****をクリックできます[!UICONTROL 停止]****スプリントの移行プロセス中の任意の時点で、スプリントの移行を中止します。

スプリントデータ項目とコンテンツごとに、移行ステータスが表示されます。 移行スプリントを実行する際に、成功した項目と失敗した項目の数を確認します。

モジュールコンテンツをアップロードする場合は、コンテンツフォルダーのパスが*module_version.csv *ファイルに指定されていることを確認してください。 この手順を実行しないと、移行中にエラーが発生する可能性があります。 例えば、動画などのセルフペースのモジュールコンテンツをアップロードする場合は、 *module_version.csv *ファイルでBox URL相対パスを指定する必要があります。

移行の進行状況のサンプルスナップショットについては、以下を参照してください。 スナップショットに示すように、各移行データ項目に対して処理されたレコードの数を、成功した項目および失敗した項目のステータスとともに表示できます。 エラーログをダウンロードして表示するには、失敗したアイテムの「エラーレコードをダウンロード」をクリックします。 CSVで問題を修正し、FTPに再度アップロードできます。

![](assets/migrating-the-content-4.png)

移行プロジェクトのすべてのスプリントのリストを表示するには、をクリックします**[!UICONTROL **スプリント**]**左側のナビゲーションペイン内。 以下のサンプルスナップショットに示すように、すべてのスプリントのリスト、各スプリントの実行数、開始日、期間、および完了ステータスを表示できます。

![](assets/migrating-the-content-5.png)

移行プロジェクトのすべてのスプリントのリストを表示するには、をクリックします**[!UICONTROL **スプリント**]**左側のナビゲーションペイン内。 以下のサンプルスナップショットに示すように、すべてのスプリントのリスト、各スプリントの実行数、開始日、期間、および完了ステータスを表示できます。

移行プロジェクトのすべてのスプリントのリストを表示するには、をクリックします**[!UICONTROL **スプリント**]**左側のナビゲーションペイン内。 以下のサンプルスナップショットに示すように、すべてのスプリントのリスト、各スプリントの実行数、開始日、期間、および完了ステータスを表示できます。

***移行プロジェクトを完了とマークする前に、プロジェクト内のすべてのスプリントが完了していることを確認してください。 移行プロジェクトを完了とマークすると、そのプロジェクトに戻ってスプリントを作成することはできません。 そのプロジェクトを変更することはできません。 別の移行プロジェクトを作成し、それにスプリントを追加することのみが可能です。***

組織のレガシーLMSから学習データとコンテンツを移行した後に、データとコンテンツが正しく読み込まれたことを確認します。 確認するには、管理者としてログインし、読み込んだモジュール、コースデータおよびコンテンツの可用性を検証します

移行に役立つリソースについては、以下を参照してください。

* 移行に関する問題のトラブルシューティング
* CSVアップロードに関するFAQ

