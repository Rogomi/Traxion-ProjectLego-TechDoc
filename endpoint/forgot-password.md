# Forgot password

**URL** : `/api/v1/auth/forgotPassword`

**Method** : `POST`

**Auth required** : Basic

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
