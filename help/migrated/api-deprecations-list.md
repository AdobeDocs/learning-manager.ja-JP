---
jcr-language: en_us
title: Adobe Learning ManagerでのAPIの廃止
description: Adobe Learning ManagerのAPIの進化に伴い、APIは定期的に再編成またはアップグレードされます。 APIが進化すると、古いAPIは廃止され、最終的に削除されます。 このページでは、非推奨のAPIバージョンから新しく安定したバージョンに移行する際に知っておく必要がある情報を記載しています。
contentowner: saghosh
exl-id: 0fe9a3cb-9114-42d6-81ae-1a4f28c984fa
source-git-commit: dd0b8aecbe54d6aecf17e4d9acec5769e7302ecd
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 20%

---

# Adobe Learning ManagerでのAPIの廃止と変更

## Adobe Learning Managerの2024年3月リリースのAPIの廃止

<!-- ### Changes in Rate Limits

With the next release of Adobe Learning Manager, we're restructuring API rate limits for new accounts. For existing accounts, only the Admin APIs will be rate-limited. After 90 days (about 3 months), we will restructure rate limits for all APIs, but existing accounts will be whitelisted according to current usage. Existing accounts need to revisit their learner API usage. 

For new accounts, if they want to increase the rate limits, they must contact the Customer Success team of ALM. 

#### Which APIs will be rate limited 

For new accounts, all Admin, Learner, and Search APIs will have rate limits and burst enforced.  

The API burst rate or burst limit refers to the maximum number of requests allowed to be made to an API in a short burst within a limited timeframe. 

The following table lists the rate and burst limits for the APIs.

<table>
    <tr>
        <th>API</th>
        <th>Number of requests-RPM</th>
        <th>Number of requests-Burst</th>
    </tr>
    <tr>
        <td>Admin</td>
        <td>5</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Learner</td>
        <td>20</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Search</td>
        <td>50</td>
        <td>5</td>
    </tr>
</table>
-->

### オフセット制限の変更

オフセット値によって多くのレコードが取得されるため、全体的なパフォーマンスが低下するため、 **500** レコード。 次回のリリースでは、管理者と学習者の両方に対して、 **GETユーザー** APIは最大 **500** レコード。

さらにレコードを取得する必要がある場合は、 **GETジョブ** API。

オフセット制限の変更は、すべての新規顧客に適用されます。 既存のお客様には、90日間のルールが適用されます。

### パスを除外

現在、Learning Manager APIはグラフデータ構造に従っているため、インクルードを介してAPIモデルを走査することでデータを取得できます。 最大7つのレベルのAPIをトラバースできますが、単一のAPI呼び出しを使用したデータの取得は計算上、高コストです。

既存および新規のお客様は、1回の大電話ではなく、何度も少額電話をかけることをお勧めします。 この方法では、不要なデータがコールにロードされるのを防ぐことができます。

新しいアカウントではこれらの制限を適用し、既存のアカウントのホワイトリストを保持します。

#### 非推奨のパス

次のパスは非推奨です。

* /learningObjects
   * 非推奨のパス：
      * enrollment.loInstance.loResources.resources
      * instances.loResources.resources
   * 新しいパス：
      * enrollment.loInstance.loResources
      * instances.loResources

* /learningObjects/{id}
   * 非推奨のパス：
      * enrollment.instances.subLoInstances.learningObject
   * 新しいパス：
      * enrollment.instances.subLoInstances

* /enrollments
   * 非推奨のパス：
      * loInstance.learningObject.enrollment
   * 新しいパス：
      * loInstance.learningObject

* /learningObjects/{id}
   * 非推奨のパス：
      * instance.subLoInstances.learningObject.enrollment.loResourceGrades
   * 新しいパス：
      * instance.subLoInstances

### インスタンスのサマリ数の変更

現在、LOサマリーエンドポイントでは、使用可能なすべてのインスタンスの数を取得します。 例えば、コースの場合、次の回答の登録数とキャンセル待ちの数を表示できます **GET /learningObjects/{loId}/instances/{loInstanceId}/summary**. 次に、応答のcompletionCountとenrollmentCountを表示できます。 コースがVCまたは教室の場合は、人数制限とキャンセル待ちの制限も表示できます。

完了数と登録数を取得するプロセスは計算上コストがかかるため、リクエストに基づいて計算が実行されます。 キャッシュにデータが存在しない場合、データは再ロードされ、計算処理が集中します。 コースに多数のユーザーが登録されている場合、カウントは大きくなり、CPUのパフォーマンスに実質的な影響を与えます。

Adobe Learning Managerの次のリリースでは、LOインスタンスの概要エンドポイントに、completionCount、enrollmentCount、seatLimit、およびwaitlistCountがキャッシュされます。 キャッシュされた情報は、登録または登録解除に変更が加えられるまで保持されます。 登録数が1000を超えた場合は、見積もり数を想定し、既存および新規のすべてのアカウントの結果を無効にします。

>[!NOTE]
>
>completionCount、enrollmentCount、seatLimit、waitlistCount exceeding1000などのカウントの場合は、キャッシュから取得されるため、正確な数値ではなく推定値として解釈することをお勧めします。

### 名前で並べ替え

Adobe Learning Managerの次のリリースでは、次のAPIの並べ替えフィールドでnameと – nameが非推奨になりました。

* GET /userGroups/{userGroupId}/users
* GET/ユーザー

>[!NOTE]
>
>既存および新規のすべてのアカウントでは、名前で並べ替えおよび – nameは使用できなくなります。


## Adobe Learning Managerの2023年11月リリースのAPIの廃止

### 上書きフラグ

Adobe Learning Managerの2023年11月リリースでは、APIからのオーバーライドフラグが廃止されました。 上書きフラグはパブリック API 仕様の一部ではなく、バックエンドテストでの使用を目的としています。 学習者 API のフラグは廃止されました。 ただし、このフラグは管理者用 API に対して引き続き有効です。

学習者APIのフラグを廃止する理由は、オーバーライドフラグにより学習者APIを介して大量のデータが取得されていたためです。

今後、次の学習者 API は上書きフラグがあるため機能しなくなります。

_/primeapi/v2/users?page[offset]=0&amp;page[極限値]=10&amp;sort=id&amp;override=TRUE_

### スキルベースの新しい推奨事項に対するAPIの変更

Adobe Learning Manager では、お客様とパートナーのアカウントに提供される学習コンテンツの推奨が改善されます。 コース、学習パス、資格認定向けランキングアルゴリズムの変更に伴うこの推奨アルゴリズムの改善により、コンテンツディスカバリーのユーザーエクスペリエンスが向上します。

このアルゴリズムでは、ピアベースの推奨事項が使用できなくなります。 この変更は既存のユーザーには影響しませんが、「業界に適合」オプションは存続します。 「カスタム」オプションの場合、Adobe Learning Manager ではカスタムピアベースの選択が使用できなくなります。

ピアグループがアカウントになり、学習者にはグループ内のトレンドのトピックを示す文字列が表示されます。 すべての推奨事項は説明が可能です。 例えば、あるテーマに関する何かを表示している場合、ストリップのカードにコースの目的が表示されます。

### 通知アナウンスレポートの変更点

Adobe Learning Managerの以前のリリースでは、通知アナウンスレポートにフィルターがありませんでした。 Adobe Learning Manager ではアカウント内のすべての通知がダウンロードされていました。

2023年11月のリリースでは、日付フィルターが追加され、指定した期間内の通知をダウンロードできるようになりました。  ただし、過去6か月間のレポートのみをダウンロードできます。

### GET/usersエンドポイントの高いオフセット値の廃止

システムのパフォーマンスを向上させ、リソース使用率をより効果的に管理するために、Adobeは両方のGET/usersエンドポイントの高オフセット値を廃止しました **管理者** および **学習者** スコープ： ここでは、 **ジョブAPI** オフセット値を持つレコードを取得します。

