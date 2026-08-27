---
description: 設定、設定、イベント処理など、iframeを使用して学習者アシスタントをアプリに埋め込む方法を説明します
jcr-language: en_us
title: iFrameを埋め込むことで学習者アシスタントを統合
source-git-commit: 1549a4592b7a930631dcff6b2e75ec3a3d4f5592
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 1%

---


# iframeを使用したLearner Assistantの埋め込み

## 概要

Adobe Learning Manager(ALM)を使用すると、**学習者アシスタント**&#x200B;を学習者向けのアプリケーション（カスタムポータル、LMSフロントエンド、ラーニングハブなど）に直接埋め込むことができます。 標準のHTML `<iframe>`を使用しています。

iFrame経由で埋め込んだ場合、学習者アシスタントでは、次を含むすべての学習者アシスタント機能にアクセスできます。

* Orchestrator
* 回答担当者
* サポート情報担当者
* 学習パスエージェント

>[!IMPORTANT]
>
>iFrameの埋め込みにより、アプリケーションはLearner Assistantの基盤となるエージェントにフルアクセスできます。 ただし、アシスタントが発生するすべてのイベントの処理は、アプリケーション（「親アプリ」）が担当します。 例えば、学習者がアシスタントの応答内の引用文またはコースリンクをクリックすると、アシスタントによってイベントが発生します。このイベントを親アプリケーションが処理して、実際のナビゲーションを実行する必要があります。 学習者アシスタントは、アプリケーションに代わって操作することはありません。

## 前提条件

始める前に、次の点を確認してください。

* 学習者アシスタントが有効になっているALMテナント。 管理者設定ページから必要なカタログを設定します。
* 学習者（または管理者）セッションを認証するための有効なaccessToken。 アクセストークンを生成するには、[OAuth 2.0](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual#authentication-using-oauth-20)を使用した認証ページの手順に従います。 このページには、続行に必要なアクセストークンの認証および生成に必要な手順が含まれています。
* `<iframe>`をアプリケーションに埋め込み、ブラウザーのpostMessage APIを介して通信する機能。
* アプリケーションは、埋め込まれたiFrameからのメッセージをリッスンし、応答する必要があるため、親アプリケーションのフロントエンドコードの所有権。

## Learning Assistantの設定パラメーター

| パラメーター名 | 値 | 概要 |
|---|---|---|
| hostName | learningmanager.adobe.com | アプリケーションのホストドメインを指定します。 |
| accessToken | token123（実際のアクセストークン） | ユーザー・セッションの認証と承認に使用するトークン。 |

## iFrameを初期化

埋め込みiFrame設定ハンドシェイクを使用して、postMessage APIを介して設定を学習者アシスタントに渡します。

1. 親アプリケーションでは、学習アシスタントが`<iframe>`として埋め込まれます。
2. URLベースの設定が見つからない場合、Learning Assistantは親アプリケーションにALM_CHAT_REQUEST_CONFIGイベントを送信します。
3. 親アプリケーションは、設定ペイロードを含むALM_CHAT_CONFIGイベントで応答します。 以下に例を示します。

   ```json
   {
     "hostName": "learningmanager.adobe.com",
     "accessToken": "token123",
     "openByDefault": false,
     "isAdmin": false
   }
   ```

4. 初期化が正常に完了すると、学習者アシスタントがレンダリングされ、使用可能になります。

## iFrameイベントの概要

学習者アシスタントと親アプリケーションは、両方の方向でpostMessageイベントを介して通信します。

### 送信イベント（学習者アシスタントiFrameから親アプリ）

| イベント名 | 概要 | 渡されたパラメーター |
|---|---|---|
| ALM_CHAT_OPENED | チャットが開かれたときに発生します。 | -- |
| ALM_CHAT_CLOSED | チャットが閉じられたときに発生します。 | -- |
| ALM_CHAT_LO_REDIRECT | パーソナライズされた学習パスの概要ページに移動します。 | loId、loType、instanceId |
| ALM_CHAT_URL_REDIRECT | チャットメッセージで外部リンクがクリックされたときに発生します。 | URL |
| ALM_CHAT_REQUEST_CONFIG | 親アプリケーションから構成を要求します。 | -- |
| ALM_CHAT_WAITING_FOR_REPLY | アシスタントが要求を処理しているか、応答を待っていることを示します。 | isWaitingForReply |
| ALM_CHAT_PERSONALIZED_PATH_CREATED | 学習パスが保存されたときにトリガーされます。 | -- |

### 受信イベント（学習者アシスタントの親アプリ）

| イベント名 | 概要 | ペイロード |
|---|---|---|
| ALM_CHAT_CONFIG | アシスタントの初期化に必要な構成ペイロードを送信します。 | 設定オブジェクト |
| ALM_CHAT_OPEN | 学習者アシスタントを開きます。 | なし |
| ALM_CHAT_CLOSE | 学習者アシスタントを閉じます。 | なし |
| ASK_AI_ASSISTANT_QUERY | チャットウィンドウを開き、アシスタントにクエリを送信します。 | { query: &quot;Question text&quot; } |

## 親アプリケーションでのイベント処理要件

iFrame経由で学習者アシスタントを埋め込んでも、完全に自己完結型のウィジェットになるわけではありません。 親アプリケーションは、送信イベントをアクティブにリッスンし、適切なアクションを実行する必要があります。 アプリケーションは、少なくとも次のことを行う必要があります。

* ALM_CHAT_REQUEST_CONFIGをリッスンし、アシスタントが初期化できるようにALM_CHAT_CONFIGで応答します。
* ALM_CHAT_LO_REDIRECTを処理する：学習者がアシスタントの返信で引用文またはソースをクリックすると、アプリケーションはloId、loType、およびinstanceIdを受信し、学習者を正しいコースまたは学習目標に誘導する責任を負います。
* ALM_CHAT_URL_REDIRECTを処理する：学習者がチャットメッセージの外部リンクをクリックすると、アプリケーションがそのURLを受信し、そのURLを開くか、移動する必要があります（新しいタブなど）。
* オプションで、ALM_CHAT_OPENED / ALM_CHAT_CLOSED / ALM_CHAT_WAITING_FOR_REPLYをトラックして、アシスタントの状態を独自のUIに反映します（例えば、isWaitingForReplyがtrueのときに読み込みインジケーターを表示します）。
* オプションでALM_CHAT_OPEN / ALM_CHAT_CLOSE / ASK_AI_ASSISTANT_QUERYを使用して、アシスタントをプログラムで制御します。 例えば、アシスタントを開き、アプリケーションの別の場所にある&#x200B;**ヘルプ**&#x200B;ボタンからクエリを事前入力します。

## サポートが必要な場合

Adobeのカスタマーサクセスマネージャーに連絡して、技術的なチュートリアルを設定してください。
