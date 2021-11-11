#  Fetch Product Usage records on a Tenant Company
**Path** : `/api/v1/product-usage`

**URL Parameters** :

* `tenantId` : [required; string]
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
      "date": "2021-11-08",
      "product": "metrics",
      "amount": 0,
      "usageQuantity": {
        "mb": 0,
        "b": 0
      }
    },
    {
      "date": "2021-11-09",
      "product": "metrics",
      "amount": 58.4855,
      "usageQuantity": {
        "mb": 389.9038,
        "b": 408843766
      }
    },
    {
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