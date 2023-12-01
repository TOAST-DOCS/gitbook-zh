## Contact Center > Online Contact > API Guide for Developers > FAQ

### Category List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/helpdoc/categories.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/helpdoc/categories.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Category List|HTTPS  |GET    |UTF-8|JSON    |Acquire FAQ category list|No need |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID|serviceId|String|path|O|{serviceId} which is set in URL path|
|Language Code|language  |String|query |X|Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents|categoryId|Integer|Category ID|
|                |parent    |Integer|Parent category ID|
|                |name      |String  |Category name|
|                |level   |Integer|Depth(1, 2, 3)|
|                |path      |String  |Depth path(\level1\level2\)|
|                |orderNo  |Integer|Sort order(Default value: 0)|
|                |languages|Object  |Multilingual name, value|

#### Response Body
```

    "header": {
        "resultCode": 200,
        "resultMessage": "",
        "isSuccessful": true
    },
    "result": {
        "contents": [
            {
                "categoryId": 2546,
                "parent": 0,
                "name": "유형1",
                "level": 1,
                "path": "\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1",
                    "th": "พิมพ์1",
                    "ja": "タイプ1",
                    "en": "Type1",
                    "zh": "类型1"
                }
            },
            {
                "categoryId": 2548,
                "parent": 2546,
                "name": "유형1-1",
                "level": 2,
                "path": "\\2546\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1-1",
                    "th": "พิมพ์1-1",
                    "ja": "タイプ1-1",
                    "en": "Type1-1",
                    "zh": "类型1-1"
                }
            },
            {
                "categoryId": 2550,
                "parent": 2548,
                "name": "유형1-1-1",
                "level": 3,
                "path": "\\2546\\2548\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1-1-1",
                    "th": "พิมพ์1-1-1",
                    "ja": "タイプ1-1-1",
                    "en": "Type1-1-1",
                    "zh": "类型1-1-1"
                }
            },
            {
                "categoryId": 2547,
                "parent": 0,
                "name": "유형2",
                "level": 1,
                "path": "\\",
                "orderNo": 1,
                "languages": {
                    "ko": "유형2",
                    "th": "พิมพ์2",
                    "ja": "タイプ2",
                    "en": "Type2",
                    "zh": "类型2"
                }
            },
            {
                "categoryId": 2549,
                "parent": 2546,
                "name": "유형1-2",
                "level": 2,
                "path": "\\2546\\",
                "orderNo": 1,
                "languages": {
                    "ko": "유형1-2",
                    "th": "พิมพ์1-2",
                    "ja": "タイプ1-2",
                    "en": "Type1-2",
                    "zh": "类型1-2"
                }
            },
            {
                "categoryId": 2551,
                "parent": 2548,
                "name": "유형1-1-2",
                "level": 3,
                "path": "\\2546\\2548\\",
                "orderNo": 1,
                "languages": {
                    "ko": "유형1-1-2",
                    "th": "พิมพ์1-1-2",
                    "ja": "タイプ1-1-2",
                    "en": "Type1-1-2",
                    "zh": "类型1-1-2"
                }
            }
        ]
    }
}
```

### FAQ List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/helpdoc/list.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/helpdoc/list.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|FAQ List|HTTPS  |GET    |UTF-8|JSON    |Help center FAQ list|No need   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID    |serviceId|String  |path  |O|{serviceId} which is set in URL path|
|Language Code    |language  |String  |query|X|Help center language code(Default value: Default language code)|
|Category ID  |categoryId|Integer|query|X|FAQ category ID|
|Keyword        |query    |String  |query|X|Search keywords(Search scope: FAQ title, content)|
|Sort Field    |sort      |String  |query|X|Can be sorted by isTop, isRecommend, createdDt, updatedDt fields, separated by [,] when sorting multiple fields. asc: ascending order; desc: descending order|
|Page        |page      |Integer|query|X  |Page number(Default value: 1)|
|Number of exposures per page|pageSize  |Integer|query|X|Number of data per page(Default value: 10, MAX: 200)|

The format and example of sort parameter is as follows.

- Format: field1:sort,field2:sort,……
- Example: isTop:desc,createdDt:asc
- Default sort(if category ID is not empty value): isTop:desc,isRecommend:desc,updatedDt:desc
- Default sort(if category ID is empty value): isTop:desc,updatedDt:desc

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents|helpDocId  |Integer|FAQ ID|
|                |title      |String  |FAQ title|
|                |content    |String  |FAQ contents|
|                |isRecommend|Boolean|Fixed by category(true: Fixed; false: Not fixed)|
|                |isTop      |Boolean|Fixed in main screen(true: Fixed; false: Not fixed)|
|                |createdDt  |Long    |Created time|
|                |updatedDt  |Long    |Updated time|
|                |categoryId  |Integer|FAQ category ID|
|                |categoryName|String  |Category name, the category name of the language corresponding to the language code of the request parameter is displayed|
|                |isNew      |String  |Whether the FAQ is new or not(true: Displayed time(displayDt) value is today, false: Displayed time(displayDt) value is not today|
|result          |total      |Integer|Total number of cases|
|                |pages      |Integer|Total pages|
|                |pageNum    |Integer|page|
|                |pageSize    |Integer|Number of exposures per page|

#### Response Body
```
{
    "header": {
        "resultCode": 200,
        "resultMessage": "",
        "isSuccessful": true
    },
    "result": {
        "contents": [
            {
                "helpDocId": 3414,
                "title": "자주 묻는 질문 제목2",
                "content": "자주 묻는 질문 내용2",
                "isRecommend": false,
                "isTop": true,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657265718000,
                "updatedDt": 1657265718000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2551,
                "categoryName": "유형1-1-2",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3413,
                "title": "자주 묻는 질문 제목1",
                "content": "자주 묻는 질문 내용1",
                "isRecommend": true,
                "isTop": true,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657265403000,
                "updatedDt": 1657265403000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3423,
                "title": "자주 묻는 질문 제목11",
                "content": "자주 묻는 질문 내용11",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657266235000,
                "updatedDt": 1657266235000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3422,
                "title": "자주 묻는 질문 제목10",
                "content": "자주 묻는 질문 내용10",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657266185000,
                "updatedDt": 1657266196000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3421,
                "title": "자주 묻는 질문 제목9",
                "content": "자주 묻는 질문 내용9",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657266110000,
                "updatedDt": 1657266110000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3420,
                "title": "자주 묻는 질문 제목8",
                "content": "자주 묻는 질문 내용8",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657266059000,
                "updatedDt": 1657266059000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3419,
                "title": "자주 묻는 질문 제목7",
                "content": "자주 묻는 질문 내용7",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657266009000,
                "updatedDt": 1657266009000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2550,
                "categoryName": "유형1-1-1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3418,
                "title": "자주 묻는 질문 제목6",
                "content": "자주 묻는 질문 내용6",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657265956000,
                "updatedDt": 1657265956000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2547,
                "categoryName": "유형2",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3417,
                "title": "자주 묻는 질문 제목5",
                "content": "자주 묻는 질문 내용5",
                "isRecommend": false,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657265902000,
                "updatedDt": 1657265902000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2546,
                "categoryName": "유형1",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            },
            {
                "helpDocId": 3416,
                "title": "자주 묻는 질문 제목4",
                "content": "자주 묻는 질문 내용4",
                "isRecommend": true,
                "isTop": false,
                "readCnt": null,
                "attachmentYn": null,
                "createdDt": 1657265838000,
                "updatedDt": 1657265838000,
                "parentCategoryList": null,
                "category": null,
                "categoryId": 2549,
                "categoryName": "유형1-2",
                "categoryFullName": null,
                "attachments": null,
                "isNew": false
            }
        ],
        "total": 11,
        "pages": 2,
        "pageNum": 1,
        "pageSize": 10
    }
}
```

### FAQ Details
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/helpdoc/detail/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/helpdoc/detail/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|FAQ Details |HTTPS  |GET    |UTF-8|JSON    |Obtain the contents of FAQ via FAQ ID|No need |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID|serviceId|String |path |O |{serviceId} which is set in URL path|
|FAQ ID    |id       |Integer|path  |O|{id} which is set in URL path|
|Language Code|language  |String |query |X |Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content	|helpDocId	                    |Integer		 |FAQ ID|
|	              |title	                        |String		   |FAQ title|
|	              |content	                      |String		   |FAQ contents|
|               |isRecommend	                  |Boolean		 |recommendation|
|	              |isTop	                        |Boolean		 |Top fixed|
|	              |readCnt	                      |Integer		 |Views|
|	              |attachmentYn	                  |Boolean		 |Whether attachments are included|
|	              |createdDt	                    |Long	     	 |created time|
|	              |updatedDt	                    |Long		     |updated time|
|	              |parentCategoryList	            |Array	  	 |Parent category information|
|	              |parentCategoryList.categoryId	|Integer		 |Category ID|
|	              |parentCategoryList.parent	    |Integer		 |Parent category ID|
|	              |parentCategoryList.name	      |String		   |Category name|
|	              |parentCategoryList.level	      |Integer		 |Depth of category(0, 1, 2)|
|	              |parentCategoryList.path	      |String		   |Depth path of category(Associate each depth ID with \\\\)|
|	              |parentCategoryList.orderNo	    |Integer		 |Category display order|
|	              |parentCategoryList.languages  	|Object		   |Multilingual category name|
|	              |category	                      |Object		   |Category information|
|	              |category.categoryId			      |            |Category ID|
|	              |category.parent			          |            |Parent category ID|
|	              |category.name			            |            |Category name|
|	              |category.level			            |            |Depth of category(0, 1, 2)|
| 	            |category.languages			        |            |Multilingual category name|
|	              |categoryId	                    |Integer		 |Announcement category ID|
|	              |categoryName	                  |String		   |Category name|
|	              |categoryFullName	              |String		   |Full path of category|
|	              |attachments	                  |Array		   |Attachment|
|	              |attachments.attachmentId	      |String		   |Attachment ID|
|	              |attachments.fileName	          |String		   |Attachment name|
|	              |attachments.contentType	      |String		   |Attachment type|
|	              |attachments.size	              |Long		     |Attachment size|
|        	      |isNew	                        |String		   |Whether the notice is new or not. true: Displayed time(displayDt) value is today, false: Displayed time(displayDt) value is not today|

#### Response Body
```
{		
    "header": {		
        "resultCode": 200,		
        "resultMessage": "",		
        "isSuccessful": true		
    },		
    "result": {		
        "content": {		
            "helpDocId": 3413,		
            "title": "자주 묻는 질문 제목1",		
            "content": "<p>자주 묻는 질문 내용1</p>",		
            "isRecommend": true,		
            "isTop": true,		
            "readCnt": 12,		
            "attachmentYn": "Y",		
            "createdDt": 1657265404000,		
            "updatedDt": 1657265404000,		
            "parentCategoryList": [		
                {		
                    "categoryId": 2546,		
                    "parent": 0,		
                    "name": "유형1",		
                    "level": 1,		
                    "path": "\\",		
                    "orderNo": 0,		
                    "languages": {		
                        "ko": "유형1",		
                        "th": "พิมพ์1",		
                        "ja": "タイプ1",		
                        "en": "Type1",		
                        "zh": "类型1"		
                    }		
                },		
                {		
                    "categoryId": 2548,		
                    "parent": 2546,		
                    "name": "유형1-1",		
                    "level": 2,		
                    "path": "\\2546\\",		
                    "orderNo": 0,		
                    "languages": {		
                        "ko": "유형1-1",		
                        "th": "พิมพ์1-1",		
                        "ja": "タイプ1-1",		
                        "en": "Type1-1",		
                        "zh": "类型1-1"		
                    }
                },
                {
                    "categoryId": 2550,
                    "parent": 2548,
                    "name": "유형1-1-1",
                    "level": 3,
                    "path": "\\2546\\2548\\",
                    "orderNo": 0,
                    "languages": {
                        "ko": "유형1-1-1",
                        "th": "พิมพ์1-1-1",
                        "ja": "タイプ1-1-1",
                        "en": "Type1-1-1",
                        "zh": "类型1-1-1"
                    }
                }
            ],
            "category": {
                "categoryId": 2550,
                "parent": 2548,
                "name": "유형1-1-1",
                "level": 3,
                "languages": {
                    "ko": "유형1-1-1",
                    "th": "พิมพ์1-1-1",
                    "ja": "タイプ1-1-1",
                    "en": "Type1-1-1",
                    "zh": "类型1-1-1"
                }
            },
            "categoryId": 2550,
            "categoryName": "유형1-1-1",
            "categoryFullName": "유형1>유형1-1>유형1-1-1",
            "attachments": [
                {
                    "attachmentId": "badf8fac176e42cc85e232e19759ad2f",
                    "fileName": "nhn.png",
                    "contentType": "image/png",
                    "size": 9682
                },
                {
                    "attachmentId": "d4f3667f13c14ddea57cd55b71df868c",
                    "fileName": "logo_footer.png",
                    "contentType": "image/png",
                    "size": 1412
                }
            ],
            "isNew": false
        }
    }
}
```

### Open and Download FAQ Attachments
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/helpdoc/attachments/{id}
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/helpdoc/attachments/{id}

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Open and Download FAQ Attachments |HTTPS  |GET    |UTF-8|JSON    |Open/download FAQ attachments|No need   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID          |serviceId|String|path   |O    |{serviceId} which is set in URL path|
|File ID      |id        |String  |path   |O     |Uploaded file ID|
|Method of Reading        |type      |String|query   |X     |Default value: Open(download: download, open: open)|

#### Result Data
File