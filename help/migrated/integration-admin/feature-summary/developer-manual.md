---
jcr-language: en_us
title: アプリケーションデベロッパーマニュアル
description: Learning Manager V1 APIは非推奨になりました。 V1 APIは、2021年2月28日をもって終了します。 今後はLearning Managerを操作する際に、V2 APIを使用することをお勧めします。
contentowner: jayakarr
source-git-commit: ab6737e8b43222a6538921b0628a504a5f15859d
workflow-type: tm+mt
source-wordcount: '3279'
ht-degree: 0%

---



# アプリケーションデベロッパーマニュアル

Learning Manager V1 APIは非推奨になりました。 V1 APIは、2021年2月28日をもって終了します。 今後はLearning Managerを操作する際に、V2 APIを使用することをお勧めします。

## 概要 {#overview}

[Learning ManagerのAdobe](http://www.adobe.com/in/products/learningmanager.html) は、クラウドホスト環境で学習者中心のセルフサービス学習管理ソリューションです。 Learning Manager APIを使用すると、プログラムでLearning Managerリソースにアクセスして、他のエンタープライズアプリケーションと統合することができます。 Adobeパートナーは、APIを使用して機能を拡張したり、他のアプリケーションやサービスと統合したりすることで、Learning Managerの価値提案を高めることもできます。

### 使用シナリオ {#usagescenario}

Learning Manager APIを使用すると、開発者はLearning Managerの機能を拡張する自己完結型アプリケーションを構築したり、Learning Managerを他のエンタープライズアプリケーションワークフローと統合したりできます。 お好みのテクノロジーを使用して、webアプリケーション、デスクトップクライアント、またはモバイルアプリを開発できます。 開発者は、Learning Manager内からアプリケーションデータにアクセスできます。 開発するアプリケーションのデプロイメントはLearning Managerプラットフォームの外部で行われ、アプリケーションの進化に合わせてソフトウェア開発ライフサイクルを完全に制御できます。 通常、Learning Managerアカウントで使用するアプリケーションは、顧客組織によって開発されます。これらのアプリケーションは非公開で、その特定の顧客組織でのみ使用されます。 また、Adobeパートナーは、Learning Manager APIを使用して、Learning Managerの多数のお客様が使用できる汎用アプリケーションを構築することもできます。

## Learning Manager API {#apidescription}

Learning Manager APIは、RESTの原則に基づいており、Learning Managerオブジェクトモデルの主要な要素をアプリケーション開発者にHTTPで公開します。 開発者は、APIエンドポイントとHTTPメソッドの詳細を知らなくても、さまざまなLearning Managerオブジェクト、その属性および相互関係について理解できます。 モデルを理解できたら、APIのリクエストと応答の構造に関する基本的な理解と、API全体で一般的に使用される一般的なプログラミング用語を習得すると役立ちます。

さまざまなAPIエンドポイントとメソッドの詳細については、  [Learning Manager APIドキュメント](https://learningmanager.adobe.com/docs/primeapi/v2/).

## API認証 {#apiauthentication}

Learning ManagerにAPI呼び出しを行うアプリケーションを作成する場合は、統合管理アプリを使用してアプリケーションを登録する必要があります。

Learning Manager APIでは、OAuth 2.0フレームワークを使用して、クライアントアプリケーションを認証および承認します。

**手順**

**1. アプリケーションの設定**

適切なエンドポイントを使用するように、クライアントIDとクライアントシークレットを使用してアプリケーションを設定できます。 アプリケーションを登録すると、clientIdとclientSecretを取得できます。 Get URLは、SSOやAdobe IDなどの事前設定されたアカウントを使用して、ブラウザーでLearning Managerユーザーを認証する際に使用されます。

```
GET https://learningmanager.adobe.com/oauth/o/authorize?client_id=<Enter your clientId>&redirect_uri=<Enter a url to redirect to>&state=<Any String data>&scope=<one or more comma separated scopes>&response_type=CODE.
```

認証が成功すると、ブラウザーは上記のURLに記載されているredirect_uriにリダイレクトされます。 パラメーター **コード** リダイレクトURIとともに追加されます。

**2. コードから更新トークンを取得**

`POST https://learningmanager.adobe.com/oauth/token Content-Type: application/x-www-form-urlencoded`

POSTリクエストの本文：

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

POSTリクエストの本文：

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

**アクセストークンの詳細情報の確認用URL**

`GET https://learningmanager.adobe.com/oauth/token/check?access_token=<access_token>`

**使用制限**

アクセストークンの有効期間は7日間です。 1日後には、更新トークンを使用して新しいアクセストークンを生成する必要があります。 既存のアクセストークンが有効な状態で、更新トークンから新しいアクセストークンを生成すると、既存のトークンが返されます。

Learning Manager APIでよく使用される用語の一部が、参考のために以下に説明されています。

**含む**

開発者は、単一のAPIオブジェクトモデルにアクセスできるだけでなく、そのモデルに関連付けられた複数のモデルにもアクセスできます。 後続の関連モデルにアクセスするには、各モデルと他のモデルとの関係を理解する必要があります。 **含む** パラメータを使用すると、開発者は依存モデルにアクセスできます。 カンマ区切りを使用して複数のモデルにアクセスできます。 サンプルの使用方法および詳細： **includes**&#x200B;このページのサンプルAPIモデルのセクションを参照してください。

**APIリクエスト**

APIリクエストは、HTTPリクエストを作成することで行うことができます。 エンドポイントやメソッドによっては、開発者はGET、PUT、POST、DELETE、PATCHなどの様々なHTTP動詞を選択することができます。 一部のリクエストでは、クエリパラメーターを渡すことができます。 特定のデータモデルをリクエストする際、ユーザーはJSON API仕様に記載されている関連モデルをリクエストすることもできます。 一般的なAPIリクエストの構造については、を参照してください。 [サンプルモデルの使用](#main-pars_header_1415780624).

**API応答**

クライアントからAPI要求があった場合、JSON API仕様に従ってSON文書が取得されます。 このレスポンスにはHTTPステータスコードも含まれています。開発者はこのコードを確認することで、アプリケーションロジックで適切な次のステップを実行することができます。 一般的なAPI応答の構造については、を参照してください。  [サンプルモデルの使用](#main-pars_header_1415780624).

**エラー**

APIリクエストが失敗すると、エラー応答が取得されます。 応答で返されるHTTPステータスコードは、エラーの性質を示しています。 エラーコードは、APIリファレンスで各モデルの番号で表されます。 200、204、400、および404は、HTTPアクセスの問題を示すAPIで表現される一般的なエラーの一部です。

**フィールド**

APIオブジェクトの属性とその関係を総称してフィールドと呼びます。 詳しくは、「 [詳しくは、 JSON APIを参照してください。](http://jsonapi.org/format/#document-resource-object-fields) API呼び出しを行ってモデルから1つ以上の特定の属性を取得する際に、パラメーターとしてフィールドを使用できます。 Fieldsパラメーターが指定されていない場合、API呼び出しはモデルから使用可能なすべての属性を取得します。 例えば、次のAPI呼び出しでは、[技能]=nameスキルモデルの名前属性のみを取得します。

https://learningmanager.adobe.com/primeapi/v2/users/{userId}/userSkills/{id}?include=skillLevel.skill&amp;fields[skill]=name

**ページ設定**

APIリクエストにより、応答で返されるオブジェクトの長いリストが生成される場合があります。 このような場合、ページ番号属性を使用すると、開発者は、各ページに一定範囲のレコードが含まれている複数のページに関して、結果を順番に取得できます。 例えば、Learning Managerのページネーション属性により、1ページに表示するレコードの最大数を設定できます。 また、ページに表示するレコードの範囲値を定義することもできます。

**並べ替え**

並べ替えは、APIモデルで許可されています。 モデルに基づいて、結果に適用するソートのタイプを選択します。 並べ替えは、昇順または降順で適用できます。 例えば、 `code sort=name`名前で昇順に並べ替えられます。 指定する場合 `code sort=-name`名前で降順にソートされます。 詳しくは、「 [詳細についてはJSON APIの仕様](http://jsonapi.org/format/#fetching-sorting).

## APIの使用方法の図 {#samplemodel}

開発者がスキル名、スキルレベルに割り当てられた最大ポイント数、学習者がそのスキルについて獲得したポイント数を取得する必要がある場合を考えてみましょう。

Learning Manager APIのuserSkillモデルは、デフォルト属性として、id、type、dateAchieved、dateCreated、pointsEarnedで構成されます。 そのため、開発者がuserSkillモデルの詳細を取得するためにGETメソッドを使用すると、デフォルト属性に関する最新のデータがレスポンス出力に表示されます。

ただし、このシナリオでは、開発者はユーザーのスキル名とスキルレベルのポイントを取得する必要があります。 Learning Manager APIでは、関係フィールドを使用してこの関連情報にアクセスし、パラメーターを含めることができます。 userSkillの関連モデルは、関連タグで取得されます。 これらのモデルをuserSkillと共に呼び出すことで、関連付けられた各モデルの詳細を取得できます。 この情報を取得するには、 **`code include`** 関連する各モデルのドット（ピリオド）区切りの値を持つパラメータ。 カンマを区切り文字として使用して、ユーザーinclude=skillLevel.skill,courseなどの別のモデルを要求できます

**API呼び出し**

`https://learningmanagerqe1.adobe.com/primeapi/v1/users/%7buserId%7d/userSkills/%7bid%7d?include=skillLevel.skill&fields%5bskill%5d=name&fields%5bskillLevel%5d=maxCredits&fields%5buserSkill%5d=pointsEarned`

たとえば、userIdを746783に、userSkills idを746783_4426_1に設定できます。

**API呼び出しの応答**

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

## Learning Managerモデル {#models}

Learning Manager APIを使用すると、開発者はLearning ManagerオブジェクトにRESTfulリソースとしてアクセスできます。 各APIエンドポイントは、リソース、通常はバッジなどのオブジェクトインスタンス、またはそのようなオブジェクトのコレクションを表します。 次に、PUT、GET、POST、DELETEなどのHTTP動詞を使用して、これらのオブジェクト（コレクション）に対するCRUD操作を実行します。

+++V1 API

次の図は、V1 APIのLearning Managerオブジェクトモデルのさまざまな要素を示しています。

![](assets/er-diag-primemodels.png)

次の表では、Learning Manager V1オブジェクトモデルの様々な要素について説明します。

<table border="1" cellspacing="0" cellpadding="0">
 <tbody>
  <tr>
   <td>
    <p><strong>シリアル番号</strong></p></td>
   <td>
    <p><strong>Learning Managerオブジェクト</strong></p></td>
   <td>
    <p><strong>説明</strong></p></td>
  </tr>
  <tr>
   <td>
    <p>1.      </p></td>
   <td>
    <p>user</p></td>
   <td>
    <p>Learning Managerにおける主要なモデルはユーザーです。 通常、ユーザーは、学習目標を使用する組織の内部学習者または外部学習者です。 ただし、学習者の役割に加えて、作成者やマネージャーなど、他の役割を果たす場合もあります。 インライン属性には、ユーザーID、タイプ、電子メールなどがあります。 </p></td>
  </tr>
  <tr>
   <td>
    <p>2.      </p></td>
   <td>
    <p>コース</p></td>
   <td>
    <p>Learning Managerでサポートされる学習オブジェクトの1つで、1つ以上のモジュールで構成される。 </p></td>
  </tr>
  <tr>
   <td>
    <p>3.      </p></td>
   <td>
    <p>module</p></td>
   <td>
    <p>モジュールは、Learning Managerで学習オブジェクトを作成するための構成要素です。 モジュールには、クラスルーム、バーチャルクラスルーム、アクティビティ、セルフペースなど、4つの異なるタイプがあります。 このモジュールモデルを使用して、アカウント内のすべてのモジュールの詳細を取得する </p></td>
  </tr>
  <tr>
   <td>
    <p>4.      </p></td>
   <td>
    <p>資格認定</p></td>
   <td>
    <p>コースを完了した学習者には、資格認定が付与されます。 資格認定を使用するには、アプリケーションでコースが必要です。 </p></td>
  </tr>
  <tr>
   <td>
    <p>5.      </p></td>
   <td>
    <p>学習プログラム</p></td>
   <td>
    <p>学習プログラムは、ユーザーの特定の学習要件を満たす独自に設計されたコースです。 通常、学習プログラムは、個々のコースにまたがる学習目標を推進するために使用されます。 </p></td>
  </tr>
  <tr>
   <td>
    <p>6.      </p></td>
   <td>
    <p>バッジ</p></td>
   <td>
    <p>学習者がコースを進めていく中で、特定のマイルストーンに到達したときに得られる功績の証を指す </p></td>
  </tr>
  <tr>
   <td>
    <p>7.      </p></td>
   <td>
    <p>技能</p></td>
   <td>
    <p>スキルモデルは、レベルと単位で構成されています。 学習者は、関連するコースの完了後にスキルを取得できます。 </p></td>
  </tr>
  <tr>
   <td>
    <p>8.      </p></td>
   <td>
    <p>certificationEnrollment</p></td>
   <td>
    <p>このモデルは、ユーザーによる1つの資格認定への登録の詳細を示す。</p></td>
  </tr>
  <tr>
   <td>
    <p>9.  </p></td>
   <td>
    <p>courseEnrollment</p></td>
   <td>
    <p>このモデルでは、ユーザーによる1つのコースへの登録の詳細を表します。 </p></td>
  </tr>
  <tr>
   <td>
    <p>10.  </p></td>
   <td>
    <p>courseInstance</p></td>
   <td>
    <p>1つまたは複数のインスタンスを関連付けることができる。 コースインスタンスを取得できます </p></td>
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
    <p>学習プログラムは、学習プログラムの類似したプロパティを持つ複数のインスタンス、またはカスタマイズされたインスタンスで構成できます。 </p></td>
  </tr>
  <tr>
   <td>
    <p>14.  </p></td>
   <td>
    <p>作業計画書</p></td>
   <td>
    <p>作業計画書とは、登録や完了条件なしに学習者がアクセスできる学習コンテンツを指します。 更新日、状態、ID情報に加えて、作業計画書のバージョン、作成者、スキルレベルなどの関連するモデルを取得できます。 </p></td>
  </tr>
  <tr>
   <td>
    <p>15.  </p></td>
   <td>
    <p>jobAidVersion</p></td>
   <td>
    <p>作業計画書には、コンテンツの改訂数とアップロード数に基づいて、1つまたは複数のバージョンを関連付けることができます。 このモデルは、1つの作業計画書バージョンの詳細を示します。 </p></td>
  </tr>
  <tr>
   <td>
    <p>16.  </p></td>
   <td>
    <p>learningProgramInstanceEnrollment</p></td>
   <td>
    <p>学習プログラムは1つまたは複数のインスタンスで構成されます。 学習者は、自分で学習プログラムインスタンスに登録することも、管理者に割り当てることもできます。 このモデルは、ユーザーが1つの学習プログラムインスタンスに登録する際の詳細情報を提供する。 </p></td>
  </tr>
  <tr>
   <td>
    <p>17.  </p></td>
   <td>
    <p>moduleVersion</p></td>
   <td>
    <p>モジュールには、改訂されたコンテンツアップロードに基づいて、1つ以上のバージョンを含めることができます。 このモデルを使用すると、1つのモジュールバージョンに関する特定の情報を取得できます。 </p></td>
  </tr>
  <tr>
   <td>
    <p>18.  </p></td>
   <td>
    <p>skillLevel</p></td>
   <td>
    <p>1つまたは複数のコースで構成されるスキルレベルを使用して、レベルとそれに関連する単位を取得します。 </p></td>
  </tr>
  <tr>
   <td>
    <p>19.  </p></td>
   <td>
    <p>userBadge</p></td>
   <td>
    <p>UserBadgeは、単一のバッジを単一のユーザーに関連付けます。 いつ達成したかや、assertionUrlなどの詳細が含まれています。 </p></td>
  </tr>
  <tr>
   <td>
    <p>20。  </p></td>
   <td>
    <p>userSkill</p></td>
   <td>
    <p>UserSkillは、1人のユーザーが1つのスキルレベルをどの程度達成しているかを示します。</p></td>
  </tr>
 </tbody>
</table>

+++

+++V2 API

以下は、V2 APIのLearning Managerのさまざまな要素を示したクラス図です。

![](assets/v2api-class-diagram.jpg)

<table>
 <tbody>
  <tr>
   <th><b>Learning Managerオブジェクト</b></th>
   <th><b>説明</b></th>
  </tr>
  <tr>
   <td>勘定</td>
   <td>Learning Managerのお客様の詳細情報をカプセル化します。</td>
  </tr>
  <tr>
   <td><code>
     badge
    </code></td>
   <td>学習者がコースを進めていく中で、特定のマイルストーンに到達したときに得られる功績の証を指す <br></td>
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
   <td>Learning Managerにおける主要なモデルはユーザーです。 通常、ユーザーは、学習目標を使用する組織の内部学習者または外部学習者です。 ただし、学習者の役割に加えて、作成者やマネージャーなど、他の役割を果たす場合もあります。 インライン属性には、ユーザーID、タイプ、電子メールなどがあります。 </td>
  </tr>
  <tr>
   <td>resource</td>
   <td>これは、モジュールがカプセル化しようとしている各コンテンツリソースをモデル化するために使用されます。 内にカプセル化されたすべてのリソース <code>
     an
    </code> <code>
     loResource
    </code> は、学習目標の点では同等ですが、配信タイプやコンテンツのロケールの点では互いに異なります。<br></td>
  </tr>
  <tr>
   <td>userNotification</td>
   <td>このモデルには、学習者に関する通知情報が含まれています。<br></td>
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
   <td>技能</td>
   <td>スキルモデルは、レベルと単位で構成されています。 学習者は、関連するコースの完了後にスキルを取得できます。 <br></td>
  </tr>
  <tr>
   <td>skillLevel</td>
   <td>1つまたは複数のコースで構成されるスキルレベルを使用して、レベルとそれに関連する単位を取得します。 <br></td>
  </tr>
  <tr>
   <td>learningObject</td>
   <td>学習目標は、ユーザーが登録および学習できる様々な種類のオブジェクトの抽象化です。 現在、Learning Managerには4種類の学習目標（コース、資格認定、学習プログラム）があります <code>
     and
    </code> 作業計画書<br></td>
  </tr>
  <tr>
   <td>learningObjectInstance<br></td>
   <td>学習目標の特定のインスタンス。<br></td>
  </tr>
  <tr>
   <td>learningObjectResource</td>
   <td>これは～の概念と同等である <code>
     module
    </code>. 1つのコースは1つから構成されます <code>
     of
    </code> その他のモジュール。 Learning Managerでは、モジュールをさまざまな同等の方法で提供できます。 したがって、 <code>
     loResource
    </code> 基本的には、これらと同等のリソースをすべてカプセル化します。<br></td>
  </tr>
  <tr>
   <td>loResourceGrade<br></td>
   <td>これにより、登録されている学習目標のコンテキストで特定のリソースを使用したユーザーの結果がカプセル化されます。 期間などの情報が表示されます <code>
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
   <td>学習目標に関連したフィードバックの質問に対して学習者が回答する内容を、L1フィードバックにカプセル化します。 学習者からフィードバックを収集するように設定されている場合、通常は、ユーザーが学習目標を完了した後に収集されます。<br></td>
  </tr>
  <tr>
   <td>enrollment<br></td>
   <td>この抽象化により、特定の学習目標インスタンスに対する特定のユーザーの割り当てを表すトランザクションに関する詳細がカプセル化されます。<br></td>
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
名前\
サブドメイン\
themeData\
timeZoneCode

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
名前\
state

+++

+++catalog

**属性**
dateCreated\
dateUpdated\
description\
id\
isDefault\
isInternalSearchable\
isListable\
名前\
state

+++

+++data

**属性**
id\
名前

+++

+++ゲーミフィケーション

**属性**
カラー\
名前\
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
state\
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
seatLimit\
state\
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
state

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
名前\
onlyQuiz\
reportingInfo\
reportingType\
seatLimit

+++

+++skill

**属性**
description\
id\
名前\
state

**関連付け**
levels(skillLevel)

+++

+++skillLevel

**属性**
id\
レベル\
maxCredit\
名前\
**関連付け**
バッジ（バッジ）\
スキル

+++

+++user

**属性**
avatarUrl\
バイオ\
contentLocale\
電子メール\
フィールド\
id\
名前\
pointsEarned\
プロフィール\
ロール\
state\
timeZoneCode\
uiLocale

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
か月\
1/4

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
pointsEarned

**関連付け**
learnerBadge(userBadge)\
learningObject(learningObject)\
skillLevel(skillLevel)\
user(user)

+++

## アプリケーション開発プロセス {#registration}

## 前提条件 {#prerequisites}

開発者はLearning Managerで体験版アカウントを作成し、そのアカウント内のすべての役割にフルアクセスできるようにする必要があります。 開発者がアプリケーションを記述できるようにするには、いくつかのユーザーとコースを作成し、アカウントを適切な状態に設定して、開発中のアプリケーションがそのサンプルデータにアクセスできるようにする必要があります。

## クライアントIDとシークレットの作成 {#createclientidandsecret}

1. イン **統合管理者** ログイン、クリック **[!UICONTROL アプリケーション]** をクリックします。

   ![](assets/application-development-menu.png)

   *統合管理者のアプリケーションを選択*

1. クリック **[!UICONTROL 登録]** ページの右上隅に、アプリケーションの詳細が表示されます。 登録ページが表示されます。

   ![](assets/register-application.png)

   *アプリケーションの登録*

   このページのすべてのフィールドに入力する必要があります。

   **アプリケーション名**：アプリケーション名を入力します。 同じアプリケーション名を使用する必要はありません。任意の有効な名前を使用できます。

   **URL**：アプリケーションがホストされている正確なURLがわかっている場合は、それを記載できます。 不明な場合は、会社のURLを記載してください。 このフィールドには、有効なURL名が必須です。

   **リダイレクトドメイン**:OAuth認証後にLearning Managerアプリケーションをリダイレクトするアプリケーションのドメイン名を入力します。 複数のURLを指定できますが、次のような有効なURLを使用する必要があります `http://google.com`, `http://yahoo.com` など。

   **説明：** アプリケーションの簡単な説明を入力します。

   **スコープ：** アプリケーションの範囲を定義する4つのオプションのいずれかを選択します。 ここに示された選択に基づき、Learning Manager APIエンドポイントはアプリケーションからアクセスできます。 例えば、 **学習者ロールの読み取りアクセス**&#x200B;を使用している場合、Learning Managerの学習者APIエンドポイントのすべてで、アプリケーションから読み取り専用のアクセスが可能になります。

   **このアカウントのみですか？**\
   **はい**  – はい選択した場合、他のアカウント管理者がアプリケーションを見ることはできません。\
   **いいえ** - 「いいえ」を選択した場合、他のアカウント管理者も、このアプリケーションにアクセスできますが、このアプリケーションにアクセスするには、アプリケーションidを使用する必要があります。 アプリケーションIDが生成され、Learning Managerアプリケーションの編集モードに表示されます。

   以下を選択した場合 **管理者ロールの読み取りおよび書き込みアクセス** 適用範囲としてアプリケーションを登録し、 **管理者ロールの読み取りアクセス権** apiのオーサリング中も、アプリケーションの書き込みアクセス権を維持できます。これは、アプリケーションの登録スコープが認証ワークフローに優先するためです。

1. クリック **[!UICONTROL 登録]** 登録ページに詳細を入力して、右上隅に表示されます。

## アプリケーションの開発とテスト {#applicationdevelopmentandtesting}

Learning Manager APIは、デベロッパーが任意のアプリケーションを構築するために使用できます。 開発者は、アカウントに有効なユーザーとコースが含まれていることを確認する必要があります。 ダミーのユーザーとコースをいくつか作成し、体験版アカウントでアクティビティをシミュレートして、アプリケーションの機能をテストできます。

## アプリケーションの導入 {#applicationdeployment}

実稼働アカウントでは、Learning Manager管理者または統合管理者が、組織内のユーザーにアプリケーションを使用する権限を与えるようにすることをお勧めします。 アプリケーションのテストが完了し、本番環境への移行が可能であると判断されたら、管理者に本番アカウントを知らせます。 理想的には、管理者は、アプリケーションの新しいクライアントIDとクライアントシークレットを本番アカウントで生成し、それらを安全な方法でアプリケーションに組み込むために必要な手順を実行します。 アプリケーションをデプロイする実際の手順は、企業によって異なります。デプロイを完了するには、組織のLearning Manager管理者が、組織内のIT/IS部門からサポートを受ける必要があります。

## 外部申請の承認 {#externalapplicationapproval}

をクリックすると、外部アプリケーションを追加できます。 **承認** 右上隅に **アプリケーション** ページです。 外部アプリケーションIDを入力し、をクリックします。 **をクリックします。**

![](assets/add-external-application.png)

*外部アプリケーションの追加と承認*

## よくある質問

+++Learning Managerはeコマースと統合されていますか？

AdobeのLearning ManagerにはEコマース統合機能がありません。 ただし、独自のヘッドレスLMSを作成してeコマース機能を実装できるように、APIを提供しています。
+++
