---
description: ALMでサポートされる各コネクターの概要
jcr-language: en_us
title: Adobe Learning Managerのコネクターの概要
contentowner: mmanuel
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '1426'
ht-degree: 6%
---

# コネクター

## 概要

Adobe Learning Manager(ALM)は、サードパーティ製アプリケーションやエンタープライズシステムとシームレスに統合できる包括的なコネクタースイートを提供します。 これらのコネクターは、学習管理システムと外部プラットフォームを橋渡しする役割を果たし、データ同期、ユーザー管理、コンテンツの読み込み、学習記録の書き出しを自動化します。

このドキュメントは、組織の学習エコシステムに適したコネクターを理解して選択するための完全なリファレンスガイドとして機能します。 人事システム、eコマースプラットフォーム、仮想ミーティングツール、ビジネスインテリジェンスソリューションとの統合を検討しているかどうか。

Adobe Learning Managerでサポートされているコネクターの一覧については、左側の目次のこの記事の下にネストされているコネクターの記事を参照してください。

>[!NOTE]
>
>この機能は、FedRAMP認定の環境でも部分的に利用できます。 詳細については、[FedRAMP環境での機能の可用性](/help/migrated/feature-availability-in-fedramp-authorized-environment.md)を参照してください。

>[!NOTE]
>
>2022年11月リリースのAdobe Learning Managerでは、Zoomは2023年6月までの[JWT認証](https://developers.zoom.us/docs/internal-apps/s2s-oauth/)を廃止しました。 このため、JWT を使用した Zoom コネクターは前述の期日まで利用可能ですが、アカウントの機能を置き換えるためにサーバー間 OAuth アプリを作成することをお勧めします。 新しい接続では、デフォルトで Zoom OAuth 認証が使用されます。

## コネクターのカテゴリ

Adobe Learning Manager コネクターは、その主な目的と統合機能に基づいて、いくつかの機能的なカテゴリに分類できます。

| カテゴリ | 目的 | コネクターの例 |
|---------|--------|-------------------|
| データ転送 | ファイル・ベースのデータ交換と一括操作 | FTP,カスタムFTP, Box |
| バーチャルクラスルーム | ライブトレーニングとミーティングの統合 | Microsoft Teams、ズーム、Adobe Connect |
| Enterprise Systems | 人事およびビジネスシステムの統合 | Workday、Salesforce、ADFS |
| コンテンツプラットフォーム | 外部学習コンテンツの統合 | LinkedIn Learning、Harvard ManageMentor、getAbstract |
| Analytics &amp; BI | レポート作成とデータの視覚化 | Power BI、トレーニングデータアクセス |
| 認証 | ID管理とセキュリティ | ADFS（SSO機能） |
| eコマースとマーケティング | 販売とマーケティングの統合 | Adobe Commerce、Marketo Engage |

## データ転送およびﬁle管理コネクター

これらのコネクターは、ﬁle転送プロトコルを介した自動データ交換を容易にし、一括操作やシステム間の通信を可能にします。

### ADOBE LEARNING MANAGER FTP コネクター

FTP コネクターを使用すると、広く採用されているファイル転送プロトコルを使用して、Adobe Learning Managerと外部システム間のデータ同期を自動化できます。 このコネクターは、セキュリティを強化するために、SFTP(SSH File Transfer Protocol)やFTPS(FTP Secure)などの安全なバリアントをサポートします。

#### 主な機能：

- Adobe Learning Managerとリモートサーバー間でﬁをアップロードおよびダウンロードします。
- ユーザー情報とトレーニング記録のデータ交換を自動化
- セキュアなﬁle転送プロトコル(SFTP、FTPS)のサポート。
- サイズの大きいデータセットのバッチ処理

詳細については、[FTP コネクター](/help/migrated/integration-admin/feature-summary/ftp-connector.md)を参照してください。

### カスタムFTP コネクター

カスタムFTP コネクターは、構造化データフォーマットとxAPIステートメント交換をサポートし、より高度なﬁle転送機能を提供します。 このコネクターは、データ交換プロセスをより詳細に制御する必要がある企業向けに設計されています。

#### 主な機能：

- 構造化されたCSV ﬁルを介してユーザーデータを読み込みおよび書き出します。
- 学習記録とxAPIステートメントを処理します。
- 指定されたFTPフォルダーからの自動ﬁle処理。
- 機密データ転送のための拡張セキュリティ機能。

詳細については、[カスタムFTP コネクター](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md)を参照してください。

### Box コネクター

Boxコネクターは、Boxのクラウドストレージプラットフォームを活用して、外部システムとAdobe Learning Managerの間のシームレスなデータ同期を容易にします。 このコネクターは、既にBoxを使用してﬁル管理を行っている場合に特に便利です。

#### 主な機能：

- クラウドベースのﬁleストレージと同期。
- CSVデータの自動処理。
- 既存のBoxワークフローﬂの統合。
- 指定フォルダからのリアルタイムのデータ更新。

詳細については、「[Box コネクタ](/help/migrated/integration-admin/feature-summary/box-connector.md)」を参照してください。

## バーチャルクラスルームとミーティングのコネクター

これらのコネクターは、Adobe Learning Managerを人気のビデオ会議やバーチャルミーティングプラットフォームと統合し、ライブトレーニングセッションをシームレスに提供します。

### Microsoft Teams コネクター

コネクターは、Adobe Learning Managerをチームの会議機能と直接統合することで、包括的なバーチャルクラスルームソリューションに変形します。 このコネクターは、Microsoft 365エコシステムを使用する組織に不可欠です。

#### 主な機能：

- バーチャルクラスルームセッションをAdobe Learning Managerから直接スケジュールできます。
- チーム会議の自動作成と管理。
- 個別の会議リンクを使用せずに、シームレスに学習者にアクセスできます。

詳細については、[MS Teams コネクター](/help/migrated/integration-admin/feature-summary/install-microsoft-teams-connector.md)を参照してください。

### ズームコネクター

Zoom コネクターを使用すると、Zoomの強力なビデオ会議機能をAdobe Learning Manager内で直接活用できます。これにより、インストラクターと学習者の両方がシームレスにビデオ会議を楽しむことができます。

#### 主な機能：

- Adobe Learning ManagerからZoomのダイレクトミーティングのスケジュールを設定。
- 会議リンクの生成と配布を自動化
- リアルタイムの出席の監視。
- 録音管理と再生の統合。
- インタラクティブセッションのブレイクアウトルームのサポート。

詳細については、[コネクターのズーム](/help/migrated/integration-admin/feature-summary/zoom-connector.md)を参照してください。

### コネクター

コネクターは、Adobe独自のバーチャルクラスルームプラットフォームと緊密に連携し、インタラクティブなオンライン学習体験を実現する高度な機能をﬀ備えています。

#### 主な機能：

- 高度なインタラクティブ機能（ポーリング、クイズ、ブレイクアウト）。
- 高品質の画面共有およびプレゼンテーションツール。
- 包括的なセッション録音と再生。
- モバイルに最適化されたバーチャルクラスルームのエクスペリエンス。

詳細については、[Adobe Connect コネクター](/help/migrated/integration-admin/feature-summary/adobe-connect-connector.md)を参照してください。

## エンタープライズシステム統合のコネクター

これらのコネクターにより、Adobe Learning Managerは基幹業務システムと連携し、自動化されたユーザー管理と組織のデータ同期を実現します。

### Workday コネクタ

コネクターは、人事システムとLearning Management Platformの間にシームレスなブリッジを構築し、社員の記録、組織構造、ロール割り当てが両方のシステム間で同期された状態を維持します。

#### 主な機能：

- Workdayからの自動ユーザープロビジョニング。
- リアルタイムの従業員データ同期。
- 組織階層マッピング。
- ロールベースの学習割り当ての自動化。

詳細については、[Workday コネクター](/help/migrated/integration-admin/feature-summary/workday-connector.md)を参照してください。

### Salesforce コネクタ

Salesforceのコネクターを利用すると、カスタマーリレーションシップ管理システムとラーニングイニシアチブを統合し、セールストレーニング、カスタマー教育、パフォーマンス追跡の機会を得ることができます。

#### 主な機能：

- Salesforceからの自動ユーザーインポート。
- カスタムデータﬁeldマッピング。
- Salesforceへの学習記録の書き出し。
- セールスパフォーマンスとトレーニングの完了の相関関係。
- お客様教育プログラムの管理

詳細については、[Salesforce コネクター](/help/migrated/integration-admin/feature-summary/salesforce-connector.md)を参照してください。

### ADFS （Active Directoryフェデレーションサービス） コネクター

ADFS コネクターを使用すると、エンタープライズレベルの認証と承認を実装して、既存のActive Directory資格情報を使用してAdobe Learning Managerにアクセスできます。

#### 主な機能：

- シングルサインオン(SSO)の実装
- エンタープライズセキュリティコンプライアンス
- シームレスなユーザー認証
- 自動ユーザー読み込み
- スケジュールを設定する機能
- フィルター機能

詳細については、[ADFS コネクター](/help/migrated/integration-admin/feature-summary/adfs-connector.md)を参照してください。

## コンテンツとラーニングプラットフォームのコネクター

これらのコネクターは、外部コンテンツライブラリと専用の学習プラットフォームを統合して、学習カタログを拡張します。

### LinkedIn Learning コネクタ

linkedInラーニングコネクターでは、LinkedInのプロフェッショナル育成コースの豊富なライブラリにアクセスでき、企業は社内向けトレーニングを業界をリードする社外コンテンツで補うことができます。

#### 主な機能：

- linkedIn学習の完全なコースカタログにアクセスできます。
- 自動コース検出および読み込み。
- Adobe Learning Manager内での学習者の進行状況のトラッキング。

詳細については、[LinkedIn コネクター](/help/migrated/integration-admin/feature-summary/linkedin-learning-connector.md)を参照してください。

### Harvard ManageMentor コネクタ

Harvard ManageMentor コネクターは、トップクラスのリーダーシップとマネジメントに関するトレーニングコンテンツをお客様のAdobe Learning Manager環境に直接提供し、Harvard Business Schoolの著名な教育機関リソースへのアクセスを可能にします。

#### 主な機能：

- ハーバードビジネススクールのプレミアムコンテンツアクセス。
- 管理およびリーダーシップ開発モジュール。
- シームレスなコンテンツの読み込みと整理

詳細については、[Harvard ManageMentor コネクター](/help/migrated/integration-admin/feature-summary/harvard-managementor-connector.md)を参照してください。

### getAbstract コネクター

getAbstractコネクターは、簡潔なビジネス書のまとめや専門的な洞察にアクセスし、消化しやすいコンテンツ形式を通じて継続的な学習をﬀ可能にします。

#### 主な機能：

- ビジネス帳簿の概要と洞察にアクセスします。
- 使用状況データの追跡とレポート。
- 完了記録の自動作成

詳細については、[getAbstract コネクター](/help/migrated/integration-admin/feature-summary/getabstract-connector.md)を参照してください。

## Business Intelligenceと分析のコネクター

これらのコネクターは、学習データを外部の分析プラットフォームと統合することで、高度なレポート作成機能、データビジュアライゼーション機能、ビジネスインテリジェンス機能を実現します。

### Power BI コネクター

コネクターは、Microsoftの強力なビジネスインテリジェンスプラットフォームと学習指標を自動的に同期させることで、学習データを実用的なビジネスインサイトに変形します。

#### 主な機能：

- リアルタイムの学習データ同期：
- カスタムダッシュボードの作成と管理。
- 高度なデータ可視化とレポート作成。
- 学習者のトランスクリプトとスキルレポートの統合。

詳細については、「[Power BI コネクタ](/help/migrated/integration-admin/feature-summary/power-bi-connector.md)」を参照してください。

### Training Data Access コネクタ

トレーニングデータアクセスコネクターを使用すると、トレーニングデータやコース情報へのAPIアクセスを提供することで、カスタム学習インターフェイスやヘッドレスラーニングエクスペリエンスを構築できます。

**主な機能：**

- コースおよび学習パスデータへのパブリックAPIアクセス。
- カスタムユーザーインターフェイス開発サポート。
- ヘッドレス学習体験の作成。
- 高度な検索ﬁフィルタリング機能。

詳細については、[トレーニングデータアクセスコネクター](/help/migrated/integration-admin/feature-summary/training-data-access-connector.md)を参照してください。

## eコマースとマーケティングのコネクター

これらのコネクターにより、学習コンテンツの収益化とマーケティング自動化プラットフォームとの統合が可能になります。

### Adobe Commerce connector

コネクターは、Adobe Learning Managerを包括的なlearning commerceプラットフォームに変形し、完全に統合されたeコマース体験を通じて、コース、資格認定ﬁ、トレーニングプログラムを販売できるようにします。

**主な機能：**

- シームレスなeコマースプラットフォーム統合。
- コースカタログと価格管理。
- 支払い処理と登録を自動化

詳細については、[Adobe Commerce コネクター](/help/migrated/integration-admin/feature-summary/adobe-commerce-connector.md)を参照してください。

### Adobe Marketo Engage コネクター

コネクターは、学習活動とマーケティングキャンペーンの間に強力な相乗効果を生み出し、企業が教育エンゲージメントを活用して、見込み客の育成と顧客開拓を行えるようにします。

#### 主な機能：

- リードの自動作成と更新。
- マーケティングインサイトのための学習活動の追跡。
- コースの登録および完了イベントがトリガーされます。

詳細については、[コネクター](/help/migrated/integration-admin/feature-summary/marketo-engage-connector.md)を参照してください。
