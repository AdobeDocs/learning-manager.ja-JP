---
jcr-language: en_us
title: Learning Manager AdobeのAPIの廃止
description: AdobeのLearning ManagerのAPIの進化に伴い、APIが定期的に再編成またはアップグレードされます。 APIが進化すると、古いAPIは廃止され、最終的に削除されます。 このページでは、非推奨のAPIバージョンから新しく安定したバージョンに移行する際に知っておく必要がある情報を記載しています。
contentowner: saghosh
source-git-commit: 83fdd06aed823a50458d50c8ac240d56af873a6d
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 19%

---


# Learning Manager AdobeのAPIの廃止

## 2024年3月リリースのAdobe Learning ManagerにおけるAPIの廃止

### レート制限の変更

Adobe版Learning Managerの次回リリースでは、新しいアカウントのAPIレート制限が再構築されます。 既存のアカウントの場合、レートが制限されるのはAdmin APIのみです。 90日後（約3か月）、すべてのAPIのレート制限を再構築しますが、既存のアカウントは現在の使用状況に応じてホワイトリストに登録されます。 既存のアカウントでは、学習者のAPIの使用を見直す必要があります。

新規アカウントでレート制限を上げたい場合は、ALMのカスタマーサクセスチームに連絡する必要があります。

#### どのAPIのレートが制限されるか

新しいアカウントの場合、すべての管理者、学習者、検索APIにレート制限とバーストが適用されます。

APIバースト率またはバースト制限とは、限られた期間内にショートバーストでAPIに対して行うことができる最大要求数を指します。

次の表に、APIのレートとバーストの制限を示します。

<table>
    <tr>
        <th>API</th>
        <th>リクエスト数 – RPM</th>
        <th>要求数 – バースト</th>
    </tr>
    <tr>
        <td>管理者</td>
        <td>5</td>
        <td>5</td>
    </tr>
    <tr>
        <td>学習者</td>
        <td>20</td>
        <td>5</td>
    </tr>
    <tr>
        <td>検索</td>
        <td>50</td>
        <td>5</td>
    </tr>
</table>

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

AdobeのLearning Managerの次のリリースでは、LOインスタンスのサマリーエンドポイントに、completionCount、enrollmentCount、seatLimit、およびwaitlistCountがキャッシュされます。 キャッシュされた情報は、登録または登録解除に変更が加えられるまで保持されます。 登録数が1000を超えた場合は、見積もり数を想定し、既存および新規のすべてのアカウントの結果を無効にします。

>[!NOTE]
>
>completionCount、enrollmentCount、seatLimit、waitlistCount exceeding1000などのカウントの場合は、キャッシュから取得されるため、正確な数値ではなく推定値として解釈することをお勧めします。

### 名前で並べ替え

Adobe版Learning Managerの次のリリースでは、次のAPIの並べ替えフィールドにnameと – nameが使用されなくなりました。

* GET /userGroups/{userGroupId}/users
* GET/ユーザー

>[!NOTE]
>
>既存および新規のすべてのアカウントでは、名前で並べ替えおよび – nameは使用できなくなります。


## 2023年11月リリースのAdobe Learning ManagerにおけるAPIの廃止

### 上書きフラグ

2023年11月リリースのAdobe Learning Managerでは、APIからのオーバーライドフラグが廃止されました。 上書きフラグはパブリック API 仕様の一部ではなく、バックエンドテストでの使用を目的としています。 学習者 API のフラグは廃止されました。 ただし、このフラグは管理者用 API に対して引き続き有効です。

学習者APIのフラグを廃止する理由は、オーバーライドフラグにより学習者APIを介して大量のデータが取得されていたためです。

今後、次の学習者 API は上書きフラグがあるため機能しなくなります。

<code>https://captivateprime.adobe.com/primeapi/v2/users?page[offset]=0&amp;page[極限値]=10&amp;sort=id&amp;override=TRUE</code>

### スキルベースの新しい推奨事項に対するAPIの変更

Adobe Learning Manager では、お客様とパートナーのアカウントに提供される学習コンテンツの推奨が改善されます。 コース、学習パス、資格認定向けランキングアルゴリズムの変更に伴うこの推奨アルゴリズムの改善により、コンテンツディスカバリーのユーザーエクスペリエンスが向上します。

このアルゴリズムでは、ピアベースの推奨事項が使用できなくなります。 この変更は既存のユーザーには影響しませんが、「業界に適合」オプションは存続します。 「カスタム」オプションの場合、Adobe Learning Manager ではカスタムピアベースの選択が使用できなくなります。

ピアグループがアカウントになり、学習者にはグループ内のトレンドのトピックを示す文字列が表示されます。 すべての推奨事項は説明が可能です。 例えば、あるテーマに関する何かを表示している場合、ストリップのカードにコースの目的が表示されます。

### 通知アナウンスレポートの変更点

以前のリリースのAdobe Learning Managerでは、通知アナウンスレポートにフィルターがありませんでした。 Adobe Learning Manager ではアカウント内のすべての通知がダウンロードされていました。

2023年11月のリリースでは、日付フィルターが追加され、指定した期間内の通知をダウンロードできるようになりました。  ただし、過去6か月間のレポートのみをダウンロードできます。