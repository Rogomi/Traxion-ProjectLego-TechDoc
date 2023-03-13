# Get List of Punchlists

Show the list of buyer punchlists.

**URL** : `/api/v1/punchlist/list`

**Query Parameters** : 

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "881bbb54-fc5e-4639-841e-44d21234cbb2",
		"refNo": "BPLTEST123000002",
    		"buyerName" : "James Reid"
		"status": "",
		"type": "Buyer",
		"filedBy": {
			"firstName": "Media",
			"lastName": "Gulapa",
		},
		"unit": {
			"unitNo": "02A",
			"contractNo": "0000100004593"
		},
		"project": {
			"name": "Sample BE 123",
			"projectCode": "00048100"
		},
		"building": {
			"name": "The Residences Place Tower C",
			"bldgCode": "TEST125"
		}
	}
  ....
 ]
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`
