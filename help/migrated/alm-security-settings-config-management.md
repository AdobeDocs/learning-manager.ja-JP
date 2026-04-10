---
title: Adobe Learning Manager – セキュリティ設定と構成管理
description: この文書では、Adobe Learning Managerの管理アカウントタイプ、セキュリティ関連の設定、推奨されるセキュリティのデフォルト設定、API機能、書き出し機能、設定比較方法、公開方法、およびバージョン履歴について説明します。 また、特権アカウントの動作方法、セキュリティへの影響、およびプラットフォーム全体で構成管理がどのようにサポートされているかについて、詳細なガイダンスを提供します。
jcr-language: en-us
exl-id: a2e34104-c417-407f-af85-9f3f4b2a9fcb
source-git-commit: 3188d7f5593aeee87978e1e46456f01e1f41d57b
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 0%

---

# セキュリティ設定と構成管理

このガイドでは、Adobe Learning Manager(ALM)に関するFedRAMP Recommendations（FRR-RSC-03からFRR-RSC-08）への対応について詳しく説明します。 ここでは、セキュリティのベストプラクティス、推奨される安全なデフォルト、および特権アカウント設定を監査、書き出し、および管理するためのツールについて説明します。 このドキュメントは、管理者とコンプライアンスチームがALMアカウントの安全な設定と管理を行うために作成されています。

また、ALMがFedRAMP標準を満たしている、または部分的に満たしている領域についても説明します。また、Adobe Experience Leagueで利用可能なサポートドキュメントやリソースについても触れています。

+++Adobe Learning Managerでカスタム管理者または統合管理者のみが操作できるセキュリティ関連の設定とそのセキュリティへの影響

Adobe Learning Managerの2つの特権アカウントタイプ – カスタム管理者と統合管理者。 それぞれに、セキュリティ関連の設定が定義されており、その意味が文書化されています。

**カスタム管理者 – 管理者が操作できるもの**:

* カスタムの役割は、ALM管理者/ユーザー/カスタムの役割で、完全な管理者によって構成されます。 カスタム管理者には、アカウント権限（アナウンス、ゲーミフィケーション、スキル、ユーザー管理）、機能権限（カタログ、レポート、タグ）、学習目標権限（コース、資格認定、学習パス）のうち1つ以上の権限カテゴリへのアクセス権を付与できます。
* スコープは、セキュリティに最も影響を受けやすい設定です。カスタムの役割は、特定のユーザーグループやカタログに制限することができます。 範囲の制限がない場合、カスタムの役割は、付与された機能に対するプラットフォーム全体のアクセス権を効果的に持ち、完全な管理者のフットプリントに近いものになります。
* カスタム役割に「アカウント権限」で「設定」アクセス権が付与されている場合、そのカスタム管理者は、ログイン方法、通知設定、アカウントレベルの設定を変更できます。影響の大きい権限は、明確なビジネス上の理由がある場合にのみ付与する必要があります。

**統合管理者 – 管理者が操作できるもの**:

* 統合管理者は、「統合管理者/アプリケーション/登録」でOAuth 2.0アプリケーション登録を管理します。 学習者の読み取りアクセス権から管理者の役割の読み取り/書き込みアクセス権まで、6つのOAuthスコープのいずれかを選択します。 管理者読み取り/書き込みスコープは、APIを介して、登録アプリケーションに完全管理者と同じ権限を付与します。
* 統合管理者は、FTP、SFTP、Salesforce、Workday、その他のコネクタを設定して、ユーザーレコード、ロール割り当て、コース完了を読み込み、プラットフォームデータを外部システムに書き出します。
* 統合管理者は、リアルタイムALMイベントデータ（登録、完了、ロールの変更）を外部URLにプッシュするwebhookを設定します。 Webhookエンドポイントの漏洩または設定の誤りは、データ抽出のリスクとなります。
* 統合管理者は、LTI統合を設定できます。 有効にすると、LTIは無効にできません。

**参照**:

* [カスタムの役割| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)
* [CSVを使用したカスタムロールの管理| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/configure-role-csv-files)
* [アプリケーションデベロッパーマニュアル\| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)
* [Adobe Learning Managerコネクタ](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/connectors)

+++

+++Adobe Learning Managerの最上位の管理アカウントと特権アカウントに推奨される安全なデフォルトは何ですか。また、どこで設定しますか？

Adobe Learning Managerに、Administratorロールと特権アカウントタイプの両方に推奨される安全なデフォルト値を記載します。

* **トップレベルの管理者アカウントの既定値（最初のプロビジョニング時に構成）**:

* 内部ユーザーのログイン方法： SAML 2.0を介したシングルサインオン(SSO): ALM管理者/設定/ログイン方法で設定します。 Adobe IDを社員向けや管理者向けに使用しないでください。
* 2段階認証(2FA)：すべてのユーザーに強制：Adobe Admin Console/設定/プライバシーとセキュリティ/認証設定で設定
* 最大セッション時間： 8時間（または組織ポリシーごと）: Adobe Admin Console/設定/プライバシーとセキュリティ/詳細設定で設定。
* 最大アイドル時間： 30分（または組織ポリシーごと）：上記と同じ場所。
* 非アクティブなユーザーの自動削除：組織が定義した保持期間（非アクティブ状態が90日間など）で有効：ALM管理者/設定/一般
* 外部ユーザープロファイルの有効期限：作成時に各外部プロファイルに設定します（ALM管理/ユーザー/外部）。 無期限の外部プロファイルはありません。
* IPアクセスの制限：可能な場合は、承認されたIP範囲（Admin Console/設定/詳細設定）に制限します。

**カスタムの管理者役割の既定値（各役割を作成するときに構成）**:

* 登録アプリケーションのOAuthスコープ：最低限必要なスコープ。 絶対に必要な場合を除き、管理者ロールに読み取り/書き込みアクセス権を付与しないでください。
* カスタム役割の範囲：特定のユーザーグループと特定のカタログに制限します。 機能で本当に必要な場合を除き、「すべてのユーザー」および「すべてのカタログ」スコープを持つカスタムの役割を作成しないでください。
* カスタムの役割での設定アクセス：権限のエスカレーションリスクを考慮し、特定の機能で必要な場合を除き、付与しないでください。

**統合管理者の既定値**:

* API OAuth範囲：統合の要件を満たす最も制限の厳しい範囲を選択します。 学習者の読み取りアクセス権のみを必要とするアプリケーションに対しては、管理者への読み取り/書き込み権限を付与しないでください。
* コネクタの資格情報、LTI資格情報、Webhook URL：機密シークレットとして扱われ、メールで共有したり、ソース管理にコミットしたりすることはありません。

**参照**:

* [設定| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)
* [安全なユーザー認証とパスワード| Adobe Admin Console](https://helpx.adobe.com/enterprise/using/authentication-settings.html)
* [カスタムの役割| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)

+++

+++Adobe Learning Managerを使用すると、管理者は現在のアカウント設定を推奨されるセキュリティで保護されたデフォルトと比較できますか？

Adobe Learning Managerには、推奨される安全なデフォルトと一緒に現在の設定を自動的に表示する専用の比較ダッシュボードはありません。

**カスタムロールレポート：現在の特権ロールの割り当て**:

* ALMで、管理者/ユーザー/カスタムの役割に移動し、「ダウンロード」（右上）をクリックして、すべてのカスタムの役割、その権限セット、およびその範囲割り当てのCSVを書き出します。
* この書き出しをFRR-RSC-02のセクション8で推奨されているデフォルトと比較し、特に文書化された正当な理由がなく、任意のカスタム役割が設定アクセス、すべてのユーザーのスコープ、またはすべてのカタログのスコープを持つかどうかを確認します。

**ALM REST API:プログラムによる構成の取得**:

* GET /accountエンドポイントは、アカウントレベルの設定データをJSON形式で返します。このデータには、Admin role OAuthスコープを使用してアクセスできます。 お客様は、このエンドポイントをプログラムで呼び出し、FRR-RSC-02のセクション8で推奨されるデフォルトから派生したベースラインに対して応答を比較できます。
* GET/usersエンドポイント（include=roleフィルター付き）は、すべてのユーザーの現在のロール割り当てを返し、予期しないロール割り当てを自動検出します。

>[!NOTE]
>
>Adobe Learning Managerには、ネイティブの並べて比較できるUIはありません。 自動構成コンプライアンスチェックを必要とするお客様は、ALM REST APIを既存のツールと統合する必要があります。

**参照**

* [アプリケーションデベロッパーマニュアル| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)

+++

+++管理者は、セキュリティに関連する現在の設定をAdobe Learning Managerからコンピューターで読み取り可能な形式で書き出せますか？

Adobe Learning Managerは、いくつかのメカニズムを使用して、セキュリティ関連の設定データの書き出しをサポートしています。 1回の書き出しですべてのセキュリティ設定の完全なスナップショットを一度に作成することはできませんが、次の書き出しはまとめてセキュリティ関連のデータの全範囲をカバーします。

**ALM REST API：現在の役割の割り当てとアカウント構成のJSON書き出し**:

* GET /account:アクティブなログイン設定データとアカウントメタデータを含む、アカウントレベルの設定をJSONで返します。
* GET /users?include=role: JSONで現在割り当てられているロールを持つすべてのユーザーを返します。
* GET/userGroups – カスタムロールスコープの監査に関連するすべてのユーザーグループとそのメンバーシップを返します。
* すべてのAPI応答はJSON(vnd.api+json)です。 認証では、管理者役割の読み取り/書き込みスコープを持つOAuth 2.0を使用します。

**カスタムの役割のCSVのエクスポート：現在の特権ロールの定義**:

* ALM管理者/ユーザー/カスタムの役割/ダウンロードでは、すべてのカスタムの役割定義、権限カテゴリ、およびスコープ割り当てのCSVが書き出されます。
* このエクスポートは、現在の特権アカウント構成のコンピューターで読み取り可能なスナップショットとして使用できます。
**

**ジョブAPI：一括ユーザーおよびロールデータ**:

* ALMジョブAPIは、CSV形式でのユーザーレポート（ロール割り当てを含む）のオンデマンド生成をサポートしています。 これらは、外部コンプライアンスまたはSIEMツールによってスケジュールして使用できます。

**参照**

* [アプリケーションデベロッパーマニュアル| Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)

+++

+++Adobe Learning Managerには、セキュリティに関連する設定をプログラムで表示および調整できるAPIが用意されていますか？

Adobe Learning Managerには、OAuth 2.0認証を使用してセキュリティ関連の設定をプログラムで表示および調整できる完全なREST API v2が用意されています。 セキュリティ設定に関連する特定のAPI機能を以下に示します。

**認証とスコープ**:

* アプリケーションは、統合管理者が統合管理/アプリケーション/登録から登録します。 OAuth 2.0クライアントIDとシークレットは、アプリケーションごとに発行されます。
* 6つのスコープを使用できます。 セキュリティ設定の管理には、管理者の役割の読み取り/書き込みアクセス権が必要です。 これにより、アプリケーションには、APIを介したフル管理者と同じアクセス権が付与されます。
* アクセストークンは、標準のOAuth認可コードまたはクライアント資格情報フローを介して取得されます。 ベースURL: https://learningmanager.adobe.com/primeapi/v2/

**APIを介したユーザーと役割の管理**:

* GET/users：すべてのユーザーとその現在のロールを取得します
* POST/users：新規ユーザーをプログラムによってプロビジョニングします
* PATCH/users/{id}:ロールの割り当てを含むユーザー属性を更新します
* DELETE/users/{id}:ユーザーアカウントを無効にする
* POST/users/{id}/purge:ユーザーとすべての関連レコードを完全に削除します

アカウント構成の取得：

* GET /account: complianceLabelDefaultID、showComplianceLabel、custom_injectionなどのフィールドを含む、JSON形式のアカウント設定データを含むアカウントレベルの設定を返します。

+++

+++Adobe Learning Managerは、OSCAL、JSON、YAMLなどの機械読み取り可能な形式で安全な設定ガイダンスを公開しますか？

Adobe Learning Managerは現在、セキュリティで保護された設定ガイドをコンピューターで読み取り可能な形式で公開していません。 [FRR-RSC-01](/help/migrated/alm-administrative-lifecycle.md)と[FRR-RSC-02](/help/migrated/alm-secure-administration-guide.md)のガイダンスは、HTML形式およびダウンロード可能な文書形式で、Adobe Experience League上の人間が読める文書として公開されています。

Adobe Learning Managerで推奨される安全なデフォルトをエンコードする、公開されているOSCALコンポーネント定義、YAMLベースライン、またはJSONポリシーファイルはありません。

推奨ベースラインに対する現在の設定の自動比較が必要なお客様は、[ALM REST API](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)を使用して、現在の構成データをJSON形式で取得する必要があります。

+++

+++Adobe Learning Managerのセキュア設定ガイドは、ログインや特別なアクセスを必要とせずに公開されていますか？

**一般公開されているコンテンツ**:

* [FRR-RSC-01:セキュリティで保護された管理ガイド](/help/migrated/alm-administrative-lifecycle.md):トップレベルの管理者アカウントのライフサイクルに関するガイダンス全文。
* [FRR-RSC-02：管理セキュリティの設定と影響](/help/migrated/alm-secure-administration-guide.md):セキュリティに関連するすべての設定、その影響、および推奨される既定。
* FRR-RSC-03-10（本書） — 8つのFedRAMP SHOULD RECOMMENDATIONSに対するQ&amp;A回答。

+++

+++Adobe Learning Managerには、セキュリティに関連する設定や推奨されるデフォルトへの経時的な変更をエージェンシーが追跡できるバージョン管理とリリース履歴が用意されていますか？

Adobe Learning Managerでは、すべての製品アップデートについて、公開されている詳細なリリース履歴を保持しています。 管理設定、認証機能、APIエンドポイント、および役割管理機能に対するセキュリティ関連の変更については、各リリースで文書化されています。

**ALMリリースノート：番号付き、累積的な変更履歴**:

* Adobeでは、Adobe Learning Managerのアップデート（アップデート100、アップデート99など）ごとに番号付きのリリースノートを公開しています。 これらはExperience Leagueに公開され、すべての新機能、既存の設定の変更、APIの追加と削除、コネクタの変更、非推奨の機能について説明します。
* 各リリースノートには、セキュリティ関連の設定機能に直接関連する、新しいエンドポイント、変更された応答フィールド、および廃止を一覧表示するAPI変更の専用セクションが含まれています。

**新機能ページ：リリースごとの機能の概要**:

* 各メジャーリリースには、セキュリティに関連する新しい機能をコンテキスト付きで説明した専用の「新機能」ページがあります。 例えば、リリースノートには、カスタムの役割権限処理の変更、カスタムの役割に対するCSV作成の権限表示の追加、APIレート制限の変更が含まれています。

**APIの廃止の一覧：削除されたAPI機能の権限のあるレコード** s:

* Adobeでは、すべての非推奨および削除されたALM APIエンドポイントと、各非推奨が発生したリリースバージョンをリストする専用のAPI廃止ページを管理しています。

**参照**:

* [Adobe Learning Managerリリースノート](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/release-notes)
* [Adobe Learning Managerの新機能](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/whats-new-july-2024)
* [Adobe Learning ManagerでのAPIの廃止](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/api-deprecations-list)

+++
