# Get Viewing Schedules

Show a viewing schedule based on submitted time range.

**URL** : `/api/v1/schedule/viewSchedule`

**Query Parameters** : 

- `unitNo=[string]` 02A
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST125

**Method** : `GET`

**Auth required** : Basic


## Success Response

**Code** : `200 OK`

**Content example**

```json
[
	{
		"id": "881bbb54-fc5e-4639-841e-44d21234cbb2",
		"propertyAddress": "Hello",
    		"buyerName" : "James Reid"
		"viewingDate": "2023-02-25T16:00:00.000Z",
		"timeFrom": "07:00:00",
		"timeTo": "09:30:00",
		"turnoverEngineer": {
			"firstName": "Media",
			"lastName": "Gulapa",
			"position": "Turnover Engineer"
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
