---
description: Microsoft Teams 向け Adobe Learning Manager アプリ
jcr-language: en_us
title: Microsoft Teams 向け Adobe Learning Manager アプリ
contentowner: saghosh
source-git-commit: 81dd3cecf7393c08434a70e15457d967a56df8d3
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 41%

---


# Microsoft Teams 向け Adobe Learning Manager アプリ

## 設定方法

MS Teams に ALM を設定するには 3 つのステップがあり、ALM 管理者と Microsoft Azure 管理者のサポートが必要です。 一部の組織では Azure 管理と MS Teams 管理を担当するスタッフが異なるため、MS Teams 管理者を別途任命することが必要です。

**ALM管理者 – 統合管理者の役割がTeamsアプリを承認**

統合管理者がMS Teamsアプリを承認すると、AdobeのLearning ManagerアプリがMS Teamsアプリストアで利用できるようになり、学習者はアプリにアクセスできるようになります。 ただし、このアプリには通知やサイレントログインの機能がなく、アプリを MS Teams で学習者用にピン留めできません。

**Microsoft Azure管理者がAzureダッシュボードでALMアプリの権限を承認**

Azure 管理者は、ALM アプリに必要な権限を承認する必要があります。 管理者が承認すると、ALM アプリから MS Teams に通知を送信することや、サイレントログインを実行することが可能になります。 サイレントログインの場合は、ブラウザーで Adobe Learning Manager にログインする必要がなくなります。

**MS Teams管理者がALMグループ版のポリシーを作成**

管理センターの MS Teams 管理者は、すべてのユーザーに対して ALM アプリをピン留めし、グローバルポリシーとして許可する必要があります。 ALM を社内で使用するのが特定のグループのみの場合、MS Teams 管理者はカスタムポリシーを選択し、ポリシーをその特定のグループにのみ適用する必要があります。

## 統合管理者の役割がTeamsアプリを承認

以下の手順を実行します。

1. 統合管理者アプリで、 **[!UICONTROL アプリケーション]** > **[!UICONTROL おすすめアプリ]**、を選択します **[!UICONTROL ALM Teamsアプリ]**.

   ![](assets/featuredapps.jpg)
   *ALM Teamsアプリを選択*

1. 画面の右上隅で、を選択します。 **[!UICONTROL 承認]**.

   ![](assets/integration_admin_approval_form.jpg)
   *アプリ設定ページで「承認」を選択します*

1. 選択 **[!UICONTROL OK]** をクリックします。

   ![](assets/integration_admin_approved_dialog_box.jpg)
   *承認後に「 OK 」を選択します*

1. 承認されると「外部アプリ」セクションに「ALM Teamsアプリ」が表示されます。

   ![](assets/integration_admin_external_apps.jpg)
   *ALM Teamsアプリがアプリページに表示されます*

これで、ユーザーがMS TeamsでALMアプリにアクセスできるようになりました。

## Microsoft Azure 管理者：Azure ダッシュボードでの ALM アプリの権限の承認

以下の手順を実行します。

1. Azure管理者として、Azureダッシュボードの「 Azure Active Directoryの管理」セクションに移動します。

   ![](assets/microsoft_azure.jpg)
   *Azureダッシュボードを起動*

1. 次のリンクを別のブラウザーウィンドウに貼り付けます。

   `https://login.microsoftonline.com/<tenantIdTobeReplaced>/oauth2/authorize?client_id=8d349d9f-bf59-4ece-8022-a41e87d81903&response_type=code&redirect_uri=https://learningmanager.adobe.com`

1. 上記のリンクで、次を置換します： `<tenantIdTobeReplaced>` テナントIDは、以下の概要ページで使用できます。 新しいURLを入力します。

1. AdobeのLearning ManagerアプリをAzureアプリケーションに追加します。

   ![](assets/microsoft_azure_dashboard.jpg)
   *Azureに追加*

1. 「エンタープライズアプリケーション」タブを選択し、「すべてのアプリケーション」を選択します。 そこにALMTeamsAppが表示されます。

   ![](assets/microsoft_azure_enterprise_applications.jpg)
   *ALMアプリを表示*

1. アプリをクリックして、「権限」タブに移動します。

   ![](assets/microsoft_azure_ALMTeamsNonProdApp.jpg)
   *「アクセス許可」タブの表示*

1. 「アクセス許可」タブで「 」を選択します。 **[!UICONTROL MSFTの管理者の同意を付与]**&#39;を追加して、ALMグループ版アプリの権限を付与します。

   ![](assets/microsoft_azure_ALMTeamsNonProdApp_permissions.jpg)
   *権限を選択*

1. 選択 **[!UICONTROL 承認]**.

   ![](assets/microsoft_azure_ALMTeamsNonProdApp_permission_request.jpg)
   *「承認」を選択します*

1. 付与されると、これらの権限により、ALMアプリはサイレントログインを許可し、MS Teamsアプリで学習者に通知を送信できるようになります。

   ![](assets/microsoft_azure_ALMTeamsNonProdApp_permission_request_granted.jpg)
   *アクセス権が付与されます*

## MS Teams 管理者：Teams アプリ向けのポリシーの作成

以下の手順を実行します。

1. MS Teams管理者として、管理センターで、Teamsアプリを学習者のTeamsアプリに追加するためのポリシーを作成します。

   ![](assets/microsoft_teams_admin_center.png)
   *ポリシーの作成*

1. 「ポリシーの設定」セクションに移動します。 グローバルポリシーを作成し、 **[!UICONTROL アプリを追加]** （「固定されたアプリ」サブセクション）。

   ![](assets/microsoft_teams_admin_center_add_installed_apps.png)
   *ポリシーの追加*

1. 次のダイアログで&#x200B;**[!UICONTROL 「Adobe Leaning Manager」]**&#x200B;を検索して、アプリを追加します。 これにより、Learning Manager Adobeが「インストール済みアプリ」セクションに追加されます。

   ![](assets/microsoft_teams_admin_center_installed_apps.png)
   *アプリをインストール*

1. このポリシーを保存します。 これにより、組織内のすべてのユーザーがアプリを使用できるようになります。

管理者はグローバルポリシーを使用せずに、カスタムポリシーを作成することも可能です。 AdobeのLearning Managerをそのカスタムポリシーに追加し、AdobeのLearning Managerにアクセスする必要があるユーザーグループにのみカスタムポリシーを適用します。
