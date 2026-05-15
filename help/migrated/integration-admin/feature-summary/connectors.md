---
description: ALMでサポートされる各コネクタの概要
jcr-language: en_us
title: ALM対応コネクタの概要
contentowner: mmanuel
source-git-commit: bd80ca31ff633e21ec81e717772e43989f0d9aae
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 6%

---


# Adobe Learning Managerコネクタ

## 概要

Adobe Learning Manager(ALM)は、サードパーティ製アプリケーションやエンタープライズシステムとシームレスに統合できる包括的なコネクタスイートを提供します。 これらのコネクターは、学習管理システムと外部プラットフォームを橋渡しする役割を果たし、自動化されたデータ同期、ユーザー管理、コンテンツの読み込み、学習記録の書き出しを促進します。

このドキュメントは、組織の学習エコシステムに適切なコネクタを理解して選択するための完全なリファレンスガイドとして機能します。 人事システム、eコマースプラットフォーム、仮想ミーティングツール、ビジネスインテリジェンスソリューションとの統合を検討しているかどうか。

Adobe Learning Managerでサポートされているコネクタの一覧については、左側の目次のこの記事の下にネストされているコネクタの記事を参照してください。

>[!NOTE]
>
>この機能は、FedRAMP認定の環境でも部分的に利用できます。 詳細については、[FedRAMP環境での機能の可用性](/help/migrated/feature-availability-in-fedramp-authorized-environment.md)を参照してください。

>[!NOTE]
>
>2022年11月リリースのAdobe Learning Managerでは、Zoomは2023年6月までの[JWT認証](https://developers.zoom.us/docs/internal-apps/s2s-oauth/)を廃止しました。 このため、JWT を使用した Zoom コネクターは前述の期日まで利用可能ですが、アカウントの機能を置き換えるためにサーバー間 OAuth アプリを作成することをお勧めします。 新しい接続では、デフォルトで Zoom OAuth 認証が使用されます。

## コネクタカテゴリ

Adobe Learning Managerコネクタは、主な目的と統合機能に基づいて、いくつかの機能的なカテゴリに分類できます。

| カテゴリ | 目的 | コネクタの例 |
|---------|--------|-------------------|
| データ転送 | ファイル・ベースのデータ交換と一括操作 | FTP,カスタムFTP, Box |
| バーチャルクラスルーム | ライブトレーニングとミーティングの統合 | Microsoft Teams、ズーム、Adobe Connect |
| Enterprise Systems | 人事およびビジネスシステムの統合 | Workday、Salesforce、ADFS |
| コンテンツプラットフォーム | 外部学習コンテンツの統合 | LinkedIn Learning、Harvard ManageMentor、getAbstract |
| Analytics &amp; BI | レポート作成とデータの視覚化 | Power BI、トレーニングデータアクセス |
| 認証 | ID管理とセキュリティ | ADFS（SSO機能） |
| eコマースとマーケティング | 販売とマーケティングの統合 | Adobe Commerce、Marketo Engage |

## データ転送およびﬁle管理コネクタ

これらのコネクタは、ﬁle転送プロトコルを介した自動データ交換を容易にし、一括操作とシステム間通信を可能にします。

### Adobe Learning Manager FTPコネクタ

FTPコネクターを使用すると、広く採用されているファイル転送プロトコルを使用して、Adobe Learning Managerと外部システム間のデータ同期を自動化できます。 このコネクタは、セキュリティを強化するために、SFTP(SSH File Transfer Protocol)やFTPS(FTP Secure)などの安全なバリエーションをサポートしています。

#### 主な機能：

- Adobe Learning Managerとリモートサーバー間でﬁをアップロードおよびダウンロードします。
- ユーザー情報とトレーニング記録のデータ交換を自動化
- セキュアなﬁle転送プロトコル(SFTP、FTPS)のサポート。
- サイズの大きいデータセットのバッチ処理

詳細については、[FTPコネクタ](/help/migrated/integration-admin/feature-summary/ftp-connector.md)を参照してください。

### カスタムFTPコネクタ

カスタムFTPコネクタは、構造化データ形式やxAPIステートメント交換をサポートし、より高度なﬁル転送機能を提供します。 このコネクタは、データ交換プロセスをより詳細に制御する必要がある組織向けに設計されています。

#### 主な機能：

- 構造化されたCSV ﬁルを介してユーザーデータを読み込みおよび書き出します。
- 学習記録とxAPIステートメントを処理します。
- 指定されたFTPフォルダーからの自動ﬁle処理。
- 機密データ転送のための拡張セキュリティ機能。

詳細については、[カスタムFTPコネクタ](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md)を参照してください。

### Box コネクター

Boxコネクターは、Boxのクラウドストレージプラットフォームを活用して、外部システムとAdobe Learning Managerの間のシームレスなデータ同期を容易にします。 このコネクターは、既にBoxを使用してﬁル管理を行っている組織にとって特に便利です。

#### 主な機能：

- クラウドベースのﬁleストレージと同期。
- CSVデータの自動処理。
- 既存のBoxワークフローﬂの統合。
- 指定フォルダからのリアルタイムのデータ更新。

詳細については、「[Box コネクタ](/help/migrated/integration-admin/feature-summary/box-connector.md)」を参照してください。

## バーチャルクラスルームおよび会議コネクタ

これらのコネクターは、Adobe Learning Managerを人気のビデオ会議やバーチャルミーティングプラットフォームと統合し、ライブトレーニングセッションをシームレスに提供します。

### Microsoft Teams コネクター

Microsoft Teamsコネクタは、Teamsの会議機能と直接統合することで、Adobe Learning Managerを包括的なバーチャルクラスルームソリューションに変えます。 このコネクタは、Microsoft 365エコシステムを使用する組織に不可欠です。

#### 主な機能：

- バーチャルクラスルームセッションをAdobe Learning Managerから直接スケジュールできます。
- チーム会議の自動作成と管理。
- 個別の会議リンクを使用せずに、シームレスに学習者にアクセスできます。

詳細については、[MS Teamsコネクター](/help/migrated/integration-admin/feature-summary/install-microsoft-teams-connector.md)を参照してください。

### Zoomコネクタ

Zoomコネクターを使用すると、Zoomの強力なビデオ会議機能をAdobe Learning Manager内で直接活用でき、インストラクターと学習者の両方にシームレスなエクスペリエンスを提供できます。

#### 主な機能：

- Adobe Learning ManagerからZoomのダイレクトミーティングのスケジュールを設定。
- 会議リンクの生成と配布を自動化
- リアルタイムの出席の監視。
- 録音管理と再生の統合。
- インタラクティブセッションのブレイクアウトルームのサポート。

詳細については、[Zoomコネクタ](/help/migrated/integration-admin/feature-summary/zoom-connector.md)を参照してください。

### Adobe Connectコネクタ

Adobe Connectコネクタは、インタラクティブなオンライン学習体験のための高度な機能を備えた、Adobe独自のバーチャルクラスルームプラットフォームとﬀの深い統合を提供します。

#### 主な機能：

- 高度なインタラクティブ機能（ポーリング、クイズ、ブレイクアウト）。
- 高品質の画面共有およびプレゼンテーションツール。
- 包括的なセッション録音と再生。
- モバイルに最適化されたバーチャルクラスルームのエクスペリエンス。

詳細については、[Adobe Connectコネクタ](/help/migrated/integration-admin/feature-summary/adobe-connect-connector.md)を参照してください。

## エンタープライズシステム統合コネクタ

これらのコネクターを使用することで、Adobe Learning Managerは基幹業務システムと連携し、ユーザー管理の自動化とデータの同期の効率化を実現できます。

### Workday コネクタ

Workdayコネクタは、人事システムとLearning Management Platformの間にシームレスなブリッジを構築し、従業員の記録、組織構造、ロール割り当てが両方のシステム間で同期された状態を維持します。

#### 主な機能：

- Workdayからの自動ユーザープロビジョニング。
- リアルタイムの従業員データ同期。
- 組織階層マッピング。
- ロールベースの学習割り当ての自動化。

詳細については、[Workdayコネクタ](/help/migrated/integration-admin/feature-summary/workday-connector.md)を参照してください。

### Salesforce コネクタ

Salesforceコネクターを使用すると、組織は顧客関係管理システムと学習イニシアチブを統合し、セールストレーニング、顧客教育、パフォーマンス追跡の機会を創出できます。

#### 主な機能：

- Salesforceからの自動ユーザーインポート。
- カスタムデータﬁeldマッピング。
- Salesforceへの学習記録の書き出し。
- セールスパフォーマンスとトレーニングの完了の相関関係。
- お客様教育プログラムの管理

詳細については、[Salesforceコネクタ](/help/migrated/integration-admin/feature-summary/salesforce-connector.md)を参照してください。

### ADFS （Active Directoryフェデレーションサービス）コネクタ

ADFSコネクターを使用すると、エンタープライズレベルの認証と承認を実装して、既存のActive Directory資格情報を使用してAdobe Learning Managerにアクセスできます。

#### 主な機能：

- シングルサインオン(SSO)の実装
- エンタープライズセキュリティコンプライアンス
- シームレスなユーザー認証
- 自動ユーザー読み込み
- スケジュールを設定する機能
- フィルター機能

詳細については、[ADFSコネクタ](/help/migrated/integration-admin/feature-summary/adfs-connector.md)を参照してください。

## コンテンツと学習プラットフォームコネクタ

これらのコネクターは、外部コンテンツライブラリと専用の学習プラットフォームを統合して、学習カタログを拡張します。

### LinkedIn Learning コネクタ

linkedInラーニングコネクターを使用すると、LinkedInのプロフェッショナル向け開発コースの豊富なライブラリにアクセスして、業界をリードする外部コンテンツで社内トレーニングを補完できます。

#### 主な機能：

- linkedIn学習の完全なコースカタログにアクセスできます。
- 自動コース検出および読み込み。
- Adobe Learning Manager内での学習者の進行状況のトラッキング。

詳細については、[LinkedInコネクタ](/help/migrated/integration-admin/feature-summary/linkedin-learning-connector.md)を参照してください。

### Harvard ManageMentor コネクタ

Harvard ManageMentorコネクタは、トップクラスのリーダーシップとマネージメントに関するトレーニングコンテンツをお客様のAdobe Learning Manager環境に直接提供し、Harvard Business Schoolの著名な教育機関リソースへのアクセスを可能にします。

#### 主な機能：

- ハーバードビジネススクールのプレミアムコンテンツアクセス。
- 管理およびリーダーシップ開発モジュール。
- シームレスなコンテンツの読み込みと整理

詳細については、[Harvard ManageMentorコネクタ](/help/migrated/integration-admin/feature-summary/harvard-managementor-connector.md)を参照してください。

### getAbstractコネクタ

getAbstractコネクターを使用すると、ビジネス帳簿の簡潔な概要やプロフェッショナルな洞察にアクセスでき、組織は消化しやすいコンテンツ形式を通じて継続的ﬀな学習を行うことができます。

#### 主な機能：

- ビジネス帳簿の概要と洞察にアクセスします。
- 使用状況データの追跡とレポート。
- 完了記録の自動作成

詳細については、[getAbstractコネクタ](/help/migrated/integration-admin/feature-summary/getabstract-connector.md)を参照してください。

## ビジネスインテリジェンスと分析コネクタ

これらのコネクターを使用すると、学習データを外部の分析プラットフォームと統合することで、高度なレポート機能、データ視覚化機能、ビジネスインテリジェンス機能を利用できます。

### Power BI コネクター

Power BIコネクタは、Microsoftの強力なビジネスインテリジェンスプラットフォームと学習指標を自動的に同期させ、学習データを実用的なビジネスインサイトに変換します。

#### 主な機能：

- リアルタイムの学習データ同期：
- カスタムダッシュボードの作成と管理。
- 高度なデータ可視化とレポート作成。
- 学習者のトランスクリプトとスキルレポートの統合。

詳細については、「[Power BI コネクタ](/help/migrated/integration-admin/feature-summary/power-bi-connector.md)」を参照してください。

### Training Data Access コネクタ

トレーニングデータアクセスコネクタを使用すると、トレーニングデータやコース情報へのAPIアクセスを提供することで、組織はカスタム学習インターフェイスやヘッドレス学習体験を作成できます。

**主な機能：**

- コースおよび学習パスデータへのパブリックAPIアクセス。
- カスタムユーザーインターフェイス開発サポート。
- ヘッドレス学習体験の作成。
- 高度な検索ﬁフィルタリング機能。

詳細については、[トレーニングデータアクセスコネクタ](/help/migrated/integration-admin/feature-summary/training-data-access-connector.md)を参照してください。

## eコマースおよびマーケティングコネクタ

これらのコネクターにより、学習コンテンツの収益化とマーケティング自動化プラットフォームとの統合が可能になります。

### Adobe Commerce connector

Adobe Commerceコネクタにより、Adobe Learning Managerは包括的なラーニングコマースプラットフォームに変わり、完全に統合されたeコマースのエクスペリエンスを通じて、コース、資格認定ﬁ、トレーニングプログラムを販売できるようになります。

**主な機能：**

- シームレスなeコマースプラットフォーム統合。
- コースカタログと価格管理。
- 支払い処理と登録を自動化

詳細については、[Adobe Commerceコネクタ](/help/migrated/integration-admin/feature-summary/adobe-commerce-connector.md)を参照してください。

### Adobe Marketo Engage コネクター

Marketo Engageコネクタは、学習活動とマーケティングキャンペーンの間に強力な相乗効果を生み出し、企業が教育を活用して、見込み客の育成と顧客開拓を行えるようにします。

#### 主な機能：

- リードの自動作成と更新。
- マーケティングインサイトのための学習活動の追跡。
- コースの登録および完了イベントがトリガーされます。

詳細については、[Marketo Engageコネクタ](/help/migrated/integration-admin/feature-summary/marketo-engage-connector.md)を参照してください。
