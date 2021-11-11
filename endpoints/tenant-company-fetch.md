#  Fetch a tenant company
**Path** : `/api/v1/tenants/{tenantId}`

**Path Arguments** : `tenantId`

**Method** : `GET`

**Auth required** : YES

**Headers**
```
Authorization: [string; required]
```

##  Response

**Status Code** : `200 OK`

**Content Type** : `application/json`

**Condition** : `tenant company was found within the partner account`
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