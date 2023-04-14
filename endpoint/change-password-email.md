# Change Password from Reset Link

**URL** : `/api/v1/auth/changePasswordEmail`

**Method** : `POST`

**Auth required** : Basic

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
