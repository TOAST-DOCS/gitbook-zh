## Contact Center > Online Contact > API Guide for Developers > Notice

### Heading List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/notice/categories.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/notice/categories.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Heading List|HTTPS  |GET  |UTF-8|JSON    |Obtain a list of headings|No need|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	|serviceId	|String	|path	  |O	|{serviceId} which is set in URL path|
|Language Code	|language	  |String	|query	|X	|Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents	|categoryId	|Integer		|Heading ID|
|	                |parent	    |Integer		|Parent heading ID（Fixed value: 0）|
|	                |name	      |String		  |Heading name|
|	                |level	    |Integer		|Depth（Fixed value: 1）|
|	                |path	      |String		  |Depth path（Fixed value: "\\\\"）|
|	                |orderNo	  |Integer		|Sort order|
|	                |languages	|Object		  |Multilingual name, value(Language code: Corresponding language code name)|

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
                "categoryId": 2543,	
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
                "categoryId": 2544,	
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
                "categoryId": 2545,	
                "parent": 0,	
                "name": "유형3",	
                "level": 1,	
                "path": "\\",	
                "orderNo": 2,	
                "languages": {	
                    "ko": "유형3",	
                    "th": "พิมพ์3",	
                    "ja": "タイプ3",	
                    "en": "Type3",	
                    "zh": "类型3"	
                }	
            }	
        ]	
    }	
}	
```

### Tag List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/notice/tags.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/notice/tags.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Tag List |HTTPS  |GET    |UTF-8|JSON    |Obtain a list of notice tags|No need|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	|serviceId	|String	|path  |O	|{serviceId} which is set in URL path|
|Tag Keyword |language	|String	|query |X	|Tag search phrase|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents	|tagId	|Integer		|Tag ID|
|	                |tag	  |String		  |Tag name|
|	                |languages	|Object		|Multilingual name, value(Language code: Corresponding language code name)|

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
                "tagId": 391,	
                "tag": "태그1",	
                "languages": {	
                    "ko": "태그1",	
                    "th": "แท็ก1",	
                    "ja": "タグ1",	
                    "en": "Tag1",	
                    "zh": "标签1"	
                }	
            },	
            {	
                "tagId": 392,	
                "tag": "태그2",	
                "languages": {	
                    "ko": "태그2",	
                    "th": "แท็ก2",	
                    "ja": "タグ2",	
                    "en": "Tag2",	
                    "zh": "标签2"	
                }	
            }	
        ]	
    }	
}	
```

### Notice List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/notice/list.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/notice/list.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Notice List|HTTPS  |GET    |UTF-8|JSON    |Help Center notice list|Common authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	       |serviceId	  |String	    |path	  |O	|{serviceId} which is set in URL path|
|Language Code	         |language	   |String	  |query	|X	|Service help center default language code|
|Category ID	     |categoryId	 |Integer	  |query	|X	|Category ID|
|Tag ID	         |tagId	       |Integer	  |query	|X	|Tag ID|
|Search Keywords	      |query	     |String	  |query	 |X	 |Search keywords(Search scope: title, content)|
|Sort Order	        |sort	       |String	  |query	 |X	 |Can be sorted by isTop, createdDt, updatedDt, displayDt fields, separated by [,] when sorting multiple fields. asc: ascending order; desc: descending order|
|Page  	          |page   	   |Integer	  |query	 |X	 |Default value: 1|
|Number of exposures per page	 |pageSize	  |Integer	 |query	  |X	|Default value: 10; max=200|

The format and example of sort parameter is as follows.

- Format: field1:sort,field2:sort,……
- Example: isTop:desc,createdDt:asc
- Default sort: isTop:desc,displayDt:desc,updatedDt:desc

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents	|noticeId	    |Integer		|Notice ID|
|	                |categoryId	  |Integer		|Notice category ID|
|	                |isTop	      |Boolean		|Top fixed marking (true: yes; false: no)|
|	                |title	      |String		  |Notice title|
|	                |content	    |String		  |Notice contents|
|	                |displayDt	  |String		  |Displayed time(yyyyMMddHHmmss)|
|	                |updatedDt	  |Long		    |Updated time|
|	                |categoryName	|String		  |Category name|
|	                |tagStr	      |Integer		|Tag name|
|	                |isNew	      |String		  |Whether the notice is new or not. true: Displayed time(displayDt) value is today, false: Displayed time(displayDt) value is not today|
|result   	      |total	      |Integer		|Total number of cases|
|	                |pages	      |Integer		|Total pages|
|	                |pageNum	    |Integer		|page|
|	                |pageSize	    |Integer		|Number of exposures per page|

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
                "noticeId": 1241,	
                "categoryId": 2543,	
                "isTop": true,	
                "title": "공지제목7",	
                "content": "공지내용7",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657243026000,	
                "categoryName": "유형1",	
                "tagStr": "태그2",	
                "isNew": false	
            },	
            {	
                "noticeId": 1246,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목11",	
                "content": "공지내용11",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657243165000,	
                "categoryName": "유형1",	
                "tagStr": "태그1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1245,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목10",	
                "content": "공지내용10",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657243148000,	
                "categoryName": "유형1",	
                "tagStr": "태그1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1244,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목9",	
                "content": "공지내용9",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657243129000,	
                "categoryName": "유형1",	
                "tagStr": "태그1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1243,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목8",	
                "content": "공지내용8",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657243106000,	
                "categoryName": "유형1",	
                "tagStr": "태그1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1240,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목6",	
                "content": "공지내용6",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657242949000,	
                "categoryName": "유형1",	
                "tagStr": "태그2",	
                "isNew": false	
            },	
            {	
                "noticeId": 1239,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목5",	
                "content": "공지내용5",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657242735000,	
                "categoryName": "유형1",	
                "tagStr": "태그1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1238,	
                "categoryId": 2543,	
                "isTop": false,	
                "title": "공지제목4",	
                "content": "공지내용4",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657242576000,	
                "categoryName": "유형1",	
                "isNew": false	
            },	
            {	
                "noticeId": 1237,	
                "categoryId": 2545,	
                "isTop": false,	
                "title": "공지제목3",	
                "content": "공지내용3",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657242501000,	
                "categoryName": "유형3",	
                "tagStr": "태그1,태그2",	
                "isNew": false	
            },	
            {	
                "noticeId": 1236,	
                "categoryId": 2544,	
                "isTop": false,	
                "title": "공지제목2",	
                "content": "공지내용2",	
                "displayDt": "2022.07.08",	
                "updatedDt": 1657242420000,	
                "categoryName": "유형2",	
                "tagStr": "태그2",	
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

### Notice Details
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/notice/detail/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/notice/detail/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Notice Details|HTTPS  |GET    |UTF-8|JSON    |Obtain the contents of notice through notice ID|No need|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	  |serviceId	|String	  |path	  |O	|{serviceId} which is set in URL path|
|Notice ID	|id	        |Integer	|path	  |O	|Notice ID|
|Language Code	  |language	  |String	  |query	|X	|Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content	|noticeId	                |Integer|Notice ID|
|	              |categoryId	              |Integer|Heading ID|
|	              |isTop	                  |Boolean|Top fixed marking|
|	              |title	                  |String|Notice title|
|	              |content	                |String|Notice contents|
|	              |displayDt	              |String|Displayed time(yyyyMMddHHmmss)|
|	              |attachmentYn	            |Boolean|Whether attachments are included，value(true: included; false: not included)|
|	              |readCnt	                |Integer|Number of views|
|	              |updatedDt	              |Long  |Updated time|
|	              |attachments	            |Array|Notice attachments|
|	              |attachments.attachmentId	|String|Attachment ID|
|	              |attachments.fileName	    |String|Attachment Name|
|	              |attachments.contentType	|String|Attachment type|
|	              |attachments.size	        |Long  |Attachment size|
|	              |tags	                    |Array|Notice tags|
|	              |tags.tagId	              |Integer|Tag ID|
|	              |tags.tag	                |String|Tag name|
|               |categoryName	            |String|Heading name|
|	              |isNew	                  |String|Whether the notice is new or not. true: Displayed time(displayDt) value is today, false: Displayed time(displayDt) value is not today|

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
            "noticeId": 1240,
            "categoryId": 2543,
            "isTop": true,
            "title": "공지제목6",
            "content": "<p>공지내용6</p>",
            "displayDt": "2022.07.08",
            "attachmentYn": "Y",
            "readCnt": 5,
            "updatedDt": 1658114209000,
            "attachments": [
                {
                    "attachmentId": "42fb4c8801ed4c278475f70f531b8c92",
                    "fileName": "logo_footer.png",
                    "contentType": "image/png",
                    "size": 1412
                }
            ],
            "tags": [
                {
                    "tagId": 391,
                    "tag": "태그1"
                },
                {
                    "tagId": 392,
                    "tag": "태그2"
                }
            ],
            "categoryName": "유형1",
            "isNew": false
        }
    }
}
```

### Open and Download Notice Attachments
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/notice/attachments/{id}
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/notice/attachments/{id}

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Open and Download Notice Attachments|HTTPS  |GET    |UTF-8|JSON    |Open and Download Notice Attachments|No need|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	    |serviceId	|String	  |path	 |O	|{serviceId} which is set in URL path|
|File ID	|id	         |String	|path	  |O	|Uploaded file ID|
|Method of Reading	    |type	       |String	|query	|X	|Default value: Open(download: download, open: open)|

#### Result Data
File
