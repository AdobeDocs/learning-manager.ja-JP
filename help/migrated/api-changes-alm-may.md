---
description: ALMでのAPIの変更
jcr-language: en_us
title: 4月リリースのAPIの変更
source-git-commit: 7d3314f9293e1ad7e4ff4f6e537e19c82f7416e9
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# 2026年5月リリースのAPIの変更

## GET /learningObjects APIの機能強化

インスタンスリレーションシップを含める場合、GET /learningObjects APIにlearningObjectInstanceリソースに新しいstartDate属性が含まれるようになりました。

**エンドポイント**
GET /learningObjects/{id}?include=instances

**変更**
新しいフィールドstartDateが次の下に追加されました。
included[].attributes.startDate

**説明**
startDateは、学習目標インスタンスのスケジュールされた開始日時を表します。

**例**
https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects/course:13209797?include=instances
サンプル応答（切り捨て）

```
{
  "id": "course:13209797_16226533",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2026-05-20T04:35:46.000Z",
    "isAET": false,
    "isDefault": true,
    "isFlexible": false,
    "startDate": "2026-10-06T18:29:59.000Z",
    "state": "Active",
    "timeZoneCode": "IST"
  }
}
```

**メモ**

* このフィールドは、該当する学習目標インスタンスに対してのみ返されます。
* この値は、ISO 8601 UTC日付時刻形式で返されます。
* 既存の統合は、下位互換性を維持します。
