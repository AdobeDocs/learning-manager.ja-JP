---
jcr-language: en_us
title: AdobeのLearning Managerモバイルアプリでのホワイトラベル
description: ホワイトラベルとは、アプリやサービスのブランド名を変更し、元のクリエイターのようにカスタマイズする行為です。 Adobe Learning Managerでは、モバイルアプリにホワイトラベルを適用して、アプリのブランドを変更したり、自分のブランドの下でアプリを使用したりすることができます。
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: 0c97b147a1e4c6e1a4a0cc69f56f8e9420c4602b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# AdobeのLearning Managerモバイルアプリでのホワイトラベル

Adobe Learning Managerモバイルアプリは、ホワイトラベルをサポートするようになりました。これにより、独自のブランディングでアプリをリリースできるようになりました。

ALMは、次のタイムラインに従って、更新された白いラベルの付いたバイナリファイルを利用可能にします。

1. モバイルアプリのメジャーリリースの場合、ファイルは2週間前に利用可能になります。
2. 緊急の修正のために計画された更新の場合、ファイルは1週間前に利用可能になります。
3. 計画外の緊急および即時の修正の場合、ファイルはベストエフォート型で利用可能になります。

バイナリは、お客様の指定フォルダで使用できるようになります。 CSMに連絡してファイルにアクセスしてください。 お客様は、タイムリーな公開と関連プロセスに対する責任を負います。

## 白いラベルのアプリを起動する準備を開始する方法

独自の白いラベルのアプリをデプロイして管理するには、次の手順に従います。

1. アセット（スプラッシュスクリーン画像など）とテキストを準備して、アプリとapp/playストアの説明の両方で使用できるようにします。

1. 次の能力を持つ技術リソースを割り当てます。

   * プッシュ通知証明書ファイルを生成しています。
   * ALMチームが提供するアプリのバイナリに署名しています。
   * 公開プロセスをアップロードおよび管理しています。 公開プロセスでは、アプリマネージャーとアプリ/Playストアチームの間で、アプリがすべての公開ガイドラインに準拠していることを伝える必要があります。 ALMから、完全に準拠したアプリバイナリを受け取ります。

## 概要

ホワイトラベルとは、アプリやサービスのブランド名を変更し、元のクリエイターのようにカスタマイズする行為です。 Adobe Learning Managerでは、モバイルアプリにホワイトラベルを適用して、アプリのブランドを変更したり、自分のブランドの下でアプリを使用したりすることができます。

## カスタマイズ可能な項目

以下をカスタマイズできます。

### フィールド

<table>

 <tbody>

  <tr>

   <td>

    <p>アカウントID</p>

   </td>

   <td>

    <p>アカウントのID。 他のアカウントに属する学習者は、白いラベルのアプリにアクセスできません。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>追加のアカウントId</p>

   </td>

   <td>

    <p>必要に応じて、複数のアカウント（サブドメイン）を追加します。 サブドメインをスペースなしでコンマ区切りとして追加します。 たとえば、 acc01、acc02、acc03などです。<br> <b>注意：</b>サブドメインを指定するときは、アカウントIDを追加する必要があります。</br> </p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリ名</p></td>

   <td>

    <p>アプリに使用する名前です。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリの短い名前</p>

   </td>

   <td>

    <p>アプリ名が長い場合は、デバイスに表示される短い名前をアプリに付けます。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>内部アプリ名</p></td>

   <td>

    <p>OSがアプリを識別するために使用する名前です。 通常使用される形式は、 com.company-name.product-nameです。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>内部アプリ名 – iOS</p>

   </td>

   <td>

    <p>ユーザーがiOSを使用している場合は、アプリに別の名前を付けてください。 iOSとAndroidの両方に同じ名前を使用することをお勧めします。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリアイコン</p>

   </td>

   <td>

    <p>アプリアイコンをpngに変換します。 このアイコンはアプリに表示されます。 名前の形式はaccount-id_appIcon.pngです。 アプリアイコンのサイズは512 × 512ピクセルです。<div>Appleのアプリアイコンでは、Alphaチャンネルを使用できません。 そのため、必ずアセットからAlphaチャンネルを削除してから送信してください。</div></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリのスプラッシュ画面</p></td>

   <td>

    <p>アプリのスプラッシュ画面には、ユーザーがアプリを起動したときに表示される画像(png)を指定します。 名前の形式はaccount-id_splashIcon.pngです。 正方形ベースのスプラッシュ画面の寸法は1052×1052ピクセルであり、円ベースのスプラッシュ画面は768 x 768ピクセルである。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>クライアントIDとクライアントシークレット</p>

   </td>

   <td>

    <p>アプリの登録時に、アカウントの統合管理者が詳細を提供します。 統合管理者は、以下を使用する必要があります。<ul><li>学習者：読み取り，学習者：ロールとして書き込み</li><li>リダイレクトURLとしての内部アプリname://redirect</li></ul></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アカウントロゴ</p>

   </td>

   <td>

    <p>組織のロゴをホストするURL。 アカウントロゴとしてcpcontentsリンクを提供します。 URLはWebでエンコードする必要があります。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリのアプリストアID(iOS)</p>

   </td>

   <td>

    <p>強制更新の実装に必要なIDです。 アプリを更新するには、学習者をアプリストアにリダイレクトする必要があることをアプリに伝える必要があります。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>アプリのGoogle playストアID(Android)</p>

   </td>

   <td>

    <p>強制更新の実装に必要なIDです。</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>ディープリンクのホスト名</p>

   </td>

   <td>

    <p>ディープリンクをホストするには、learningmanagerを使用します。 別のホスト名URLをディープリンクとして使用する場合は、ホストのURLを指定します。 例えば、learningmanager.adobe.comのように入力します。</p>

   </td>

  </tr>

 </tbody>

</table>

>[!NOTE]
>
>CSAMにデータを提供して、カスタマイズされたアプリバイナリに追加できるようにします。


#### カスタムのディープリンクを処理するためのサイトの関連付けの更新

カスタムドメインまたはlearningmanager\*.adobe.comをホストとして使用している場合は、何もする必要はありません。 ただし、URLにカスタムソリューションまたは特定のホスト名を使用する場合は、サイト関連付けファイルを追加します。

>[!CAUTION]
>
>ファイルが存在しない場合、ディープリンクは機能しません。 ファイルが存在することを確認します。


詳細については、次のリンクを参照してください。

* [Android](https://learningmanager.adobe.com/.well-known/assetlinks.json)
* [iOS](https://learningmanager.adobe.com/.well-known/apple-app-site-association)

## App StoreのグループIDを取得

チームIDを取得するには：

1. **[!UICONTROL Appleデベロッパー]**&#x200B;アカウントにログインします。
2. ページ上部の&#x200B;**[!UICONTROL メンバーシップの詳細]**&#x200B;を選択し、チームIDをコピーします。

このIDは、ディープリンクを有効にするために、メタデータファイルに白いラベルの付いたアプリエントリを追加するために必要です。

## Android用SHA-256指紋の取得

白いラベルのアプリエントリを追加する場合は、Android署名証明書用のSHA-256指紋が必要です。

SHA-256指紋を生成するには：

1. 次のコマンドを実行します。

```
keytool -list -v -keystore <keystore/jks file> -alias <aliaskey> -storepass <storepassword> -keypass <keypassword>
```

出力で、証明書の指紋を見つけ、SHA-256の値をコピーします。 ディープリンク設定の場合は、必要に応じてこのフィンガープリントを共有します。

## プッシュ通知の生成

AndroidアプリとiOSアプリにプッシュ通知を送信するには、2つの異なるメカニズムが必要です。

* iOSの場合、プッシュ通知証明書を生成します。
* Androidの場合は、Firebaseプロジェクトから生成されたサーバーキーを提供します。

Firebaseでプロジェクトを設定するには、以下の手順に従います。

### iOSでのプッシュ通知

iOSアプリの開発では、プッシュ通知証明書はAppleが発行する暗号化資格情報で、これによりサーバーはAppleのプッシュ通知サービス(APN)を介してiOSデバイスにプッシュ通知を安全に送信できます。

証明書は、iOSデバイスにプッシュ通知を送信する際に、サーバー（またはプロバイダー）とAppleのAPN間の安全な通信を保証します。

Android版とiOS版はどちらも、デバイスにプッシュ通知を送信するためのサービスとしてFirebase Cloud Messaging(FCM)を使用しています。

### iOSで証明書を生成する方法

以下の手順に従います。

1. **プッシュ通知証明書**&#x200B;と秘密キー(.p12)を生成またはダウンロードします。 詳しくは、[Appleデベロッパーのドキュメント](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns)を参照してください。

1. ファイルのダウンロードが完了したら、p12ファイルをインストールします。 パスワードを使用して、**キーチェーンアクセス**&#x200B;にインストールします。

1. **証明書**&#x200B;に移動し、証明書をエクスポートします。 MIMEタイプとして.cerが選択されていることを確認します。

1. p12ファイルとcerファイルが使用可能になったら、次のコマンドを実行します。

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```

サーバーに接続できる場合は、作成した証明書が有効です。 myapnappkey.pemファイルから、証明書とプライベートキーの値をコピーします。

### Androidでのプッシュ通知

Androidの場合、ユーザーはFirebaseプロジェクトからservices.jsonファイルを提供して、SNSサービスにエントリを追加する必要があります。

Firebaseでプロジェクトを作成し、 services.jsonファイルをCSMチームと共有します。 このファイルは、SNSのトークンベースのエントリに必要です。 サーバーキーはもう使用されていないことに注意してください。 [Firebaseでのプロジェクトの作成](#create-project-in-firebase)を参照してください。

services.jsonファイルをダウンロードするには、次の手順に従います。

1. **Firebase**&#x200B;コンソールにログインします。
1. **プロジェクト設定**&#x200B;に移動し、**クラウドメッセージング**&#x200B;を選択します。
1. **Firebase Cloud Messaging API**&#x200B;を検索し、**サービスアカウントの管理**&#x200B;を選択します。
1. **サービスアカウント**&#x200B;ページの左側のパネルで、**サービスアカウント**&#x200B;を選択します。
1. プロジェクトのエントリを探し、[アクション]で[**詳細の管理**]を選択します。

   >[!NOTE]
   >
   >   プロジェクトエントリの形式は、&lt;-accountname->@appspot.gserviceaccount.comになります。

1. 「**キー**」タブに移動し、「**キーを追加**」を選択します。
1. キーがない場合は、**新しいキーの作成**&#x200B;を選択し、キーの種類として&#x200B;**JSON**&#x200B;を選択します。 これにより、JSONファイルが生成およびダウンロードされます。
1. 既にキーがある場合は、**既存のキーをアップロード**&#x200B;を選択し、キーを貼り付けてアップロードします。 これにより、JSONファイルが生成およびダウンロードされます。

<!-- Set up a project in Firebase and share the server key with the CSAM.-->

AWSでSNSサービスにエントリを追加するためのJSONファイルを共有する方法については、CSMチームにお問い合わせください。 ユーザーは、プッシュ通知のためにSNSサービスに登録されたエントリを取得する必要があります。これにより、上記で生成された証明書を検証のために共有することが求められます。

## Firebaseでのプロジェクトの作成 {#create-project-in-firebase}

### Android

上記の手順で作成したのと同じプロジェクトをプッシュ通知に再利用します。

[プロジェクト](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging)をFirebaseに追加し、***google-services.json***&#x200B;ファイルを取得します。

### iOS

[プロジェクト](https://firebase.google.com/docs/ios/setup)をFirebaseに追加し、***GoogleService-Info.plist***&#x200B;ファイルを取得します。

>[!IMPORTANT]
>
>このファイルをAdobe Learning Manager CSAMチームに送り、アプリのバイナリファイルのビルドに含めます。


## 署名されたバイナリを生成する

### iOS

<!--```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist {ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```-->

`<root>`フォルダーには、**Runner.xcarchive.zip**&#x200B;ファイルが含まれています。 次のコマンドを実行して、署名されたバイナリを生成します。

1. 次のコマンドを実行して、アーカイブを解凍します。

   ```
   unzip Runner.xcarchive.zip
   ```

2. appディレクトリに移動します。

   ```
   cd Runner.xcarchive/Products/Applications/Runner.app
   ```

3. モバイルプロビジョニングファイルのコピー：

   ```
   cp <path>/<mobile-provisioningfile>.mobileprovision embedded.mobileprovision
   ```

4. 次のコマンドを実行して、署名情報をフレームワークライブラリに更新します。

   ```
   codesign -f -s "Distribution Certificate Name" Frameworks/*
   ```

5. `<root>`フォルダー（ Runner.xcarchive.zipがある場所）に戻ります：

   ```
   cd <root>
   ```

6. xcodebuildを使用してアーカイブをエクスポートします。

   ```
   xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath ipa_path/ -exportOptionsPlist <path>/<ExportOptions-file>.plist
   ```

7. ipa_pathフォルダーで.ipaファイルを探します。
8. .ipaファイルを`Diawi` Webサイトにアップロードします。
9. 完全にアップロードされたら、**[!UICONTROL [送信]]**&#x200B;ボタンを選択します。
10. 完了すると、QRコードとリンクが届きます。
11. SafariでQRコードまたはリンクを直接開きます。

デバイスがプロビジョニングプロファイルに含まれている場合は、デバイス上でインストールが続行されます。

>[!NOTE]
>
>署名されたバイナリをビルドするにはXCode 15.2以上が必要です。


### Android

**APKファイルの場合**

>[!IMPORTANT]
>
>`apksigner`コマンドを実行する前に、次のコマンドを実行して、キーストアパスワードとキーエイリアスパスワードを環境変数としてエクスポートします。
>
>```
>export KS_PASS=your_keystore_password
>export KEY_PASS=your_key_password
>```

```
sh""" <path>/apksigner sign --ks $storeFile. --ks-pass env:KS_PASS --ks-key-alias $key_alias --key-pass env:KEY_PASS --out app-release-signed.apk -v app-release.apk """
```

>[!NOTE]
>
>`apksigner`ツールへのパスは通常、～/Library/Android/sdk/build-tools/30.0.3/apksignerのようになります。

**aabファイルの場合**

>[!NOTE]
>
>署名されたバイナリをビルドするには、Android sdk build-toolsが必要です。

Playストアでは、公開するためにaab形式のAndroidバイナリが必要です。 したがって、署名されていない.aabファイルを提供します。

>[!NOTE]
>
>キーストアファイルを作成する場合、キーストアパスワード、署名キーエイリアス、および署名キーエイリアスのパスワードを生成する必要があります。

.aabファイルに署名するには、次の手順を実行します。

次のコマンドを実行します。

```
<path>/jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore <keystore-file> app-release.aab <signingKeyAlias>
```

>[!NOTE]
>
>**[!UICONTROL jarsigner]**&#x200B;はJavaに含まれています。 Java 21を使用していることを確認します。

プロンプトが表示されたら、次のパスワードを入力してください。

* キーストアのパスワード
* 署名キーエイリアスのパスワード

付属のapkを使用できます。 ただし、aabファイルからapkを生成する必要がある場合は、次の手順に従います。

>[!NOTE]
>
>APKを生成するには、**[!UICONTROL bundletool]**&#x200B;をインストールする必要があります。


次のコマンドを実行して、apkファイルを作成します。

```
java -jar <path>/bundletool-all.jar  build-apks --bundle=app-release.aab --output=my_app.apks --mode=universal
```

ファイルを解凍するには、次のコマンドを実行します。

```
unzip my_app.apks -d output_dir
```

**[!UICONTROL output_dir]**&#x200B;フォルダーからapkファイルを取得します。

**次のステップ**

バイナリを生成したら、バイナリをPlayストアまたはApp Storeにプッシュします。

### レビューのためにアプリをストアにプッシュする

最終的なバイナリを取得したら、それらを対応するアプリストア(iOSまたはAndroid)にアップロードしてレビューできます。 次の手順に従って、バイナリをアプリストアにアップロードします。

**iOS**

1. App Storeの資格情報を使用して、 Transporterアプリにログインします。
2. 左側の上部にある「**+**」ボタンを選択し、本番証明書（.ipaファイル）をアップロードします。
3. .ipaファイルが正しい場合は、App Storeにアプリケーションをアップロードするように求められます。
4. アプリが配信されたら、App Storeにログインします。 数時間以内に、バイナリがTestFlightセクションに表示されます。 アプリのレビュー前にTestFlightで最終的なサニティーテストを有効にし、新しいリリース用にアプリを送信する際に、このIPAをバイナリとして使用できます。

**Android**

1. Google Play Storeコンソールを開きます。
2. **[!UICONTROL ダッシュボード]** > **[!UICONTROL アプリのリリースを表示]** > **[!UICONTROL ダッシュボードをリリース]**&#x200B;に移動し、**[!UICONTROL 新しいリリースを作成]**&#x200B;を選択します。
3. 生成された.aabファイルをアプリバンドルとしてアップロードし、バージョン番号や新機能などのリリース情報を入力します。
4. 変更を保存し、アプリをレビュー用に送信します。
5. アプリの配布は必ず100%に設定してください(Googleではデフォルトで20%に設定されています)。

#### アプリ公開に役立つリンク

**Android**

[アプリを作成してセットアップする](https://support.google.com/googleplay/android-developer/answer/9859152?hl=en)
[レビュー用にアプリを準備](https://support.google.com/googleplay/android-developer/answer/9859455?sjid=2454409340679630327-AP)

**iOS**

[レビュー用に送信](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-for-review)

## 変更を適用する方法

必要なアセットとファイルをCSMチームに送信します。 次に、CSMチームが[フォーム](https://forms.office.com/r/bJRRaRBvSh)に必要な変更を入力し、必要なアセットを添付します。 チームは、変更を確認し、エンジニアリングチームに通知します。 エンジニアリングチームがビルドを生成し、CSMチームと共有します。

CSMチームがお客様とビルドを共有します。

## カスタマイズできない内容

* パスワードの更新画面
* アカウントの作成画面
