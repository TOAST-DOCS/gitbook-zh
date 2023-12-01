## Contact Center > Online Contact > API Guide for Developers > Inquiry History

### Customer Ticket List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/list.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/list.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Customer Ticket List |HTTPS  |POST    |UTF-8|JSON    |View a list of tickets for customers who meet the search criteria|Common authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	       |serviceId	|String	    |path	|O	|{serviceId} which is set in URL path|
|User Code	       |usercode	|String	    |path	|O	|User code(unique)，{usercode} which is set in URL path|
|Category ID	   |categoryId	|Integer	|query	|X	|Category(Submission type) ID|
|Ticket Status	       |status	    |String  	|query	|X	|Ticket status. new: Unassigned, open: Processing, reply: Pending, solved: Resolved, closed: Completed|
|Language Code	       |language	|String	    |query	|X	|Service help center default language code|
|Channel	           |source  	|String 	|query	|X	|Inquiry channel(web: PC web, spweb: mobile web, api: API. Separate multiple channels with commas.(Example: web,spweb,api). Default value : web,spweb,api|
|Sort Method	       |sort	     |String	|query	|X	|Sort method(Default value: updatedDt:desc; Sort format: ascending order: asc, descending order: desc)|
|Page	           |page	     |Integer	|query	|X	|Default value: 1|
|Number of exposures per page	|pageSize	  |Integer	 |query	 |X	 |Default value: 10; max=200|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents	|ticketId	        |String		    |Ticket ID|
|	                |subject	        |String		    |Ticket title|
|	                |categoryId	        |Integer		|Submission type ID|
|	                |categoryName	    |String		    |Submission type name|
|	                |categoryFullName	|String		    |Full path of category(Connect each depth to >)|
|	                |status 	        |String		    |Ticket status. new: Unassigned, open: Processing, reply: Pending, solved: Resolved, closed: Completed|
|	                |statusName	        |String		    |Name of status|
|	                |createdDt	        |Long		    |Created time|
|	                |updatedDt	        |Long		    |Updated time|
|	                |displayDt	        |String		    |Exposure time(yyyy.MM.dd)|
|result 	        |total	            |Integer		|Total number of cases|
|	                |pages	            |Integer		|Total pages|
|	                |pageNum	        |Integer		|Current page|
|                   |pageSize	        |Integer		|Number of exposures per page|

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
        "ticketId": "T1658213182227yb9hI",		
        "subject": "유형11",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "reply",		
        "statusName": "추가 확인",		
        "content": null,		
        "createdDt": 1658213182000,		
        "updatedDt": 1658215682000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T16582131010751o8BM",		
        "subject": "유형10",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "solved",		
        "statusName": "답변 완료",		
        "content": null,		
        "createdDt": 1658213101000,		
        "updatedDt": 1658215702000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658213078429EFmxm",		
        "subject": "유형9",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "closed",		
        "statusName": "최종 완료",		
        "content": null,		
        "createdDt": 1658213078000,		
        "updatedDt": 1658215720000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658213060072Witj6",		
        "subject": "유형8",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "open",		
        "statusName": "문의 확인",		
        "content": null,		
        "createdDt": 1658213060000,		
        "updatedDt": 1658215646000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658212816320fVxqS",		
        "subject": "유형7",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658212816000,		
        "updatedDt": 1658212816000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658211072628h00Qf",		
        "subject": "유형6",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658211073000,		
        "updatedDt": 1658211073000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658211058049HP1U0",		
        "subject": "유형5",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658211058000,		
        "updatedDt": 1658211058000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T165821104308563aoM",		
        "subject": "유형4",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658211043000,		
        "updatedDt": 1658211043000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658211028245FwMKd",		
        "subject": "유형3",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658211028000,		
        "updatedDt": 1658211028000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      },		
      {		
        "ticketId": "T1658211012753VCyy2",		
        "subject": "유형2",		
        "categoryId": 2542,		
        "categoryName": "유형1-1-1-1-1",		
        "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
        "status": "new",		
        "statusName": "접수 완료",		
        "content": null,		
        "createdDt": 1658211013000,		
        "updatedDt": 1658211013000,		
        "contents": null,		
        "attachments": null,		
        "displayDt": "2022.07.19"		
      }		
    ],		
    "total": 12,		
    "pages": 2,		
    "pageNum": 1,		
    "pageSize": 10		
  }		
}		
```

### Ticket Details
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/{ticketId}/detail.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/{ticketId}/detail.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Ticket Details  |HTTPS  |GET    |UTF-8|JSON    |Inquire ticket details received by the customer|Common authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	|serviceId	|String	|path	|O	|{serviceId} which is set in URL path|
|ID	    |usercode	|String	|path	|O	|ID(User unique ID), Usercode at the time of receipt of the inquiry|
|Ticket ID	|ticketId	|String	|path	|O	|Ticket ID|
|Language Code	|language	 |String	|query	|X	|Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content	|ticketId	|String		    |Ticket ID|
|	            |subject	|String		    |Service ID|
|	            |categoryId	|Integer		|Category(Submission type) ID|
|	            |categoryName	|String		|Category name|
|	            |categoryFullName	|String		|Full path of category(Connect each depth to >)|
|	            |status	            |String		|Ticket status. new: Unassigned, open: Processing, reply: Pending, solved: Resolved, closed: Completed|
|	            |statusName	        |String		|Ticket status name|
|	            |content	        |String		|Inquiry contents|
|	            |createdDt	        |Long		|Created time|
|	            |updatedDt	        |Long		|Updated time|
|	            |contents	        |Array		|Ticket details|
|	            |contents.content	|String		|Content details|
|	            |contents.type	    |String		|Type of inquiry. enduser: Inquiry(Submitted), csuser: 답변(Submitted)|
|	            |contents.typeName	|String		|Content type name|
|	            |contents.createdDt	|Long		|Processed time|
|	            |contents.displayDt	|String		|Content exposure time(yyyy.MM.dd)|
|	            |contents.attachments	|Array		|Attachment(Ticket processing)|
|	            |contents.attachments.attachmentId	|String		|Attachment ID(Ticket processing)|
|	            |contents.attachments.fileName	    |String		|Attachment name(Ticket processing)|
|	            |contents.attachments.contentType	|String		|Attachment type(Ticket processing)|
|	            |contents.attachments.disposition	|String		|Attachment processing type(attachment: attachment file)(Ticket processing)|
|	            |contents.attachments.size	        |Long		|Attachment size(Ticket processing)|
|	            |contents.attachments.createdDt	    |Long		|Attachment uploaded time(Ticket processing)|
|	            |attachments	                    |Array		|Attachment(Inquiry)|
|	            |attachments.attachmentId	        |String		|Attachment ID(Inquiry)|
|               |attachments.fileName	            |String		|Attachment name(Inquiry)|
|	            |attachments.contentType	        |String		|Attachment type(Inquiry)|
|	            |attachments.disposition	        |String		|Attachment processing type(attachment: attachment file)(Inquiry)|
|	            |attachments.size	                |Long		|Attachment size(Inquiry)|
|	            |attachments.createdDt	            |Long		|Attachment uploaded time(Inquiry)|
|	            |displayDt	                        |String		|Exposure time(yyyy.MM.dd)|
|result	        |total	                            |Integer	|Total number of cases|
|	            |pages	                            |Integer	|Total pages|
|	            |pageNum	                        |Integer	|Page|
|	            |pageSize	                        |Integer	|Number of cases per page|

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
      "ticketId": "T1658199661153IXTfw",		
      "subject": "유형",		
      "categoryId": 2542,		
      "categoryName": "유형1-1-1-1-1",		
      "categoryFullName": "유형1>유형1-1>유형1-1-1>유형1-1-1-1>유형1-1-1-1-1",		
      "status": "solved",		
      "statusName": "답변 완료",		
      "content": "문의내용",		
      "createdDt": 1658199661000,		
      "updatedDt": 1658279983000,		
      "contents": [		
        {		
          "content": "<p>solved</p>",		
          "type": "reply",		
          "typeName": "답변",		
          "createdDt": 1658279983000,		
          "displayDt": "2022.07.20",		
          "attachments": [		
            {		
              "attachmentId": "a9e126cf01654631acc2d1e56e8c694e",		
              "fileName": "image.png",		
              "contentType": "image/png",		
              "disposition": "attachment",		
              "size": 90576,		
              "createdDt": 1658279969000		
            }		
          ]		
        },		
        {		
          "content": "<p>append commnet</p>",		
          "type": "enduser",		
          "typeName": "질문",		
          "createdDt": 1658279813000,		
          "displayDt": "2022.07.20",		
          "attachments": null		
        },		
        {		
          "content": "<p>append comment</p>",		
          "type": "enduser",		
          "typeName": "질문",		
          "createdDt": 1658216460000,		
          "displayDt": "2022.07.19",		
          "attachments": null		
        },		
        {		
          "content": "<p>solved</p>",		
          "type": "reply",		
          "typeName": "답변",		
          "createdDt": 1658216406000,		
          "displayDt": "2022.07.19",		
          "attachments": null		
        }		
      ],		
      "attachments": null,		
      "displayDt": "2022.07.19"		
    }		
  }		
}		
```

### Open and Download Ticket Attachments
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/ticket/attachments/{id}
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/ticket/attachments/{id}

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Open and Download Ticket Attachments  |HTTPS  |GET    |UTF-8|JSON    |Open/download ticket attachments|No need   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	    |serviceId	|String	|path   |O	|{serviceId} which is set in URL path|
|Attachment ID	|id	        |String	|path   |O	|Attachment ID, {id} which is set in URL path| 
|Process Method	    |type	    |String	|query  |X	|Default value: Open with browser(download: Download file, open: Open with browser）|

#### Result Data
File

### Customer Re-Inquiry
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/{ticketId}/comment.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/ticket/enduser/{usercode}/{ticketId}/comment.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Customer Re-Inquiry  |HTTPS  |POST    |UTF-8|JSON    |Re-inquiry based on ticket ID|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID	|serviceId	|String	|path	|O	|{serviceId} which is set in URL path|
|ID	    |usercode	|String	|path	|O	|ID(User unique ID), Usercode at the time of receipt of the inquiry|
|Ticket ID	|ticketId	|String	|path	|O	|Ticket ID|
|Contents	    |comment	|String	|body	|O	|the contents of re-inquiry|
|Attachments	|attachments	|String	|query	|X	|Attachment ID. Separate file IDs with (,) when attaching multiple files, max = 5 cases(FileID1,FileID2,…,FileID5)|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content	|content	|String		|Contents of re-inquiry|
|	            |type	    |String		|Type. Fixed value: enduser|
|               |typeName	|String		|Name of type|
|	            |createdDt	|Long		|Created time|
|	            |displayDt	|String		|Displayed time(yyyy.MM.dd)|
|	            |attachments	|Array		|Attachment|
|	            |attachments.attachmentId	|String		|Attachment ID|
|	            |attachments.fileName	    |String		|Attachment name|
|	            |attachments.contentType	|String		|Attachment type|
|	            |attachments.disposition	|String		|Process method(attachment: attachment file)|
|	            |attachments.size	        |Long		|Attachment size|
|	            |attachments.createdDt	    |Long		|Attachment upload time|

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
      "content": "<p>append comnment</p>",		
      "type": "enduser",		
      "typeName": null,		
      "createdDt": 1658286589999,		
      "displayDt": null,		
      "attachments": [		
        {		
          "attachmentId": "a9e126cf01654631acc2d1e56e8c694e",		
          "fileName": "image.png",		
          "contentType": "image/png",		
          "disposition": "attachment",		
          "size": 90576,		
          "createdDt": 1658279969000		
        }		
      ]		
    }		
  }		
}		
```