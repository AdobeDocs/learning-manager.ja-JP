---
jcr-language: en_us
title: アプリケーションデベロッパーマニュアル
description: Learning Manager V1 API は非推奨になりました。 V1 API は、2021 年 2 月 28 日をもって終了します。今後はLearning Managerを操作する際に、V2 APIを使用することをお勧めします。
contentowner: jayakarr
source-git-commit: 956c119a5650b535a906157dc4d36f2ff075cf01
workflow-type: tm+mt
source-wordcount: '3385'
ht-degree: 62%

---



# アプリケーションデベロッパーマニュアル

>[!NOTE]
>
>Learning Manager V1 API は非推奨になりました。 今後はLearning Managerを操作する際に、V2 APIを使用することをお勧めします。


## 概要 {#overview}

[Adobe Learning Manager](http://www.adobe.com/in/products/learningmanager.html) は、クラウドホスト環境で学習者中心のセルフサービス学習を実現できる管理ソリューションです。Learning Manager API を使用すると、プログラムで Learning Manager リソースにアクセスして、他のエンタープライズアプリケーションと統合させることができます。アドビパートナーは、API を使用して機能を拡張したり、他のアプリケーションやサービスと統合したりすることで、Learning Manager の価値提案を高めることもできます。

### 使用シナリオ {#usagescenario}

デベロッパーは Learning Manager API を使用して、Learning Manager の機能を拡張した自己完結型アプリケーションを構築したり、Learning Manager を他のエンタープライズアプリケーションワークフローと統合したりできます。お好みのテクノロジーを使用して、Web アプリケーション、デスクトップクライアント、モバイルアプリを開発することもできます。 開発者は、Learning Manager内からアプリケーションデータにアクセスできます。 開発するアプリケーションのデプロイメントはLearning Managerプラットフォームの外部で行われ、アプリケーションの進化に合わせてソフトウェア開発ライフサイクルを完全に制御できます。 通常、Learning Manager アカウントで使用するアプリケーションは、顧客組織により開発されます。それらのアプリケーションは非公開で、その特定の顧客組織にのみ対応します。Learning Manager API を使用すると、アドビパートナーが、大勢の Learning Manager のお客様にご利用いただける汎用アプリケーションを構築することも可能です。

## Learning Manager API {#apidescription}

Learning Manager API は、REST の原則に基づいており、Learning Manager オブジェクトモデルの主要な要素をアプリケーションデベロッパーに HTTP で公開します。デベロッパーは、API エンドポイントと HTTP メソッドの詳細を知らなくても、さまざまな Learning Manager オブジェクト、その属性および相互関係について理解できます。モデルを理解できたら、API リクエストと API 応答の構造に関する基本を学び、API 全体でよく使用される一般的なプログラミング用語を覚えることは有益です。

さまざまなAPIエンドポイントとメソッドの詳細については、  [Learning Manager APIドキュメント](https://learningmanager.adobe.com/docs/primeapi/v2/).

## 学習者API

Adobeの学習マネージャー – 学習者APIを使用すると、ユーザーにカスタムの学習エクスペリエンスを提供できます。 これらのAPIを使用するには、有効なユーザートークンが必要です。このAPIは、完全にライセンスを取得し、登録された学習者が存在するワークフローの目的でのみ使用されます。

>[!IMPORTANT]
>
>ログインしていないユーザー/共有ユーザーやその他のケースをサポートするためのデータ取得には、そのまま使用しないでください。

ログインしていないユースケースでは、特別な処理が必要です。

**これらのAPIの適切な使用方法について質問がある場合は、ソリューションアーキテクチャチームにご連絡いただき、ソリューションを展開する前にソリューションアーキテクトがソリューションを確認します**.

## API 認証 {#apiauthentication}

Learning Manager に API 呼び出しを行うアプリケーションを作成する場合は、統合管理アプリを使用してアプリケーションを登録する必要があります。

Learning Manager API では、OAuth 2.0 フレームワークを使用して、クライアントアプリケーションを認証および承認します。

**手順**

**1.アプリケーションの設定**

適切なエンドポイントを使用するように、クライアントIDとクライアントシークレットを使用してアプリケーションを設定できます。 アプリケーションを登録すると、clientIdとclientSecretを取得できます。 Get URL は、SSO やアドビ ID などの事前設定されたアカウントを使用して、ブラウザーで Learning Manager ユーザーを認証する際に使用されます。

```
GET https://learningmanager.adobe.com/oauth/o/authorize?client_id=<Enter your clientId>&redirect_uri=<Enter a url to redirect to>&state=<Any String data>&scope=<one or more comma separated scopes>&response_type=CODE.
```

認証が成功すると、ブラウザーは上記の URL に示された redirect_uri にリダイレクトします。 パラメーター&#x200B;**コード**&#x200B;がリダイレクト URI と共に表示されます。

**2. コードから更新トークンを取得**

`POST https://learningmanager.adobe.com/oauth/token Content-Type: application/x-www-form-urlencoded`

POST リクエストの本文：

```
client_id: 
<enter your clientid>
 & 
 client_secret: 
 <enter your clientsecret>
  & 
  code: 
  <code from step 1></code>
 </enter>
</enter>
```

**3.** **更新トークンからアクセストークンを取得する**

アクセストークンを取得するためのURL:

POST [https://learningmanager.adobe.com/oauth/token/refresh](https://learningmanager.adobe.com/oauth/token/refresh) Content-Type: application/x-www-form-urlencoded

POST リクエストの本文：

```
client_id: 
<enter your clientid>
 & 
 client_secret: 
 <enter your clientsecret>
  & 
  refresh_token: 
  <refresh token>
   
  </refresh>
 </enter>
</enter>
```

**アクセストークンの詳細情報の確認用 URL**

`GET https://learningmanager.adobe.com/oauth/token/check?access_token=<access_token>`

**使用制限**

アクセストークンの有効期間は7日間です。 その後は、更新トークンを使用して新しいアクセストークンを生成する必要があります。 既存のアクセストークンが有効な場合に、更新トークンから新しいアクセストークンを生成すると、既存のトークンは返却されます。

Learning Manager API でよく使用される用語の一部が、参考のために以下に説明されています。

**Includes**

デベロッパーは、単一の API オブジェクトモデルと、そのモデルに関連付けられた複数のモデルにアクセスできます。 後続の関連するモデルにアクセスするには、各モデルと他のモデルとの関係性を理解する必要があります。 **含む** パラメータを使用すると、開発者は依存モデルにアクセスできます。 カンマ区切りを使用して複数のモデルにアクセスできます。 サンプルの使用方法および詳細： **includes**&#x200B;このページのサンプルAPIモデルのセクションを参照してください。

**API リクエスト**

API リクエストは、HTTP リクエストで実行できます。 エンドポイントやメソッドに応じて、デベロッパーは、GET、PUT、POST、DELETE、PATCH など、さまざまな HTTP 動詞を選択する場合があります。 リクエストの中には、クエリパラメーターを渡すことができるものもあります。 ユーザーは、特定のデータモデルをリクエストする場合に、JSON API 仕様に従って、関連するモデルをリクエストすることもできます。 一般的な API リクエストの構造は、[サンプルモデルの使用例](#main-pars_header_1415780624)で説明されています。

**API 応答**

クライアントにより API リクエストが実行されると、JSON API 仕様に従って SON ドキュメントの取得が行われます。 このレスポンスにはHTTPステータスコードも含まれています。開発者はこのコードを確認することで、アプリケーションロジックで適切な次のステップを実行することができます。 一般的なAPI応答の構造については、を参照してください。  [サンプルモデルの使用](#main-pars_header_1415780624).

**エラー**

API リクエストに失敗すると、エラー応答を取得します。 応答で返される HTTP ステータスコードに、エラーの性質が示されています。 エラーコードは、API リファレンス内の各モデルの番号を使って表示されます。 200、204、400、および404は、HTTPアクセスの問題を示すAPIで表現される一般的なエラーの一部です。

**フィールド**

API オブジェクトの属性や関係は、総称としてフィールドと呼ばれます。 詳しくは、[JSON API を参照してください。](http://jsonapi.org/format/#document-resource-object-fields) API呼び出しを行ってモデルから1つ以上の特定の属性を取得する際に、パラメーターとしてフィールドを使用できます。 フィールドパラメーターがない場合、API 呼び出しは、モデルから使用可能な属性をすべて取得します。 例えば、次のAPI呼び出しでは、[技能]=nameスキルモデルの名前属性のみを取得します。

https://learningmanager.adobe.com/primeapi/v2/users/{userId}/userSkills/{id}?include=skillLevel.skill&amp;fields[skill]=name

**ページネーション**

API リクエストにより、応答でオブジェクトの長いリストが返ってくる場合があります。 このような場合、デベロッパーはページネーション属性を使用して、結果を順番に取得できます。記録の範囲を各ページに示した複数のページが単位となります。 例えば、Learning Manager のページネーションの属性により、1 ページに表示する記録の最大数を設定できます。また、ページに表示される記録の範囲値を定義することもできます。

**並べ替え**

API モデルでは並べ替えが可能です。 モデルに基づいて、結果に適用するソートのタイプを選択します。 並べ替えは、昇順または降順で適用できます。 例えば、 `code sort=name`名前で昇順に並べ替えられます。 指定する場合 `code sort=-name`名前で降順にソートされます。 詳しくは、「 [詳細についてはJSON APIの仕様](http://jsonapi.org/format/#fetching-sorting).

## API の使用例 {#samplemodel}

開発者がスキル名、スキルレベルに割り当てられた最大ポイント数、学習者がそのスキルについて獲得したポイント数を取得する必要がある場合を考えてみましょう。

Learning Manager API の userSkill モデルは、デフォルトの属性として id、type、dateActived、dateCreated、pointsEarned で構成されています。したがって、デベロッパーが GET メソッドを使用して userSkill モデルの詳細を取得すると、デフォルト属性に付随する現在のデータが応答出力に表示されます。

ただし、このシナリオでは、デベロッパーはユーザーのスキル名と、スキルレベルに対するポイントを取得するものとします。 Learning Manager API により、関係フィールドを使用して関連情報にアクセスし、パラメーターを含めることが可能です。userSkill に関連付けられたモデルは、関連タグで取得できます。 これらのモデルを userSkill と一緒に呼び出して、関連付けられた各モデルの詳細を取得できます。 この情報を取得するには、 **`code include`** 関連する各モデルのドット（ピリオド）区切りの値を持つパラメータ。 カンマを区切り文字として使用して、ユーザーinclude=skillLevel.skill,courseなどの別のモデルを要求できます

**API 呼び出し**

`https://learningmanagerqe1.adobe.com/primeapi/v1/users/%7buserId%7d/userSkills/%7bid%7d?include=skillLevel.skill&fields%5bskill%5d=name&fields%5bskillLevel%5d=maxCredits&fields%5buserSkill%5d=pointsEarned`

例として、userId は 746783、userSkill ID は 746783_4426_1 とします。

**API 呼び出しの応答**

```
\{ 
 "links": {"self": "https://learningmanager.adobe.com/primeapi/v2/users/746783/userSkills/746783_4426_1?include=skillLevel.skill&fields[userSkill]=pointsEarned&fields[skillLevel]=maxCredits&fields[skill]=name"}, 
 "data": { 
 "id": "746783_4426_1", 
 "type": "userSkill", 
 "attributes": {"pointsEarned": 5}, 
 "links": {"self": "https://learningmanager.adobe.com/primeapi/v2/users/746783/userSkills/746783_4426_1"} 
 }, 
 "included": [ 
 { 
 "id": "4426", 
 "type": "skill", 
 "attributes": {"name": "Java"}, 
 "links": {"self": "https://learningmanager.adobe.com/primeapi/v2/skills/4426"} 
 }, 
 { 
 "id": "4426_1", 
 "type": "skillLevel", 
 "attributes": {"maxCredits": 10} 
 } 
 ] 
} 
```

## Learning Manager モデル {#models}

Learning Manager API を使用すると、開発者は Learning Manager オブジェクトに RESTful リソースとしてアクセスできます。 各 API エンドポイントは、通常、バッジなどのオブジェクトインスタンスといったリソースを指しており、そのようなオブジェクトのコレクションを指すこともあります。 デベロッパーは、PUT、GET、POST、DELETE などの HTTP 動詞を使用して、それらのオブジェクト（コレクション）に対する CRUD 操作を実行します。

+++V1 API

次の図は、V1 API の Learning Manager オブジェクトモデルのさまざまな要素を示しています。

![](assets/er-diag-primemodels.png)

次の表では、Learning Manager V1オブジェクトモデルの様々な要素について説明します。

<table border="1" cellspacing="0" cellpadding="0">
 <tbody>
  <tr>
   <td>
    <p><strong>シリアル番号</strong></p></td>
   <td>
    <p><strong>Learning Manager オブジェクト</strong></p></td>
   <td>
    <p><strong>説明</strong></p></td>
  </tr>
  <tr>
   <td>
    <p>1.      </p></td>
   <td>
    <p>user</p></td>
   <td>
    <p>Learning Manager における主要なモデル。通常、学習目標を使用する、組織の内部学習者や外部学習者を指す。 ただし、学習者という役割に加えて、作成者や管理者など、他の役割を果たす場合もある。インライン属性には、ユーザー ID、タイプ、電子メールなどがある </p></td>
  </tr>
  <tr>
   <td>
    <p>2.      </p></td>
   <td>
    <p>course</p></td>
   <td>
    <p>Learning Manager でサポートされる学習オブジェクトの 1 つで、1 つ以上のモジュールで構成される。 </p></td>
  </tr>
  <tr>
   <td>
    <p>3.       </p></td>
   <td>
    <p>module</p></td>
   <td>
    <p>Learning Manager で学習オブジェクトを形成する構成要素を指す。モジュールには、クラスルーム、バーチャルクラスルーム、アクティビティおよびセルフペースなど、4 つの異なるタイプがある。 このモジュールモデルを使用して、アカウント内にあるすべてのモジュールの詳細を取得する </p></td>
  </tr>
  <tr>
   <td>
    <p>4.      </p></td>
   <td>
    <p>certification</p></td>
   <td>
    <p>コースを完了した学習者には、資格認定が付与される。 資格認定を使用するためには、アプリケーションでコースが必要である </p></td>
  </tr>
  <tr>
   <td>
    <p>5.       </p></td>
   <td>
    <p>learning program</p></td>
   <td>
    <p>ユーザーの特定の学習要件を満たす独自に設計されたコースを指す。 通常、学習プログラムは、個々のコースにわたる学習目標を推進するために使用される。 </p></td>
  </tr>
  <tr>
   <td>
    <p>6.      </p></td>
   <td>
    <p>badge</p></td>
   <td>
    <p>学習者がコースを進めていく中で、指定のマイルストーンに到達したときに得られる功績の証を指す </p></td>
  </tr>
  <tr>
   <td>
    <p>7.      </p></td>
   <td>
    <p>skill</p></td>
   <td>
    <p>スキルモデルは、レベルとクレジットで構成される。 学習者は関係のあるコースを完了すると、スキルを取得できる </p></td>
  </tr>
  <tr>
   <td>
    <p>8.      </p></td>
   <td>
    <p>certificationEnrollment</p></td>
   <td>
    <p>このモデルでは、ユーザーによる 1 つの資格認定への登録の詳細を表す</p></td>
  </tr>
  <tr>
   <td>
    <p>9.  </p></td>
   <td>
    <p>courseEnrollment</p></td>
   <td>
    <p>このモデルでは、ユーザーによる 1 つのコースへの登録の詳細を表す </p></td>
  </tr>
  <tr>
   <td>
    <p>10.  </p></td>
   <td>
    <p>courseInstance</p></td>
   <td>
    <p>1 つまたは複数のインスタンスを関連付けることができる。 コースインスタンスを取得できます </p></td>
  </tr>
  <tr>
   <td>
    <p>11.  </p></td>
   <td>
    <p>courseSkill</p></td>
   <td>
    <p>courseSkillモデルは、コースを完了することで達成される1つのスキルの進捗状況を指定します。</p></td>
  </tr>
  <tr>
   <td>
    <p>12.  </p></td>
   <td>
    <p>courseModule</p></td>
   <td>courseModuleモデルは、モジュールをコースに含める方法を指定します。 例えば、モジュールがプリテスト用とコンテンツ用のどちらに使用されるかを指定します。</td>
  </tr>
  <tr>
   <td>
    <p>13.  </p></td>
   <td>learningProgramInstance</td>
   <td>
    <p>学習プログラムは、学習プログラムの類似した特性を持つ複数のインスタンスやカスタマイズされたインスタンスで構成できる </p></td>
  </tr>
  <tr>
   <td>
    <p>14.  </p></td>
   <td>
    <p>job aid</p></td>
   <td>
    <p>作業計画書とは、登録や完了条件なしに学習者がアクセスできる学習コンテンツを指す。 更新日、ステート、ID 情報に加えて、作業計画書のバージョン、作成者、スキルレベルなどの関連するモデルを使用できる </p></td>
  </tr>
  <tr>
   <td>
    <p>15.  </p></td>
   <td>
    <p>jobAidVersion</p></td>
   <td>
    <p>作業計画書には、コンテンツの改訂数とアップロード数に基づいて、1 つまたは複数のバージョンを関連付けられる。 このモデルは、1 つの作業計画書のバージョンの詳細を表す </p></td>
  </tr>
  <tr>
   <td>
    <p>16.  </p></td>
   <td>
    <p>learningProgramInstanceEnrollment</p></td>
   <td>
    <p>学習プログラムは、1 つまたは複数のインスタンスで構成される。 学習プログラムインスタンスへの登録は学習者自身が行うことも、管理者が割り当てることもできる。 このモデルは、ユーザーによる 1 つの学習プログラムインスタンスへの登録の詳細を表す </p></td>
  </tr>
  <tr>
   <td>
    <p>17.  </p></td>
   <td>
    <p>moduleVersion</p></td>
   <td>
    <p>モジュールには、改訂されたコンテンツアップロードに基づいて、1 つ以上のバージョンを含めることができる。 このモデルを使用して、1 つのモジュールバージョンに関する特定の情報を取得する </p></td>
  </tr>
  <tr>
   <td>
    <p>18.  </p></td>
   <td>
    <p>skillLevel</p></td>
   <td>
    <p>1 つまたは複数のコースで構成されており、レベルとそれに関連するクレジットを取得するために使用される </p></td>
  </tr>
  <tr>
   <td>
    <p>19.  </p></td>
   <td>
    <p>userBadge</p></td>
   <td>
    <p>UserBadgeは、単一のバッジを単一のユーザーに関連付けます。 いつ達成したかや、assertionUrl 等の詳細を含む </p></td>
  </tr>
  <tr>
   <td>
    <p>20.  </p></td>
   <td>
    <p>userSkill</p></td>
   <td>
    <p>UserSkillは、1人のユーザーが1つのスキルレベルをどの程度達成しているかを示します。</p></td>
  </tr>
 </tbody>
</table>

+++

+++V2 API

以下は、V2 API の Learning Manager のさまざまな要素を示したクラス図です。

![](assets/v2api-class-diagram.jpg)

<table>
 <tbody>
  <tr>
   <th><b>Learning Manager オブジェクト</b></th>
   <th><b>説明</b></th>
  </tr>
  <tr>
   <td>account</td>
   <td>Learning Managerのお客様の詳細情報をカプセル化します。</td>
  </tr>
  <tr>
   <td><code>
     badge
    </code></td>
   <td>学習者がコースを進めていく中で、指定のマイルストーンに到達したときに得られる功績の証を指す <br></td>
  </tr>
  <tr>
   <td><code>
     catalog
    </code></td>
   <td>カタログは、学習目標のコレクションです。</td>
  </tr>
  <tr>
   <td><code>
     user
    </code></td>
   <td>Learning Manager における主要なモデル。通常、学習目標を使用する、組織の内部学習者や外部学習者を指す。 ただし、学習者という役割に加えて、作成者や管理者など、他の役割を果たす場合もある。 インライン属性には、ユーザー ID、タイプ、電子メールなどがある </td>
  </tr>
  <tr>
   <td>resource</td>
   <td>モジュールでカプセル化しようとする各コンテンツリソースをモデル化するために使用される。 内にカプセル化されたすべてのリソース <code>
     an
    </code> <code>
     loResource
    </code> は、学習目標の点では同等ですが、配信タイプやコンテンツのロケールの点では互いに異なります。<br></td>
  </tr>
  <tr>
   <td>userNotification</td>
   <td>学習者に関連した通知情報が含まれる<br></td>
  </tr>
  <tr>
   <td>userSkill</td>
   <td>UserSkillは、1人のユーザーが1つのスキルレベルをどの程度達成しているかを示します。<br></td>
  </tr>
  <tr>
   <td>userBadge</td>
   <td>UserBadgeは1つのバッジを関連付けます <code>
     with
    </code> 1人のユーザー。 それはいつ達成したかといった詳細を含んでいる <code>
     assertionUrl
    </code> など。 <br></td>
  </tr>
  <tr>
   <td>skill</td>
   <td>スキルモデルは、レベルとクレジットで構成される。 学習者は関係のあるコースを完了すると、スキルを取得できる <br></td>
  </tr>
  <tr>
   <td>skillLevel</td>
   <td>1 つまたは複数のコースで構成されており、レベルとそれに関連するクレジットを取得するために使用される <br></td>
  </tr>
  <tr>
   <td>learningObject</td>
   <td>ユーザーが登録して学習できる、さまざまな種類のオブジェクトを抽象化したもの。 現在、Learning Managerには4種類の学習目標（コース、資格認定、学習プログラム）があります <code>
     and
    </code> 作業計画書<br></td>
  </tr>
  <tr>
   <td>learningObjectInstance<br></td>
   <td>学習目標の特定のインスタンス<br></td>
  </tr>
  <tr>
   <td>learningObjectResource</td>
   <td>これは～の概念と同等である <code>
     module
    </code>. 1つのコースは1つから構成されます <code>
     of
    </code> その他のモジュール。 Learning Manager では、モジュールをさまざまな同等の方法で配信できる。したがって、 <code>
     loResource
    </code> 基本的には、これらと同等のリソースをすべてカプセル化します。<br></td>
  </tr>
  <tr>
   <td>loResourceGrade<br></td>
   <td>ユーザーが登録した学習目標のコンテキストで特定のリソースを使用した結果をカプセル化する。 期間などの情報が表示されます <code>
     user
    </code> リソースでは、ユーザーが行った進捗率、合格/不合格のステータス、および関連するクイズでユーザーが取得したスコア。<br></td>
  </tr>
  <tr>
   <td>calendar<br></td>
   <td>カレンダーオブジェクトは、 <code>
     upcoming classroom
    </code> またはユーザーが登録できるバーチャルクラスルームコース。<br></td>
  </tr>
  <tr>
   <td>l1FeedbackInfo<br></td>
   <td>学習目標に関連したフィードバックの質問に対して、学習者が提出した回答をカプセル化する。 学習者からフィードバックを収集するように設定されている場合、通常は、ユーザーが学習目標を完了した後に収集されます。<br></td>
  </tr>
  <tr>
   <td>enrollment<br></td>
   <td>この抽象化したものにより、特定の学習目標のインスタンスに対する、特定のユーザーの割り当てに関連したトランザクションの詳細をカプセル化する。<br></td>
  </tr>
 </tbody>
</table>

+++

オブジェクトの属性と関係のリスト。

+++account

**属性**
dateCreated\
gamificationEnabled\
id\
locale\
loginUrl\
logoUrl\
name\
サブドメイン\
themeData\
timeZoneCode（タイムゾーン）

**関連付け**
contentLocales(localizationMetadata)\
gamificationLevels(gamificationLevel)\
timeZones(timeZone)\
uiLocales(localizationMetadata)

+++

+++badge

**属性**
id\
imageUrl\
name\
state（状態）

+++

+++catalog

**属性**
dateCreated\
dateUpdated\
説明\
id\
isDefault\
isInternalSearchable\
isListable\
name\
state（状態）

+++

+++data

**属性**
id\
名前

+++

+++ゲーミフィケーション

**属性**
カラー\
name\
ポイント

+++

+++learningObject

**属性**
authorNames\
dateCreated\
datePublished\
dateUpdated\
effectivenessIndex\
enrollmentType\
id\
imageUrl\
isExternal\
isSubLoOrderEnforced\
loType\
state（状態）\
タグ

**関連付け**
authors(user)\
enrollment(learningObjectInstanceEnrollment)\
instances(learningObjectInstance)\
prerequisiteLOs(learningObject)\
skills(learningObjectSkill)\
subLOs(learningObject)\
supplementaryLOs(learningObject)\
supplementaryResources(resource)

+++

+++learningObjectInstance

**属性**
completionDeadline\
dateCreated\
enrollmentCount\
id\
isDefault\
座席の上限\
state（状態）\
効力

**関連付け**
バッジ（バッジ）\
l1FeedbackInfo(feedbackInfo)\
learningObject(learningObject)\
loResources(learningObjectResource)\
localizedMetadata(localizationMetadata)\
subLoInstances(learningObjectInstance)

+++

+++learningObjectInstanceEnrollment

**属性**
dateComplete\
dateEnrolled\
dateBegin\
hasPassed\
id\
progressPercent\
スコア\
state（状態）

**関連付け**
learner(user)\
learnerBadge(userBadge)\
learningObject(learningObject)\
loInstance(learningObjectInstance)\
loResourceGrades(learningObjectResourceGrade)

+++

+++learningObjectResource

**属性**
externalReporting\
id\
loResourceType\
resourceType\
version

**関連付け**
learningObject(learningObject)\
loInstance(learningObjectInstance)\
localizedMetadata(localizationMetadata)\
resources(resource)

+++

+++learningObjectResourceGrade

**属性**
dateComplete\
dateBegin\
dateSuccess\
duration\
hasPassed\
id\
progressPercent\
スコア

**関連付け**
loResource(learningObjectResource)

+++

+++learningObjectSkill

**属性**
クレジット\
id\
**関連付け**
learningObject(learningObject)\
skillLevel(skillLevel)

+++

+++recommendation

**属性**
id\
理由

**関連付け**
learningObject(learningObject)

+++

+++resource

**属性**
authorDesiredDuration\
completionDeadline\
contentStructureInfoUrl\
contentType\
contentZipSize\
contentZipUrl\
dateCreated\
dateStart\
desiredDuration\
downloadUrl\
extraData\
hasQuiz\
hasToc\
id\
instructorNames\
isDefault\
locale\
location\
name\
onlyQuiz\
reportingInfo\
reportingType\
座席の上限

+++

+++skill

**属性**
description\
id\
name\
state（状態）

**関連付け**
levels(skillLevel)

+++

+++skillLevel

**属性**
id\
レベル\
maxCredit\
name\
**関連付け**
バッジ（バッジ）\
スキル

+++

+++user

**属性**
avatarUrl\
バイオ\
contentLocale（コンテンツのロケール）\
電子メール\
フィールド\
id\
name\
pointsEarned（獲得ポイント）\
profile（プロファイル）\
役割\
state（状態）\
timeZoneCode（タイムゾーン）\
uiLocale（UI のロケール）

**関連付け**
account(account)\
manager（ユーザー）

+++

+++userBadge

**属性**
assertionUrl\
dateAchieved\
id\
modelType

**関連付け**
バッジ（バッジ）\
learner(user)\
model(learningObject)

+++

+++userCalendar

**属性**
コース\
courseType\
dateStart\
登録済み\
id\
月\
四半期

**関連付け**
containerLO(learningObject)\
course(learningObject)

+++

+++userNotification

**属性**
actionTaked\
チャンネル\
dateCreated\
id\
message\
modelIds\
modelNames\
modelTypes\
read\
role

+++

+++userSkill

**属性**
dateAchieved\
dateCreated\
id\
pointsEarned（獲得ポイント）

**関連付け**
learnerBadge(userBadge)\
learningObject(learningObject)\
skillLevel(skillLevel)\
user(user)

+++

## アプリケーション開発プロセス {#registration}

## 前提条件 {#prerequisites}

デベロッパーは、Learning Manager で体験版アカウントを作成して、そのアカウント内すべての役割にフルアクセス権を持つ必要があります。アプリケーションの作成にあたって、デベロッパーはユーザーやコースを作成して、アカウントを適切な状態にする必要があります。そのようにして、開発中のアプリケーションがサンプルデータにアクセスできるようにします。

## クライアント ID とシークレットの作成 {#createclientidandsecret}

1. イン **統合管理者** ログイン、クリック **[!UICONTROL アプリケーション]** をクリックします。

   ![](assets/application-development-menu.png)

   *統合管理者のアプリケーションを選択*

1. クリック **[!UICONTROL 登録]** ページの右上隅に、アプリケーションの詳細が表示されます。 登録ページが表示されます。

   ![](assets/register-application.png)

   *アプリケーションの登録*

   このページにあるフィールドは、すべて入力必須です。

   **アプリケーション名**：アプリケーション名を入力します。 同じアプリケーション名を使用する必要はありません。任意の有効な名前を使用できます。

   **URL**：アプリケーションがホストされる正確な URL がわかっている場合は、その URL を指定できます。 わからない場合は、会社の URL を指定できます。 このフィールドには、有効なURL名が必須です。

   **リダイレクトドメイン**：OAuth 認証後に Learning Manager アプリケーションをリダイレクトするアプリケーションのドメイン名を入力します。複数のURLを指定できますが、次のような有効なURLを使用する必要があります `http://google.com`, `http://yahoo.com` など。

   **説明：** アプリケーションの簡単な説明を入力します。

   **スコープ：** アプリケーションの範囲を定義する4つのオプションのいずれかを選択します。 ここに示された選択に基づき、アプリケーションから、Learning Manager API エンドポイントへのアクセスが可能になります。例えば、 **学習者ロールの読み取りアクセス**&#x200B;を使用している場合、Learning Managerの学習者APIエンドポイントのすべてで、アプリケーションから読み取り専用のアクセスが可能になります。

   **このアカウントのみですか？**\
   **はい**  – はい選択した場合、他のアカウント管理者がアプリケーションを見ることはできません。\
   **いいえ** - 「いいえ」を選択した場合、他のアカウント管理者も、このアプリケーションにアクセスできますが、このアプリケーションにアクセスするには、アプリケーションidを使用する必要があります。 アプリケーションIDが生成され、Learning Managerアプリケーションの編集モードに表示されます。

   以下を選択した場合 **管理者ロールの読み取りおよび書き込みアクセス** 適用範囲としてアプリケーションを登録し、 **管理者ロールの読み取りアクセス権** apiのオーサリング中も、アプリケーションの書き込みアクセス権を維持できます。これは、アプリケーションの登録スコープが認証ワークフローに優先するためです。

1. 登録ページで詳細を入力したら、右上隅の&#x200B;**[!UICONTROL 「登録」]**&#x200B;をクリックします。

## アプリケーション開発とテスト {#applicationdevelopmentandtesting}

Learning Manager API は、デベロッパーがさまざまなアプリケーションを構築する際に使用できます。デベロッパーは、アカウントが有効なユーザーとコースで構成されていることを確認する必要があります。 複数のダミーユーザーやコースを作成して、体験版アカウントでアクティビティをシミュレートして、アプリケーションの機能をテストできます。

## アプリケーションデプロイメント {#applicationdeployment}

実用アカウントでは、Learning Manager の管理者や統合管理者が、組織内のユーザーにアプリケーションを使用する権限を与えるようにすることをお勧めします。アプリケーションのテストが完了して、実用の準備が整ったら、実用アカウントの管理者に通知します。 管理者が、実用アカウントでアプリケーションの新しいクライアント ID とクライアントシークレットを生成し、それらを安全に組み込めるよう、アプリケーション内で必要な手順を取るのが理想的です。 アプリケーションをデプロイする実際の手順は、企業によって異なります。デプロイを完了するには、組織の Learning Manager 管理者が、組織内の IT/IS 部門からサポートを受ける必要があります。

## 外部アプリケーションの承認 {#externalapplicationapproval}

をクリックすると、外部アプリケーションを追加できます。 **承認** 右上隅に **アプリケーション** ページです。 外部アプリケーション ID を入力し、**「保存」**&#x200B;をクリックします。

![](assets/add-external-application.png)

*外部アプリケーションの追加と承認*

## よくある質問

+++Learning Managerはeコマースと統合されていますか？

Adobe Learning Manager に e コマース統合機能はありません。ただし、独自のヘッドレス LMS を作成し、e コマース機能を実装できるように、API を提供しています。
+++
