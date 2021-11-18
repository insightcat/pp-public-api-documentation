#  Fetch Product Usage records on All Tenants
**Path** : `/api/v1/product-usage`

**URL Parameters** :

* `periodStart` : [required; string; date (Y-m-d)]
* `periodEnd` : [required; string; date (Y-m-d)]

**Method** : `GET`

**Auth required** : YES

**Headers**
```
Authorization: [string; required]
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `all went smoothly`

**Json Schema** : [here](../json-schema/1.json)
```json
{
  "daily": [
    {
      "tenantId": "a46859b8-95bc-4ded-b0a2-2656287901fd",
      "date": "2021-11-08",
      "product": "metrics",
      "amount": 0,
      "usageQuantity": {
        "mb": 0,
        "b": 0
      }
    },
    {
      "tenantId": "bb799a72-b6a7-4433-8310-04257e5276b0",
      "date": "2021-11-09",
      "product": "metrics",
      "amount": 58.4855,
      "usageQuantity": {
        "mb": 389.9038,
        "b": 408843766
      }
    },
    {
      "tenantId": "87691acb-a2ed-4ec4-aaf2-f756a007a12e",
      "date": "2021-11-11",
      "product": "metrics",
      "amount": 0,
      "usageQuantity": {
        "mb": 0,
        "b": 0
      }
    }
  ],
  "total": [
    {
      "product": "metrics",
      "amount": 58.48,
      "usageQuantity": {
        "mb": 389.9038,
        "b": 408843766
      }
    }
  ]
}
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