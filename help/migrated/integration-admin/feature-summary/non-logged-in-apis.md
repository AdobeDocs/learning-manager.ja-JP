---
description: ヘッドレスインターフェイスを開発するためのログインしていない API について説明します。
jcr-language: en_us
title: 非ログイン API
source-git-commit: 21e2a4a5e73fcbddb64e0afec0a896b315e38688
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 非ログイン API

ヘッドレスエクスペリエンスまたは非ログインエクスペリエンスのデータを提供する Adobe Learning Manager API について詳しくは、この記事を参照してください。公開検索 API

## 公開検索 API

### パブリック ES を使用したデータのフィルター処理

パブリック検索 API を使用すると、基本的な検索 API でコースをフィルター処理するために使用できるフィルター データを取得できます。 この API には、検索 API で使用できるすべてのフィルターが用意されています。

**サンプルカール**

GET メソッドを使用して、次の要求を行います。 &lt;Base_URL> 以下のcurlコマンドでベースURLに&lt;/Base_URL>置き換えます。トレーニング &lt;Base_URL> データ アクセス コネクタのページにあります。&lt;/Base_URL>

```
curl --location '<Base_URL>/filterableData'
```

**サンプル応答**

```
{
    "terms": {
        "loSkillLevels": [
            "1"
        ],
        "catalogNames": [
            "Default Catalog"
        ],
"catalogLabelIds": [
            "0000_1111"
        ],
        "loType": [
            "course"
        ],
        "availability": [
            "waitlistAvailable",
            "seatAvailable"
        ],
        "loSkillNames": [
            "General"
        ],
        "tags": [
            "course_tag"
        ],
        "authors": [
            "author_1"        
]
    },
    "range": {
        "duration": [
            "0"
        ],
        "dateCreated": [
            "2024-06-13T04:32:17.000Z"
        ],
        "price": [
            "0.0"
        ],
        "sessionEndTime": [
            "2024-06-18T20:30:00.000Z"
        ],
        "averageRating": [
            "0.0"
        ],
        "sessionStartTime": [
            "2024-06-18T19:30:00.000Z"
        ],
        "publishDate": [
            "2024-06-13T04:32:51.000Z"
        ],
        "ratingsCount": [
            "0"
        ]
    },
    "term": {}
}
```

**フィルターオプション**

| オプション | 説明 |
| --- | --- |
| `loSkillLevels` | コースに登録するために必要な習熟度レベル。 |
| `catalogNames` | 使用可能なカタログ名のリスト。 |
| `loType` | 使用可能な学習オブジェクトのタイプ。 |
| `availability` | 空席状況と空席待ち状況。 |
| `loSkillNames` | ラーニングオブジェクトに追加されたスキル名。 |
| `tags` | 学習オブジェクトに関連付けられているタグ。 |
| `authors` | 学習オブジェクトの作成者の名前 |
| `duration` | 学習オブジェクトの期間。 |
| `dateCreated` | ラーニングオブジェクトが作成された日付。 |
| `sessionEndTime` | セッションが終了した時刻。 |
| `averageRating` | 学習オブジェクトの平均星評価。 |
| `sessionStartTime` | セッションが開始された時刻。 |
| `publishDate` | ラーニングオブジェクトの公開日。 |
| `ratingsCount` | 学習オブジェクトの評価カウントの数。 |

### 検索 API

パブリック検索 API を使用すると、提供されたデータを使用して基本的な検索データを取得できます。

**カールのサンプル**

POST メソッドを使用して、次の要求を行います。 &lt;Base_URL> 以下のcurlコマンドでベースURLに&lt;/Base_URL>置き換えます。トレーニング &lt;Base_URL> データ アクセス コネクタのページにあります。&lt;/Base_URL>

```
curl --location '<Base_URL>/search?size=1000' \
--header 'content-type: application/json' 

--data '{
   "query": "",
   
    "sort": {
        "name": "publishDate",
        "order": "desc"
    },
    "lang": [
        "en-US"
    ],
    "filters": {
        "terms": {
            "loType": [
                "course",
                "learningProgram",
                "certification"
            ],
            "availability": [
                "seatAvailable",
                "waitlistAvailable"
            ]
        },
        "term": {
            "enrollmentDeadlinePassed": "true"
        },
        "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
            "sessionStartTime": [
                {
                   "gte": "2024-06-18T19:30:00.000Z"
                }
            ],
            "sessionEndTime": [
                {
                   "lte": "2024-06-20T09:30:00.000Z"     
                }
            ]
        }
    }
}'
```

**API 呼び出しのサンプル応答**

```
{
    "results": [
        {
            "loId": "course:11332313",
            "loType": "course",
            "tags": [
                "course_tag"
            ],
            "authors": [
                "author1",
                "author2"
            ],
            "status": "Published",
            "duration": 0,
            "publishDate": "2024-06-13T04:32:51.000Z",
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "name": "vc coursse to check ",
            "averageRating": 0.0,
            "ratingsCount": 0,
            "loSkillNames": [
                "General"
            ],
            "loSkillLevels": [
                "1"
            ],
            "loInstances": [
                {
                    "id": "14346696",
                    "name": "Default Instance",
                    "status": "Active",
                    "price": 0.0
                }
            ],
            "catalogInfo": [
                {
                    "id": "37779",
                    "name": "Default Catalog"
                }
            ]
        }
    ],
    "request": {
        "query": "",
        "filters": {
            "terms": {
                "loType": [
                    "course",
                    "learningProgram",
                    "certification"
                ],
                "loSkillNames": [
                    "General"
                ],
                "deliveryType": [],
                "availability": [
                    "seatAvailable",
                    "waitlistAvailable"
                ]
            },
            "term": {
                "enrollmentDeadlinePassed": "true"
            },
            "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
                "sessionStartTime": [
                    {
                        "gte": "2024-06-18T19:30:00.000Z"
                    }
                ],
                "sessionEndTime": [
                    {
                        "lte": "2024-06-20T09:30:00.000Z"
                    }
                ]
            }
        },
        "sort": {
            "name": "publishDate",
            "order": "desc"
        },
        "lang": [
            "en-US"
        ]
    },
    "self": "<Base_URL>/search?page=0&size=1000",
    "count": 1
}
```

**検索 API の並べ替えオプション**

次の並べ替えオプションを選択して、結果に適用できます。

| オプション | 説明 |
| --- | --- |
| `duration` | ラーニングオブジェクトの継続時間。 |
| `publishDate` | ラーニングオブジェクトの公開日。 |
| `dateCreated` | ラーニングオブジェクトが作成された日付。 |
| `name_en` | 学習オブジェクトの名前。 |
| `averageRating` | 学習者が提供する平均星評価。 |
| `ratingsCount` | 学習オブジェクトの評価カウントの数。 |
| `relevance(default)` | 関連データは検索キーワードに基づいています。 |

### 公開検索APIを使用した学習オブジェクトデータの取得

パブリック ES ラーニングオブジェクト API を使用すると、ヘッドレスインターフェイスで使用できるラーニングオブジェクトのタイプと ID のリストを取得できます。

**サンプルカール**

GET メソッドを使用して、次の要求を行います。 &lt;Base_URL> 以下のcurlコマンドでベースURLに&lt;/Base_URL>置き換えます。トレーニング &lt;Base_URL> データ アクセス コネクタのページにあります。&lt;/Base_URL>

```
curl --location '<Base_URL>/learningObjectIds'
```

**API 呼び出しのサンプル応答**

```
{
    "loIds": [
        "course:1132800",
"certification:126009",
"learningProgram:104433"
    ]
}
```

## コース概要API

コースサマリーAPIを使用すると、特定のコースに関する詳細情報を取得できます。

**サンプルカール**

GET メソッドを使用して、次の要求を行います。 &lt;Base_URL> 以下のcurlコマンドでベースURLに&lt;/Base_URL>置き換えます。トレーニング &lt;Base_URL> データ アクセス コネクタのページにあります。 &lt;/Base_URL>&lt;Course_ID> 特定のコースIDに置き換えます。&lt;/Course_ID>

```
curl --location '<Base_URL>/loSummary?loId=course%3A<Course_ID>'
```

**API 呼び出しのサンプル応答**

```
{
    "results": [
        {
            "instanceId": "14336686",
            "courseId": "11312313",
            "accountId": "44355",
            "seatConsumed": 1,
            "seatLimit": 1,
            "waitlistLimit":1,
            "waitlistCount": 1,
            "seatAvailable": false,
            "waitlistAvailable": false
        }
    ],
    "count": 1
}
```

>[!NOTE]
>
>コースに複数のインスタンスがある場合は、すべてのインスタンスの詳細が表示されます。

## コースの詳細に関する CDN JSON API

CDN JSON API を使用すると、特定のコースに関する完全なコース情報を取得できます。

**コースのサンプルカール**

GET メソッドを使用して、次の要求を行います。 &lt;CDN_path> 以下のcurlコマンドでベースURLに&lt;/CDN_path>置き換えます。トレーニング &lt;CDN_path> データ アクセス コネクタのページにあります。 &lt;/CDN_path>&lt;Course_ID> 特定のコースIDに置き換えます。&lt;/Course_ID>

```
curl --location '<CDN_path_URL>/course/<Course_ID>.json'
```

**学習パスと認定のためのサンプルカール**

```
curl --location '<CDN_path_URL>/learningProgram/<LearningProgram_ID>.json'
```

```
curl --location '<CDN_path_URL>/ certification /<Certification_ID>.json'
```

**API 呼び出しのサンプル応答**

```
{
    "data": {
        "id": "course:11342313",
        "type": "learningObject",
        "attributes": {
            "authorNames": [
                "author1",
                "author2"
            ],
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "datePublished": "2024-06-13T04:32:51.000Z",
            "dateUpdated": "2024-06-13T04:32:51.000Z",
            "duration": 0,
            "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
            "effectivenessIndex": 0,
            "enrollmentType": "Self Enroll",
            "hasOptionalLoResources": false,
            "hasPreview": false,
            "isExternal": false,
            "isMqaEnabled": false,
            "isPrerequisiteEnforced": false,
            "isSubLoOrderEnforced": false,
            "loResourceCompletionCount": 1,
            "loType": "course",
            "moduleResetEnabled": false,
            "state": "Published",
            "tags": [
                "course_tag"
            ],
            "unenrollmentAllowed": true,
            "localizedMetadata": [
                {
                    "description": "",
                    "locale": "en-US",
                    "name": "vc coursse to check "
                }
            ],
            "rating": {
                "averageRating": 0,
                "ratingsCount": 0
            }
        },
        "relationships": {
            "authors": {
                "data": [
                    {
                        "id": "13138897",
                        "type": "user"
                    }
                ]
            },
            "instances": {
                "data": [
                    {
                        "id": "course:11332313_14336696",
                        "type": "learningObjectInstance"
                    }
                ]
            },
            "skills": {
                "data": [
                    {
                        "id": "course:11332313_237719",
                        "type": "learningObjectSkill"
                    }
                ]
            }
        }
    },
    "included": [
        {
            "id": "237719",
            "type": "skill",
            "attributes": {
                "name": "General",
                "state": "Active"
            },
            "relationships": {
                "levels": {
                    "data": [
                        {
                            "id": "237719_1",
                            "type": "skillLevel"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313",
            "type": "learningObject",
            "attributes": {
                "authorNames": [
                    "m 41",
                    "rae"
                ],
                "dateCreated": "2024-06-13T04:32:17.000Z",
                "datePublished": "2024-06-13T04:32:51.000Z",
                "dateUpdated": "2024-06-13T04:32:51.000Z",
                "duration": 0,
                "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
                "effectivenessIndex": 0,
                "enrollmentType": "Self Enroll",
                "hasOptionalLoResources": false,
                "hasPreview": false,
                "isExternal": false,
                "isMqaEnabled": false,
                "isPrerequisiteEnforced": false,
                "isSubLoOrderEnforced": false,
                "loResourceCompletionCount": 1,
                "loType": "course",
                "moduleResetEnabled": false,
                "state": "Published",
                "tags": [
                    "course_tag"
                ],
                "unenrollmentAllowed": true,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "course name "
                    }
                ],
                "rating": {
                    "averageRating": 0,
                    "ratingsCount": 0
                }
            },
            "relationships": {
                "authors": {
                    "data": [
                        {
                            "id": "13128897",
                            "type": "user"
                        }
                    ]
                },
                "instances": {
                    "data": [
                        {
                            "id": "course:11312313_14336696",
                            "type": "learningObjectInstance"
                        }
                    ]
                },
                "skills": {
                    "data": [
                        {
                            "id": "course:11312313_237719",
                            "type": "learningObjectSkill"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0",
            "type": "learningObjectResource",
            "attributes": {
                "externalReporting": false,
                "isExpiredSubmission": false,
                "loResourceType": "Content",
                "multipleAttemptEnabled": false,
                "previewEnabled": false,
                "resourceType": "Virtual Classroom",
                "submissionEnabled": false,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "vc session"
                    }
                ]
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "resources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0_resource",
                            "type": "resource"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_237719",
            "type": "learningObjectSkill",
            "attributes": {
                "credits": 1,
                "learningObjectId": "course:11312313"
            },
            "relationships": {
                "skillLevel": {
                    "data": {
                        "id": "237719_1",
                        "type": "skillLevel"
                    }
                }
            }
        },
        {
            "id": "13128897",
            "type": "user",
            "attributes": {
                "avatarUrl": "https://abccontents.adobe.com/public/images/default_user_avatar.svg",
                "binUserId": "1f8c01aa-7f58-42e9-bc40-11537eb6498d",
                "email": "manjusha+41re@adobetest.com",
                "enrollOnClick": false,
                "gamificationEnabled": true,
                "lastLoginDate": "2024-06-13T04:23:45.000Z",
                "name": "m 41",
                "pointsEarned": 0,
                "pointsRedeemed": 0,
                "preferredResolution": "AUTO",
                "profile": "admin",
                "roles": [
                    "Learner",
                    "Admin",
                    "Author",
                    "Instructor",
                    "Integration Admin"
                ],
                "state": "ACTIVE",
                "userType": "Internal"
            },
            "relationships": {
                "account": {
                    "data": {
                        "id": "44355",
                        "type": "account"
                    }
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0_resource",
            "type": "resource",
            "attributes": {
                "avatarUrls": [
                    "https://abccontents.adobe.com/public/images/default_user_avatar.svg"
                ],
                "completionDeadline": "2024-06-18T20:30:00.000Z",
                "contentType": "Virtual Classroom",
                "dateStart": "2024-06-18T19:30:00.000Z",
                "desiredDuration": 3600,
                "hasQuiz": false,
                "hasToc": false,
                "instructorNames": [
                    "instructor1"
                ],
                "isDefault": true,
                "locale": "en-US",
                "location": "http://google.com",
                "name": "vc session",
                "onlyQuiz": false,
                "reportingType": "NONE"
            }
        },
        {
            "id": "course:11312313_14336696",
            "type": "learningObjectInstance",
            "attributes": {
                "dateCreated": "2024-06-13T04:32:18.000Z",
                "isDefault": true,
                "isFlexible": false,
                "state": "Active",
                "localizedMetadata": [
                    {
                        "locale": "en-US",
                        "name": "Default Instance"
                    }
                ],
                "seatConsumed": 0,
                "waitlistCount": 0
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "loResources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0",
                            "type": "learningObjectResource"
                        }
                    ]
                }
            }
        },
        {
            "id": "237719_1",
            "type": "skillLevel",
            "attributes": {
                "level": "1",
                "maxCredits": 1,
                "name": "Level 1"
            },
            "relationships": {
                "skill": {
                    "data": {
                        "id": "237719",
                        "type": "skill"
                    }
                }
            }
        }
    ]
}
```
