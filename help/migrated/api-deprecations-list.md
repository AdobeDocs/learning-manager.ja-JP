---
jcr-language: en_us
title: Adobe Learning ManagerでのAPIの廃止
description: Adobe Learning ManagerのAPIの進化に伴い、APIは定期的に再編成またはアップグレードされます。 APIが進化すると、古いAPIは廃止され、最終的に削除されます。 このページでは、非推奨のAPIバージョンから新しく安定したバージョンに移行する際に知っておく必要がある情報を記載しています。
contentowner: saghosh
exl-id: 0fe9a3cb-9114-42d6-81ae-1a4f28c984fa
source-git-commit: 670d0477b246af2a0257e41eca799817e391b348
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 32%

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

オフセット値によって取得されるレコード数が多いため、全体的なパフォーマンスが低下し、**500**&#x200B;レコードの制限が適用されます。 次回のリリースでは、管理者と学習者の両方に対して、**GETユーザー** APIで最大&#x200B;**500**&#x200B;件のレコードが返されます。

さらにレコードを取得する必要がある場合は、**GETジョブ** APIを使用してください。

<!--### Exclude paths 

At present, Learning Manager APIs follow a graph data structure, which allows you to fetch data by traversing the API model through includes. Even though you could traverse an API up to seven levels, fetching the data using a single API call is computationally expensive. 

We recommend that all existing and new customers make small calls multiple times instead of one large call. This approach will prevent unwanted data from being loaded in the call. 

We want to enforce these restrictions on new accounts and maintain a whitelist of existing accounts.-->

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

<!--### Instance summary count changes 

Currently, in the LO summary endpoint, you fetch the number of all possible instances. For example, for a course, you can view the number of enrollments and waitlists in the response for **GET /learningObjects/{loId}/instances/{loInstanceId}/summary**. You can then view the completionCount and enrollmentCount in the response. If the course is a VC or classroom, you can also view its seat limit and waitlist limit. 

The process of retrieving the completion and enrollment counts is computationally expensive, therefore the calculation is done on a request basis. If the data is not present in the cache, the data is reloaded, which is computationally intensive. If there are many users enrolling in a course, the counts will be large, and effectively impacts CPU performance. 

In the next release of Adobe Learning Manager, in the LO Instance summary endpoint, the completionCount, enrollmentCount, seatLimit, and waitlistCount are cached. The cached information persists till there are changes in enrollments or unenrollments. For counts exceeding 1000 enrollments, we'll assume the estimated counts, and invalidate the results for all existing and new accounts.

>[!NOTE]
>
>For counts, such as, completionCount, enrollmentCount, seatLimit, and waitlistCount exceeding1000, it's advisable to interpret them as estimates rather than precise figures, as these will be retrieved from cache.-->

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

_/primeapi/v2/users?page[offset]=0&amp;page[limit]=10&amp;sort=id&amp;override=TRUE_

### スキルベースの新しい推奨事項に対するAPIの変更

Adobe Learning Manager では、お客様とパートナーのアカウントに提供される学習コンテンツの推奨が改善されます。 コース、学習パス、資格認定向けランキングアルゴリズムの変更に伴うこの推奨アルゴリズムの改善により、コンテンツディスカバリーのユーザーエクスペリエンスが向上します。

このアルゴリズムでは、ピアベースの推奨事項が使用できなくなります。 この変更は既存のユーザーには影響しませんが、「業界に適合」オプションは存続します。 「カスタム」オプションの場合、Adobe Learning Manager ではカスタムピアベースの選択が使用できなくなります。

ピアグループがアカウントになり、学習者にはグループ内のトレンドのトピックを示す文字列が表示されます。 すべての推奨事項は説明が可能です。 例えば、あるテーマに関する何かを表示している場合、ストリップのカードにコースの目的が表示されます。

### 通知アナウンスレポートの変更点

Adobe Learning Managerの以前のリリースでは、通知アナウンスレポートにフィルターがありませんでした。 Adobe Learning Manager ではアカウント内のすべての通知がダウンロードされていました。

2023年11月のリリースでは、日付フィルターが追加され、指定した期間内の通知をダウンロードできるようになりました。  ただし、過去6か月間のレポートのみをダウンロードできます。

### GET/usersエンドポイントの高いオフセット値の廃止

システムパフォーマンスを向上させ、リソース使用率をより効果的に管理するために、Adobeは、**ADMIN**&#x200B;と&#x200B;**LEARNER**&#x200B;の両方のスコープのGET/usersエンドポイントの高オフセット値を廃止しました。 **ジョブAPI**&#x200B;を使用して、オフセット値を持つレコードを取得することをお勧めします。

