---
description: このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、Adobe Learning Manager デスクトップアプリケーションのインストールや使用中に発生する一般的な問題のいくつかを解決できます。
jcr-language: en_us
title: Adobe Learning Manager デスクトップアプリケーションのトラブルシューティング
contentowner: kuppan
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 54%

---



# Adobe Learning Manager デスクトップアプリケーションのトラブルシューティング

このドキュメントに記載されている基本的なトラブルシューティングのヒントを活用すると、Adobe Learning Manager デスクトップアプリケーションのインストールや使用中に発生する一般的な問題のいくつかを解決できます。

## 問題 {#iamunabletodothefollowing}

+++AdobeのLearning Managerデスクトップアプリケーションをダウンロードできない

1. インターネット接続とファイアウォールの設定を確認します。
1. 「ソーシャル学習」で「**[!UICONTROL 新しい投稿]**」をクリックして、投稿を作成します。掲示板がない場合は、掲示板を先に作成します。
1. スクリーンショット、音声の録音、ビデオの録画、Learning Manager ギャラリーなど、表示される投稿ボタンオプションのいずれかをクリックして、コンテンツを作成します。Adobe Learning Manager デスクトップアプリケーションのページに自動的に移動します。このページから、Adobe Learning Manager デスクトップアプリケーションをダウンロードできます。
1. 有効な Adobe Learning Manager アカウントがあり、管理者がこのアカウントでソーシャル学習を有効にしている必要があります。管理者が、Web ブラウザーからのダウンロードを許可していない場合もあります。Adobe Learning Manager の管理者に、Adobe Learning Manager デスクトップアプリケーションをダウンロードする方法を確認してください。

+++

+++AdobeのLearning Managerデスクトップアプリケーションをインストールできない

1. システムが最低限の必要システム構成を満たしていることを確認します。[「Adobe Learning Manager デスクトップアプリケーションの必要システム構成」](../learners/adobe-learning-manager-app-for-desktop/adobe-learning-manager-desktop-app-system-requirements.md)をご参照ください。
1. 以前にインストールした Adobe Learning Manager デスクトップアプリケーションを削除します。詳しくは、「  [以前のインストールをクリーンアップする方法](#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp) 」を参照してください。
1. インストールプロセス中のエラーについては、以下を参照してください [アプリケーションログの検索方法](#howtofindapplicationlogs). さらにサポートが必要な場合は、Adobe Learning Manager デスクトップアプリケーションの管理者までお問い合わせください。

+++

+++AdobeのLearning Managerデスクトップアプリケーションを起動できない

1. Adobe Learning Manager デスクトップアプリケーションがダウンロードおよびインストールされていることを確認してください。
1. 「ソーシャル学習」で「**[!UICONTROL 新しい投稿]**」をクリックします（掲示板がない場合は掲示板を作成します）。スクリーンショット、音声の録音、ビデオの録画、AdobeのLearning Managerギャラリーなど、表示される投稿ボタンオプションのいずれかをクリックします。 Adobe Learning Manager デスクトップアプリケーションを起動できるページに自動的に移動します。
1. アプリケーションが起動しない場合は、Windows のステートメニューまたは Mac OS X の Launchpad から起動することもできます。

+++

+++AdobeのLearning Managerデスクトップアプリケーションでアカウントにログインできない

1. インターネットに接続していることを確認します。さらに、Adobe Learning Manager デスクトップアプリケーションが、ファイアウォールの設定でブロックされていないことを確認します。
1. 有効な Adobe Learning Manager 学習者アカウントがあり、このアカウントでソーシャル学習が有効になっていることを確認します。
1. それでもログインできない場合は、Adobe Learning Manager デスクトップアプリケーションを終了して再起動してから、再試行してください。
1. さらにサポートが必要な場合は、Adobe Learning Manager 管理者までお問い合わせください。

+++

+++AdobeのLearning ManagerデスクトップアプリケーションにWebカメラ/マイクが表示されない

1. Web カメラ / マイクがシステムに正しく接続され、正常に動作していることを確認します。
1. Webカメラ/マイクの最新ドライバーがインストールされていることを確認します。 専用のドライバーがないと正しく動作しない機器もあります。
1. アプリケーションの環境設定をリセットし、Adobe Learning Manager デスクトップアプリケーションを再起動してから、再試行してください。詳細については、「[アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences)」を参照してください。
1. Mac OS X Mojave 10.14 の場合は、Web カメラやマイクに対するアクセス権を Adobe Learning Manager デスクトップアプリケーションに付与します。詳細については、「[OSX Mojave で Web カメラ / マイクを設定する方法](#howtosetwebcammicrophonepermissionsonMacOSXMojave)」を参照してください。

+++

+++AdobeのLearning Managerデスクトップアプリケーションから投稿を公開できない

1. 有効な Adobe Learning Manager 学習者アカウントがあり、Adobe Learning Manager 管理者によって、このアカウントでソーシャル学習が有効にされていることを確認します。
1. アプリケーションの環境設定をリセットし、Adobe Learning Manager デスクトップアプリケーションを再起動してから、再試行してください。詳しくは、「 [アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences).
1. 公開中にエラーが発生した場合は、詳細ログを有効にします。 詳細については「[詳細ロギングを有効にする方法](#howtoenableadvancedlogging)」を参照のうえ、Adobe Learning Manager デスクトップアプリケーションを再起動して、エラーの原因となった上記の手順を再試行します。最新のアプリケーションログを Adobe Learning Manager 管理者に送信します。詳細については、「[アプリケーションログを見つける方法](#howtofindapplicationlogs)」を参照してください。

+++

+++古いプロジェクトを表示できない、または開くことができない

1. 表示されるのは、Adobe Learning Manager アカウントで作成したプロジェクトのみです。そのプロジェクトは、同じコンピューターに作成されています。
1. アプリケーションの環境設定をリセットし、Adobe Learning Manager デスクトップアプリケーションを再起動してから、再試行してください。ヘルプについては、以下を参照してください [アプリケーションの環境設定をリセットする方法](#howtoresetapplicationpreferences).
1. プロジェクトを開く際にエラーが発生した場合は、高度なログ記録を有効にします。 詳しくは、「 [詳細ログを有効にする方法](#howtoenableadvancedlogging). Adobe Learning Manager デスクトップアプリケーションを再起動して、エラーの原因となった手順を再試行します。最新のアプリケーションログを Adobe Learning Manager 管理者に送信します。詳細については、「[アプリケーションログを見つける方法](#howtofindapplicationlogs)」を参照してください。

+++

## アプリケーションの環境設定をリセットする方法 {#howtoresetapplicationpreferences}

### Windows {#windows}

1. 実行ダイアログを開くには、 **Windows + R** キー。
1. 種類 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` キーを押します。
1. **preferences.json** と **preferences.xml** を削除します。

### Mac OS X {#macosx}

1. Finderを開きます。
1. を開きます **に移動** フォルダーダイアログ、を押す **Cmd + Shift + G** キー。
1. 種類 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` キーを押します。
1. **preferences.json** と **preferences.xml** を削除します。

## アプリケーションログを見つける方法 {#howtofindapplicationlogs}

### Windows {#application-logs}

1. ファイル名を指定して実行ダイアログボックスを開くには、 **Windows + R** キー。
1. 種類 `**%TEMP%\\elthor**` キーを押します。
1. フォルダーを **更新日** 最後に使用したフォルダーを開きます。 このフォルダーには、最新のアプリケーションログが含まれています。

### Mac OS X {#MacOSX-1}

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

### Mac OS X {#MacOSX-2}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G**.
1. 「 」と入力&#x200B;**～/Library/Application Support/Adobe/Learning Manager 1.0**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. **preferences.json** のバックアップを作成し、元のファイルをテキストエディターで開きます。
1. キーの検索 **debugMode** このキーのvalueプロパティを&quot;に変更します&#x200B;**true**&quot; （引用符なし）

## Mac OS X MojaveでWebカメラ/マイクを設定する方法 {#howtosetwebcammicrophonepermissionsonmacosxmojave}

1. クリック **[!UICONTROL システム環境設定]** アイコンをドックに追加します。
1. クリック **[!UICONTROL セキュリティとプライバシー]** > **[!UICONTROL プライバシー].**
1. **[!UICONTROL 「Web カメラとマイクのオプション」]**&#x200B;をクリックして、Adobe Learning Manager チェックボックスが選択されていることを確認します。リストに Learning Manager がない場合は、Adobe Learning Manager デスクトップアプリケーションをインストールして起動します。

## Adobe Learning Manager for Desktop の更新キャッシュをクリーンアップする方法 {#howtocleanupadobecaptivateprimefordesktopupdatescache}

### Windows {#clean-previous-installation}

1. ファイル名を指定して実行ダイアログを開くには、 **Windowsキー+ R**.
1. 種類 `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**` キーを押します。
1. **updates** というフォルダーを削除します。

### Mac OS X {#MacOSX-3}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G**.
1. 種類 `**~/Library/Application Support/Adobe/Learning Manager 1.0**` キーを押します。
1. **updates** というフォルダーを削除します。

## Adobe Learning Manager for Desktop の一時フォルダーをクリーンアップする方法 {#howtocleanupadobecaptivateprimefordesktoptempfolder}

### Windows {#clean-previous-installation-1}

1. 実行ダイアログを開くには、次を押します **Windowsキー+ R**.
1. 「 」と入力&#x200B;**%TEMP%**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. 「 」という名前のフォルダーを削除します&#x200B;**エルトール**“。

### Mac OS X {#MacOSX-4}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G** キー。
1. 「 」と入力&#x200B;**/var/folders**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. 「 」を検索&#x200B;**エルトール**&#x200B;検索バーの「。
1. 「 」という名前のフォルダーを削除します&#x200B;**エルトール**“。

## Adobe Learning Manager for Desktop プロジェクトを探す方法 {#howtolocateadobecaptivateprimefordesktopprojects}

### Windows {#Windows-2}

1. ファイル名を指定して実行ダイアログを開くには、 **Windowsキー+ R**.
1. 「 」と入力&#x200B;**～/Documents/My AdobeのLearning Managerプロジェクト**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. ユーザーまたは Adobe Learning Manager 管理者が、デフォルトのプロジェクトフォルダーの場所を変更している可能性があります。プロジェクトの検索とクリーンアップの詳細については、管理者に問い合わせてください。

### Mac OS X {#MacOSX-5}

1. Finderを開きます。
1. を開きます **フォルダーに移動** ダイアログ、を押す **Cmd + Shift + G** キー。
1. 「 」と入力&#x200B;**～/Documents/My AdobeのLearning Managerプロジェクト**&quot; （引用符は除く）と入力し、Enterキーを押します。

   ユーザーまたは Adobe Learning Manager 管理者が、デフォルトのプロジェクトフォルダーの場所を変更している可能性があります。プロジェクトの検索とクリーンアップの詳細については、管理者に確認してください。

## 以前にインストールした Adobe Learning Manager デスクトップアプリケーションをクリーンアップする方法 {#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp}

### Windows {#Windows-3}

1. を開きます **実行ダイアログ、**&#x200B;押す&#x200B;**Windowsキー+ R**.
1. regeditと入力して検索します。**HKEY_LOCAL_MACHINE \\SOFTWARE\\Classes\\Installer\\**&quot; （引用符なし）または&quot;**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Installer\\UserData\\S-1-5-18\\Products\\**&quot; （引用符は除く）と入力し、Enterキーを押します。
1. Adobe Learning Manager という名前のフォルダーを検索して、以前にインストールしているかどうかを確認します。レジストリエントリを削除します。  キーを見つけるには、F3キーを押します。

### Mac OS X {#MacOSX-6}

次のパスからファイルを移動します&#x200B;**/Applications/Adobe版Learning Manager/Users/Shared/Adobe/Learning Manager Assets/1.0**「ゴミ箱にして、ゴミ箱を空にしてください。
