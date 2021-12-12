#  Fetch tenant company's API Keys
**Path** : `/api/v1/tenants/{tenantId}/api-keys`

**Method** : `GET`

**Auth required** : YES

**Headers**
```
Content-Type: application/json
Authorization: [string; required]
```

##  Response

**Status Code** : `200`

**Content Type** : `application/json`

**Condition** : `all good`

**Json Schema** : [here](../json-schema/7.json)

```json
[
  {
    "id": "95b23430-b480-4311-8b43-dbc1ba2d8a20",
    "projectId": "92fe3824-64e7-466f-a73a-b520218f5865",
    "validUntil": 1951893246,
    "createdAt": 1636360446,
    "keySecret": "6GYV7XK572H:fOJdlFH6Wq8z2AFXmQPWMGwIOwks1GI",
    "name": "Main"
  }
]
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