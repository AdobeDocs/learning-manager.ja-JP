---
description: Adobe Learning Manager で Microsoft Teams コネクターをインストール
jcr-language: en_us
title: Adobe Learning Manager で Microsoft Teams コネクターをインストール
contentowner: saghosh
exl-id: 68092187-ac69-4727-a3dc-f3047a1e164d
source-git-commit: 6192559436074c3270644850b202589961e7b81b
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 17%

---

# Adobe Learning Manager で Microsoft Teams コネクターをインストール

## 概要

Microsoft Teams®は、文書の共有、オンラインミーティング、その他ビジネスコミュニケーション機能全般をサポートする、チャットベースの持続的なコラボレーションプラットフォームです。

Adobe Learning Managerでは、Microsoft TeamsミーティングをLearning Managerに統合するために、バーチャル教室コネクターを使用しています。

Microsoft Teams のコネクターにより、Learning Manager と Microsoft Teams のシステムを接続することで、バーチャルミーティングを自動的に同期できます。Microsoft Teams コネクターの機能は以下のとおりです。

**Microsoft Teamsを使用してバーチャルセッションを設定する**

コネクターを用いることで、Adobe Learning Manager のアカウントと Microsoft Teams のアカウントを統合することができます。 統合されると Learning Manager の作成者は、Learning Manager で作成されたバーチャル教室モジュールのテクノロジーサービスプロバイダーとして、Microsoft Teams を使用することができます。

**Microsoft Teamsがバーチャルクラスルームに入るときに学習者の認証を許可する**

コネクターを使用することで、ミーティングの作成時にLearning Managerからミーティング主催者をMicrosoft Teamsとして設定できます。 ミーティング主催者はロビーを管理することで、ミーティングへの入室を制限または許可するとともに、Microsoft Teams が提供する他のミーティングオプションを制御することができます。

**ユーザー完了の自動同期を使用する**

ユーザーによる自動的な完了の同期プロセスにより、Learning Manager管理者はMicrosoft Teamsミーティングの完了記録および記録用URLを自動で取得できます。

## Microsoft Teams の役割

複数の参加者が含まれるミーティングを開催する場合は、各参加者に役割を割り当てて、参加者がミーティングで何ができるかを把握できるようにすることができます。

役割は&#x200B;**presenter**&#x200B;と&#x200B;**attendee**&#x200B;から選択できます。

詳細については、[Teams Meeting - Microsoftのロール](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)を参照してください。

## Microsoft Teams コネクターの設定

>[!NOTE]
>
>以下の&lt;開発者/オプション>とマークされている項目はオプションであり、プロダクションテナントを持たないユーザーが、主にMicrosoftでトライアル/開発者テナントを設定する場合に用いられます。 これらはチームの管理者によって既に実行されていることが多いため、オプションです。

## デベロッパーE5 Microsoftアカウントを作成&lt;デベロッパー/オプション>

Office 365 E3またはOffice 365 E5を使用している場合は、Microsoft Teamsコネクタにアクセスできます。 推奨されるオプションはOffice 365 E5です。

* [Microsoftプラン](https://www.microsoft.com/en-in/microsoft-365/enterprise/compare-office-365-plans?&ef_id=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&OCID=AID2100137_SEM_CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&lnkd=Google_O365SMB_Brand&gclid=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE)をご覧ください。 ウェブページで、E3またはE5アカウントを購入するか、「無料で試す」をクリックします。
* 必要な情報を入力し、アカウントを作成します。

>[!NOTE]
>
>アカウントは`<username>@<company name>.onmicrosoft.com`の形式を使用する必要があります。

## Microsoft Teamsコネクタのアプリケーションを作成

1. [Microsoft Azure®ポータル](https://portal.azure.com/)にアクセスします。
1. 前セクションで作成したMicrosoft E5アカウントでログインします。
1. **Azure Active Directory**&#x200B;を検索します。
1. [**[!UICONTROL アプリの登録]**]をクリックします。
1. **[!UICONTROL 新規登録]**&#x200B;をクリックし、以下の情報を入力してアプリケーションを登録してください：

   1. **名前** – 任意の名前
   1. **サポートされているアカウントの種類** – 任意の組織ディレクトリ（Azure Active Directory – マルチテナント）のアカウント
   1. **リダイレクトURI （任意）** – 返信URLを示す任意のフィールド

1. **Essentials**&#x200B;列に、統合時に用いられる以下のIDを入力します。

   1. **アプリケーション（クライアント） ID**
   1. **ディレクトリ（テナント） ID**

1. クライアントの資格情報を検索し、[**[!UICONTROL 証明書または秘密の追加]**]をクリックします。
1. **[!UICONTROL 新しいクライアントシークレット]**&#x200B;をクリックし、次の詳細を追加します：

   1. **説明** – 任意の名前を入力
   1. **有効期限** – 任意の値を設定します（推奨値は24か月です）。 期限が超過すると新たなクライアントの認証情報が生成されることを確認）

統合時に用いられるクライアントシークレットを書き留めます。

## Microsoft Teamsコネクタのアクセス権限の取得

1. [Microsoft Azureポータル](https://portal.azure.com/)にアクセスします。
1. 以前に作成したMicrosoft E5でログインします。
1. **Azure Active Directory**&#x200B;を検索します。
1. [**[!UICONTROL アプリの登録]**]をクリックします。
1. 前セクションで作成したアプリをクリックします。
1. **[!UICONTROL APIのアクセス許可]**&#x200B;をクリックします。
1. **[!UICONTROL [権限の追加]]**&#x200B;をクリックします。
1. **[!UICONTROL Microsoft Graph]**/**[!UICONTROL アプリケーションのアクセス許可]**&#x200B;を選択し、次のアクセス許可を追加します：

   1. Chat.Read.All
   1. Directory.Read.All
   1. OnlineMeetingArtifact.Read.All
   1. OnlineMeetings.Read.All
   1. OnlineMeetings.ReadWrite.All
   1. User.Read.All
   1. OnlineMeetingRecording.Read.All

1. [**[!UICONTROL Adobeに管理者アクセス権を付与]**]をクリックします。
1. **[!UICONTROL アプリの役割]** > **[!UICONTROL アプリの役割の作成]**&#x200B;をクリックします。
1. 次の値を入力します。

   1. **表示名** - API/許可名（例： Calendars.ReadWrite）

   1. **許可されたメンバーの種類** – ユーザーとアプリケーションの両方を指定します（ユーザー/グループ+アプリケーション）。

   1. **値** - API/許可名（例： Calendars.ReadWrite）。

   1. **説明** - API/許可名（例： Calendars.ReadWrite）

   1. **このアプリロールを有効にしますか？** – このチェックボックスを選択します。

1. 追加された9つのAPI/権限すべてに対して上記の手順を繰り返します。

## PowerShellスクリプトを使用してアクセスポリシーを構成する

PowerShellスクリプトを実行してMicrosoft Teamsコネクタのアプリケーションアクセスポリシーを構成するには、この[文書](https://docs.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy)に記載されている手順に従ってください。

これにより、コネクタから Microsoft Teams オンライン会議にアクセスできます。

>[!NOTE]
>
>また、すべてのアクティブなユーザーにLearning Manager作成者アプリから主催者の役割が割り当てられるよう、上記のオプション手順5も実行してください。 この操作が実行されないと、主催者に必要なアクセス権がユーザーに付与されないため、ミーティングを正しく作成できません(Microsoft APIでは、Teamsミーティングの主催者が作成者と見なされます)。

## Learning ManagerでのMicrosoft Teamsコネクタの設定

1. Learning Managerに&#x200B;**統合管理者**&#x200B;としてサインインします。

1. [コネクタ]ページで[Microsoft Teamsコネクタ]を選択し、[**[!UICONTROL 接続]**]をクリックします。

1. 次の値を入力します。

   1. **接続名** – セッションの作成中に作成者に表示される名前を入力します。

   1. **Microsoft TeamsテナントID** – 所定の値を入力します。

   1. **Microsoft TeamsクライアントID** – 所定の値を入力してください。

   1. **Microsoft Teamsクライアントシークレット** – 所定の値を入力してください。

   1. **Microsoft Teams管理者ユーザーの電子メール** – 既定の主催者電子メールを入力します。 Learning Manager作成者アプリから主催者が明示的に選択されていない場合、このユーザー（通常はサービスユーザー）がミーティングの作成者となります。

## ユーザーへのライセンスの割り当て&lt;開発者/オプション>

1. [https://admin.microsoft.com/#/homepage](https://admin.microsoft.com/#/homepage)にアクセスします。
1. **[!UICONTROL ユーザー]** > **[!UICONTROL アクティブなユーザー]**&#x200B;をクリックします。
1. Microsoft Teamsへのアクセスを提供するユーザーに対して、**[!UICONTROL ユーザーのその他のアクション]**&#x200B;をクリックします。
1. **[!UICONTROL [製品ライセンスの管理]]**&#x200B;をクリックします。
1. 電話会議機能のないOffice 365 E5のライセンスを有効にします。

<!--## Record a session

The API used for recording a session is a protected API. To access the API, you must request access from Microsoft. For more information, see this  [document](https://docs.microsoft.com/en-us/graph/teams-protected-apis).

In the document,

*"To request access to these protected APIs, complete the following  [request form](https://aka.ms/teamsgraph/requestaccess). We review access requests every Wednesday and deploy approvals every Friday, except during major holiday weeks in the U.S. Submissions during those weeks will be processed the following non-holiday week. To verify whether your request has been approved, test your application access on the next applicable Monday."*

For learners, the recording URL is displayed on the VC course overview page.

After 30 minutes of completing a course, the attendance for the learner gets marked. -->

## よくある質問

+++誰が主催者およびプレゼンターになりますか？

Microsoft Teamsでサポートされている役割と機能の詳細については、Microfsoftの[ドキュメント](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)を参照してください。

+++

+++主催者はLearning ManagerとMicrosoft Teamsの両方に登録されたユーザーでなければなりませんか？

はい。主催者は Learning Manager および Microsoft Teams の両方に登録されている必要があります。また統合管理アプリで設定されたMicrosoftテナントにも登録されていなければなりません。

+++

+++プレゼンターはLearning ManagerとMicrosoft Teamsの両方に登録されたユーザーであることが必要ですか？

はい。プレゼンターはLearning ManagerおよびMicrosoft Teamsの両方に登録されている必要があります。 プレゼンターにはAzure Active Directory IDが必要です（主催者と同じテナント、または他のテナントに登録できます）。 また、ミーティング中に主催者/既存プレゼンターが、匿名ユーザー（Active Directoryに登録されていない、ユーザー名のみでログインしたユーザー）をプレゼンターに指名することも可能です。

+++

+++Microsoft Teamsは会議、ウェビナー、ライブイベントを開催 そのうち Teams コネクターでサポートされているのはどれですか？

現在、Teamsコネクターでサポートされているのは、Microsoft Teams内の会議のみです。 詳細については、この[ドキュメント](https://docs.microsoft.com/en-us/microsoftteams/quick-start-meetings-live-events)を参照してください。

+++
