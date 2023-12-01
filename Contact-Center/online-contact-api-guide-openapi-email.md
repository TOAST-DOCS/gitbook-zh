## Contact Center > Online Contact > API Guide for Developers > Email Set-up

### Create representative account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/create.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/create.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Create representative account|HTTPS  |POST    |UTF-8|JSON    |Create service representative account. (Cannot be modified after creation) Format: \*\*@oc.toast.com|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|Email information	|mail	|String	|O	|Email information(Example:'mail' part of mail@oc.toast.com)|

#### Query String
- mail=mail

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|result.content	|displayMail	|String	|	  |Sender address|
|	              |external	    |String	|	  |List of external accounts|
|	              |mail	        |String	|O	|Address of representative account : mail@oc.toast.com|
|	              |name	        |String	|	  |Sender name|
|	              |template	    |String	|	  |Email format|
|	              |updatedDt	  |Long	  |	  |Updated time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "displayMail":"noreply@toast.com",
            "external":{},
            "mail":"mail@oc.toast.com",
            "name":"noreply",
            "template":"<p>#{content}</p>",
            "updatedDt":1597369998000
        }
    }
}
```

### Query email information
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Query email information|HTTPS  |GET    |UTF-8|JSON    |View all email information in the service|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|

#### Result Data
|Name |Variable |Data type |Required | Description|
|----|-----|-----------|-----|----|
|result.content	|displayMail	|String	|	  |Sender address|
|	              |external	    |String	|	  |List of external accounts|
|	              |mail	        |String	|O	|Address of representative account : mail@oc.toast.com|
|	              |name	        |String	|	  |Sender name|
|	              |template	    |String	|	  |Email format|
|	              |updatedDt	  |Long	  |	  |Updated time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "displayMail":"noreply@toast.com",
            "external":{},
            "mail":"mail@oc.toast.com",
            "name":"noreply",
            "template":"<p>#{content}</p>",
            "updatedDt":1597371255000
        }
    }
}
```

### Check Validation of External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external/verify.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external/verify.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Check validation of external account|HTTPS  |POST    |UTF-8|JSON    |Check validation of external account|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External Account Information	|request body	|String	  |O	|External account information(JSON)|
|	             |id	         |Integer	 |   |External account ID (Not required when creating new account, only for modification)|
|	             |name	       |String	 |O	 |External account name(Length:min=1, max=20)|
|	             |active	     |Boolean	 |O	 |External account status(true:Enable ,false:Disable), Only required for modification|
|	             |host	       |String	 |O	 |Mail server|
|	             |port	       |Integer  |O	 |Port(Example:993)|
|	             |ssl	         |Boolean	 |O	 |SSL usage(true:use, false:do not use)|
|	             |mail	       |String	 |O	 |External account address(Precise email address)|
|	             |password	   |String	 |O	 |External account password(The email address and password you entered during your subscription will be retained.)|
|	             |mailDel   	 |Boolean	 |O	 |Use Leave Source feature(true:Delete(Email will be automatically deleted when converted to ticket）,false:Hold)|

#### Request Body
```
{
    "id":21,
    "name":"octest1",
    "active":true
    "host":"imap.163.com",
    "port":993,
    "ssl":true
    "mail":"octest1@163.com",
    "password":"yourpassword",
    "mailDel":false
}
```

#### Result Data
|Name |Variable |Data type |Required | Description|
|-------|--------|-------------|-----|---|
|result|content|String     |O   |SUCCESS(success)|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
         "content":"SUCCESS",
    }
}
```

### Register External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Register External Account|HTTPS|POST|UTF-8|JSON|Register External Account(Can register after validation checked)|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External Account Information	|request body	|String	  |O	|External account information(JSON)|
|	             |name	       |String	 |O	 |External account name(Length:min=1, max=20)|
|	             |host	       |String	 |O	 |Mail server|
|	             |port	       |Integer  |O	 |Port(Example:993)|
|	             |ssl	         |Boolean	 |O	 |SSL usage(true:use, false:do not use)|
|	             |mail	       |String	 |O	 |External account address(Precise email address)|
|	             |password	   |String	 |O	 |External account password(The email address and password you entered during your subscription will be retained.)|
|	             |mailDel   	 |Boolean	 |O	 |Use Leave Source feature(true:Delete(Email will be automatically deleted when converted to ticket）,false:Hold)|

#### Request Body
```
{
    "name":"octest1",
    "host":"imap.163.com",
    "port":993,
    "ssl":true
    "mail":"octest1@163.com",
    "password":"yourpassword",
    "mailDel":false
}
```

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|----|-----------|-----|----|
|result.content	|id	      |Integer	|	  |External account ID|
|               |name	    |String	  |O	|External account name|
|	              |active	  |Boolean	|O	|External account status(Fixed value:true)|
|	              |host	    |String	  |O	|Mail server|
|	              |port	    |Integer	|O	|Port(Example:993)|
|               |ssl	    |Boolean	|O	|SSL usage(true:In use,false:Not in use)|
|	              |mail	    |String	  |O	|External account address|
|	              |password	|String	  |O	|External account password|
|	              |mailDel	|Boolean	|O	|Use Leave Source feature(true:Delete, false:Hold)|
|	              |createdDt	|Long	  |	  |Created time|
|	              |updatedDt	|Long   |		|Edited time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "id":16,
            "name":"octest1",
            "active":true
            "host":"imap.163.com",
            "port":993,
            "ssl":true
            "mail":"octest1@163.com",
            "password":"********",
            "mailDel":false,
            "createdDt":1597382469685,
            "updatedDt":1597382469685
        }
    }
}
```

### Edit External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Edit external account|HTTPS|PUT|UTF-8|JSON|Edit external account(Editable after validation checked)|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External Account ID	   |id	         |Integer   |O	 |External account ID, {id} which is set in URL path|
|External Account Information	 |request body	|String	  |O	  |External account information(JSON)|
|	              |name	         |String	 |O	   |External account name(Length:min=1, max=20)|
|	              |active	       |Boolean	 |	   |External account status(true:Enable ,false:Disable)|
|	              |host	         |String	 |O	   |Mail server|
|	              |port	         |Integer	 |O	   |Port(Example:993)|
|	              |ssl	         |Boolean	 |O	   |SSL usage(true:use,false:Not use)|
|	              |mail	         |String	 |O	   |External account address(precise email address)|
|	              |password	     |String	 |O	   |External account password(The email address and password you entered during your subscription will be retained.)|
|	              |mailDel	     |Boolean	 |O	   |Use Leave Source feature(true:Delete(Email will be automatically deleted when converted to ticket）,false:Hold)|

#### Request Body
```
{
    "name":"octest1",
    "host":"imap.163.com",
    "port":993,
    "ssl":true
    "mail":"octest1@163.com",
    "password":"yourpassword",
    "mailDel":false
}
```

#### Result Data
|Name |Variable |Data type |Required | Description|
|----|-----|------------|----|----|
|result.content	|id	      |Integer	|	  |External account ID|
|               |name	    |String	  |O	|External account name|
|	              |active	  |Boolean	|O	|External account status(true:Enable ,false:Disable)|
|	              |host	    |String	  |O	|Mail server|
|	              |port	    |Integer	|O	|Port(Example:993)|
|               |ssl	    |Boolean	|O	|SSL usage(true:In use,false:Not in use)|
|	              |mail	    |String	  |O	|External account address|
|	              |password	|String	  |O	|External account password|
|	              |mailDel	|Boolean	|O	|Use Leave Source feature(true:Delete, false:Hold)|
|	              |createdDt	|Long	  |	  |Created time|
|	              |updatedDt	|Long   |		|Edited time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "id":null,
            "name":"octest1",
            "active":null
            "host":"imap.163.com",
            "port":993,
            "ssl":true
            "mail":"octest1@163.com",
            "password":"********",
            "mailDel":false,
            "createdDt":null,
            "updatedDt":1597382469685
        }
    }
}
```

### Enable External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}/enable.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}/enable.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Enable External Account|HTTPS|PUT|UTF-8|JSON|Enable disabled external account|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External account ID	|id	       |Integer	|O	|External account ID, {id} which is set in URL path|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|result.content	|id	      |Integer	|	  |External account ID|
|               |name	    |String	  |O	|External account name|
|	              |active	  |Boolean	|O	|External account status(Fixed value:true)|
|	              |host	    |String	  |O	|Mail server|
|	              |port	    |Integer	|O	|Port(Example:993)|
|               |ssl	    |Boolean	|O	|SSL usage(true:In use,false:Not in use)|
|	              |mail	    |String	  |O	|External account address|
|	              |password	|String	  |O	|External account password|
|	              |mailDel	|Boolean	|O	|Use Leave Source feature(true:Delete, false:Hold)|
|	              |createdDt	|Long	  |	  |Created time|
|	              |updatedDt	|Long   |		|Edited time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "id":21,
            "name":"octest1",
            "active":true
            "host":"imap.163.com",
            "port":993,
            "ssl":true
            "mail":"octest1@163.com",
            "mailDel":false,
            "createdDt":1578376856000,
            "updatedDt":1597384423000
        }
    }
```

### Disable External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}/disable.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}/disable.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Disable external account|HTTPS|PUT|UTF-8|JSON|Disable enabled external account|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External account ID	|id	       |Integer	|O	|External account ID, {id} which is set in URL path|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|----|-----------|-----|----|
|result.content	|id	      |Integer	|	  |External account ID|
|               |name	    |String	  |O	|External account name|
|	              |active	  |Boolean	|O	|External account status(Fixed value:false)|
|	              |host	    |String	  |O	|Mail server|
|	              |port	    |Integer	|O	|Port(Example:993)|
|               |ssl	    |Boolean	|O	|SSL usage(true:In use,false:Not in use)|
|	              |mail	    |String	  |O	|External account address|
|	              |password	|String	  |O	|External account password|
|	              |mailDel	|Boolean	|O	|Use Leave Source feature(true:Delete, false:Hold)|
|	              |createdDt	|Long	  |	  |Created time|
|	              |updatedDt	|Long   |		|Edited time|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":{
            "id":21,
            "name":"octest1",
            "active":false
            "host":"imap.163.com",
            "port":993,
            "ssl":true
            "mail":"octest1@163.com",
            "mailDel":false,
            "createdDt":1578376856000,
            "updatedDt":1597384423000
        }
    }
```

### Delete External Account
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail/external/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Delete external account|HTTPS|DELETE|UTF-8|JSON|Delete disabled external account|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	|serviceId	|String	|O	|Service ID，{serviceId} which is set in URL path|
|External account ID	|id	       |Integer	|O	|External account ID, {id} which is set in URL path|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|----|------------|-----|---|
|result.content|		|String|		|"SUCCESS":Delete success|

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":{
        "content":"SUCCESS"
    }
}
```

### Save email information
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/mail.json
- URL(Dev):	https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/mail.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restricted|
|------------|-------|--------|-----|--------|--------------|------------|
|Save email information|HTTPS|POST|UTF-8|JSON|Save email information|Common authentication|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|---|
|Service ID	        |serviceId	   |String	|O	|Service ID|
|Email Setting Information	 |request body	|String	 |O	 |Email Setting Information(JSON)|
|	                 |name	        |String	 |	 |Sender name(Length:min = 0, max = 45)|
|	                 |displayMail	  |String	 |	 |Sender address(Example：noreply@oc.toast.com)|
|	                 |template	    |String	 |	 |Email layout. Example) \<p\>\#\{content\}\<\/p\> This mail layout is applied in all sent mail. #{content} tag must be included.|

#### Request Body
```
{
    "name":"noreply",
    "displayMail":"noreply@oc.toast.com",
    "template":"<p>#{content}</p>"
}
```

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|----|-----------|-----|----|
|result	|		|	        |      |    |

#### Response Body
```
{
    "header":{
        "resultCode":200,
        "resultMessage":"",
        "isSuccessful":true
    },
    "result":null
}
```
