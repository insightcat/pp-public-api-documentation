# HTTP API

Dear reader, if you are planning on setting up an integration with InsightCat PP Public API, we recommend that you read this first
- [Error Response](misc/error-response.md)
- [Metadata](misc/metadata.md)
- [Logical Context Map](misc/context-map.md)
- [API Key Application](misc/api-key-application.md)

## Endpoints that require Authentication

Closed endpoints require a valid access token to be included in the header of the request.

### Tenant Company related
* [Fetch](endpoints/tenant-company-fetch.md) : `GET /api/v1/tenants/{tenantId}`
* [Create](endpoints/tenant-company-create.md) : `POST /api/v1/tenants`
* [Update](endpoints/tenant-company-update.md) : `PATCH /api/v1/tenants/{tenantId}`
* [Disable API Keys](endpoints/tenant-company-disable-api-keys.md) : `POST /api/v1/tenants/{tenantId}/disable-api-keys`
* [Enable API Keys](endpoints/tenant-company-enable-api-keys.md) : `POST /api/v1/tenants/{tenantId}/enable-api-keys`

### API Keys related
* [Fetch All](endpoints/api-keys-fetch.md) : `GET /api/v1/tenants/{tenantId}/api-keys`

### User related
* [Update password](endpoints/user-update-password.md) : `PUT /api/v1/tenants/{tenantId}/users/{userId}/password`

### Agent Config related
* [Download](endpoints/download-agent-config.md) : `GET /api/v1/agent-config`

### Product Usage related
* [Fetch](endpoints/product-usage-fetch-all-tenants.md) : `GET /api/v1/product-usage`
* [Fetch for one Tenant Company](endpoints/product-usage-fetch-on-tenant-company.md) : `GET /api/v1/product-usage`

___
Made with ❤️ by [InsightCat](https://insightcat.com) 