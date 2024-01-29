---
description: 既存のLMSをLearning Manager LMSに移行する統合管理者向けの参照マニュアル
jcr-language: en_us
title: 移行マニュアル
source-git-commit: 66dfaaaf723382eada39e2be29dfd49b795107a0
workflow-type: tm+mt
source-wordcount: '3705'
ht-degree: 0%

---



# 移行マニュアル

既存のLMSをLearning Manager LMSに移行する統合管理者向けの参照マニュアル

## 概要 {#overview}

<table>
 <tbody>
  <tr>
   <td><img src="assets/migration.jpg"></td>
   <td>
    <p><a href="https://business.adobe.com/products/learning-manager/adobe-learning-manager.html">Learning ManagerのAdobe</a> は、クラウドホスト環境で学習者中心のセルフサービス学習管理ソリューションです。 Adobeを使用すると、既存のLearning Management Systems(LMS)を保有する企業が、組織のトレーニングデータとトレーニングコンテンツをLearning Manager LMSアプリケーションに移行できるようになります。 </p></td>
  </tr>
 </tbody>
</table>

### 使用シナリオ {#usagescenario}

一般的に、大企業では、社内のLMSまたは任意のベンダーが従来の学習管理システムを提供しています。 LMSは、エンタープライズ版トレーニングコンテンツとトレーニングデータで構成されます。 企業としてLearning Managerを購入した場合、既存のLMSコンテンツとデータをLearning Managerに移動すると、直感的に使用できる最新のLMSのメリットを活用でき、組織のレガシーデータが失われることはありません。

Learning Managerでは、組織の統合管理者が移行タスクを設定および実行できるように、必要なツールと仕様が用意されています。

現時点でLearning Managerの移行機能は、組織の管理者がAdobeサポートチームに問い合わせることでアクセスできます。 アカウントの移行機能を有効にするには、AdobeのLearning Managerサポートチームまでお問い合わせください。

## 移行プロセス {#apidescription}

移行の前提条件、移行プロセスで必要な主な手順、移行スプリント、仕様、データおよびコンテンツの移行手順について、このセクションで次に説明します。

### 前提条件 {#prerequisites}

Learning Managerチームは、移行プロセスを開始する前に、組織の統合管理者が以下のタスクを実行することを想定しています。

* 統合管理者は、既存のLMSからデータとコンテンツを抽出し、Learning Managerで定義されているファイル形式にデータを変換します。
* Learning Managerは、移行プロセスの一部としてユーザーの読み込みをサポートしていないため、組織はコネクタを使用してユーザーを読み込む必要があります。 Adobe Systemsでは、これらのコネクタが移行プロセスの前に設定されていることを前提としています。 詳しくは、「 [Learning Managerコネクターのヘルプ](connectors.md) 」を参照してください。

Learning Managerでは、管理者がLearning Managerの実稼働環境にデータやコンテンツを移行する前に、体験版アカウントで移行プロセスをお試しいただくことをお勧めします。

### 移行プロセスの主なステップ {#keystepsofmigrationprocess}

既存のLMSからLearning Managerにコンテンツとデータを移行する際の主要な手順は、次のとおりです。

1. 統合管理者またはパートナーは、移行が必要な既存のLMSデータおよびコンテンツを評価します。
1. 統合管理者は、Learning Managerがデータとコンテンツを取り込むために提供するツールと仕様を評価します。
1. 統合管理者は、古いLMSが提供する機能に基づいて、古いLMSからトレーニングデータとコンテンツを書き出すためのコードを作成するか、手作業を行います。
1. トレーニングのデータとコンテンツが利用可能になると、統合管理者はLearning Managerの移行仕様に一致するようにデータとコンテンツをマッピングして分析します。
1. 統合管理者は、Learning Managerのツールを使用して、次の順序で移行します。

   1. 学習者をLearning Managerに転送する
   1. トレーニングコンテンツをLearning Managerに転送し、
   1. 最後に、トレーニングデータをLearning Managerに転送します。

組織は、レガシーコンテンツと共にLearning Manager LMSの使用を開始できます。

### 移行オブジェクトの範囲 {#scopeofmigrationobjects}

コンテンツを移行できるのは、次の学習目標に対してのみです。

* モジュール
* バッジ
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
* 作業計画書
* 作業計画書のバージョン
* 作業計画書コース
* 作業計画書スキル
* 登録
* 資格認定の登録
* 学習プログラムの登録
* 作業計画書の登録
* ユーザーのコース成績



### 移行のキーコンセプト {#keyconceptsofmigration}

クイックリファレンスとして、Learning Managerの移行プロセスの主要な概念について以下に簡単に説明します。

**移行プロジェクト**

Learning Managerでは、移行プロジェクトは1つ以上のスプリントで構成されます。 アカウントに複数の移行プロジェクトを含めることもできます。 Learning Managerでの移行プロセスは、移行プロジェクトの作成から始まります。

**スプリント**

Learning Managerの移行プロセスで、スプリントは既存のLMSから移行するように選択した一連の移行項目を定義します。 移行項目には、コースモジュール、学習者レコード、一連のコースを指定できます。 スプリントには複数の学習データ項目を含めることができます。 各スプリントで移行ジョブを実行できます。

**スプリントの実行**

スプリントの実行は、スプリントの移行ジョブを開始するプロセスです。 スプリントの実行は、実行のどの時点でも停止できます。

**スプリントの再実行**

移行スプリントは、完了後にいつでも再実行できます。 このスプリントの再実行または再実行の状況は、スプリントアイテムにデータを追加してアプリケーションに再移行したり、CSVでエラーを修正したりする場合に発生します。

**CSVの仕様**

Learning Managerでは、 [標準のCSV仕様](migration-manual.md#main-pars_header_140933605). 移行プロセスを開始する前に、これらのCSV仕様を確認することをお勧めします。 組織の統合管理者は、既存のデータ形式を分析し、そのデータ形式をLearning Managerが提供するCSVテンプレート項目と一致するようにマッピングできます。

**移行プロジェクトのタグ**

Adobe Systemsでは、タグとしてさまざまなキーワードを使用し、Learning Managerアプリケーション内で移行プロジェクトを簡単に識別することをお勧めします。 これらのタグを使用すると、Learning Managerアプリケーションの内部でプロジェクトをいつでも識別できます。

**コンテンツレスモジュール**

Learning Managerでは、コンテンツを含めずにモジュールをアップロードできます。 Adobe SystemsはこれをLearning Managerのコンテンツレスモジュールと見なしています。 コンテンツを必要とせずに既存のLMSからレガシーデータの一部を移行する場合は、URL参照なしでmodule_version.csvファイルをアップロードできます。

## CSVの仕様とサンプルCSV {#csv}

以下に、既存のLMS移行データとのマッピングに使用できる標準のCSV仕様を示します。 csv-specificationsとsample-csvをクリックして、zipファイルをダウンロードします。 ダウンロードしたcsv-specifications.zipには、7つのExcelシートファイルが含まれています。 これらのExcelシートファイルは、.csvファイルの入力方法を理解するための説明を含む仕様です。 対応する.csvファイルには、各フィールドのデータが、これらの.xlsxファイルで説明されている所定の形式で含まれている必要があります。

<table border="1" cellspacing="0" cellpadding="0" width="100%">
 <tbody>
  <tr>
   <th>
    <p><b>Sl.no</b></p></th>
   <th>
    <p><b>ファイル名</b></p></th>
   <th>
    <p><b>コンテンツの説明</b></p></th>
   <th>
    <p>注意</p></th>
  </tr>
  <tr>
   <td>
    <p>1</p></td>
   <td>
    <p>module.xlsx</p></td>
   <td>
    <p>module.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>2</p></td>
   <td>
    <p>badge.xlsx</p></td>
   <td>
    <p>バッジ.xlsxのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>3</p></td>
   <td>
    <p>course.xlsx</p></td>
   <td>
    <p>course.csvのメタデータ</p></td>
   <td>
    <p>移行後は複数の作成者名がアプリケーションで正確に表示されない場合があるため、特定のコースに対して1つの作成者名を指定するようにします。 </p></td>
  </tr>
  <tr>
   <td>
    <p>4</p></td>
   <td>
    <p>module_version.xlsx </p></td>
   <td>
    <p>module_version.csvのメタデータ</p></td>
   <td>
    <p>コンテンツをアップロードしたBoxアカウントフォルダーのURLパスを指定します。 </p></td>
  </tr>
  <tr>
   <td>
    <p>5</p></td>
   <td>
    <p>course_instance.xlsx</p></td>
   <td>
    <p>course_instance.csvのメタデータ </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>6</p></td>
   <td>
    <p>session.xlsx</p></td>
   <td>
    <p>session.csvのメタデータ</p></td>
   <td>
    <p>セッションcsv内のすべてのエントリが、少なくとも1つの教室/バーチャルクラスルームモジュールに関連付けられていることを確認してください</p></td>
  </tr>
  <tr>
   <td>
    <p>7</p></td>
   <td>
    <p>course_module.xlsx</p></td>
   <td>
    <p>course_module.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>8</p></td>
   <td>
    <p>skill.xlsx</p></td>
   <td>
    <p>skill.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>9</p></td>
   <td>
    <p>skill_level.xlsx</p></td>
   <td>
    <p>skill_level.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>10</p></td>
   <td>
    <p>skill_course.xlsx</p></td>
   <td>
    <p>skill_course.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>11</p></td>
   <td>
    <p>certification.xlsx</p></td>
   <td>
    <p>Certification.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>12</p></td>
   <td>
    <p>certification_course.xlsx</p></td>
   <td>
    <p>certification_course.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>13</p></td>
   <td>
    <p>certification_commit.xlsx</p></td>
   <td>
    <p>certification_commit.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>14</p></td>
   <td>
    <p>learning_program.xlsx</p></td>
   <td>
    <p>learning_program.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>15</p></td>
   <td>
    <p>learning_program_course.xls </p></td>
   <td>
    <p>learning_program_course.csvのメタデータ </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>16</p></td>
   <td>
    <p>learning_program_instance.xlsx </p></td>
   <td>
    <p>learning_program_instance.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>17</p></td>
   <td>
    <p>learning_program_instance_course_instance.xlsx </p></td>
   <td>
    <p>learning_program_instance_course_instance.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>18</p></td>
   <td>
    <p>job_aid.xlsx</p></td>
   <td>
    <p>job_aid.csvのメタデータ</p></td>
   <td>
    <p>移行されたすべてのjob_aidには、1つ以上のjob_aidバージョンが必要です。</p></td>
  </tr>
  <tr>
   <td>
    <p>19</p></td>
   <td>
    <p>Job_aid_version.xlsx</p></td>
   <td>
    <p>job_aid_version.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>20</p></td>
   <td>
    <p>job_aid_course.xlsx</p></td>
   <td>
    <p>job_aid_course.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>21</p></td>
   <td>
    <p>job_aid_skills.xlsx</p></td>
   <td>
    <p>job_aid_skills.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>22</p></td>
   <td>
    <p>enrollments.xlsx</p></td>
   <td>
    <p>登録.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>23</p></td>
   <td>
    <p>certification_enrollement.xlsx</p></td>
   <td>
    <p>certification_enrollement.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>24</p></td>
   <td>
    <p>learning_program_enrollment.xlsx</p></td>
   <td>
    <p>learning_program_enrollment.csvのメタデータ<br><br></p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>25</p></td>
   <td>
    <p>job_aid_enrollment.xlsx</p></td>
   <td>
    <p>job_aid_enrollment.csvのメタデータ</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>26</p></td>
   <td>
    <p>user_course_grade.xlsx</p></td>
   <td>
    <p><br>
      user_course_grade.csvのメタデータ</p></td>
   <td>
    <p>必須ではない学習者のレコードデータを.csvファイルに入力します。 この情報がない場合、.csvファイルを移行対象として処理しても、Learning Managerアプリケーションでデータが反映されない可能性があります。 sample-csvs.zipファイルには、上記と同じ命名規則を持つ7つの.csvファイルが含まれています。</p></td>
  </tr>
 </tbody>
</table>

Learning Managerでは、UTF 8および32ビット形式の日付と時刻の値のみをサポートしています。 範囲外の日付を2038-07-17T08としてCSVファイルに日付を記載すると、移行中にエラーが発生することがあります:53:21.000Zまたは1980-04-17T08:13:25.322Z。
[sample-csvs.zip](assets/sample-csvs.zip) [csv_specifications.zip](assets/csv-specifications.zip)読み込み時には、CSVファイルに対する次の依存関係に注意する必要があります。

* module_version.csvはmodule.csvに依存している
* course_instance.csvはcourse.csvに依存している
* course_module.csvはcourse.csv、module.csvおよびmodule_version.csvに依存している
* course_instance.csvはcourse.csvに依存している
* session.csvはcourse.csvおよびmodule.csvに依存している
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

## 移行手順 {#migrationprocedure}

移行手順を開始する前に、次の点に注意する必要があります。

* 1つのアカウント内で同時にアクティブにできる移行プロジェクトは1つのみです。 プロジェクト内で同時にアクティブにできるスプリントは1つだけです。
* 既に移行プロセス中の実行は取り消せません。 ただし、Learning Managerの各機能にある既存の削除オプションを使用すると、データやコンテンツの移行を取り消すことができます。
* 移行プロジェクトが開始されるとすぐに、移行は「移行中」の状態になります。 移行中は、統合管理者以外の役割のユーザーはLearning Managerにログインできません。

### FTPアカウントとBoxアカウントの作成 {#creatingftpandboxaccounts}

移行プロジェクトの計画は非常に重要です。 プロジェクトを複数のスプリントに分割し、各スプリントで移行する対象を明確にすることをお勧めします。 各スプリントの後に、プロジェクトの最後に1つの大規模な検証フェーズを行うのではなく、スプリントに移行されたデータについて自信を持って検証を行うことをお勧めします。 移行プロジェクトの一環としてスプリントを開始する前に、データとコンテンツのCSVファイルをそれぞれFTPサーバーとBoxサーバーにアップロードする必要があります。 カスタムFTPおよびBox用のアカウントがない場合は、それらを作成できます。

**FTPアカウントの作成**

クリック **[!UICONTROL CSV FTPフォルダーの要求]**. 電子メールIDの入力を求めるポップアップダイアログが表示されます。 オンラインの手順に従って、FTPアカウントを作成します。 アカウントを作成するとすぐに、FTPで移行プロジェクトとスプリントプロジェクトのフォルダーを表示できます。

参考までに、プロジェクトファイルおよびFTPのフォルダーのサンプルスナップショットを以下に示します。

<!--![](assets/exavault-migration-upload-folders.png)-->

**Boxアカウントの作成**

FTPフォルダーの作成と同様のプロセスで、コンテンツアップロードフォルダーを作成します。 左ペインで「移行」をクリックし、表示されるページの下部にあるコンテンツアップロードフォルダーのリクエストをクリックします。

共有フォルダーへのリンクが記載されたメールがBoxから届きます。 Boxアカウントをお持ちでない場合は、「新規登録」をクリックしてアカウントを作成します。 ログイン手順は、統合管理者の電子メールIDに送信されます。

**FTPフォルダーまたはBoxフォルダーへのデータ（.csvファイル）のアップロード**

移行プロジェクトを作成する前に、FTPアカウントまたはBoxアカウントを作成することが前提条件となります。 この段階で、Learning Managerアプリケーションで移行プロジェクトとスプリントを作成できます。  詳しくは、「 **データとコンテンツの移行手順** このページの「 」セクションで、移行プロジェクトを作成します。

FTPアカウントまたはBoxアカウントで、プロジェクトフォルダー名をクリックし、スプリント名をクリックします。 スプリントフォルダー内で、移行する.csvデータファイルをアップロードできます。 アップロードするには、FTPサーバーまたはBoxサーバーの上部にある「ファイルをアップロード」ボタンをクリックし、.csvファイルをドロップします。 FTPにアップロードした後のサンプルスナップショットは、参考までに以下のとおりです。

<!--![](assets/exavault-upload.png)-->

Learning Manager移行プロジェクトに戻るには、次をクリックします。 **[!UICONTROL 更新]** 移行スプリントに一覧表示されているすべての.csvデータタイプを表示します。

**コンテンツフォルダーへのトレーニングコンテンツのアップロード**

既存のLMSのトレーニングコンテンツをBoxアカウントにアップロードします。 移行プロジェクトとスプリントをすでに作成している場合は、Boxアカウントが移行プロジェクトとスプリントの名前に入力されます。 同じパスにコンテンツをアップロードできます。 詳しくは、「 **データとコンテンツの移行手順** このページの「 」セクションで、移行プロジェクトを作成します。

コンテンツファイルをドラッグ&amp;ドロップするか、をクリックします **[!UICONTROL アップロード]** デスクトップからファイルを選択します。 コンテンツのファイルサイズが非常に大きい場合、ファイルのアップロードに時間がかかることがあります。 ファイルのサイズに応じて、Boxアカウントへのファイルのアップロードにかかる時間は異なります。

参考までに、コンテンツをアップロードした後のBoxアカウントのサンプルスナップショットを以下に示します。

![](assets/box-account.png)

*Boxアカウントのファイル*

ファイルがBoxアカウントにアップロードされたら、module_version.csvファイルでこのBoxコンテンツファイルの相対パスを指定してください。 これは、モジュールコンテンツのパスを示すために必須の手順です。

FTPサーバーとBoxサーバーにログインしてコンテンツをアップロードすると、Learning Managerで以下のスナップショットのようにCSVの場所が表示されます。

![](assets/after-setup.jpg)

*BoxアカウントでのCSVの場所*

## データとコンテンツの移行手順 {#dataandcontentmigrationprocedure}

企業のLMSデータとコンテンツをLearning Managerに移行する手順は、次のとおりです。

移行を開始する前に、移行プロセスの前提条件を確認してください。 詳しくは、「 [CSVの仕様とサンプルCSV](migration-manual.md#main-pars_header_140933605) このページの「 」セクションで、データおよびコンテンツを移行するためのCSVを準備します。

1. 統合管理者としてLearning Managerアプリケーションにログインして、 **[!UICONTROL 移行]** をクリックします。

   移行プロジェクト・ホームページが表示されます。 組織が既に移行プロジェクトを作成している場合は、このページですべての移行プロジェクトのリストを表示できます。

1. クリック **[!UICONTROL 新規]** ページの右上隅に、移行プロジェクトを作成します。 または、をクリックします。 **[!UICONTROL 移行プロジェクトの作成]** 移行プロジェクトを作成するためのページ上のリンクです。 移行プロジェクトの作成ページが表示されます。

   FTPフォルダーをまだ作成していない場合は、アカウントにFTPフォルダーを作成するように求められます。 これは、移行プロジェクトの作成を開始する前に行う必須の手順です。

   ![](assets/create-project.png)
   *FTPフォルダーの作成*

   移行プロジェクトのプロジェクト名、プロジェクトタグ、コースカタログ、説明を入力します。 クリック **[!UICONTROL 作成]**.

   移行データ項目は、この移行プロジェクトタグを使用して識別されます。 特定のコースカタログがない場合は、ドロップダウンからデフォルトのカタログを選択します。 移行プロジェクトを使用して移行するすべてのコースが、この段階で選択するカタログに含まれます。 カタログを選択しない場合、移行したすべてのコースがデフォルトのカタログに含まれます。

1. 次のスナップショットに示すように、スプリントの設定ページが表示されます。 移行プロジェクトの一環として、スプリントを作成する必要があります。 スプリントの名前を選択し、スプリントの簡単な説明を入力します。 このスプリントの一部としてコンテンツを移行する場合は、「はい」を選択します。 クリック **[!UICONTROL Next]**.

   ![](assets/users-modified-sprint.png)
   *スプリントの移行*

   タイトル付きのチェックボックスを選択します **前回の実行後に追加または変更されたユーザー**&#x200B;をクリックして、Learning Managerアプリケーションとユーザーリストを同期します。 コンテンツとデータをLearning Managerアプリケーションに移行する場合、この操作は不要な場合があります。 ただし、前回のスプリントを移行してから最新のスプリントを移行するまでに長時間経過している場合は、ユーザーリストを同期することをお勧めします。 この手順により、Learning ManagerデータベースをLMSユーザーと同期させることができます。

   enrollment.csvとuser_course_grade.csvを移行する場合は、この同期手順を実行することをお勧めします。 この手順により、Learning Managerデータベースを移行データベースと同期させることができます。また、レコードがスプリントに移行されるすべてのユーザーが移行データベースで利用可能になります。

1. アップロードされたデータとコンテンツを使用して、スプリントの移行を開始できます。 クリック **[!UICONTROL 更新]** リンクスプリントの実行を開始する前に、Learning ManagerアプリケーションでFTPフォルダーとコンテンツフォルダーを同期します。

   ![](assets/sprint1-filesupload.png)
   *スプリントの移行を開始*

   クリック **[!UICONTROL 開始]** をクリックします。 次をクリックできます **[!UICONTROL 停止]** スプリントの移行プロセス中の任意の時点で、スプリントの移行を中止します。

   スプリントデータ項目とコンテンツごとに移行ステータスが表示されます。 移行スプリントを実行する際に、成功した項目と失敗した項目の数を確認します。

   モジュールコンテンツをアップロードする場合は、コンテンツフォルダーのパスがmodule_version.csvに指定されていることを確認してください。 この手順を実行しないと、移行中にエラーが発生する可能性があります。 例えば、動画などのセルフペースのモジュールコンテンツをアップロードする場合は、module_version.csvでBox URL相対パスを指定する必要があります。 アクティビティモジュールのコンテンツの場合、URL名を指定できます。

   参考までに、進行状況のサンプルダイアログを以下に示します。 スナップショットに示すように、各移行データ項目に対して処理されたレコードの数を、成功した項目および失敗した項目のステータスとともに表示できます。 エラーログをダウンロードして表示するには、失敗したアイテムの「エラーレコードをダウンロード」をクリックします。 CSVで問題を修正し、FTPに再度アップロードできます。

   ![](assets/sample-sprint-progress-status.png)
   *スプリントの進行状況を表示*

   移行プロジェクトのすべてのスプリントのリストを表示する場合は、左ペインの「スプリントのリスト」をクリックします。 以下のサンプルスナップショットに示すように、すべてのスプリントのリスト、各スプリントの実行数、開始日、期間、および完了ステータスを表示できます。

   ![](assets/sprint-list.png)
   *スプリントのリストの表示*

1. 更新された最新のCSVをアップロードした後、ページの右上隅にある「再実行」をクリックします。 再実行を実行すると、変更のない項目を無視して、すべてのデータ項目が再度処理されます。 スプリント内のデータ項目の移行に問題がなければ、ページの上部にあるボタンをクリックして、春の移行を完了としてマークできます。 新しいスプリントを開始して、後でより多くのデータ項目を追加できます。 スプリントが完了とマークされると、再実行することはできません。 同様に、移行プロジェクトでは、任意の数のスプリントを設定できます。 すべてのスプリントの移行ステータスに問題がなければ、をクリックして、移行プロジェクトを「完了」とマークできます **プロジェクトを完了としてマーク** スプリントリストページのリンク。

   移行プロジェクトを完了とマークする前に、プロジェクトのすべてのスプリントが完了していることを確認する必要があります。 移行プロジェクトを完了とマークすると、そのプロジェクトに戻ってスプリントを作成したり、そのプロジェクトに変更を加えたりすることはできません。 別の移行プロジェクトを作成し、それにスプリントを追加する必要があります。

## 移行の確認 {#registration}

組織のレガシーLMSから学習データとコンテンツを移行した後、様々な学習目標機能を使用して、読み込まれたデータとコンテンツを確認できます。 例えば、Learning Managerアプリケーションに管理者としてログインし、読み込んだモジュール、コースデータおよびコンテンツの利用状況を確認できます。

## 移行時再適合 {#retrofittinginmigration}

この統合機能により、従来の学習管理システムからLearning Managerで作成されたアクティブコースに、学習目標の履歴データを組み込むことができます。

以下に、既存のLMS移行データとのマッピングに使用できる標準のCSV仕様を示します。 csv-specificationsとsample-csvをクリックして、zipファイルをダウンロードします。 ダウンロードしたcsv-specifications.zipには、4つのExcelシートファイルが含まれています。 これらのExcelシートファイルは、.csvファイルの入力方法を理解するための説明を含む仕様です。 対応する.csvファイルには、各フィールドのデータが、これらの.xlsxファイルで説明されている所定の形式で含まれている必要があります。

1-enrollment.xlsx:retrofit_enrollment.csvファイルに必要なメタデータの説明が含まれます。

2-certification_enrollment.xlsx- retrofit_certification_enrollment.csvファイルに必要なメタデータの説明が含まれます。

3-learning_program_enrollment.xlsx- retrofit_learning_program_enrollment.csvファイルに必要なメタデータの説明が含まれます。

4-user_course_grades.xlsx - retrofit_user_course_grades.csvファイルに必要なメタデータの説明が含まれます。
[csv-specifications.zip](assets/csv-specifications.zip)

## 移行に関する問題のトラブルシューティング {#troubleshootingmigrationissues}

[ここをクリック](../../kb/troubleshooting-migration.md) データとコンテンツを既存のLMSからLearning Managerアプリケーションに移行する際、統合管理者が直面する問題に対する回避策や解決策について説明します。

## ユーザー管理のヒント {#usermanagement}

このトピックでは、Learning Managerでユーザーが処理および管理される方法を理解するためのヒントを紹介します。 これらの概念は、CSVの読み込み、コネクタ、およびLearning Managerの移行機能を使用する際に、ユーザーをより適切に管理するのに役立ちます。

## Learning Manager Id {#captivateprimeids}

Learning Managerでは、次の2種類の一意のIDがユーザーに提供されます。

* 電子メールID
* UUID（汎用一意Id）

Learning ManagerはUUIDをサポートすることで、組織がユーザーアカウントを柔軟に制御できるようにします。 管理者は、アカウントにユーザーのUUIDがある場合、そのアカウントのユーザーの電子メールIDを変更できます。

**組織でのUUIDの使用シナリオ**

従業員AがLearning Managerという名前の会社に契約社員として入社するシナリオを考えてみます。 契約期間中、Learning Managerの会社は会社の電子メールIDをA@example.comとして提供せず、従業員の個人の電子メールアカウント(例えば、A@gmail.com)のみを検討する場合があります。 契約期間が6か月を完了した後、同じ従業員Aが常勤の従業員としてLearning Managerに参加する場合、Learning Managerでは電子メールIDを会社の電子メールID( A@example.com )に変更する必要があります。

上記のシナリオで、ユーザーアカウントにUUIDでアクセスできれば、Learning Managerにとってもメリットがあります。 Learning Managerでは、従業員Aの個人メールIDを公式のメールIDに簡単に置き換えることができます。 このアカウントに関連する従業員のレコードは、この変更の影響を受けません。

## シングルユーザーID {#singleuseridentification}

Learning Managerは、単一のユーザーが追加された方法（セルフ登録、CSVアップロード、ユーザーインターフェイス、APIなど）を識別して記憶します。

* ユーザーインターフェイス(UI)またはAPIを使用して1人のユーザーを追加した場合、UIやAPIを使用してそのようなタイプのシングルユーザーを削除できます。
* CSVアップロードプロセスを使用して単一ユーザーを更新できますが、これらの単一ユーザーはCSVユーザーとして扱われ、CSVワークフローはこれらのユーザーに適用されることに注意する必要があります。

## マネージャーの役割の割り当て {#assigningmanagerrole}

マネージャーの役割をLearning Managerのどのユーザーにも直接割り当てることはできません。 ユーザーXがLearning Managerのマネージャーになることができるのは、そのアカウント内の任意のユーザー（例えば、Y）のマネージャー属性をXとして設定した場合のみです。

Xがユーザーのマネージャー（A、B、Cなど）であるシナリオで、Xが組織を離脱した場合、A、B、Cのマネージャー属性が新しいマネージャーに設定されていることを確認する必要があります。 または、これらのユーザーのマネージャー属性を一時的にROOTとして設定し、後で新しいマネージャー名を割り当てることもできます。

このトピックの詳細については、次のヘルプコンテンツを参照してください。

* [CSVアップロードに関するFAQ](/help/migrated/administrators/add-users-in-bulk.md)
* [ユーザー追加機能のヘルプ](/help/migrated/administrators/feature-summary/add-users-user-groups.md)

