---
description: 掲示板サブスクリプション設定と購読者APIを使用して、ダイジェスト電子メールを設定し、掲示板の購読者を管理する方法について説明します
jcr-language: en_us
title: 2026年11月のAPIの変更
exl-id: 9b2d3856-810c-4352-bf18-667f698d4d70
source-git-commit: 4234f3cc3b9d77a7f9d197d2df2160ec62edd6d6
workflow-type: tm+mt
source-wordcount: '5724'
ht-degree: 4%
---

# 2026年12月のAPIの変更

## ディスカッション掲示板のインストラクター通知のAPI {#api-discussion-board-instructors}

この記事では、ディスカッションボードのインストラクターの通知をサポートする新しいAPIについて説明します。 これらを使用して、インストラクターやコホートマネージャーをディスカッション掲示板に登録したり、ダイジェスト電子メールに表示されるアクティビティを制御したりできます。

### APIシーケンス {#api-sequence}

APIは2つのグループに分類されます。 `boardSubscriptionSettings` APIはアカウントレベルで動作します。 サブスクライバーAPIは、掲示板レベルで動作します。 次の順序でAPIを使用します。

| 手順 | API | 目的 | 範囲 |
|---|---|---|---|
| 1 | [`POST /boardSubscriptionSettings`](#api-create-settings) | アカウントレベルの設定を行います。 | `admin:write` |
| 2 | [`PATCH /boardSubscriptionSettings`](#api-update-settings) | アカウントレベルの設定を更新します。 | `admin:write` |
| 3 | [`GET /boardSubscriptionSettings`](#api-get-settings) | アカウントレベルの設定を取得します。 | `admin:read` |
| 4 | [`GET /boards/{id}/subscribers`](#api-get-subscribers) | 掲示板に登録しているユーザーのリストを取得します。 | `admin:read` |
| 5 | [`POST /boards/{id}/subscribers`](#api-subscribe-users) | 掲示板にユーザーを登録する。 | `admin:write` |
| 6 | [`DELETE /boards/{id}/subscribers/{userId}`](#api-unsubscribe-user) | 掲示板からユーザーを登録解除する。 | `admin:write` |

### 認証と権限

OAuthを使用して認証し、`admin:read`および`admin:write`のスコープを持つすべてのユーザーが、これらのAPIを呼び出すことができます。 APIでは、次のOAuthスコープを使用します。

* `admin:read`:サブスクライバーの一覧表示と通知設定の読み取り（`GET`件の要求）。
* `admin:write`：通知設定を作成または変更し、サブスクライバーを追加または削除します（`POST`要求、`PATCH`要求、`DELETE`要求）。

>[!NOTE]
>
>通知が送信されると、掲示板へのアクセスが再度確認されます。 サブスクライバーが掲示板にアクセスできない場合、その掲示板での配信はスキップされますが、サブスクリプションは保持されます。 アクセスが戻ると配信が再開されます。

### 制限事項と考慮事項

* 追加できるサブスクライバーの数には上限があります。
* ダイジェストは、ページネーションのない単一の電子メールとして送信されます。電子メールの本文にはサイズ制限があります。 アクティビティの多い掲示板の場合は、各電子メールを管理しやすくするダイジェストの頻度を選択します（6時間ごとなど）。
* ダイジェストリンクを使用すると、ログインしているユーザーに対してのみ投稿、コメント、返信が開きます。

## アカウントレベルの設定を作成するためのAPI {#api-create-settings}

### APIの目的 {#purpose-create-settings}

このAPIを使用して、初めて掲示板サブスクリプション通知のアカウントレベルの設定を行います。 この設定では、アカウント全体で通知ダイジェストを生成する方法を制御します。

* どのディスカッション掲示板イベントが通知を生成するか。
* ダイジェスト電子メールの送信頻度。
* 投稿、コメント、返信、投票を含めるかどうか。

後で設定を変更するには、[`PATCH /boardSubscriptionSettings`](#api-update-settings)を使用します。

### エンドポイント {#endpoint-create-settings}

```http
POST /primeapi/v2/boardSubscriptionSettings
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:write` |
| 形式をリクエスト | `application/vnd.api+json;charset=UTF-8` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### リクエストの本文 {#request-body-create-settings}

設定を`boardSubscriptionSettings`リソースの属性として送信します。

| フィールド | タイプ | 説明 |
|---|---|---|
| `notifyNewPost` | ブール値 | 新しい投稿が掲示板に追加されたときにサブスクライバーに通知するかどうかを指定します。 |
| `notifyComment` | ブール値 | 投稿にコメントが追加されたときに、購読者に通知するかどうかを指定します。 |
| `notifyReply` | ブール値 | コメントに返信が追加されたときに購読者に通知するかどうかを指定します。 |
| `digestFrequencyHours` | integer | ダイジェスト電子メールの送信頻度（時間単位）。 有効な値の範囲は1 ～ 168（1週間）です。 例えば、24は毎日のダイジェストを送信し、168は毎週のダイジェストを送信します。 |

### リクエストの例 {#example-request-create-settings}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyNewPost": true,
      "notifyComment": true,
      "notifyReply": true,
      "digestFrequencyHours": 24
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 応答の例 – 201を作成しました {#example-response-create-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 応答コード {#response-codes-create-settings}

| ステータス | 意味 |
|---|---|
| 201 | 要求は成功しました。 アカウントレベルの設定が作成されました。 |
| 400 | 一般的な無効な要求エラーです。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |

## アカウントレベルの設定を更新するAPI {#api-update-settings}

### APIの目的 {#purpose-update-settings}

このAPIを使用して、[`POST /boardSubscriptionSettings`](#api-create-settings)で作成したアカウントレベルの設定を更新します。 例えば、ダイジェスト頻度を変更したり、イベントタイプのオンとオフを切り替えたりすることができます。

### エンドポイント {#endpoint-update-settings}

```http
PATCH /primeapi/v2/boardSubscriptionSettings
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:write` |
| 形式をリクエスト | `application/vnd.api+json;charset=UTF-8` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### リクエストの本文 {#request-body-update-settings}

変更する属性を作成APIと同じ形式で送信します： `notifyNewPost`、`notifyComment`、`notifyReply`、および`digestFrequencyHours`。 送信しない属性は、現在の値を保持します。 各属性の説明については、[アカウントレベル設定を作成するためのAPI](#api-create-settings)を参照してください。

### リクエストの例 {#example-request-update-settings}

```bash
curl -X PATCH \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyReply": true,
      "digestFrequencyHours": 12
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 応答例 – 200 OK {#example-response-update-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 12,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 応答コード {#response-codes-update-settings}

| ステータス | 意味 |
|---|---|
| 200 | 要求は成功しました。 アカウントレベルの設定が更新され、応答に現在の設定が含まれています。 |
| 400 | 一般的な無効な要求エラーです。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |

## アカウントレベルの設定を取得するためのAPI {#api-get-settings}

### APIの目的 {#purpose-get-settings}

掲示板を購読すると、Adobe Learning Managerはダイジェスト電子メールを通じて、その掲示板でのアクティビティについてユーザーに通知できます。 アカウントレベルの設定によって、通知をトリガーするアクティビティの種類と、ダイジェストの送信頻度が決まります。

このAPIを使用すると、これらの設定を取得できます。 このボタンを使用して、アプリケーションの現在の通知構成を表示したり、設定に依存する機能を作成する前に設定を確認したりできます。

### エンドポイント {#endpoint-get-settings}

```http
GET /primeapi/v2/boardSubscriptionSettings
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:read` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### リクエストの例 {#example-request-get-settings}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 応答例 – 200 OK {#example-response-get-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### リソーススキーマ {#resource-schema-get-settings}

**`boardSubscriptionSettings`属性**

| フィールド | タイプ | 説明 |
|---|---|---|
| `notifyNewPost` | ブール値 | 新しい投稿が掲示板に追加されたときにサブスクライバーに通知するかどうかを指定します。 |
| `notifyComment` | ブール値 | 投稿にコメントが追加されたときに、購読者に通知するかどうかを指定します。 |
| `notifyReply` | ブール値 | コメントに返信が追加されたときに購読者に通知するかどうかを指定します。 |
| `digestFrequencyHours` | integer | ダイジェスト電子メールの送信頻度（時間単位）。 有効な値の範囲は1 ～ 168（1週間）です。 この値を使用して、ダイジェスト電子メールを受信する頻度をユーザーに指定します。 例えば、値が24の場合は「Daily」と表示し、値が168の場合は「Weekly」と表示します。 |

### 応答コード {#response-codes-get-settings}

| ステータス | 意味 |
|---|---|
| 200 | 要求は成功しました。 応答には、アカウントレベルの掲示板サブスクリプションの設定が含まれます。 |
| 400 | 一般的な無効な要求エラーです。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |

### 統合でこのAPIを使用する {#integration-get-settings}

一般的なユースケースは、掲示板サブスクリプションの電子メールがアカウントに対してどのように設定されているかを示す通知設定画面です。

1. アプリケーションの通知設定画面が読み込まれたら、`GET /boardSubscriptionSettings`に電話してください。
1. 応答の値を使用して、通知をトリガーするアクティビティの種類と、ダイジェスト電子メールの送信頻度を表示します。

## 掲示板サブスクライバーを取得するためのAPI {#api-get-subscribers}

### APIの目的 {#purpose-get-subscribers}

特定の掲示板を購読しているユーザーのリストを取得します。 掲示板を購読しているユーザーには、掲示板の新しいアクティビティが通知されます。 このAPIは、特定の掲示板に現在登録しているユーザーと、各サブスクリプションが作成された日時と作成者に関する詳細を返します。

このAPIを使用して、アプリケーションでのサブスクライバーリストの表示、ボードのアップデートの受信者の監査、またはボードのサブスクリプションデータの外部システムとの同期を行います。

応答にページが割り当てられます。 大きなサブスクライバーリストを移動するには、`page[offset]`および`page[limit]`クエリパラメーターを使用します。 返されるデータは、要求されたボード上の呼び出し元ユーザーの権限に従います。

### エンドポイント {#endpoint-get-subscribers}

```http
GET /primeapi/v2/boards/{id}/subscribers
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:read` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### パラメーター {#parameters-get-subscribers}

| パラメーター | / | 必須 | デフォルト | 概要 |
|---|---|---|---|---|
| `id` | パス | 可 | 該当しません | 取得するサブスクライバがあるボードのID。 アクセスは、掲示板での呼び出し元の権限に従います。 |
| `page[offset]` | query | 不可 | 0 | 返すレコードの開始位置。 |
| `page[limit]` | query | 不可 | 10 | 1ページあたりに返すサブスクライバーの数です。 指定できる最大値は200です。 |

### リクエストの例 {#example-request-get-subscribers}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers?page[offset]=0&page[limit]=50'
```

### 応答例 – 200 OK {#example-response-get-subscribers}

```json
{
  "data": [
    {
      "id": "1234:5678",
      "type": "boardSubscriber",
      "attributes": {
        "boardId": 1234,
        "dateSubscribed": 1757000000000,
        "subscribedByUserId": 5678,
        "user": {
          "id": "5678",
          "name": "Jane Doe",
          "email": "jane.doe@example.com",
          "avatarUrl": "https://example.com/avatars/5678.png",
          "bio": "Learning enthusiast",
          "contentLocale": "en-US",
          "uiLocale": "en-US",
          "timeZoneCode": "PST",
          "userType": "INTERNAL",
          "state": "ACTIVE",
          "profile": "Learner",
          "roles": ["Learner"],
          "gamificationEnabled": true,
          "pointsEarned": 120,
          "pointsRedeemed": 20,
          "enrollOnClick": true,
          "preferredResolution": "720p",
          "lastLoginDate": "2026-09-23T18:12:04.000Z"
        }
      }
    }
  ]
}
```

### リソーススキーマ {#resource-schema-get-subscribers}

応答に新しいリソース`boardSubscriber`が含まれています。 属性には、`boardId`、`dateSubscribed`、`subscribedByUserId`および`user`が含まれます。 埋め込みユーザーオブジェクトは、ユーザーID、名前、電子メール、プロファイル、役割、およびその他のユーザーメタデータなどのサブスクライバー情報を持ちます。

**`boardSubscriber`属性**

| フィールド | タイプ | 説明 |
|---|---|---|
| `id` | string | 不透明なサブスクリプションID。 |
| `type` | string | リソースの種類。 |
| `boardId` | 数値 | ユーザーがサブスクライブしているボードのID。 |
| `dateSubscribed` | 数値 | ユーザーがボードをサブスクライブした時点のタイムスタンプ。 |
| `subscribedByUserId` | 数値 | サブスクリプションを作成したユーザーのID。 |
| `user` | オブジェクト | サブスクライブしているユーザーの詳細（埋め込まれています。以下を参照）。 |

**`user`（埋め込み、サブスクライバー内）**

| フィールド | タイプ | 説明 |
|---|---|---|
| `id` | string | 不透明なユーザーID |
| `name` | string | ユーザーの表示名です。 |
| `email` | string | ユーザーの電子メールアドレス。 |
| `avatarUrl` | string | ユーザーのプロファイル画像のURLです。 |
| `bio` | string | ユーザーの簡単な経歴。 |
| `binUserId` | string | ユーザーの内部識別子。 |
| `userUniqueId` | string | アカウント内のユーザーを表す一意の識別子です。 |
| `userType` | string | ユーザーのタイプ（内部または外部など）。 |
| `state` | string | ユーザーアカウントの現在の状態。 |
| `profile` | string | ユーザーに割り当てられたプロファイル。 |
| `roles` | 文字列配列 | ユーザーが保持するロール。 |
| `contentLocale` | string | ユーザーがコンテンツを表示するロケール。 |
| `uiLocale` | string | ユーザーインターフェイスに使用されるロケール。 |
| `timeZoneCode` | string | ユーザー用に構成されたタイムゾーン。 |
| `preferredResolution` | string | ユーザーの推奨ビデオ解像度。 |
| `enrollOnClick` | ブール値 | 学習目標の選択時にユーザーを自動的に登録するかどうかを指定します。 |
| `gamificationEnabled` | ブール値 | ユーザーに対してゲーミフィケーションを有効にするかどうかを指定します。 |
| `pointsEarned` | 数値 | ユーザーが獲得したゲーミフィケーションポイントの合計。 |
| `pointsRedeemed` | 数値 | ユーザーが交換したゲーミフィケーションポイントの合計です。 |
| `lastLoginDate` | string | ユーザーが最後にログインした日時。 |
| `fields` | オブジェクト | カスタムユーザーフィールドとその値。 |
| `metadata` | オブジェクト | ユーザーに関連付けられている追加のメタデータ。 |

### 応答コード {#response-codes-get-subscribers}

| ステータス | 意味 |
|---|---|
| 200 | 要求は成功しました。 応答には掲示板のサブスクライバーが含まれています。 |
| 400 | 一般的な無効な要求エラーです。 例えば、ボードIDやページ番号の値の形式が間違っています。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |

### 統合でこのAPIを使用する {#integration-get-subscribers}

一般的なユースケースは、掲示板の更新を受け取ったすべての人を表示する管理者またはモデレーターのビューです。

1. ビューが読み込まれたら、ボードIDとレイアウトに適した`page[limit]`値（最大200）を指定してこのエンドポイントを呼び出します。
1. 各サブスクライバーの`user.name`、`user.email`、および`dateSubscribed`の値を表示します。
1. 返されたレコードの数が`page[limit]`に等しい場合は、サブスクライバーの数が多くなる可能性があります。 ページから返されるレコードが要求された数よりも少なくなるまで、`page[offset]`をページサイズだけ増やしてエンドポイントを再度呼び出します。

## 掲示板にユーザーを登録するAPI {#api-subscribe-users}

### APIの目的 {#purpose-subscribe-users}

1人以上のユーザーをディスカッション掲示板に登録して、そのユーザーがダイジェスト電子メールを受信できるようにします。 ユーザーをユーザーID、電子メールアドレス（アカウント内のユーザーIDに解決）、またはその両方で識別します。 1回のリクエストで複数のユーザーを追加できます。 [一括サブスクリプション](#bulk-subscriptions)を参照してください。

### エンドポイント {#endpoint-subscribe-users}

```http
POST /primeapi/v2/boards/{id}/subscribers
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:write` |
| 形式をリクエスト | `application/vnd.api+json;charset=UTF-8` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### パラメーター {#parameters-subscribe-users}

| パラメーター | / | 必須 | 概要 |
|---|---|---|---|
| `id` | パス | 可 | ユーザーをサブスクライブする掲示板のID。 |

### リクエストの本文 {#request-body-subscribe-users}

ユーザーを`boardSubscriberBulkRequest`リソースの属性として送信します。 `userIds`または`emails`の少なくとも1つが必要です。

| フィールド | タイプ | 説明 |
|---|---|---|
| `data.attributes.userIds` | 数値配列 | 登録するユーザーのID。 |
| `data.attributes.emails` | 文字列配列 | 登録するユーザーの電子メールアドレス。 各アドレスは、アカウント内のユーザーIDに解決されます。 |

### リクエストの例 {#example-request-subscribe-users}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriberBulkRequest",
    "attributes": {
      "userIds": [
        1234,
        5678
      ],
      "emails": [
        "abc@xyz.com"
      ]
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1010/subscribers'
```

### 応答の例 – 207マルチステータス {#example-response-subscribe-users}

```json
{
  "added": [
    {
      "userId": "12345",
      "status": "SUCCESS"
    }
  ],
  "failed": [
    {
      "userId": "78910",
      "errorCode": "NO_BOARD_ACCESS"
    }
  ]
}
```

**応答属性**

| フィールド | タイプ | 説明 |
|---|---|---|
| `added` | 配列 | 登録されたユーザー。 各エントリには`userId`と`status`があります。 既にサブスクリプションを購入しているユーザーも、ここに成功として報告されます。 |
| `failed` | 配列 | サブスクライブできなかったユーザー。 各エントリには、`userId`と`errorCode`があります（例： `NO_BOARD_ACCESS`）。 |

### 応答コード {#response-codes-subscribe-users}

| ステータス | 意味 |
|---|---|
| 207 | マルチステータス： 要求が処理され、応答によって`added`と`failed`の各ユーザーの結果が一覧表示されました。 |
| 400 | 一般的な無効な要求エラーです。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |
| 404 | ボードなどの要求されたリソースが見つかりませんでした。 |
| 409 | 掲示板が非アクティブ、削除、または廃止されているため、要求全体が拒否されます。 |

### 一括サブスクリプション {#bulk-subscriptions}

一括サブスクリプションを使用すると、1回の要求で複数のユーザーをディスカッション掲示板に追加できます。 一括サブスクリプションは、サブスクライバーの管理に必要なAPI呼び出しの数を減らすのに役立ちます。 次の場合に便利です。

* インストラクターは複数のグループを管理します。
* コホートのマネージャーは、多くのディスカッション掲示板にアクセスする必要があります。
* 外部システムは、基板サブスクリプションを一括して同期する。
* 複数のインストラクターは、グループの作成時にサブスクライブする必要があります。

#### 一括追加動作

一括要求には、ユーザーID、電子メールアドレス、またはその両方を組み合わせて含めることができます。 各ユーザーは個別に処理されます。

#### べき等の行動

一括追加は権限がありません。 ユーザーが既に掲示板に登録している場合、リクエストは成功し、重複するサブスクリプションは作成されず、既存のサブスクリプションは変更されません。 これにより、クライアントは要求を安全に再試行できます。

#### 部分的成功

サブスクリプションを購入できるユーザーと検証できないユーザーがいます。 1人以上のユーザーが無効であるため、操作は失敗しません。

| ケース | 結果 |
|---|---|
| ユーザーが存在し、掲示板にアクセスできる | 成功 |
| ユーザーは既にサブスクリプションに登録されています | 成功 |
| ユーザーは掲示板にアクセスできません | エラー(`NO_BOARD_ACCESS`) |
| ユーザーが存在しません | 失敗 |
| ユーザーが非アクティブです | 失敗 |
| ユーザーが削除されました | 失敗 |

#### 応答形式

一括サブスクリプションは、[応答の例](#example-response-subscribe-users)のように、各ユーザーの結果が`added`で、結果が`failed`のHTTP 207 Multi-Statusを返します。

#### 一般的な検証エラー

* **ユーザーは掲示板にアクセスできません。** ユーザーが掲示板を表示できない場合は、そのユーザーに対して`NO_BOARD_ACCESS`が返されます。 残りのユーザーは引き続き正常に処理されます。
* **掲示板は非アクティブか、削除されているか、廃止されています。** 掲示板がサブスクリプションの対象にならない場合、リクエストは拒否され、「HTTP 409の競合」が発生します。
* **ユーザーが無効です。** ユーザーアカウントが存在しない、非アクティブである、または削除された場合、操作はそのユーザーのエラーエントリを返します。

## 掲示板からユーザーの購読を解除するためのAPI {#api-unsubscribe-user}

### APIの目的 {#purpose-unsubscribe-user}

ディスカッション掲示板からユーザーの購読を解除します。 サブスクリプションが削除されると、その掲示板の通知やダイジェスト電子メールはユーザーに送信されなくなります。

### エンドポイント {#endpoint-unsubscribe-user}

```http
DELETE /primeapi/v2/boards/{id}/subscribers/{userId}
```

| プロパティ | 値 |
|---|---|
| 範囲 | `admin:write` |
| 応答形式 | `application/vnd.api+json;charset=UTF-8` |

### パラメーター {#parameters-unsubscribe-user}

| パラメーター | / | 必須 | 概要 |
|---|---|---|---|
| `id` | パス | 可 | ボードのID。 |
| `userId` | パス | 可 | 登録解除するユーザーのID。 |

### リクエストの例 {#example-request-unsubscribe-user}

```bash
curl -X DELETE \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers/5678'
```

### 応答の例 – 204 No Content {#example-response-unsubscribe-user}

応答に本文がありません。

### 応答コード {#response-codes-unsubscribe-user}

| ステータス | 意味 |
|---|---|
| 204 | 要求は成功しました。 ユーザーが掲示板の購読を取り消されました。 |
| 400 | 一般的な無効な要求エラーです。 |
| 401 | 要求に有効な資格情報がないか、資格情報が無効なため、アクセスが拒否されました。 |
| 404 | ボードまたはサブスクリプションなどの要求されたリソースが見つかりませんでした。 |

## ブックマークAPIの順序と廃止されたコンテンツ処理 {#bookmark-api-ordering-retired-content}

### APIの目的

学習者が再確認したいトレーニングをブックマークします。 この変更の前は、ブックマークAPIが特定の順序でブックマークを返していました。 統合、特にヘッドレス実装では、最後に保存されたブックマークを最初に表示できませんでした。 多くのブックマークを持つ学習者は、古いアイテムをスクロールして最新のアイテムを見つける必要がありました。

廃止された学習目標のブックマークもリストに残りました。 1つ選択すると、「ページが見つかりません」というエラーが発生します。

この変更により、ブックマークAPIが次の2つの方法で改善されました。

* ブックマークは時系列で、最新から順に返されます。
* 廃止された学習目標のブックマークは返されなくなりました。

新しいエンドポイント、パラメーター、または応答属性は導入されません。 既存の統合は、変更されることなく引き続き機能します。

### ベースURLと規則

ブックマークAPIでは、次の基本パスと表記規則を使用します。

| アイテム | 値 |
|---|---|
| 基本パス | `/primeapi/v2` |
| コンテンツタイプ | `application/vnd.api+json` |
| 認証 | 学習者の読み取りアクセス権を持つOAuthトークン |
| デフォルトの順序 | 新しいブックマークを先に追加 |
| 新しいパラメーター | なし |
| 応答構造 | 変更なし |

### エンドポイント

#### ブックマークを返すエンドポイント

次のエンドポイントでは、ブックマークが新しい順序で返されます。

| エンドポイント | 戻り値 |
|---|---|
| `GET /primeapi/v2/learningObjects?filter.bookmarks=true` | 学習者がブックマークした学習目標 |
| `GET /primeapi/v2/bookmarks` | 学習者のブックマーク |

#### ブックマークされた学習目標を順番に取得

`GET /primeapi/v2/learningObjects?filter.bookmarks=true`

<!-- Content Review by Claude: Please confirm the endpoint list. The dev-to-QE hand-off confirms ordering for GET /learningObjects?filter.bookmarks=true. The PRD (ALMER-442) also lists GET /primeapi/v2/bookmarks. Please also confirm the OAuth scope. -->

呼び出し元の学習者がブックマークに登録した学習オブジェクトを返します。 最後にブックマークされた項目が最初で、最も古い項目が最後です。

**スコープ：**&#x200B;学習者の読み取りアクセス

このエンドポイントでは、次のクエリパラメーターを使用できます。

| パラメーター | / | 必須 | 概要 |
|---|---|---|---|
| `filter.bookmarks` | query | 可 | `true`に設定すると、学習者がブックマークした学習目標のみが返されます |

**サンプル要求**

```http
GET /primeapi/v2/learningObjects?filter.bookmarks=true
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

**サンプル200 OK応答**

学習者は、「Adobe Analyticsでの作業を開始」を最初に、「ワークスペースプロジェクトの構築」を2番目に、「Adobe Analyticsでの高度なセグメント化」を最後にブックマークしました。 応答には、最新のものから最も古いものまでリストされます。 簡潔にするために他の属性は省略します。

```json
{
  "data": [
    {
      "id": "course:2400162",
      "type": "learningObject",
      "attributes": {
        "name": "Advanced Segmentation in Adobe Analytics"
      }
    },
    {
      "id": "course:2400160",
      "type": "learningObject",
      "attributes": {
        "name": "Building Workspace Projects"
      }
    },
    {
      "id": "course:2400159",
      "type": "learningObject",
      "attributes": {
        "name": "Getting Started with Adobe Analytics"
      }
    }
  ]
}
```

>[!NOTE]
>
>新しい順序がデフォルトの動作で、すべてのアカウントに適用されます。

### ブックマークの順序

#### ブックマークの順序

ブックマークは、学習者が保存した日付（新しい順）で並べ替えられます。 例えば、学習者がコースA、コースB、コースCの順にブックマークを設定した場合、応答にはコースCが最初に、コースBが2番目に、コースAが最後にリストされます。

例えば、10番目に表示されているブックマークされたLOが「未保存」で、後で再度ブックマークされた場合、それは最近ブックマークされ、最初はリストに表示されます。

以前にクライアント上でブックマークをソートした統合は、そのロジックを削除し、返された順序で結果を表示できます。

### 廃止されたコンテンツの処理

#### 廃止された学習目標の処理方法

学習者が学習目標に登録されているかどうかに関係なく、撤回した学習目標のブックマークは応答に返されません。

学習者が登録されない限り、ブックマークされた廃止済みの学習目標は表示されません。

「ページが見つかりません」というエラーの原因となるブックマークが学習者に表示されなくなりました。 ブックマークは結果から非表示になりますが、削除されるわけではありません。

### 互換性

この変更により、既存のAPIコンシューマーが機能しなくなります。

* エンドポイントとそのパラメーターは変更されません。
* レスポンス構造は変更されず、属性は追加も削除もされません。
* 以前の動作と異なるのは、結果の順序と、廃止された学習目標の除外のみです。

### 統合でこのAPIを使用する

一般的なユースケースとして、ヘッドレス学習者エクスペリエンスの「後で保存」リストがあります。 学習者は、削除されたコンテンツへのリンクなしで、最新のしおりを最初に表示できます。

1. 学習者がリストを開くときに`GET /primeapi/v2/learningObjects?filter.bookmarks=true`を呼び出します。
2. 返された順序で学習目標を表示します。 最初の項目は、最後にブックマークされた項目です。
3. 回避策として追加したクライアント側の並べ替えや削除されたコンテンツフィルタリングをすべて削除します。
4. 応答の項目数を使用してブックマークの数を表示します。 廃止された学習目標のブックマークは含まれなくなりました。

### 学習者アプリの学習者コンプライアンスウィジェットで、複数登録されたインスタンスのAPIサポート {#api-multienrolled-instances-lc-widget}

パブリックAPIでは、既存の登録エンドポイントのオプションのクエリパラメーターを使用して、この動作をサポートしています。 このパラメーターを省略した場合、APIは以前と同じ結果を返すため、ヘッドレス実装を含む既存の統合は変更されずに動作し続けます。

**エンドポイント**

GET /primeapi/v2/enrollments

**クエリパラメーター**

includeMultiInstanceEnrollments （オプション）

**クエリ**

https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&filter.loTypes=course&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&sort=dateEnrolled

**値**

その通りです。 デフォルトはfalseです。

**応答の本文**

{

&quot;links&quot;: {

&quot;self&quot;: &quot;[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true)&quot;,

&quot;next&quot;: &quot;[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true&amp;page\[cursor\]=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwEwLCJs zwfybmluZ1Byb2dyYW0iOjAsImNlcnRpZmljYXRpb24iOjB9](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&page%5bcursor%5d=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwLCJsZWFybmluZ1Byb2dyYW0iOjAsImNlcnRpZmljYXRpb24iOjB9)&quot;

},

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:15067_30122_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2026-02-24T10:50:45.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:15067&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:15067_30122&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:15067_30122_41715_1_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:1108800_1997400_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;SELF_ENROLL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:1108800&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:1108800_1997400&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:1108800_1997400_2174574_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2027668_3707328_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2027668&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2027668_3707328&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2027668_3707328_2665897_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2030067_3709862_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2030067&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2030067_3709862&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2030067_3709862_2668467_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:3081896_5749155_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3081896&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3081896_5749155&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:3081896_5749155_3737554_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

},

{

&quot;id&quot;: &quot;course:3081896_5749155_3737555_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037893_3717940_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037893&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037893_3717940&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037893_3717940_3676856_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:3049434_5713130_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2020-05-05T18:29:59.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3049434&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3049434_5713130&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:3049434_5713130_3693595_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2001397_3679403_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2001397&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2001397_3679403&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2001397_3679403_2635974_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037862_3717900_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037862&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037862_3717900&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037862_3717900_3676816_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037837_3717863_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2020-02-29T18:29:59.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;SELF_ENROLL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;OTHER&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037837&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037837_3717863&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037837_3717863_3597363_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

}

\]

}

## 学習パス登録の最終アクセス日 {#api-last-access-date-lp-enrollment}

Adobe Learning Managerでは、最終アクセス日などのカスタムメタデータを学習パスの登録に保存できます。 メタデータの設定と読み取りは、APIを通じて行います。 これにより、割り当てた学習パスへの期限付きアクセスを追跡できます。

## 学習パス登録メタデータについて

APIを使用して、コースの登録に最終アクセス日を既に設定することができます。 この日付は、学習者がコースにアクセスできる期間を制御します。 学習パスの登録で一般的なメタデータフィールドがサポートされるようになり、最終アクセス日やその他の追跡対象の値を保存できるようになりました。

このフィールドをオンにしたり、特別なヘッダーを送信したりする必要はありません。 フィールドは、設定するまで空です。

>[!NOTE]
>
>メタデータはユーザー独自のトラッキング用です。 Adobe Learning Managerでは、学習者が学習パスやそのコースを開いても、学習パスへのアクセスを制御したり、学習パスを更新したりすることはできません。 また、パス内のコースにも反映されません。 各コースには独自の最終アクセス日が保持されるため、同じパス内のコースに異なる日付を設定できます。 引き続き、コースレベルのアクセスの有効期限を個別に管理します。

### メタデータのルール {#metadata-rules}

* 値はJSONオブジェクトである必要があります。 文字列、数値、ブーリアン、または配列は、メッセージ`metadata must be a JSON object`を含む400エラーを返します。
* 任意のキーを使用できます。 Adobe Learning Managerでは、キーや値は検証されません。また、日付書式は強制されません。 この記事の例では、コースの日付と同じ形式であるエポックミリ秒を使用しています。
* PATCHリクエストは、メタデータオブジェクト全体を置き換えます。 既存の値とマージされないので、除外したキーは削除されます。
* `"metadata": null`を設定すると、すべてのメタデータが消去され、200が返されます。
* 空の`attributes`オブジェクトを持つ要求、または`metadata`キーを持たない要求では、保存されたメタデータは変更されません。
* メタデータが設定されていない場合、またはクリアした後、`metadata`キーは応答に含まれていません。

## 既存の登録にメタデータを設定

adminトークンを使用します。

次のエンドポイントにPATCHリクエストを送信します。`{enrollmentId}`は`learningProgram:<lpId><instanceId><userId>`の形式の学習パス登録IDです。

```
PATCH /primeapi/v2/users/{userId}/enrollments/{enrollmentId}
```

このリクエスト本文を使用：

```json
{
  "data": {
    "id": "<enrollmentId>",
    "type": "learningObjectInstanceEnrollment",
    "attributes": {
      "metadata": {
        "lastAccessDate": 1745337600000
      }
    }
  }
}
```

### 学習者の登録時のメタデータの設定

adminトークンを使用します。

学習パスとインスタンスIDを含むPOSTリクエストを送信します。 要求の本文にオプションの`metadata`オブジェクトを含めます。

```
POST /primeapi/v2/users/{userId}/enrollments?loId=<lpId>&loInstanceId=<instanceId>
```

* `metadata`がJSONオブジェクトでない場合、要求は400を返し、ユーザーは登録されていません。
* ユーザーが既に登録されている場合、リクエストは200を返し、何も変更しません。 既存のPATCHのメタデータを変更するには、登録リクエストを使用します。
* 応答にメタデータが含まれていません。 GETリクエストを送信して読み取ります。

### メタデータの取得

管理者または学習者トークンを使用してメタデータを取得できます。 リクエストは、トークンの種類によって異なります。

| トークン | 1つの登録を取得 | 学習パス登録のリスト |
|---|---|---|
| 管理者 | `GET /primeapi/v2/users/{userId}/enrollments/{enrollmentId}` | `GET /primeapi/v2/users/{userId}/enrollments?filter.loTypes=learningProgram` |
| 学習者 | `GET /primeapi/v2/enrollments/{enrollmentId}`<br>`GET /primeapi/v2/learningObjects/{id}?include=enrollment` | `GET /primeapi/v2/enrollments?filter.loTypes=learningProgram` |

>[!NOTE]
>
>`include=enrollment`パラメーターは、学習者トークンでのみ機能します。 管理者の役割ではサポートされていません。

応答は、学習パス登録を含む`metadata`オブジェクトを返します。

### ヘッドレスおよび外部ポータルでのメタデータの使用

外部ポータルと統合は同じAPI呼び出しを使用します。 ポータルが使用するトークンと一致する要求を使用します。

* **ポータルの値を表示する：**&#x200B;上のテーブルからトークン型のGET要求を送信し、応答から`metadata`オブジェクトを読み取ります。
* **Commerce Platformなどの外部システムから値を更新する：**&#x200B;管理者トークンを使用してPATCHリクエストを送信します。

## ジョブAPI:generateCustomReportによるReport Builderレポートの書き出し {#api-job-report-builder-exports}

Adobe Learning Manager 2026年12月リリースでは、新しいジョブの種類`generateCustomReport`がジョブAPIに追加されています。 これを使用すると、レポートIDを渡してReport Builderで作成したレポートを自動的に書き出すことができます。

Report Builderの新しいL2クイズデータセットと組み合わせると、次のことができます。

* 各コースに対して`generateQuizReport`を1回実行するのではなく、複数のコースおよびモジュールにわたる質問レベル(L2)クイズデータを1つのレポートに書き出します。
* 定期的なエクスポートを自動化します。たとえば、データ・ウェアハウスまたはBIツールへの日次増分エクスポートを自動化します。

`generateQuizReport`を含む既存のジョブの種類は変更されません。

### 始める前に

* 管理者である必要があります。 `generateCustomReport`ジョブの種類は、他のロールでは使用できません。
* 最初にレポートを作成してReport Builderに保存します。 L2クイズデータの場合は、L2クイズデータセットからレポートを作成し、必要な質問レベルのフィールド（質問テキスト、学習者の回答、スコア、試行番号、回答日など）を含めます。
* レポートのIDをメモします。 要求で`reportId`として渡します。

### 求人を作成

**エンドポイント**

```
POST /primeapi/v2/jobs
```

**リクエストの本文**

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "description": "Daily L2 quiz export",
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      }
    }
  }
}
```

**属性**

| 属性 | 必須 | 概要 |
|---|---|---|
| `jobType` | 可 | `generateCustomReport`でなければなりません。 |
| `payload.reportId` | 可 | 保存されたReport BuilderレポートのID （文字列）。 正の整数である必要があり、文字列として渡されます（例： `"1478"`）。 数値、0、負、10進数、または空の値を送信すると、エラーが返されます。 |
| `description` | 不可 | 選択したジョブの説明。 |
| `callbackUrl` | 不可 | ジョブの完了時に呼び出すURL。 他のジョブタイプと同様に機能します。 |
| `payload.filters` | 不可 | 次のセクションを参照してください。 |

### 日付フィルターの上書き（オプション） {#override-date-filter}

```json
"payload": {
  "reportId": "1478",
  "filters": [
    { "columnName": "L2 Quiz - Response - Timestamp", "operator": "gte", "val": "2026-11-15T00:00:00.000Z" }
  ]
}
```

* この実行のみのレポートの保存日フィルタが置き換えられます。 エクスポートは、ジョブが実行されるまでの`val`を対象とします。
* `columnName`は形式`<Dataset name> - <Field name>`を使用します。 レポートに既に存在する日付フィルターと一致する必要があります。 大文字と小文字は区別されませんが、間隔とハイフンは完全に一致する必要があります。
* `operator`はオプションであり、`gte`のみが許可されます。
* `val`は、過去7日間のISO 8601 UTC時刻です。 時間は秒に切り捨てられます。
* 複数の列を上書きできます。 空のリストは、保存されたフィルターが使用されていることを意味します。
* 使用例：前の日次増分書き出しが終了した時点から開始する日次増分書き出し。

### ジョブの作成時に返されるエラー

| 原因 | メッセージ |
|---|---|
| `reportId`がありません | `reportId is required` |
| `reportId`は正の整数文字列ではありません | `reportId must be a positive integer string` |
| 日付がISO形式ではありません | `filters.val must be in ISO format, e.g. 2020-01-01T18:30:00.000Z` |
| 7日より古い日付、または将来の日付 | `filters.val must be within the last 7 days` |
| `gte`以外の演算子 | `filters.operator must be gte` |
| 同じ列を2回指定 | `Duplicate filter column: <column>` |
| 列はレポートのフィルターではありません | `Unsupported custom report filter column: <column>` |
| 同じレポートのジョブがまだ実行中です | `There exists an similar job with id = <jobId> which has not finished yet` |

ジョブの実行時に、保存されたレポート定義の問題のみが検出されます。 その場合、ジョブの状態は`Failed`になり、理由は返されません。

### レポートの要件

レポートが次の条件を満たしていない場合、ジョブはエラーメッセージで失敗します。

* レポート定義には、相対日付フィルタ（たとえば、過去7日間）が含まれます。
* レポートに含まれるすべての日付フィルターの範囲は、1日だけでなく7日以内である必要があります。
* 開始日と終了日が設定された固定日付範囲はサポートされておらず、ジョブは失敗します。
* 日付フィルターのないレポートは失敗します。 これには、日付フィールドのないデータセットに基づいて作成されたレポートが含まれます。

>[!NOTE]
>
>POSTリクエストはすぐに検証されます。 無効な要求がHTTP 400で拒否されました。理由は`source.info`にあります。

### ジョブステータスを確認し、レポートをダウンロードする

**エンドポイント**

```
GET /primeapi/v2/jobs/{jobId}
```

応答は、他のジョブタイプと同じ構造を使用します。 ジョブが完了すると、`status.code`は`Completed`になり、`status.data.s3Url`にはダウンロードリンクが含まれます。

```json
{
  "data": {
    "type": "job",
    "id": "12345",
    "attributes": {
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      },
      "status": {
        "code": "Completed",
        "data": {
          "s3Url": "valid for 7 days"
        }
      }
    }
  }
}
```

APIは`Submitted`、`Completed`および`Failed`を返します。 ファイルは`report.csv`という名前の単一のCSVです。

>[!NOTE]
>
>ダウンロードURLの有効期間は7日間です。 ジョブが完了したらすぐにファイルをダウンロードします。

>[!IMPORTANT]
>
>リンクを知っているすべてのユーザーは、ログインしなくてもファイルをダウンロードできます。 リンクに含まれるデータを処理する場合と同じようにリンクを処理します。

**失敗したジョブのサンプル**

```json
"status": { "code": "Failed" }
```

### 制限

一度に実行できるレポートの`generateCustomReport`ジョブは1つだけです。 2番目の要求は、最初の要求が完了するまで拒否されます。

### L2クイズレポート出力

L2クイズのデータセットからReport Builderでレポートを作成し、`generateCustomReport`で書き出すと、出力は次のような特性になります。

* 出力は、`report.csv`という名前の単一のCSVファイルです。 モジュールはファイル内のカラムです。 コースを選択すると、レポートではそのクイズモジュールのみが返されます。
* 各行は、1回の試行で1つの質問に対して1人の学習者が回答したことを表します。
* データは標準のReport Builder間隔（約15分ごと）で更新されます。
* 日付と時刻の値は、アカウントのタイムゾーンで指定します。 列ヘッダーには、タイムゾーンが表示されます（例： `L2 Quiz - Response - Timestamp (America/Argentina/Salta)`）。

### L2クイズデータセットのフィールド

| カテゴリ | フィールド |
|---|---|
| 学習者 | ユーザー ID |
| コース | コースID、コースインスタンスID、コース名 |
| モジュール | モジュールID、モジュール名、モジュールバージョン |
| 質問 | 質問ID、質問テキスト、正解、インタラクションタイプ |
| 回答 | 応答の回答、達成スコア、可能な最大スコア、正解、応答タイムスタンプ |
| 試行 | 試行回数 |

>[!NOTE]
>
>L2クイズデータセットが他のReport Builderデータセットにリンクされていません。 学習者の名前、電子メール、マネージャー、カスタム属性は、このレポートでは利用できません。 行と学習者を一致させるには、ユーザーIDを使用します。

`generateCustomReport`を使用して、他のReport Builderデータセットに基づいて作成されたレポートをエクスポートすることもできます。 出力で使用可能なフィールドは、データセットによって異なります。

## ズームコネクターを作成および管理するAPI

これらのAPIを使用して、Adobe Learning ManagerでZoomの連携を管理します。 既存の接続の取得、Zoomの資格情報の保存、接続の作成または更新、ユーザーグループとカスタム役割のアクセス権限の設定、接続の有効化または無効化を行うことができます。

### Zoom コネクター APIの設定

Zoom コネクターの設定と管理には4つのAPI呼び出しが必要です。 次の順番で作成します。

| 手順 | API | 機能 |
|---|---|---|
| 1 | `POST /ctr/authcred/uuid/20012` | Zoomの資格情報を保存します。 |
| 2 | `POST /ctr/app/esconnect` | ズーム接続を作成するか、既存の接続を更新します。 |
| 3 | `PUT /ctr/xtsa/{connectionId}/access` | 接続を使用できるユーザーグループとカスタムの役割を設定します。 |
| 4 | `POST /ctr/xtsas/{connectionId}/enable` | 接続を有効または無効にします。 |

>[!NOTE]
>
>これらのAPIは、ログインしている統合管理セッションを使用します。 APIキーやOAuthトークンは使用しません。

### ベースURLと規則

Zoom コネクター APIでは、次の表記規則を使用します。

| アイテム | 値 |
|---|---|
| ベース URL | `https://learningmanagerstage1.adobe.com` |
| コンテンツタイプ | `application/json` |
| 認証 | ログインしている統合管理者のセッション |
| 必須ヘッダー | `content-type`、`accept`、`x-acap-caller-role: ROLE_INTEGRATIONADMIN`、`x-csrf-token`および`Cookie` |
| Zoomの統合カタログUUID | `20012` |
| 接続制限 | 50ズーム接続 |

`x-csrf-token`の値は、`csrfToken`として統合管理ページのHTMLに埋め込まれています。 `Cookie`ヘッダーには、ログインしている管理者のセッションCookieが含まれています。

### 始める前に

- 統合管理者としてログインします。
- Zoomサーバー間OAuthアプリを作成します。 クライアントID、クライアントシークレット、およびアカウントIDを書き留めます。 また、Zoomスーパー管理者のメールアドレスも必要です。
- `GET /ctr/xtsas/canCreateAccount/25`を呼び出します。 別のZoom接続を作成できる場合は`true`を返します。

### 手順1 : Zoomの資格情報を保存する {#save-credentials}

接続を作成または更新する前に、このAPIを呼び出します。 コネクターがZoomへの接続に使用する資格情報が保存されます。

```
POST /ctr/authcred/uuid/20012
```

既存の接続を更新するには、`connectionId`クエリパラメーターを追加します。

```
POST /ctr/authcred/uuid/20012?connectionId={connectionId}
```

リクエスト本文は、JSONテキストとして資格情報です。 これは、入れ子になったオブジェクトではなく、JSONを含むJSON文字列です。 外側の引用符を含めます。

| キー | 概要 |
|---|---|
| `clientId` | ZoomアプリのクライアントID。 |
| `clientSecret` | Zoomアプリのクライアントシークレット。 この値は大文字と小文字が区別されます。 |
| `accountId` | ZoomアカウントID。 |
| `superAdmin` | Zoomスーパー管理者の電子メールアドレス。 |

サンプルリクエスト本文：

```
"{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}"
```

サンプル`200 OK`応答：

```json
{
  "code": 0,
  "description": "Success"
}
```

`code: 0`は、資格情報が保存されたことを意味します。

### 手順2 :ズーム接続を作成または更新する {#create-connection}

このAPIは、Zoom接続を作成します。 同じエンドポイントによって、既存の接続も更新されます。

```
POST /ctr/app/esconnect
```

リクエスト本文には次のフィールドがあります。

| フィールド | 必須 | 概要 |
|---|---|---|
| `UUID` | 可 | 統合カタログのUUID。 ズームに`20012`を使用します。 |
| `listOfConnections` | 可 | 作成する接続。 1つのアイテムを送信します。 |
| `listOfConnections[].name` | 可 | コネクターの表示名（例： `Zoom_Partner_X`）。 |
| `listOfConnections[].tag` | 可 | コネクターを作成するときに空の文字列(`""`)を送信します。 更新するときは省略します。 |
| `listOfConnections[].credentialsJson` | 可 | JSONテキストとしての資格情報。 手順1で送信した文字列と同じ文字列を使用します。 |
| `listOfConnections[].schedules` | 可 | 同期スケジュール。 `objectUUID` 10002、`priority` 1および`type` 1を送信します。 |
| `listOfConnections[].id` | 更新のみ | 更新する接続のID （例： `3474737`）。 |

サンプルリクエスト本文：

```json
{
  "UUID": 20012,
  "listOfConnections": [
    {
      "name": "Zoom_Example",
      "tag": "",
      "credentialsJson": "{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}",
      "schedules": [
        { "objectUUID": 10002, "priority": 1, "type": 1 }
      ]
    }
  ]
}
```

サンプル`200 OK`応答：

```json
[3474737]
```

応答は、新しい接続のIDを含むJSON配列です。 このIDは、手順3と4およびフォローアップの呼び出しで使用します。

### 作成と更新の比較

| 差 | 作成 | アップデート |
|---|---|---|
| `listOfConnections[].id` | 未送信 | 接続ID |
| `listOfConnections[].tag` | `""` | 未送信 |
| 手順1の資格情報の呼び出し | `POST /ctr/authcred/uuid/20012` | `POST /ctr/authcred/uuid/20012?connectionId={id}` |

### 手順3：接続を使用できるユーザーを設定する {#set-access}

このAPIは、接続を使用できるユーザーグループとカスタムの役割を定義します。

```
PUT /ctr/xtsa/{connectionId}/access
```

パスは1つの接続に単数形`xtsa`を使用します。 複数形`xtsas`は接続のコレクションです。

リクエスト本文はJSON配列です。 各アイテムは、1つのユーザーグループまたはカスタムの役割へのアクセスを許可します。

| フィールド | 必須 | 概要 |
|---|---|---|
| `accessType` | 可 | `USER_GROUP`または`CUSTOM_ROLE`。 |
| `accessId` | 可 | ユーザーグループまたはカスタムの役割のIDを表す文字列。 |

サンプルリクエスト本文：

```json
[
  { "accessType": "USER_GROUP", "accessId": "<groupId>" },
  { "accessType": "CUSTOM_ROLE", "accessId": "<roleId>" }
]
```

アクセスリストが保存されると、APIは本文を含まない`204 No Content`を返します。

>[!NOTE]
>
>リクエストによってアクセスリスト全体が置き換えられます。 それは付加にならない。 体の中にないものはアクセスできなくなります。 すべてのアクセスを削除するには、空の配列(`[]`)を送信します。

### 手順4：接続を有効または無効にする {#enable-disable}

このAPIは、接続のオン/オフを切り替えます。 接続を作成した後、状態を変更する必要がある場合に常に使用します。

```
POST /ctr/xtsas/{connectionId}/enable
```

パスは、list呼び出しやdelete呼び出しなど、複数形の`xtsas`を使用します。 手順3のアクセス呼び出しでは、単数形の`xtsa`を使用します。

| Pathパラメーター | タイプ | 説明 |
|---|---|---|
| `connectionId` | 数値 | 接続のID。 `GET /ctr/xtsas`から返された`id`で、手順2で返されたIDです。 |

リクエスト本文には次のフィールドがあります。

| フィールド | タイプ | 必須 | 概要 |
|---|---|---|---|
| `objectUUID` | 数値 | 可 | 接続の同期オブジェクト。 手順2の`schedules[].objectUUID`で送信した値と同じ`10002`を使用します。 |
| `operation` | 数値 | 可 | `1`を送信する |
| `val` | ブーリアン | 可 | 接続の新しい状態。 `false`を送信して接続を無効にします。 `true`を送信して有効にします。 |

接続を無効にするリクエスト本文の例：

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": false
}
```

接続を有効にするリクエスト本文の例：

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": true
}
```

接続を無効にするサンプルリクエスト：

```bash
curl -X POST 'https://learningmanagerstage1.adobe.com/ctr/xtsas/<connectionId>/enable' \
  -H 'accept: application/json' \
  -H 'content-type: application/json' \
  -H 'x-acap-caller-role: ROLE_INTEGRATIONADMIN' \
  -H 'x-csrf-token: <CSRF_TOKEN>' \
  -H 'Cookie: <SESSION_COOKIES>' \
  --data '{"objectUUID":10002,"operation":1,"val":false}'
```

新しい状態を確認するには、`GET /ctr/xtsas`を呼び出し、`id`によって接続を見つけ、`enabled`フラグを確認します。

>[!NOTE]
>
>`x-acap-caller-role`ヘッダーは、アクティブなプロファイルの役割と一致する必要があります。 これらのAPIには、`ROLE_INTEGRATIONADMIN`を使用します。

### 作成後の接続の管理

接続IDでは、次の呼び出しを使用できます。

| 目的 | 通話 |
|---|---|
| 接続を有効または無効にする | `POST /ctr/xtsas/{connectionId}/enable` |
| 1つの接続のアクセスリストを読み取る | `GET /ctr/xtsa/{connectionId}/access` |
| すべてのズーム接続の読み取りアクセス | `GET /ctr/xtsas/access?UUID=20012` |
| すべての接続を一覧表示します。 ズーム接続には`extsysRefId` 25があります。 | `GET /ctr/xtsas` |
| 接続を表示 | `GET /ctr/app/connection/{id}/object/10002` |
| 接続を完全に削除する | `DELETE /ctr/xtsas/{id}` |

>[!NOTE]
>
>view呼び出しは、クリアテキストでクライアントシークレットを返します。 クライアントシークレットは機密として扱い、表示されている場合はローテーションします。 HARファイルやコピーしたcURLコマンドを含め、セッションクッキー、CSRFトークン、または資格情報をコミットまたは共有しないでください。

### 統合でこれらのAPIを使用する

一般的なユースケースは、新しいアカウントまたはパートナーに対するZoom コネクターの自動設定です。

1. `GET /ctr/xtsas/canCreateAccount/25`を呼び出して、別の接続を作成できることを確認してください。
2. Zoomの資格情報を使用して`POST /ctr/authcred/uuid/20012`を呼び出します。
3. コネクター名、同じ資格情報の文字列、および同期スケジュールを使用して`POST /ctr/app/esconnect`を呼び出します。 応答から接続IDを読み取ります。
4. 接続を使用できるユーザーグループとカスタムの役割で`PUT /ctr/xtsa/{connectionId}/access`を呼び出します。
5. `val`を`true`または`false`に設定して`POST /ctr/xtsas/{connectionId}/enable`を呼び出し、接続を有効または無効にします。 次に`GET /ctr/xtsas`を呼び出し、`enabled`フラグを確認して状態を確認します。
6. 資格情報を後で変更するには、接続IDを使用して手順2と3を繰り返します。


