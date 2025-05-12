---
jcr-language: en_us
title: Adobe Connect の統合
description: 作成者は、コースの作成プロセスで Adobe Connect を使用してバーチャルクラスルームコースを作成することができます。 Learning Manager アカウントで Adobe Connect を有効にするには、組織の管理者に連絡する必要があります。
contentowner: jayakarr
exl-id: 13458f93-9ea7-4aab-8b33-3c4f4dd5886d
source-git-commit: 857dddf46e3900fbe2db4e345da2d29050ef3c82
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 49%

---

# Adobe Connect の統合

組織の管理者は、Adobe Connect と統合できるように Learning Manager アカウントを設定できます。

## Adobe Connect {#configureadobeconnect}

1. 管理者ログインで、「 **[!UICONTROL 設定]** をクリックして、会社に関する基本的な情報を表示します。 左側のペインで&#x200B;**[!UICONTROL Adobe Connect]**&#x200B;をクリックします。

   ![](assets/left-pane.png)

   *左側のウィンドウで[Adobe Connect]を選択します*

1. **[!UICONTROL Adobe Connectの設定]**&#x200B;セクションで&#x200B;**[!UICONTROL 今すぐ設定]**&#x200B;リンクをクリックします。

   <!--![](assets/configure-now-connect.png)-->

1. 会社の Adobe Connect ドメイン名とログイン資格情報を入力します。

   ![](assets/adobeconnect-config.png)

   *ドメイン名と資格情報の追加*

   Adobe Connect URLの例：mycompany.adobeconnect.com\
   Adobe接続アカウントの管理者の電子メールIDを入力する必要があります。

   Learning Manager では、アドビがホストする Connect アカウントのみがサポートされます。例：&quot;.adobeconnect.com&quot;

1. **[!UICONTROL [統合]].**&#x200B;をクリックします

   電子メールIDの認証後、Connectが正常に統合されたというメッセージがLearning Managerに表示されます。 自動的に Adobe Connect を使用してバーチャルクラスルームコースを表示できるようになります。

   Adobe Connect アカウント管理者は、Adobe Connect の利用条件に同意する必要があります。これに同意していない場合、ログイン認証が失敗する可能性があります。Adobe Connect アカウントの作成後、アカウントに 1 回ログインします。初回ログイン時に、利用条件ページが表示されます。

   <!--![](assets/mail-confirmation.png)-->

## バーチャルクラスルームセッション情報の追加 {#addvirtualclassroomsessioninformation}

バーチャルクラスルームコースの作成者がセッション情報を提供していない場合、管理者はセッションの詳細を追加することができます。

管理者ログインで、VC コース名をクリックします。左ペインで&#x200B;**[!UICONTROL インスタンス]**&#x200B;をクリックし、**[!UICONTROL セッションの詳細]**&#x200B;をクリックします。  「セッションの詳細」ページの右隅にある「編集」アイコンをクリックして、セッション情報を追加します。

![](assets/session-creation-admin.png)

*バーチャルクラスルームセッション情報の追加*

バーチャルクラスルームモジュールまたはセッションを作成するために Adobe Learning Manager と Adobe Connect を統合することで、Connect アカウントは、ユースケースに十分な数の会議室と同時ユーザーを持つ会議室をサポートします。これらの会議室は、Learning Manager のバーチャルクラスルームモジュールをホストするために使用されます。Learning Manager 内のバーチャルクラスルームモジュールまたはセッションごとに、新しい Connect の会議室が Learning Manager によって動的に作成されます。

Adobe Learning Manager とは別に、Adobe Connect を購入する必要があります。

## 学習者の出席 {#learnersattendance}

バーチャルクラスルームコースのホストがセッションに出席しない場合、セッションに出席した学習者の出席は自動的に登録されません。 このような場合、管理者は出席を手動で記録できます。

バーチャルクラスルームコースをクリックし、次のページの左ペインで「出席」をクリックして出席を記録します。

## 多くのオーディエンスを対象としたAdobe Connectセミナーのサポート

Adobe Learning Managerでは、Connectでバーチャルクラスルームセッションを設定する際に、Adobe Connectからセミナールームを選択できます。 以前は、管理者は会議室タイプのみを選択できました。 有効なセミナーライセンスを持つ管理者はこの機能を使用して、ALM内で一度だけ、または大規模なイベント（最大1,500人の参加者）をスケジュールして管理できます。

Seminar Roomの詳細については、この[記事](https://helpx.adobe.com/adobe-connect/using/creating-seminars.html)を参照してください。

### セッション分析へのアクセスのサポート

インストラクターは、セッションダッシュボードに表示された新しいリンクから、完了したAdobe ConnectセッションのSession Analyticsにアクセスできます。

![](assets/adobe-connect-session-url.png)
_セッションURLの選択_

このリンクをクリックすると、Connectのセッション分析ダッシュボードが開き、セッションのエンゲージメントに関する詳細なインサイトが表示されます。
この機能は、Adobe Connectを通じて行われたセッションでのみ使用できます。 セッション分析には、次のものが含まれます。

* **[!UICONTROL 参加度]**:ライブセッションの全体的なパフォーマンスの概要
* **[!UICONTROL インタラクション]**：異なるポッド間の参加者のアクティビティの詳細な内訳
* **[!UICONTROL 出席者のアクティビティ]**：参加者のエンゲージメントの概要
* **[!UICONTROL レポートのダウンロード]**:ポッド固有のエンゲージメントデータに関するレポートをダウンロードするオプションです

![](assets/session-dashboard.png)
_セッションダッシュボード_

セッション分析の詳細については、この[記事](https://helpx.adobe.com/in/adobe-connect/using/session-dashboard.html)を参照してください。
