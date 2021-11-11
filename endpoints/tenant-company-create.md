#  Create a tenant company
**Path** : `/api/v1/tenants`

**Method** : `POST`

**Auth required** : YES

**Headers**
```
Content-Type: application/json
Authorization: [string; required]
```

**Body Constraints ([json-scheme](../json-schema/5.json))**
```json
{
	"tenantId": "[string; required; 1 to 255 chars]",
	"email": "[string; required; a valid email address]",
	"password": "[string; required; 8 to 128 chars, at least 1 uppercase letter, at least 1 lowercase letter, at least 1 digit]",
	"metadata": "[object; optional; up to 50 keys, with string key names up to 40 characters long and string values up to 500 characters long]"
}
```

**Body Sample**
```json
{
	"tenantId": "abc-abc",
	"email": "tenant@email.com",
	"password": "VerySecurePassword1999#",
	"metadata": {"foo": "bar"}
}
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `a tenant company has been created successfully`

**Json Schema** : [here](../json-schema/3.json)

```json
{
  "tenantId": "123123336",
  "email": "first-tenant+3@company.com",
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vcG9ydGFsLWFwaS5kZXZwb3J0YWwuaW5zaWdodGNhdC5jb20vYXBpL3YxL3BwL3RlbmFudHMiLCJpYXQiOjE2MzY2MjA3MDMsImV4cCI6MTYzNjgzNjcwMywibmJmIjoxNjM2NjIwNzAzLCJqdGkiOiJTeFh4RkJpVDNvcmJIWWdqIiwic3ViIjoiNGQ0N2E2ODctNjhmNy00YjNmLWI0YjctYzlmMDk4YTY1NmU0IiwicHJ2IjoiMzM3NDQ5MmQ3NTFhN2RlMjhkMDRkZTA4OGU3ZGRmMTE4NDgzYTYwOCIsImNvbXBhbnlSb2xlIjoib3duZXIiLCJjb21wYW55SWQiOiI5M2U4M2FhNS1lOGMzLTQ1NmEtYmE2Yi0wYTU5MmRmOGMzMjAiLCJwcm9qZWN0cyI6WyI2NGI1NTJhYy1iZjNkLTRkNzEtYTg2Ni04YzBhMTg5M2JhNjMiXSwicHJvamVjdHNWMiI6W3siaWQiOiI2NGI1NTJhYy1iZjNkLTRkNzEtYTg2Ni04YzBhMTg5M2JhNjMiLCJyb2xlIjoib3duZXIifV19.L4zP7XldoEq_X9jD201DpOf2-NAWHoJgs8q23GoCVTM",
  "signInURL": "https://devportal.insightcat.com/login?token-issuer=portal&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vcG9ydGFsLWFwaS5kZXZwb3J0YWwuaW5zaWdodGNhdC5jb20vYXBpL3YxL3BwL3RlbmFudHMiLCJpYXQiOjE2MzY2MjA3MDMsImV4cCI6MTYzNjgzNjcwMywibmJmIjoxNjM2NjIwNzAzLCJqdGkiOiJTeFh4RkJpVDNvcmJIWWdqIiwic3ViIjoiNGQ0N2E2ODctNjhmNy00YjNmLWI0YjctYzlmMDk4YTY1NmU0IiwicHJ2IjoiMzM3NDQ5MmQ3NTFhN2RlMjhkMDRkZTA4OGU3ZGRmMTE4NDgzYTYwOCIsImNvbXBhbnlSb2xlIjoib3duZXIiLCJjb21wYW55SWQiOiI5M2U4M2FhNS1lOGMzLTQ1NmEtYmE2Yi0wYTU5MmRmOGMzMjAiLCJwcm9qZWN0cyI6WyI2NGI1NTJhYy1iZjNkLTRkNzEtYTg2Ni04YzBhMTg5M2JhNjMiXSwicHJvamVjdHNWMiI6W3siaWQiOiI2NGI1NTJhYy1iZjNkLTRkNzEtYTg2Ni04YzBhMTg5M2JhNjMiLCJyb2xlIjoib3duZXIifV19.L4zP7XldoEq_X9jD201DpOf2-NAWHoJgs8q23GoCVTM",
  "metadata": {
    "foo":"bar"
  }
}
```
**Status Code** : `401 Unauthorized`

**Content Type** : `application/json`

**Condition** : `invalid access token`
```json
{"code":"UNAUTHORIZED","message":"[always present; string]"}
```
**Status Code** : `409 Conflict`

**Content Type** : `application/json`

**Condition** : `supplied email already exists in the system`
```json
{"code":"EMAIL_OCCUPIED","message":"[always present; string]"}
```
**Status Code** : `409 Conflict`

**Content Type** : `application/json`

**Condition** : `partner already has a tenant company with the supplied tenantId`
```json
{"code":"TENANT_ID_OCCUPIED","message":"[always present; string]"}
```
**Status Code** : `400 Bad Request`

**Content Type** : `application/json`

**Condition** : `supplied tenantId does not match our constraints`
```json
{"code":"BAD_TENANT_ID","message":"[always present; string]"}
```
**Status Code** : `400 Bad Request`

**Content Type** : `application/json`

**Condition** : `supplied metadata does not match our constraints`
```json
{"code":"BAD_METADATA","message":"[always present; string]"}
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