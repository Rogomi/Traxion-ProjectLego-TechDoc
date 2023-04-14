# Login

For user authentication

**URL** : `/api/v1/auth/login`

**Method** : `POST`

**Auth required** : Basic

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
