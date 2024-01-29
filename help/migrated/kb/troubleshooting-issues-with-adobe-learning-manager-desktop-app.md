---
description: このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、AdobeのLearning Managerデスクトップアプリケーションのインストール時および使用時に発生する一般的な問題のいくつかを解決できます。
jcr-language: en_us
title: Adobe版Learning Managerデスクトップアプリのトラブルシューティング
contentowner: kuppan
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---



# Adobe版Learning Managerデスクトップアプリのトラブルシューティング

このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、AdobeのLearning Managerデスクトップアプリケーションのインストール時および使用時に発生する一般的な問題のいくつかを解決できます。

## 次の操作を実行できません {#iamunabletodothefollowing}

+++AdobeのLearning Managerデスクトップアプリケーションをダウンロードできない

1. インターネット接続とファイアウォールの設定を確認してください。
1. 「ソーシャル学習」で、次をクリックします。 **[!UICONTROL 新しい投稿]** 投稿を作成します。 掲示板がない場合は、掲示板を先に作成します。
1. スクリーンショット、音声の録音、ビデオの録画、Learning Managerギャラリーなど、表示される投稿ボタンオプションのいずれかをクリックして、コンテンツを作成します。 AdobeのLearning Managerデスクトップアプリケーションページにリダイレクトされます。このページから、デスクトップ用のAdobeのLearning Managerデスクトップアプリケーションをダウンロードできます。
1. 有効なAdobeのLearning Managerアカウントがあり、管理者がこのアカウントでソーシャル学習を有効にしている必要があります。 管理者がWebブラウザーからのダウンロードを無効にしている可能性もあります。 AdobeのLearning Manager管理者に、AdobeのLearning Managerデスクトップアプリをダウンロードする方法を確認してください。

+++

+++AdobeのLearning Managerデスクトップアプリケーションをインストールできない

1. システムが必要システム構成を満たしていることを確認してください。 詳しくはこちら [Learning ManagerデスクトップアプリケーションをAdobeするための必要システム構成](../learners/adobe-learning-manager-app-for-desktop/adobe-learning-manager-desktop-app-system-requirements.md).
1. 以前にインストールしたAdobeのLearning Managerデスクトップアプリケーションをクリーンアップします。 詳しくは、「  [以前のインストールをクリーンアップする方法](#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp) 」を参照してください。
1. インストールプロセス中のエラーについては、以下を参照してください [アプリケーションログの検索方法](#howtofindapplicationlogs). さらにサポートが必要な場合は、AdobeのLearning Managerデスクトップアプリケーション管理者にお問い合わせください。

+++

+++AdobeのLearning Managerデスクトップアプリケーションを起動できない

1. AdobeのLearning Managerデスクトップアプリケーションがダウンロードおよびインストールされていることを確認します。
1. 「ソーシャル学習」で、次をクリックします。 **[!UICONTROL 新しい投稿]** 掲示板がない場合は、掲示板を作成します。 スクリーンショット、音声の録音、ビデオの録画、AdobeのLearning Managerギャラリーなど、表示される投稿ボタンオプションのいずれかをクリックします。 AdobeのLearning Managerデスクトップアプリケーションを起動できるページにリダイレクトされます。
1. アプリが起動しない場合は、WindowsのスタートメニューまたはMac OS XのLaunchpadから起動することもできます。

+++

+++AdobeのLearning Managerデスクトップアプリケーションでアカウントにログインできない

1. インターネットに接続し、AdobeのLearning Managerデスクトップアプリケーションがファイアウォールでブロックされていないことを確認してください。
1. 有効なAdobeのLearning Manager学習者アカウントがあり、このアカウントでソーシャル学習が有効になっていることを確認します。
1. それでもログインできない場合は、AdobeのLearning Managerデスクトップアプリケーションを終了して再起動してから、再試行してください。
1. さらにサポートが必要な場合は、AdobeのLearning Manager管理者までお問い合わせください。

+++

+++AdobeのLearning ManagerデスクトップアプリケーションにWebカメラ/マイクが表示されない

1. Webカメラ/マイクがシステムに正しく接続され、正常に機能していることを確認します。
1. Webカメラ/マイクの最新ドライバーがインストールされていることを確認します。 専用のドライバーがないと正しく機能しないデバイスもあります。
1. アプリケーションの環境設定をリセットし、AdobeのLearning Managerデスクトップアプリケーションを再起動してから、再試行してください。 詳しくは、「 [アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences).
1. Mac OS X Mojave 10.14を使用している場合は、Webカメラやマイクに対するアクセス権限をLearning ManagerデスクトップアプリケーションをAdobeに付与します。 詳しくは、「 [OSX MojaveでWebカメラ/マイクを設定する方法](#howtosetwebcammicrophonepermissionsonMacOSXMojave).

+++

+++AdobeのLearning Managerデスクトップアプリケーションから投稿を公開できない

1. 有効なAdobeのLearning Manager学習者アカウントがあり、AdobeのLearning Manager管理者によって、このアカウントでソーシャル学習が有効にされていることを確認します。
1. アプリケーションの環境設定をリセットし、AdobeのLearning Managerデスクトップアプリケーションを再起動してから、再試行してください。 詳しくは、「 [アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences).
1. 公開中にエラーが発生した場合は、詳細ログを有効にします。 詳しくは、「 [詳細ログを有効にする方法](#howtoenableadvancedlogging)を選択した場合は、AdobeのLearning Managerデスクトップアプリケーションを再起動し、エラーの原因となった上記の手順を再試行します。 最新のアプリケーションログをAdobeのLearning Manager管理者に送信してください。 詳しくは、「 [アプリケーションログの検索方法](#howtofindapplicationlogs).

+++

+++古いプロジェクトを表示できない、または開くことができない

1. 表示されるのは、AdobeのLearning Managerアカウントで作成したプロジェクトのみです。このプロジェクトは、同じコンピューターに作成されています。
1. アプリケーションの環境設定をリセットし、AdobeのLearning Managerデスクトップアプリケーションを再起動してから、再試行してください。 ヘルプについては、以下を参照してください [アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences).
1. プロジェクトを開く際にエラーが発生した場合は、高度なログ記録を有効にします。 詳しくは、「 [詳細ログを有効にする方法](#howtoenableadvancedlogging). AdobeのLearning Managerデスクトップアプリケーションを再起動して、エラーの原因となった手順を再試行します。 最新のアプリケーションログをAdobeのLearning Manager管理者に送信してください。 詳しくは、「 [アプリケーションログの検索方法](#howtofindapplicationlogs).

+++

## アプリケーションの環境設定をリセットする方法 {#howtoresetapplicationpreferences}

### Windows {#windows}

1. 実行ダイアログを開くには、 **Windows + R** キー。
1. 種類 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` キーを押します。
1. 以下の名前のファイルを削除します **preferences.json** および **preferences.xml**.

### MAC OS X {#macosx}

1. Finderを開きます。
1. を開きます **に移動** フォルダーダイアログ、を押す **Cmd + Shift + G** キー。
1. 種類 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` キーを押します。
1. 以下の名前のファイルを削除します **preferences.json** および **preferences.xml**.

## アプリケーションログを見つける方法 {#howtofindapplicationlogs}

### Windows {#application-logs}

1. ファイル名を指定して実行ダイアログボックスを開くには、 **Windows + R** キー。
1. 種類 `**%TEMP%\\elthor**` キーを押します。
1. フォルダーを **更新日** 最後に使用したフォルダーを開きます。 このフォルダーには、最新のアプリケーションログが含まれています。

### MAC OS X {#MacOSX-1}

1. 開く **Finder**.
1. を開きます **フォルダーに移動** ダイアログボックス、を押す **Cmd + Shift + G** キー。
1. 「 」と入力&#x200B;**/var/folders**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. 「 」を検索&#x200B;**エルトール**&#x200B;検索バーで「 」をクリックし、フォルダーを開きます。
1. **変更日**でフォルダーを並べ替え、最新のフォルダーを開きます。 このフォルダーには、最新のアプリケーションログが含まれています。

## 高度なログ記録を有効にする方法 {#howtoenableadvancedlogging}

### Windows {#Windows-1}

1. ファイル名を指定して実行ダイアログを開くには、 **Windowsキー+ R**.****
1. 「 」と入力&#x200B;**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**&quot; （引用符は除く）と入力し、Enterキーを押します。****
1. ファイルのバックアップを作成 **preferences.json**&#x200B;を選択し、テキストエディターで開きます****
1. キーの検索 **debugMode** このキーのvalueプロパティを&quot;に変更します&#x200B;**true**&quot; （引用符は除く）

### MAC OS X {#MacOSX-2}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G**.
1. 「 」と入力&#x200B;**～/Library/Application Support/Adobe/Learning Manager 1.0**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. ファイルのバックアップを作成 **preferences.json**&#x200B;を選択し、テキストエディターで開きます。
1. キーの検索 **debugMode** このキーのvalueプロパティを&quot;に変更します&#x200B;**true**&quot; （引用符なし）

## Mac OS X MojaveでWebカメラ/マイクを設定する方法 {#howtosetwebcammicrophonepermissionsonmacosxmojave}

1. クリック **[!UICONTROL システム環境設定]** アイコンをドックに追加します。
1. クリック **[!UICONTROL セキュリティとプライバシー]** > **[!UICONTROL プライバシー].**
1. クリック **[!UICONTROL Webカメラとマイクのオプション]** また、AdobeのLearning Managerチェックボックスが選択されていることを確認します。 リストにLearning Manager Adobeが表示されない場合は、Learning ManagerデスクトップアプリケーションをAdobeにインストールしてから起動します。

## AdobeのLearning Manager for Desktopの更新キャッシュをクリーンアップする方法 {#howtocleanupadobecaptivateprimefordesktopupdatescache}

### Windows {#clean-previous-installation}

1. ファイル名を指定して実行ダイアログを開くには、 **Windowsキー+ R**.
1. 種類 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` キーを押します。
1. という名前のフォルダーを削除します **アップデート**.

### MAC OS X {#MacOSX-3}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G**.
1. 種類 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` キーを押します。
1. という名前のフォルダーを削除します **アップデート**.

## Learning Manager for DesktopのAdobe一時フォルダーをクリーンアップする方法 {#howtocleanupadobecaptivateprimefordesktoptempfolder}

### Windows {#clean-previous-installation-1}

1. 実行ダイアログを開くには、次を押します **Windowsキー+ R**.
1. 「 」と入力&#x200B;**%TEMP%**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. 「 」という名前のフォルダーを削除します&#x200B;**エルトール**“。

### MAC OS X {#MacOSX-4}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G** キー。
1. 「 」と入力&#x200B;**/var/folders**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. 「 」を検索&#x200B;**エルトール**&#x200B;検索バーの「。
1. 「 」という名前のフォルダーを削除します&#x200B;**エルトール**“。

## AdobeのLearning Manager for Desktopプロジェクトを見つける方法 {#howtolocateadobecaptivateprimefordesktopprojects}

### Windows {#Windows-2}

1. ファイル名を指定して実行ダイアログを開くには、 **Windowsキー+ R**.
1. 「 」と入力&#x200B;**～/Documents/My AdobeのLearning Managerプロジェクト**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. ユーザーまたはAdobeのLearning Manager管理者が、デフォルトのプロジェクトフォルダーの場所を変更した可能性があります。 プロジェクトの検索とクリーンアップの詳細については、管理者に問い合わせてください。

### MAC OS X {#MacOSX-5}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G** キー。
1. 「 」と入力&#x200B;**～/Documents/My AdobeのLearning Managerプロジェクト**&quot; （引用符は除く）と入力し、Enterキーを押します。

   ユーザーまたはAdobeのLearning Manager管理者が、デフォルトのプロジェクトフォルダーの場所を変更した可能性があります。 プロジェクトの検索とクリーンアップの詳細については、管理者に問い合わせてください。

## 以前にインストールしたAdobeのLearning Managerデスクトップアプリをクリーンアップする方法 {#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp}

### Windows {#Windows-3}

1. を開きます **実行ダイアログ、**&#x200B;押す&#x200B;**Windowsキー+ R**.
1. regeditと入力して検索します。**HKEY_LOCAL_MACHINE \\SOFTWARE\\Classes\\Installer\\**&quot; （引用符なし）または&quot;**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Installer\\UserData\\S-1-5-18\\Products\\**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. AdobeのLearning Managerを検索して、以前にインストールしたフォルダーを見つけます。 レジストリエントリを削除します。  キーを見つけるには、F3キーを押します。

### MAC OS X {#MacOSX-6}

次のパスからファイルを移動します&#x200B;**/Applications/Adobe版Learning Manager/Users/Shared/Adobe/Learning Manager Assets/1.0**「ゴミ箱にして、ゴミ箱を空にしてください。
