---
description: Adobe Learning Manager で Microsoft Teams コネクターをインストール
jcr-language: en_us
title: Adobe Learning Manager で Microsoft Teams コネクターをインストール
contentowner: saghosh
source-git-commit: ab6737e8b43222a6538921b0628a504a5f15859d
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 24%

---



# Adobe Learning Manager で Microsoft Teams コネクターをインストール

## 概要

Microsoft® Teams® は、文書の共有、オンラインミーティング、その他ビジネスコミュニケーション機能全般をサポートする、チャットベースの持続的なコラボレーションプラットフォームです。

AdobeのLearning Managerでは、Microsoft TeamsミーティングをLearning Managerに統合する際に、バーチャル教室コネクターを使用します。

Microsoft Teams のコネクターにより、Learning Manager と Microsoft Teams のシステムを接続することで、バーチャルミーティングを自動的に同期できます。Microsoft Teams コネクターの機能は以下のとおりです。

**Microsoft Teamsを使用したバーチャルセッションの設定**

コネクターを用いることで、Adobe Learning Manager のアカウントと Microsoft Teams のアカウントを統合することができます。 統合されると Learning Manager の作成者は、Learning Manager で作成されたバーチャル教室モジュールのテクノロジーサービスプロバイダーとして、Microsoft Teams を使用することができます。

**Microsoft Teamsがバーチャルクラスルームに入るときに学習者を認証することを許可**

コネクターを使用することで、ミーティングの作成時にLearning Managerからミーティング主催者をMicrosoft Teamsとして設定できます。 ミーティング主催者はロビーを管理することで、ミーティングへの入室を制限または許可するとともに、Microsoft Teams が提供する他のミーティングオプションを制御することができます。

**ユーザー完了の自動同期を使用**

ユーザーによる自動的な完了の同期プロセスにより、Learning Manager管理者はMicrosoft Teamsミーティングの完了記録および記録用URLを自動で取得できます。

## Microsoft Teams の役割

複数の参加者が含まれるミーティングを開催する場合は、各参加者に役割を割り当てて、参加者がミーティングで何ができるかを把握できるようにすることができます。

次の2つの役割から選択できます。 **presenter** および **出席者**.

詳しくは、「  [Teams Meetingのロール – Microsoft](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

## Microsoft Teams コネクターの設定

>[!NOTE]
>
>マークされた項目 &lt;developer optional=&quot;&quot;> 以下はオプションであり、プロダクションテナントを持たないユーザーが、主にMicrosoftでトライアル/デベロッパーテナントを設定する場合に用いられます。 これらはチームの管理者によって既に実行されていることが多いため、オプションです。

## デベロッパーのE5 Microsoftアカウントを作成 &lt;developer optional=&quot;&quot;>

Office 365 E3またはOffice 365 E5を使用している場合は、Microsoft Teamsコネクタにアクセスできます。 推奨されるオプションはOffice 365 E5です。

* にアクセス [Microsoftプランページ](https://www.microsoft.com/en-in/microsoft-365/enterprise/compare-office-365-plans?&amp;ef_id=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;OCID=AID2100137_SEM_CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;lnkd=Google_O365SMB_Brand&amp;gclid=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE) . ウェブページで、E3またはE5アカウントを購入するか、「無料で試す」をクリックします。

* 必要な情報を入力し、アカウントを作成します。

>[!NOTE]
>
>アカウントでは、次の形式を使用する必要があります `<username>@<company name>.onmicrosoft.com`.

## Microsoft Teamsコネクタのアプリケーションを作成

1. にアクセス  [Microsoft Azure®ポータル](https://portal.azure.com/).
1. 前セクションで作成したMicrosoft E5アカウントでログインします。
1. 検索 **Azure Active Directory**.
1. クリック **[!UICONTROL アプリの登録]**.
1. クリック **[!UICONTROL 新規登録]**&#x200B;を選択し、以下の情報を入力してアプリケーションを登録します。

   1. **名前**  – 任意の名前。
   1. **サポートされているアカウントタイプ**  – 任意の組織ディレクトリ（Azure Active Directory – マルチテナント）のアカウント
   1. **リダイレクトURI （オプション）**  – 返信URLを示すオプションのフィールド

1. を **基本** 列で、統合時に用いられる以下のIDに注意してください。

   1. **アプリケーション（クライアント） ID**
   1. **ディレクトリ（テナント）ID**

1. クライアントの認証情報を検索して「 **[!UICONTROL 証明書または秘密の追加]**.
1. クリック **[!UICONTROL 新しいクライアントシークレット]** 次の詳細を追加します。

   1. **説明**  – 任意の名前を入力
   1. **有効期限**  – 任意の値に設定(推奨値：24か月 期限が超過すると新たなクライアントの認証情報が生成されることを確認）

統合時に用いられるクライアントシークレットを書き留めます。

## Microsoft Teamsコネクタのアクセス権限の取得

1. にアクセス  [Microsoft Azureポータル](https://portal.azure.com/).
1. 以前に作成したMicrosoft E5でログインします。
1. 検索 **Azure Active Directory**.
1. クリック **[!UICONTROL アプリの登録]**.
1. 前セクションで作成したアプリをクリックします。
1. クリック **[!UICONTROL API権限]**.
1. クリック **[!UICONTROL 権限を追加]**.
1. 選択 **[!UICONTROL Microsoft Graph]** > **[!UICONTROL アプリケーションの権限]** 次の権限を追加します。

   1. Chat.Read.All
   1. Directory.Read.All
   1. OnlineMeetingArtifact.Read.All
   1. OnlineMeetings.Read.All
   1. OnlineMeetings.ReadWrite.All
   1. User.Read.All

1. クリック **[!UICONTROL Adobeへの管理者アクセス権を付与]**.
1. クリック **[!UICONTROL アプリの役割]** > **[!UICONTROL アプリの役割を作成]**.
1. 次の値を入力します。

   1. **表示名** - API/許可名（例：Calendars.ReadWrite）

   1. **許可されるメンバーの種類**  – ユーザーとアプリケーションの両方を指定します（ユーザー/グループ+アプリケーション）。

   1. **値** - API/許可名（例：Calendars.ReadWrite）

   1. **説明** - API/許可名（例：Calendars.ReadWrite）

   1. **このアプリの役割を有効にしますか？**  – このチェックボックスを選択します。

1. 追加された9つのAPI/権限すべてに対して上記の手順を繰り返します。

## PowerShellスクリプトを使用してアクセスポリシーを構成する

PowerShellスクリプトを実行してMicrosoft Teamsコネクタのアプリケーションアクセスポリシーを構成するには、次の手順に従ってください  [文書](https://docs.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

これにより、コネクタから Microsoft Teams オンライン会議にアクセスできます。

>[!NOTE]
>
>また、すべてのアクティブなユーザーにLearning Manager作成者アプリから主催者の役割が割り当てられるよう、上記のオプション手順5も実行してください。 この操作が実行されないと、主催者に必要なアクセス権がユーザーに付与されないため、ミーティングを正しく作成できません(Microsoft APIでは、Teamsミーティングの主催者が作成者と見なされます)。

## Learning ManagerでのMicrosoft Teamsコネクタの設定

1. 統合管理者としてLearning Managerにサインインします。

1. 「コネクタ」ページで「Microsoft Teamsコネクタ」を選択し、 **[!UICONTROL Connect]**.

1. 次の値を入力します。

   1. **接続名**  – セッションの作成時に作成者に表示される名前を指定します。

   1. **Microsoft TeamsテナントID**  – 所定の値を入力します。

   1. **Microsoft TeamsクライアントID**  – 所定の値を入力します。

   1. **Microsoft Teamsクライアントシークレット**  – 所定の値を入力します。

   1. **Microsoft Teams管理者ユーザーの電子メール**  – デフォルトの主催者電子メールを入力します。 Learning Manager作成者アプリから主催者が明示的に選択されていない場合、このユーザー（通常はサービスユーザー）がミーティングの作成者となります。

## ユーザーへのライセンスの割り当て &lt;developer optional=&quot;&quot;>

1. アクセス [https://admin.microsoft.com/#/homepage](https://admin.microsoft.com/#/homepage).
1. クリック **[!UICONTROL ユーザー]** > **[!UICONTROL アクティブなユーザー]**.
1. クリック **[!UICONTROL ユーザーのその他のアクション]** ユーザーへのアクセス権を付与するMicrosoft Teamsに対して使用します。
1. クリック **[!UICONTROL 製品ライセンスの管理]**.
1. 電話会議機能のないOffice 365 E5のライセンスを有効にします。

## セッションの記録

セッションの記録に用いられる API は保護されています。 API にアクセスするには Microsoft にアクセスを申請する必要があります。 詳しくは、こちらを参照してください。  [文書](https://docs.microsoft.com/en-us/graph/teams-protected-apis).

文書には以下の記載があります。

*「これらの保護されたAPIへのアクセスをリクエストするには、次の手順を実行します  [リクエストフォーム](https://aka.ms/teamsgraph/requestaccess). アクセス申請は毎週水曜日に審査され、米国の主な休日を除き毎週金曜日に承認されます。休日期間中に提出された申請は、翌営業週に処理されます。 申請が承認されたかどうかを確認するには、翌営業週の月曜日にアプリケーションへのアクセスをテストしてください。」*

学習者には、VC コースの概要ページに記録用 URL が表示されます。

学習者の出席はコース終了の 30 分後にマークされます。

## よくある質問

+++誰が主催者およびプレゼンターになりますか？

参照：  [文書](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) Microsoft Teamsでサポートされている様々な役割や機能についてMicrofsoftから問い合わせます。

+++

+++主催者はLearning ManagerとMicrosoft Teamsの両方に登録されたユーザーでなければなりませんか？

はい。主催者は Learning Manager および Microsoft Teams の両方に登録されている必要があります。また統合管理アプリで設定されたMicrosoftテナントにも登録されていなければなりません。

+++

+++プレゼンターはLearning ManagerとMicrosoft Teamsの両方に登録されたユーザーであることが必要ですか？

はい。プレゼンターはLearning ManagerおよびMicrosoft Teamsの両方に登録されている必要があります。 プレゼンターにはAzure Active Directory IDが必要です（主催者と同じテナント、または他のテナントに登録できます）。 また、ミーティング中に主催者/既存プレゼンターが、匿名ユーザー（Active Directoryに登録されていない、ユーザー名のみでログインしたユーザー）をプレゼンターに指名することも可能です。

+++

+++Microsoft Teamsは会議、ウェビナー、ライブイベントを開催 そのうち Teams コネクターでサポートされているのはどれですか？

現在、Teamsコネクターでサポートされているのは、Microsoft Teams内の会議のみです。 詳しくは、こちらを参照してください。  [文書](https://docs.microsoft.com/en-us/microsoftteams/quick-start-meetings-live-events).

+++
