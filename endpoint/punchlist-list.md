# Get Buyer Punchlists

Show the list of buyer punchlists.

**URL** : `/api/v1/punchlist/list`

**Query Parameters** : 

- `unitNo=[string]` ex. 02A
- `projectCode=[string]` ex. 00048100
- `buildingCode=[string]` ex. TEST125

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "6328dda0-aeba-4994-ab45-ac9d15e144d7",
		"refNo": "BPLTEST1230001",
		"dateAccepted": "2023-03-11T16:00:00.000Z",
		"buyerName": "Nadine",
		"status": "Accepted",
		"turnaroundTime": "15 days",
		"targetCompletionDate": "2023-07-11T16:00:00.000Z",
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
		},
		"punchlistitems": [
			{
				"sectionName": "Kitchen",
				"item": "Flooring",
				"particular": "Broken",
				"status": null
			}
		]
	}
  ....
 ]
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`
