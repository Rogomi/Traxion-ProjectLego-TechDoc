# Project Lego API Documentation

Our team utilizes both REST API authentication and GraphQL, with REST being our primary method for authenticating user requests and GraphQL serving as our primary query language for accessing and manipulating data from our server. This allows us to leverage the strengths of both technologies in order to provide a secure and efficient experience for our users.

REST API

- Staging Base URL: https://devumsapi.robinsonsland.com/
- Production Base URL: https://umsapi.robinsonsland.com/

Content: 

* User Login
* Forgot Password
* Change Password from Reset Link 
* Change Password in User Profile 
* Viewing Schedule
* List of Punchlists
* Post Buyer Remarks

* GraphQL API

<hr />

# User Login

For user authentication

**URL** : `/api/v1/auth/login`

**Method** : `POST`

**Header** : api-key: `APIKEY`

**JSON Body Parameters** : 

```json
{
	"email": "testmail@mail.com",
	"password" : "S3cr!tPass"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"token": "Bearer token to be used for authorization header",
	"userId": "bb166ce3-899d-47f9-a622-f51019b60b4b"
}
```

<hr />

# Forgot Password

**URL** : `/api/v1/auth/forgotPassword`

**Method** : `POST`

**Header** : api-key: `APIKEY`

**JSON Body Parameters** : 

```json
{
	"email": "testmail@mail.com"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	"link": "redirection link"
}
```

<hr />

# Change Password from Reset Link

**URL** : `/api/v1/auth/changePasswordEmail`

**Method** : `POST`

**Header** : api-key: `APIKEY`

**JSON Body Parameters** : 

```json
{
  "userId": "user id from link",
  "token": "token from link",
  "password": "new password",
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	message: "Password Changed Successfully"
}
```
<hr />

# Change Password on User Profile

**URL** : `/api/v1/auth/changePasswordUser`

**Method** : `POST`

**Header** : api-key: `APIKEY`

**Header** :

- Authorization: `Bearer Token`

**JSON Body Parameters** : 

```json
{
  "oldPassword": "old password",
  "password": "new password",
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
	message: "Password Changed Successfully"
}
```

<hr />

# Get Viewing Schedules

Show a viewing schedule based on submitted time range.

**URL** : `/api/v1/schedule/viewSchedule`

**Query Parameters** : 

- `unitNo=[string]` CONDO13
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST123

**Method** : `GET`

**Header** : api-key: `APIKEY`


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

**Condition** : If wrong Api Key

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# Get Buyer Punchlists

Show the list of buyer punchlists.

**URL** : `/api/v1/punchlist/list`

**Query Parameters** : 

- `unitNo=[string]` CONDO13
- `projectCode=[string]` 00048100
- `buildingCode=[string]` TEST123

**Method** : `GET`

**Header** : api-key: `APIKEY`


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

**Condition** : If wrong Api Key

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# Post Buyer Remarks

Post a buyer remarks for viewing schedule.

**URL** : `/api/v1/schedule/viewSchedule`

**Method** : `POST`

**Header** : api-key: `APIKEY`

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

**Condition** : If wrong Api Key

**Code** : `401 UNAUTHORIZED`

**Content** : `{}`

<hr />

# GRAPHQL API Documentation

Our team has adopted GraphQL as our primary method for accessing data, as it provides a streamlined and intuitive approach to fetching and manipulating data from our server. With GraphQL, we are able to easily document our API and maintain consistent communication between our frontend and backend teams.

- Staging Endpoint: https://devumsapi.robinsonsland.com/rLcTrAxi0NpR0d
- Production Endpoint: https://umsapi.robinsonsland.com/rLcTrAxi0NpR0d

Header Credentials:

- Authentication: `Bearer Token`
- api-key: `APIKEY`

Access the endpoint to test the API. You can use GraphQL Altair, a GraphQL API tool. https://altairgraphql.dev/ Also, GraphQL API Tool provides a more user-friendly and detailed documentation. 

Open this documentation for the list of queries and mutations in HTML format:

https://drive.google.com/file/d/1fcbJU41dILe6EDCAq12rBZJ65wcc3COh/view?usp=sharing




