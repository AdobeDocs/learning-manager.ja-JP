---
description: Adobe Learning Managerでパーソナライズされた学習パスのリスト表示、取得、登録、削除を行うための公開学習者向けAPIエンドポイントと、割り当てられたカタログを通じて特定の学習者が1つ以上の学習オブジェクトに直接アクセスできるかどうかを確認するためのAPIエンドポイントです。
jcr-language: en_us
title: 2026年9月のAPIの変更
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 3%
---

# Adobe Learning Managerの2026年9月リリースのAPIの変更

## 学習目標のカタログアクセスをチェックするためのAPI

学習者が学習パスまたは資格認定を通じてコンテンツに到達したかどうかにかかわらず、現在の学習者が1つ以上の学習オブジェクトに直接カタログ経由でアクセスできるかどうかを確認します。

### APIの目的

学習者が学習パスや資格認定を開くと、カタログを通じて特定のコースが学習者に直接割り当てられていない場合でも、学習者は学習パスや資格認定に含まれる個々のコースを参照できます。 これはコンテンツ発見をサポートします。学習者は、学習パスを進めるかどうかを決定する前に、学習パスに含まれている内容を調べることができます。

ただし、この方法でコースを表示できるからといって、学習者がコースに自動的に登録できるわけではありません。 登録は、含まれている学習パスを介した間接的なアクセスだけでなく、学習者がその特定のコースに直接カタログからアクセスできるかどうかによって異なります。

このAPIを使用すると、特定の学習者に割り当てられたカタログを通じて1つ以上の学習目標に直接アクセスできるかどうかを確認できます。 結果を使用して、登録関連のUIを制御できます。例えば、コースページ自体を両方の場合に表示しながら、カタログへの直接アクセスが確認されたときにのみ「登録」オプションを表示します。

### エンドポイント

`GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs`

| プロパティ | 値 |
|---|---|
| **スコープ** | 学習者の読み取りアクセス |
| **応答形式** | application/vnd.api+json |

### クエリパラメーター

| パラメーター | 必須 | タイプ | 説明 |
|---|---|---|---|
| id | 可 | 文字列または配列 | 確認する1つ以上の学習目標ID。 1つのIDまたはカンマ区切りのリストを受け入れます。 1回のリクエストで最大10個のID。 |

### リクエストの例

```
GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs?ids=course%3A2400159%2Ccourse%3A2400160%2Ccourse%3A2400161%2Ccourse%3A2400162
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

>[!NOTE]
>
>学習目標IDはURLエンコードされている必要があります。 course:2400159などのIDのコロンは%3Aとしてエンコードされ、複数のIDを区切るコンマは%2Cとしてエンコードされます。

### 応答例 – 200 OK

```json
{
  "course:2400162": false,
  "course:2400161": false,
  "course:2400160": true,
  "course:2400159": true
}
```

| 値 | 意味 |
|---|---|
| true | 呼び出し元の学習者は、この学習目標に対して直接カタログ権限を持っています。 |
| false | カタログを通じて呼び出した学習者は、学習目標を直接使用することはできません。 学習者がアクセス権を持つ学習パスまたは資格認定を介して学習者にアクセス可能な場合は、引き続き学習者がアクセスできる可能性があります。 |

### 応答コード

| ステータス | 意味 |
|---|---|
| 200 | 要求は成功しました。 応答には、要求された各IDに対する結果が含まれます。 |
| 400 | 一般的な無効な要求エラーです。 例えば、10個を超えるIDが指定された場合や、IDの形式が正しくない場合などです。 |
| 401 | リクエストに有効な学習者の資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |

### エラー応答の例

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "Either LO id is blank or not as per public api specification"
  }
}
```

### 統合でこのAPIを使用する

一般的なユースケースは、学習者が学習パスから移動して到達するコースページです。 検出のためにコースページ自体にアクセスできるようにする一方で、学習者がコースに直接カタログへのアクセス権を持っている場合にのみ&#x200B;**登録**&#x200B;アクションを表示する必要があります。

1. コースページが読み込まれたら、コースの学習目標IDを使用してこのエンドポイントを呼び出します。
2. そのIDに対して応答がtrueを返した場合は、**登録**&#x200B;オプションを表示します。
3. 応答がfalseを返した場合、コースページの表示、タイトル、説明、コースの詳細は保持し、**登録**&#x200B;オプションは非表示にします。

## 管理者監査追跡レポートのジョブAPI {#apiaudittrailreport}

### APIの目的

管理者監査追跡レポートには、次の操作に対して行われた構成変更が一覧表示されます
Adobe Learning Managerアカウント 例えば、基本、統合、
指定した日付範囲の高度なアカウント設定。 監査追跡レポートを生成するには、要求された日付範囲および設定タイプにわたって構成変更レコードを照会および集計する必要があります。 範囲のサイズと変更の量によっては、同期HTTP要求の時間制限を超える場合があり、同期HTTP要求はクライアントまたはゲートウェイのタイムアウトのリスクがあります。

これを回避するために、レポートは一般的なジョブAPIを介して非同期で生成されます。

1. **ジョブの作成** 管理者は、レポートタイプ、日付範囲、設定タイプを指定したリクエストを送信します。 APIは、レポートのコンパイルを待たずに、すぐにジョブIDを返します。

2. **ジョブをポーリングします。** 管理者は定期的にIDを使用してジョブを取得し、ステータスを確認します。 ジョブが完了すると、応答に結果または結果への参照が含まれます。

### ベースURLと規則

| アイテム | 値 |
|---|---|
| 基本パス | `/primeapi/v2` |
| コンテンツタイプ | `application/vnd.api+json;charset=UTF-8` (JSON:API) |
| 認証 | ベアラーOAuthトークン（アカウント管理者をスコープとする） |
| アカウントのコンテキスト | 呼び出し元の管理者のアカウントを識別する`x-acap-account`ヘッダー |
| ポーリング | 固定間隔は強制されません。`status`が`QUEUED`または`IN_PROGRESS`でなくなるまで、ジョブ状態の取得エンドポイントをポーリングします |

### ID

ジョブの作成時に返されるジョブ`id`は不透明な文字列です(例：
`4593`). 作成から受け取った正確な`id`値を常に返します
ステータスのポーリング時の応答。 決して構築したり解析したりしないでください。

### 認証スコープ

各エンドポイントには、次のスコープを持つOAuthトークンと、
呼び出し元ユーザーは、アカウント管理者の役割を保持する必要があります。

- `admin:write`レポートジョブを作成します（`ROLE_ADMIN`必須）
- `admin:read`がジョブの状態と結果を読み取りました（`ROLE_ADMIN`必須）

アカウントに`ROLE_ADMIN`を持っていない発信者からの要求は次のとおりです
拒否されました。[エラー処理](/help/migrated/api-changes-sep-2026.md#error-handling)を参照してください

### 端点

#### 監査追跡レポートジョブの作成

`POST /primeapi/v2/jobs`

構成変更監査追跡レポートを生成する非同期ジョブを作成します
に設定できます。 応答はすぐに返されます
`QUEUED`状態のジョブリソースでは、レポート自体は
背景：

スコープ： `admin:write`

| パラメーター | / | 必須 | 概要 |
|---|---|---|---|
| `jobType` | body | 可 | このレポートでは`generateConfigChangeAuditReport`である必要があります |
| `payload.fromDate` | body | 可 | レポートウィンドウの先頭、ISO-8601 （オフセットあり）、例： `2026-09-15T00:00:00.000+05:30` |
| `payload.toDate` | body | 可 | レポートウィンドウの最後、ISO-8601 （オフセットあり）、例： `2026-09-23T23:59:59.000+05:30` |
| `payload.settingTypes` | body | 可 | 含める1つ以上の設定カテゴリの配列。サポートされている値は`Basics`、`Integrations`、および`Advanced`です |

サンプルリクエスト本文

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "payload": {
        "fromDate": "2026-09-15T00:00:00.000+05:30",
        "toDate": "2026-09-23T23:59:59.000+05:30",
        "settingTypes": ["Basics", "Integrations", "Advanced"]
      }
    }
  }
}
```

応答： `202 Created`。 レスポンス本文は、その最初のジョブ・リソースです
`QUEUED`状態。

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "QUEUED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

>[!NOTE]
>
>非常に大きな日付範囲にまたがる`fromDate`/`toDate`ウィンドウ、または
>長い変更履歴を持つアカウントに対してすべての設定タイプを要求し、次のことを実行できます
>処理に時間がかかる。 代わりにジョブの状態の取得エンドポイントをポーリングします
>一定の遅延後にレポートの準備が整っていると仮定します。

#### 監査追跡レポートジョブのステータスを取得する

`GET /primeapi/v2/jobs/{id}`

以前に作成されたジョブの現在のステータスを返します。 仕事をしている間
実行中、`attributes.status`は`QUEUED`または`IN_PROGRESS`で、
`attributes.result`が存在しません。 ジョブが完了すると、`attributes.status`は
`COMPLETED`、`attributes.result`のレポートの場所、または
`FAILED`、エラーの詳細： `attributes.error`。

スコープ： `admin:read`

| パラメーター | / | 必須 | 概要 |
|---|---|---|---|
| `id` | パス | 可 | ジョブの作成時に返されたジョブID |

ジョブの実行中のサンプル応答

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "IN_PROGRESS",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

ジョブが完了した後のサンプル応答

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "COMPLETED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30",
      "dateCompleted": "2026-09-23T18:12:41.000+05:30",
      "result": {
        "downloadUrl": "https://learningmanager.adobe.com/primeapi/v2/jobs/4593/download",
        "expiresAt": "2026-09-24T18:12:41.000+05:30"
      }
    }
  }
}
```

### リソーススキーマ

#### ジョブ属性

| フィールド | タイプ | 説明 |
|---|---|---|
| `id` | string | 不透明なジョブID |
| `jobType` | string | このレポートの`generateConfigChangeAuditReport` |
| `status` | string | `QUEUED`、`IN_PROGRESS`、`COMPLETED`または`FAILED` |
| `dateCreated` | string型(ISO-8601) | ジョブが作成されたとき |
| `dateCompleted` | string型(ISO-8601) | ジョブが完了したとき。`status`が`COMPLETED`または`FAILED`になったときに存在します。 |
| `payload` | オブジェクト | ジョブが作成された際の要求パラメータ（埋め込み – 以下を参照） |
| `result` | オブジェクト | 完成したレポートのダウンロード先。`status`が`COMPLETED`の場合にのみ表示されます（埋め込み – 以下を参照） |
| `error` | オブジェクト | エラーの詳細。`status`が`FAILED`の場合にのみ存在します。 |

#### ペイロード（埋め込み、作成リクエスト内）

| フィールド | 説明 |
|---|---|
| `fromDate` | レポートウィンドウの開始 |
| `toDate` | レポートウィンドウの最後 |
| `settingTypes` | レポートに含まれるカテゴリの設定： `Basics`、`Integrations`、`Advanced` |

#### 結果（埋め込み、完了したジョブ内）

| フィールド | 説明 |
|---|---|
| `downloadUrl` | 生成されたレポートをダウンロードできる署名済みのURL |
| `expiresAt` | `downloadUrl`が有効でなくなったら、新しい状態チェックを要求して、この時刻を過ぎると新しいリンクを取得します |

### エラー処理 {#audit-trail-report-error-handling}

これらのエンドポイントには、次のコードが適用されます。

| HTTPステータス | エラーコード | いつ起こるか |
|---|---|---|
| 400 | `BAD_REQUEST` | `toDate`が`fromDate`より前です。`settingTypes`が空か、サポートされていない値を含んでいるか、日付が有効なISO-8601 – エンドポイントの作成のみ有効ではありません |
| 401 | `UNAUTHORIZED_ACCESS` | トークンが見つからないか、無効であるか、期限切れです |
| 403 | `FORBIDDEN` | 呼び出し元がアカウントの`ROLE_ADMIN`を保持していません |
| 400 | `OBJECT_DOESNT_EXIST` | Get by id:ジョブが存在しないか、idの形式が正しくありません。どちらの場合も、この同じ応答に折りたたまれます。 |

エラー応答の例

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "toDate must be on or after fromDate"
  }
}
```

### 統合でこのAPIを使用する

一般的なユースケースは、管理者向けの「監査追跡をダウンロード」アクションです。
アカウント設定画面

1. 管理者が日付範囲と1つ以上の設定タイプを選択し、
これらの値を使用してcreate-jobエンドポイントを呼び出すことを確認します。
2. 返されたジョブ`id`を保存し、ジョブ状態の取得エンドポイントをポーリングします
妥当な間隔（例、数秒ごと）。
3. `status`が`QUEUED`または`IN_PROGRESS`である間、進行状況の状態を表示し続けます
をクリックします。
4. `status`が`COMPLETED`になると、`result.downloadUrl`を使用して
`expiresAt`が成功する前に管理者がレポートをダウンロードします。
5. `status`が`FAILED`になると、管理者に`error`を表示して許可します
再試行します。
