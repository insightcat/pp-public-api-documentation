#  Update user's password
**Path** : `/api/v1/tenants/{tenantId}/users/{userId}/password`

**Method** : `PUT`

**Auth required** : YES

**Headers**
```
Content-Type: application/json
Authorization: [string; required]
```

**Body Constraints ([json-scheme](../json-schema/6.json))**
```json
{
  "password": "[string; required; 8 to 128 chars, at least 1 uppercase letter, at least 1 lowercase letter, at least 1 digit]"
}
```
**Body Sample**
```json
{"password": "Qwerty123#"}
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `password updated successfully`
```json
{}
```
**Status Code** : `404 Not Found`

**Content Type** : `application/json`

**Condition** : `supplied user not found`
```json
{"code": "USER_NOT_FOUND","message":"[always present; string]"}
```
**Status Code** : `404 Not Found`

**Content Type** : `application/json`

**Condition** : `tenant company not found within the partner account`
```json
{"code":"TENANT_NOT_FOUND","message":"[always present; string]"}
```
**Status Code** : `400 Bad Request`

**Content Type** : `application/json`

**Condition** : `supplied password does not match our security policy`
```json
{"code":"BAD_PASSWORD","message":"[always present; string]"}
```
**Status Code** : `401 Unauthorized`

**Content Type** : `application/json`

**Condition** : `invalid access token`
```json
{"code":"UNAUTHORIZED","message":"[always present; string]"}
```
**Status Code** : `422 Unproccessable Entity`

**Content Type** : `application/json`

**Condition** : `supplied request body does not match our constraints`
```json
{"code":"VALIDATION","message":"[always present; string]"}
```
**Status Code** : `405 Method Not Allowed`

**Content Type** : `application/json`

**Condition** : `bad http method`
```json
{"code":"METHOD_NOT_ALLOWED","message":"[always present; string]"}
```
**Status Code** : `500 Internal Server Error`

**Content Type** : `application/json`

**Condition** : `an unexpected error happened`
```json
{"code":"INTERNAL_SERVER_ERROR","message":"[always present; string]"}
```
