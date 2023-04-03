# Project Lego REST API Documentation

Base URL: https://devumsapi.robinsonsland.com/

Basic Auth Credentials:

- Username: `username`
- Password: `password`

##

# Get Viewing Schedules

Show a viewing schedule based on submitted unit details

**URL** : `/api/v1/schedule/viewSchedule`

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
		"id": "cda1e6dd-8567-43da-8152-3931b3f374eb",
		"propertyAddress": "QC",
		"viewingDate": "2023-03-15T16:00:00.000Z",
		"timeFrom": "08:00:00",
		"timeTo": "09:00:00",
		"buyerName": "JAMES REID FORD WHITE REID ORANGE BLUE",
    		"buyerRemarks": "This is a remarks",
		"turnoverEngineer": {
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
		}
  ....
 ]
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

##

# Post Buyer Remarks

Post a buyer remarks for viewing schedule.

**URL** : `/api/v1/schedule/postBuyerRemarks`

**Method** : `POST`

**Auth required** : Basic

**JSON Body Parameters** : 

```json
{
	"unitNo": "CONDO13",
	"projectCode" : "00048100",
	"buildingCode": "TEST123",
	"buyerRemarks" : "This is a remark"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"id": "e5a8836c-8a16-4bbc-a99f-f76f48af6f80",
	"message": "Buyer's Remarks Successfully Posted."
}
```

## Error Responses

**Condition** : If wrong Basic Auth Credentials

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

##

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


