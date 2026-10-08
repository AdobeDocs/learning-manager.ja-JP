---
description: ズームコネクターとAdobe Learning Managerを連携させる方法を説明します
jcr-language: en_us
title: ズームコネクター
contentowner: mmanuel
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 2%
---

# Adobe Learning Managerのズームコネクター

## 概要

Adobe Learning ManagerのZoom コネクターは、Zoomとシームレスに連携して、ライブバーチャルクラスルームセッションを提供します。 この統合により、インストラクターはLearning Managerから直接Zoomミーティングをホストし、学習者を登録して、出席と完了データを追跡できます。 学習者は自動的に招待され、Adobe Learning Managerアカウントからセッションに参加できます。 セッションが終わると、出席とパフォーマンスのデータがAdobe Learning Managerに同期され、レポートとトラッキングが行われます。

## ズームコネクターの設定

ズームコネクターを設定するには：

1. Adobe Learning Managerに統合管理者としてログインします。
2. **ズーム**&#x200B;タイルにカーソルを合わせます。

   ![](assets/zoom-connector1.png)
   _Adobe Learning Managerでズームコネクターを構成する_

3. **Connect**&#x200B;を選択します。 ズームコネクター設定ページが開きます。
4. それぞれのフィールドに次のアカウント情報を入力します。 Zoomアカウントの管理者から、次の資格情報を取得できます。

   * 接続名
   * ZoomアカウントID
   * クライアント ID
   * クライアントシークレット
   * スーパー管理者のメールアドレス

   ![](assets/zoom-connector2.png)
   _構成の詳細を入力して、ズームコネクターを設定します_

5. **接続**&#x200B;を選択して統合を確立します。

>[!NOTE]
>
>ユーザーを有効にする場合、**学習者は、コネクターデータが正しく同期されるように、ZoomアカウントとAdobe Learning Managerアカウントの両方に同じメールアドレス**&#x200B;を使用する必要があります。

## Zoomコースの作成

接続が確立されると、次のようになります。

1. **作成者**&#x200B;としてログインし、新しいバーチャルクラスルームコースを作成します。
2. コースの作成時に会議システムとして&#x200B;**Zoom**&#x200B;を選択します。
3. 管理者、マネージャー、またはセルフ登録を通じて、学習者をコースに割り当てます。
4. 登録時に、学習者はコースの詳細を記載した電子メールを受け取ります。
5. 学習者は自分のAdobe Learning Managerアカウントにログインしてコースにアクセスし、Zoomセッションに参加できます。

## 出席と完了の追跡

仮想セッションの終了後は、次の操作を行います。

* Adobe Learning Managerは、Zoomから自動的に完了ステータスを受け取ります。
* 管理者は、Adobe Learning Managerで出席とスコア付けのレポートを表示して、学習者の参加とパフォーマンスを追跡できます。

## Zoomサーバー間OAuthアプリの作成

Adobe Learning ManagerでZoom コネクターを使用するには、Zoomサーバー間OAuthアプリを作成し、必要なスコープを設定する必要があります。

### 必要なOAuth範囲

Zoomでアプリケーションを作成する場合は、次のスコープが選択されていることを確認してください。

| 必要な機能 | このキーワードを検索 | 次に選択 |
|---|---|---|
| すべてのユーザーミーティングを表示 | 会議 | `meeting:read:meeting:admin, meeting:read:list_meetings:admin` |
| すべてのユーザーミーティングを表示/管理 | 会議 | `meeting:update:meeting:admin, meeting:delete:meeting:admin, meeting:write:meeting:admin` |
| レポートデータを表示 | レポート | `report:read:meeting:admin, report:read:user:admin` （エンドポイントに一致するものを選択してください。） |
| すべてのユーザー情報を表示 | user | `user:read:user:admin, user:read:list_users:admin` |
| ユーザーの管理 | user | `user:update:user:admin, user:write:user:admin` |
| 会議登録者の追加 | 登録者 | `meeting:write:registrant:admin` |
| すべての会議登録者を一覧表示する | 登録者 | `meeting:read:list_registrants:admin` |
| サブアカウントミーティング | 会議+ :masterの検索 | `meeting:write:meeting:master` |
| ミーティング参加者レポート | 参加者 | `report:read:list_meeting_participants:admin` |

