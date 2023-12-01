## Contact Center > Online Contact > API Guide for Developers > Inquiry

### Submission Type List
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/ticket/categories.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/ticket/categories.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Submission Type List |HTTPS  |GET    |UTF-8|JSON    |Inquire list of in-service submission types|No need   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID       |serviceId|String   |path|O|{serviceId} which is set in URL path|
|Parent Category ID|parent     |Integer|query |X |List of subcategories belonging to a parent category|
|Subcategory ID|child     |Integer|query |X |List of parent categories that belong to a subcategory|
|Language Code        |language |String|query |X |Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents|categoryId|Integer|Submission type ID|
|                |parent    |Integer|Parent submission type ID|
|                |name    |String    |Submission type name|
|                |level    |Integer|Submission type level(1, 2, 3, 4, 5)|
|                |path    |String    |Submission type path(Associate Category ID for each depth with \\\\)|
|                |orderNo|Integer|Display order|
|                |languages|Object    |Multilingual names of categories|

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
                "categoryId": 2536,
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
                "categoryId": 2537,
                "parent": 0,
                "name": "유형2",
                "level": 1,
                "path": "\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형2",
                    "th": "พิมพ์2",
                    "ja": "タイプ2",
                    "en": "Type2",
                    "zh": "类型2"
                }
            },
            {
                "categoryId": 2538,
                "parent": 2536,
                "name": "유형1-1",
                "level": 2,
                "path": "\\2536\\",
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
                "categoryId": 2539,
                "parent": 2536,
                "name": "유형1-2",
                "level": 2,
                "path": "\\2536\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1-2",
                    "th": "พิมพ์1-2",
                    "ja": "タイプ1-2",
                    "en": "Type1-2",
                    "zh": "类型1-2"
                }
            },
            {
                "categoryId": 2540,
                "parent": 2538,
                "name": "유형1-1-1",
                "level": 3,
                "path": "\\2536\\2538\\",
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
                "categoryId": 2541,
                "parent": 2540,
                "name": "유형1-1-1-1",
                "level": 4,
                "path": "\\2536\\2538\\2540\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1-1-1-1",
                    "th": "พิมพ์1-1-1-1",
                    "ja": "タイプ1-1-1-1",
                    "en": "Type1-1-1-1",
                    "zh": "类型1-1-1-1"
                }
            },
            {
                "categoryId": 2542,
                "parent": 2541,
                "name": "유형1-1-1-1-1",
                "level": 5,
                "path": "\\2536\\2538\\2540\\2541\\",
                "orderNo": 0,
                "languages": {
                    "ko": "유형1-1-1-1-1",
                    "th": "พิมพ์1-1-1-1-1",
                    "ja": "タイプ1-1-1-1-1",
                    "en": "Type1-1-1-1-1",
                    "zh": "类型1-1-1-1-1"
                }
            }
        ]
    }
}
```

### List of Submission Type fields
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/ticket/field/user/{categoryId}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/ticket/field/user/{categoryId}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|List of Submission Type fields |HTTPS  |GET    |UTF-8|JSON    |Check the list of corresponding fields through the submission type|Common authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID   |serviceId|String  |path |O|{serviceId} which is set in URL path|
|Submission Type ID|categoryId|Integer   |path  |O|{categoryId} which is set in URL path|
|Language Code    |language|String   |query |X|Service help center default language code|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents|fieldId    |Integer|Customer field ID|
|                   |code        |String  |Field code|
|                |type        |String    |Field type|
|                |title        |String    |Field name|
|                |description|String    |Description|
|                |placeholder|String    |Placeholder|
|                |length        |Integer|Maximum length(0: Unlimited)|
|                |required    |Boolean|Required(true: yes, false: no)|
|                |encrypt    |Boolean|Personal information encryption(true: yes, false: no)|
|                |holdingText|Boolean|Deleted on click(true: yes, false: no)|
|                |options    |Array   |Text box, Check box, Drop box, Example:[item1,item2,...]|
|                |value        |String    |User input value|

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
                "fieldId": 1,
                "code": "category",
                "type": "dropdown",
                "title": "유형",
                "description": "",
                "placeholder": "",
                "length": 0,
                "required": true,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 3,
                "code": "mail",
                "type": "text",
                "title": "이메일",
                "description": "",
                "placeholder": "",
                "length": 100,
                "required": true,
                "encrypt": true,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 5,
                "code": "subject",
                "type": "text",
                "title": "제목",
                "description": "",
                "placeholder": "",
                "length": 200,
                "required": true,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 6,
                "code": "content",
                "type": "textarea",
                "title": "문의내용",
                "description": "",
                "placeholder": "",
                "length": 5000,
                "required": true,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 2,
                "code": "name",
                "type": "text",
                "title": "이름",
                "description": "",
                "placeholder": "",
                "length": 100,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 4,
                "code": "phone",
                "type": "text",
                "title": "전화번호",
                "description": "",
                "placeholder": "",
                "length": 30,
                "required": false,
                "encrypt": true,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 9,
                "code": "attachment",
                "type": "file",
                "title": "첨부파일",
                "description": "10MB 이내 모든 이미지 및 허용된 문서 (MS office, hwp, pdf, txt)와 zip 파일을 5개까지 첨부가능합니다.",
                "placeholder": "",
                "length": 0,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 18,
                "code": "typeOne",
                "type": "text",
                "title": "구분1",
                "description": "",
                "placeholder": "",
                "length": 200,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 19,
                "code": "typeTwo",
                "type": "text",
                "title": "구분2",
                "description": "",
                "placeholder": "",
                "length": 200,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 720,
                "code": "caption",
                "type": "caption",
                "title": "단순 텍스트 이름",
                "description": "<div style=\"color:red\">단순 텍스트 설명</div>",
                "placeholder": "<div style=\"font-size:20px;color:red\">단순 텍스트 내용</div>",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 721,
                "code": "textbox",
                "type": "text",
                "title": "텍스트 박스 이름",
                "description": "<div style=\"color:red\">텍스트 박스 설명</div>",
                "placeholder": "텍스트 박스 자리 표시자",
                "length": 50,
                "required": true,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 722,
                "code": "checkbox",
                "type": "checkbox",
                "title": "체크박스 이름",
                "description": "체크박스 설명",
                "placeholder": "",
                "length": 50,
                "required": false,
                "encrypt": true,
                "holdingText": true,
                "options": [
                    "옵션1",
                    "옵션2",
                    "옵션3"
                ],
                "value": null
            },
            {
                "fieldId": 723,
                "code": "dropdown",
                "type": "dropdown",
                "title": "드롭박스 이름",
                "description": "드롭박스 설명",
                "placeholder": "",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": [
                    "옵션1",
                    "옵션2",
                    "옵션3"
                ],
                "value": null
            },
            {
                "fieldId": 724,
                "code": "radiobutton",
                "type": "radio",
                "title": "라디오 버튼 이름",
                "description": "라디오 버튼 설명",
                "placeholder": "",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": [
                    "옵션1",
                    "옵션2",
                    "옵션3"
                ],
                "value": null
            },
            {
                "fieldId": 725,
                "code": "date",
                "type": "date",
                "title": "일자 이름",
                "description": "일자 설명",
                "placeholder": "2022-07-11",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 726,
                "code": "datetime",
                "type": "datetime",
                "title": "일시",
                "description": "일시",
                "placeholder": "2022-07-11 00:00",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 727,
                "code": "dateperiod",
                "type": "date_period",
                "title": "기간 일자 이름",
                "description": "기간 일자 설명",
                "placeholder": "2022-07-01 ~ 2022-07-31",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 728,
                "code": "datetimeperiod",
                "type": "datetime_period",
                "title": "기간 일시 이름",
                "description": "기간 일시 설명",
                "placeholder": "2022-07-01 00:00 ~ 2022-07-31 23:59",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 729,
                "code": "agreetotheterms",
                "type": "agree",
                "title": "동의하기 이름",
                "description": "안내 문구",
                "placeholder": "동의 문구",
                "length": 50,
                "required": false,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            },
            {
                "fieldId": 11,
                "code": "personalAgree",
                "type": "agree",
                "title": "개인정보수집",
                "description": "수집하는 개인 정보[(필수) 이메일, 휴대폰 번호, 문의내용, (선택) 첨부 파일]는 문의 내용 처리 및 고객 불만을 해결하기 위해 사용되며, <b><span style=\"font-size: 11pt;\">관련 법령에 따라 3년간 보관 후 삭제</span></b>됩니다. 문의 접수, 처리 및 회신을 위해 꼭 필요한 정보이므로 동의해 주셔야 서비스를 이용하실 수 있습니다.",
                "placeholder": "위, 개인정보 수집 및 활용에 동의합니다.",
                "length": 0,
                "required": true,
                "encrypt": false,
                "holdingText": true,
                "options": null,
                "value": null
            }
        ]
    }
}
```

### Upload Ticket Attachments
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/ticket/attachments/upload.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/ticket/attachments/upload.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Upload Ticket Attachments |HTTPS  |POST    |UTF-8|JSON    |Upload a file to the server|Common Authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID    |serviceId|String|path    |O|{serviceId} which is set in URL path|
|File|file    |File|formData|O|Submit file through form. Supported file types: jpg, png, gif, bmp, jpeg, tif, tiff, pdf, txt, hwp, xls, xlsx, doc, docx, ppt, pptx, mp3, wav, zip. Size<10M, File name length<100|

#### Result Data(Success)
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content|attachmentId|String|Attachment ID|
|            |fileName    |String|Attachment name|
|            |contentType|String|Attachment type|
|            |disposition|String|Processing method(attachment: attached file)|
|            |size        |Long|Attachment size(byte)|
|            |createdDt    |Long|Attached time|

#### Response Body(Success)
```
  "header": {
    "resultCode": 200,
    "resultMessage": "",
    "isSuccessful": true
  },
  "result": {
    "content": {
      "attachmentId": "8f0dc5854d2446b6aa2e6e41a0a2f55c",
      "fileName": "image.png",
      "contentType": "image/png",
      "disposition": "attachment",
      "size": 90576,
      "createdDt": null
    }
  }
}
```

#### Result Data(Failure)
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content|exception|String|Fixed value：OcException|
|            |message|String|Error message(You can only attach files up to 10MB. / File name maximum length exceeded.(100) / This file format cannot be attached.|

#### Response Body(Failure)
```
{
  "header": {
    "resultCode": 400,
    "resultMessage": "해당 파일 격식은 첨부할 수 없습니다.",
    "isSuccessful": false
  },
  "result": {
    "content": {
      "exception": "OcException",
      "message": "해당 파일 격식은 첨부할 수 없습니다."
    }
  }
}
```

### Create Ticket
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/ticket.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/ticket.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Create Ticket |HTTPS  |POST    |UTF-8|JSON    |Create new ticket|Common authentication   |

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID|serviceId        |String |path|O|{serviceId} which is set in URL path|
|Ticket Information|request body    |Object |body|O|Ticket information(JSON)|
|Category|categoryId        |Integer ||O|Category(Submission type) ID|
|Title    |subject        |String |    |O|Title(max=255)|
|Contents    |content        |String |    |O|In principle, only simple text is allowed. If you submit it as Base64 contents, it may be a problem because of many contents when checking the ticket. For images, upload them in attachment format or import them into html img src=""/{serviceId}/api/v2/ticket/attachments/{attachmentId}""/|
|Customer Information|endUser        |Object  |     |O |Customer information|
|ID    |endUser.usercode|String  |     |X |ID(Member-specific ID). If the membership system is linked, the user's unique ID on the platform side can be used as a usercode, and the member's inquiry history can be inquired through the user code. No value required to be sent for non-membership inquiries.|
|Mail    |endUser.email    |String  |     |O |Mail(If mail information is set in Service Management → Ticket → Email Settings menu, mail will be sent to the customer at the time of ticket processing.)|
|Name    |endUser.username        |String  |     |O |Name(When the mail parameter is entered, the name parameter is also required. Mail cannot be sent if not entered.)|
|Phone      |endUser.phone            |String  |     |X  |Phone|
|Attachment|attachments            |Array  |      |X |Attachment(Up to 5 cases)|
|Attachment ID|attachments.attachmentId|String   | |O |Attachment ID|
|Item1    |typeOne                |String  |     |X |Item1(Extended system field 1)|
|Item2    |typeTwo                |String   | |X |Item2(Extended system field 2)|
|Language    |language                |String  |     |X |Language|
|Channel    |source                    |String   | |X |Channel(web: web, spweb: Mobile web, api: API, Default value: web)|
|User Field|userFields            |Array   |  |X  |User field|
|Field Code    |userFields.code    |String   |  |O  |User field code|
|User Input Value|userFields.value    |String   |      |O  |User input value in user field|

The format of the userFields.value parameter by field type is as follows.

- text(Simple text): "Contents"
- checkbox(Check box): ["Item1"，"Item2"]
- dropdown(Drop box): "Item1"
- radio(Radio button): "Item1"
- date(Date): YYYY-MM-DD("2022-07-11")
- datetime(Date/time): YYYY-MM-DD HH:mm("2022-07-11 00:00")
- date_period(Date period): YYYY-MM-DD ~ YYYY-MM-DD("2022-07-01 ~ 2022-07-31")
- datetime_period(Date/time period): YYYY-MM-DD HH:mm ~ YYYY-MM-DD HH:mm("2022-07-01 00:00 ~ 2022-07-31 23:59")
- agree(Agree to the terms): true, false

#### Request Body
```
{
    "categoryId": "2542", 
    "subject": "유형", 
    "content": "문의내용", 
    "endUser": {
        "usercode": "st18888", 
        "email": "enduser_simple@nhn-st.com", 
        "username": "이름", 
        "phone": "13333333333"
    }, 
    "attachments": [
        {
            "attachmentId": "8f0dc5854d2446b6aa2e6e41a0a2f55c"
        }
    ], 
    "typeOne": "구분1", 
    "typeTwo": "구분2", 
    "language": "ko", 
    "source": "web", 
    "userFields": [
        {
            "code": "textbox", 
            "value": "텍스트 박스 이름"
        }, 
        {
            "code": "checkbox", 
            "value": [
                "옵션1", 
                "옵션2"
            ]
        }, 
        {
            "code": "dropdown", 
            "value": "옵션1"
        }, 
        {
            "code": "radiobutton", 
            "value": "옵션1"
        }, 
        {
            "code": "date", 
            "value": "2022-07-11"
        }, 
        {
            "code": "datetime", 
            "value": "2022-07-11 00:00"
        }, 
        {
            "code": "dateperiod", 
            "value": "2022-07-01 ~ 2022-07-31"
        }, 
        {
            "code": "datetimeperiod", 
            "value": "2022-07-01 00:00 ~ 2022-07-31 23:59"
        }, 
        {
            "code": "agreetotheterms", 
            "value": "true"
        }
    ]
}
```

#### Result Data(Success)
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content|ticketId    |String|Ticket ID|
|            |categoryId  |int|Submission type ID|
|            |subject    |String|Ticket title|
|            |content    |String|Ticket contents|
|            |status        |String|Ticket status(Fixed value: new(unassigned); open(Processing); closed(Processed)|
|            |createdDt   |Long|Created time|
|            |updatedDt    |Long|Updated time|
|            |attachments|Array|Attachment|
|            |attachments.attachmentId|String|Attachment ID|
|            |attachments.fileName    |String|Attachment name|
|            |attachments.contentType|String|Attachment type|
|            |attachments.disposition|String|File processing method(attachment: attached file)|
|            |attachments.size       |String|Attachment size(byt)|
|            |attachments.createdDt   |String|Updated time|

#### Response Body(Success)
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
      "categoryName": null,
      "categoryFullName": null,
      "status": "new",
      "statusName": null,
      "content": "문의내용",
      "createdDt": 1658199661151,
      "updatedDt": 1658199661151,
      "contents": null,
      "attachments": [
        {
          "attachmentId": "8f0dc5854d2446b6aa2e6e41a0a2f55c",
          "fileName": "image.png",
          "contentType": "image/png",
          "disposition": "attachment",
          "size": 90576,
          "createdDt": 1658192910000
        }
      ],
      "displayDt": null
    }
  }
}
```

#### Result Data(Failure)
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.contents|objectName|String|User field: field code|
|               |field    |String|User field: field ID|
|               |validate|String|invalid: an invalid value, length: Maximum length exceeded, required: Please enter an item|
|               |key    |String|"validate.ticket." + objectName + "." + validate|
|               |message|String|"validate.ticket." + objectName + "." + validate|

#### Response Body(Failure)
```
{
  "header": {
    "resultCode": 400,
    "resultMessage": null,
    "isSuccessful": false
  },
  "result": {
    "contents": [
      {
        "objectName": "mail",
        "field": "3",
        "validate": "invalid",
        "key": "validate.ticket.mail.invalid",
        "message": "validate.ticket.mail.invalid",
        "rejectValue": ""
      },
      {
        "objectName": "phone",
        "field": "4",
        "validate": "length",
        "key": "validate.ticket.phone.length",
        "message": "validate.ticket.phone.length",
        "rejectValue": ""
      },
      {
        "objectName": "textbox",
        "field": "721",
        "validate": "length",
        "key": "validate.ticket.textbox.length",
        "message": "validate.ticket.textbox.length",
        "rejectValue": ""
      },
      {
        "objectName": "checkbox",
        "field": "722",
        "validate": "invalid",
        "key": "validate.ticket.checkbox.invalid",
        "message": "validate.ticket.checkbox.invalid",
        "rejectValue": ""
      },
      {
        "objectName": "dropdown",
        "field": "723",
        "validate": "invalid",
        "key": "validate.ticket.dropdown.invalid",
        "message": "validate.ticket.dropdown.invalid",
        "rejectValue": ""
      }
    ]
  }
}
```