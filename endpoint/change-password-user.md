# Change Password on User Profile


**URL** : `/api/v1/auth/changePasswordUser`

**Method** : `POST`

**Auth required** : Basic

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

