#  Enable tenant company's API Keys
**Path** : `/api/v1/tenants/{tenantId}/enable-api-keys`

**Path Arguments** : `tenantId`

**Method** : `POST`

**Auth required** : YES

**Headers**
```
Authorization: [string; required]
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `all tenant company's api keys have been enabled`
```json
{}
```
**Status Code** : `404 Not Found`

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