# Error Response

Every error, be it business or semantic, that is returned by the InsightCat PP Public API, has the following structure
```json
{
  "code": "[always present; string]",
  "message": "[always present; string]"
}
```

`code` is the field that actually says the reason why the error happened.

`message` is just a "human-readable" form of the error. It was introduced for debug reasons. You SHOULD NEVER rely on the contents of this field as it may change over time. 

Examples
```json
{
  "code": "TENANT_NOT_FOUND",
  "message": "Tenant not found."
}
```
```json
{
  "code": "VALIDATION",
  "message": "os: The os field is required; agent: The agent field is required; tenantId: The tenant id field is required"
}
```
