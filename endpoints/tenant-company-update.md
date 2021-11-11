#  Update a tenant company
**Path** : `/api/v1/tenants/{tenantId}`

**Path Arguments** : `tenantId`

**Method** : `PATCH`

**Auth required** : YES

**Headers**
```
Content-Type: application/json
Authorization: [string; required]
```

**Body Constraints**
```json
{
  "metadata": "[object; optional; up to 50 keys, with string key names up to 40 characters long and (string values up to 500 characters long or null values)]"
}
```
**Body Sample**
```json
{
  "metadata": {"foo": "bar", "old_key": null}
}
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `tenant company has been updated`
```json
{}
```
**Status Code** : `400 Bad Request`

**Content Type** : `application/json`

**Condition** : `supplied metadata does not match our constraints`
```json
{"code":"BAD_METADATA","message":"[always present; string]"}
```
*Status Code** : `404 Not Found`

**Content Type** : `application/json`

**Condition** : `tenant company not found within the partner account`
```json
{"code":"TENANT_NOT_FOUND","message":"[always present; string]"}
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