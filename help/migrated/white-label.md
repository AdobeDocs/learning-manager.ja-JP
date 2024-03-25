---
jcr-language: en_us
title: AdobeのLearning Managerモバイルアプリでのホワイトラベル
description: ホワイトラベルとは、アプリやサービスのブランド名を変更し、元のクリエイターのようにカスタマイズする行為です。 AdobeのLearning Managerでは、モバイルアプリにホワイトラベルを適用することができます。これにより、アプリのブランドを変更し、自分のブランドの下でアプリを使用できるようになります。
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: 8228a6b78362925f63575098602b33d3ee645812
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---

# AdobeのLearning Managerモバイルアプリでのホワイトラベル

AdobeのLearning Managerモバイルアプリで、ホワイトラベルがサポートされるようになりました。つまり、お客様のブランディングの下でアプリをリリースできます。

## 白いラベルのアプリを起動する準備を開始する方法

独自の白いラベルのアプリをデプロイして管理するには、次の手順に従います。

1. アセット（スプラッシュスクリーン画像など）とテキストを準備して、アプリとapp/playストアの説明の両方で使用できるようにします。

1. 次の能力を持つ技術リソースを割り当てます。

* プッシュ通知証明書ファイルを生成しています。
* ALMチームが提供するアプリのバイナリに署名しています。
* 公開プロセスをアップロードおよび管理しています。 公開プロセスでは、アプリマネージャーとアプリ/Playストアチームの間で、アプリがすべての公開ガイドラインに準拠していることを伝える必要があります。 ALMから、完全に準拠したアプリバイナリを受け取ります。

## 概要

ホワイトラベルとは、アプリやサービスのブランド名を変更し、元のクリエイターのようにカスタマイズする行為です。 AdobeのLearning Managerでは、モバイルアプリにホワイトラベルを適用することができます。これにより、アプリのブランドを変更し、自分のブランドの下でアプリを使用できるようになります。

## カスタマイズ可能な項目

以下をカスタマイズできます。

### フィールド

<table>

    <tbody>

    <tr>

   <td>

    <p>アカウントID</p></td>

   <td>

    <p>アカウントのID。 他のアカウントに属する学習者は、白いラベルのアプリにアクセスできません。</p></td>

  </tr>

  <tr>

   <td>

    <p>追加のアカウントId</p></td>

   <td>

    <p>必要に応じて、複数のアカウント（サブドメイン）を追加します。 サブドメインをスペースなしでコンマ区切りとして追加します。 たとえば、 acc01、acc02、acc03などです。<br> <b>注意：</b> サブドメインを指定する場合は、アカウントIDを追加する必要があります。</br> </p></td>

  </tr>

  <tr>

  <td>

  <p>アプリ名</p></td>

  <td>

  <p>アプリに使用する名前です。</p></td>

  </tr>

  <tr>

  <td>

  <p>アプリの短い名前</p></td>

  <td>

  <p>アプリ名が長い場合は、デバイスに表示される短い名前をアプリに付けます。</p></td>

  </tr>

   <tr>

  <td>

  <p>内部アプリ名</p></td>

  <td>

  <p>OSがアプリを識別するために使用する名前です。 通常使用される形式は、 com.company-name.product-nameです。</p></td>

  </tr>

  <tr>

  <td>

  <p>内部アプリ名 – iOS</p></td>

  <td>

  <p>ユーザーがiOSを使用している場合は、アプリに別の名前を付けてください。 iOSとAndroidの両方に同じ名前を使用することをお勧めします。</p></td>

  </tr>

  <tr>

  <td>

  <p>アプリアイコン</p></td>

  <td>

  <p>アプリアイコンをpngに変換します。 このアイコンはアプリに表示されます。 名前の形式はaccount-id_appIcon.pngです。</p></td>

  </tr>

  <tr>

  <td>

  <p>アプリのスプラッシュ画面</p></td>

  <td>

  <p>アプリのスプラッシュ画面には、ユーザーがアプリを起動したときに表示される画像(png)を指定します。 名前の形式はaccount-id_splashIcon.pngです。</p></td>

  </tr>

  <tr>

  <td>

  <p>クライアントIDとクライアントシークレット</p></td>

  <td>

  <p>アプリの登録時に、アカウントの統合管理者が詳細を提供します。 統合管理者は、以下を使用する必要があります。<ul><li>学習者：読み取り，学習者：ロールとして書き込み</li><li>リダイレクトURLとしての内部アプリname://redirect</li></ul></p></td>

  </tr>

  <tr>

  <td>

  <p>アカウントロゴ</p></td>

  <td>

  <p>組織のロゴをホストするURL。 アカウントロゴとしてcpcontentsリンクを提供します。 URLはWebでエンコードする必要があります。</p></td>

  </tr>

  <tr>

  <td>

  <p>アプリのアプリストアID(iOS)</p></td>

  <td>

  <p>強制更新の実装に必要なIDです。 アプリを更新するには、学習者をアプリストアにリダイレクトする必要があることをアプリに伝える必要があります。</p></td>

  </tr>

   <tr>

  <td>

  <p>アプリのGoogle playストアID(Android)</p></td>

  <td>

  <p>強制更新の実装に必要なIDです。</p></td>

  </tr>

  <tr>

  <td>

  <p>ディープリンクのホスト名</p></td>

  <td>

  <p>ディープリンクをホストするには、learningmanagerを使用します。 別のホスト名URLをディープリンクとして使用する場合は、ホストのURLを指定します。 例えば、learningmanager.adobe.comのように入力します。</p></td>

  </tr>

    </tbody>

</table>

>[!NOTE]
>
>CSAMにデータを提供して、カスタマイズされたアプリバイナリに追加できるようにします。


#### カスタムディープリンクを処理するためのサイトの関連付けの更新

カスタムドメインまたはlearningmanager\*.adobe.comをホストとして使用している場合は、何もする必要はありません。 ただし、URLにカスタムソリューションまたは特定のホスト名を使用する場合は、サイト関連付けファイルを追加します。

>[!CAUTION]
>
>ファイルが存在しない場合、デプリンクは機能しません。 ファイルが存在することを確認します。


詳細については、次のリンクを参照してください。

- [Android](https://learningmanager.adobe.com/.well-known/assetlinks.json)

- [iOS](https://learningmanager.adobe.com/.well-known/apple-app-site-association)

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

1. 生成またはダウンロード **プッシュ通知証明書** および秘密鍵(.p12)を渡します。 詳しくは、 [Apple developer document](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns).

1. ファイルのダウンロードが完了したら、p12ファイルをインストールします。 パスワードを使用して **キーチェーンアクセス**.

1. 移動先 **自分の証明書** 証明書をエクスポートします。 MIMEタイプとして.cerが選択されていることを確認します。

1. p12ファイルとcerファイルが使用可能になったら、次のコマンドを実行します。

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```
サーバーに接続できる場合は、作成した証明書が有効です。 myapnappkey.pemファイルから、証明書とプライベートキーの値をコピーします。

### Androidでのプッシュ通知

Firebaseでプロジェクトを設定し、CSAMとサーバーキーを共有します。

CSMチームに問い合わせて、AWSのSNSサービスに追加されたファイルを取得します。 ユーザーは、プッシュ通知のためにSNSサービスに登録されたエントリを取得する必要があります。これにより、上記で生成された証明書を検証のために共有することが求められます。

>[!NOTE]
>
>Androidの場合、ユーザーはSNSサービスにエントリを追加するために、Android用に作成したFirebaseプロジェクトからサーバーキーを提供する必要があります。


## Firebaseでのプロジェクトの作成

### Android

上記の手順で作成したのと同じプロジェクトをプッシュ通知に再利用します。

[プロジェクトを追加](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging) Firebaseで、 ***google-services.json*** ファイル。

### iOS

[プロジェクトを追加](https://firebase.google.com/docs/ios/setup) をFirebaseに送信し、 ***GoogleService-Info.plist*** ファイル。

>[!IMPORTANT]
>
>AdobeのLearning Manager CSAMチームにファイルを送り、アプリのバイナリファイルのビルドに含めます。


## 署名されたバイナリを生成する

### iOS

```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist ./deviceAppBuildScripts/${ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```

>[!NOTE]
>
>署名されたバイナリをビルドするにはXCode 15.2以上が必要です。


## Android

```
sh""" ~/Library/Android/sdk/build-tools/30.0.3/apksigner sign --ks $storeFile --ks-pass "pass:$store\_password" --ks-key-alias $key\_alias --key-pass "pass:$key\_password" --out app-release-signed.apk -v app-release.apk """
```

>[!NOTE]
>
>署名されたバイナリをビルドするには、Android sdk build-toolsが必要です。

**次へ**

バイナリを生成したら、バイナリをPlayストアまたはApp Storeにプッシュします。

## 変更を適用する方法

必要なアセットとファイルをCSMチームに送信します。 CSMチームが [様式](https://forms.office.com/r/bJRRaRBvSh) 必要な変更を加え、必要なアセットを添付します。 チームは、変更を確認し、エンジニアリングチームに通知します。 エンジニアリングチームがビルドを生成し、CSMチームと共有します。

CSMチームがお客様とビルドを共有します。

## カスタマイズできない内容

- パスワードの更新画面
- アカウントの作成画面
