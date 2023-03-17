# Get Buyer Punchlists

Show the list of buyer punchlists.

**URL** : `/api/v1/punchlist/list`

**Query Parameters** : 

- `unitNo=[string]` CONDO13
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST123

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "e064f6bd-165d-4cf6-bc74-cb1d333e1b42",
		"refNo": "BPLTEST1230009",
		"dateAccepted": "2023-04-16T16:00:00.000Z",
		"buyerName": "Mediatrix Gulapa",
		"status": "Accepted",
		"turnaroundTime": "15 days",
		"targetCompletionDate": "2023-04-15T16:00:00.000Z",
		"filedBy": {
			"firstName": "Media",
			"lastName": "Gulapa",
			"position": "Turnover Engineer"
		},
		"unit": {
			"unitNo": "CONDO13",
			"contractNo": "0000100001771"
		},
		"project": {
			"name": "Sample BE 123",
			"projectCode": "00048100"
		},
		"building": {
			"name": "The Residences TEST A",
			"bldgCode": "TEST123"
		},
		"punchlistitems": [
			{
				"sectionName": null,
				"item": "Floor tiles",
				"particular": "okay",
				"status": "Accepted"
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
