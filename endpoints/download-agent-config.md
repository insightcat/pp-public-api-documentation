#  Download an agent config file
**Path** : `/api/v1/agent-config`

**URL Parameters**: `os`, `agent`, `tenantId`

`os`, available values: `mac`, `windows`, `linux`, `redhat`, `ubuntu`

`agent`, available values: `fluentbit`, `fluentd`, `insightcat`, `logstash`, `prometheus`, `telegraf`

**Full URL example** : `https://pp-public-api.insightcat.com/api/v1/agent-config?os=linux&agent=telegraf&tenantId=b2728ae4-0b4e-4422-bb90-94d735921dfa`

**Method** : `GET`

**Auth required** : YES

**Headers**
```
Authorization: [string; required]
```

##  Response

**Status Code** : `200 OK`

**Condition** : `agent config was found and returned`

**Content Type** : `text/html`

```text
filter {
      mutate {
         rename => {"@timestamp" => "date"}
      }
}

# Output section
output {
  http {
    format => "json_batch"
    headers => {"Authorization" => "Bearer PMU1KH34UUR:OMXq53u1Lew7URjlLNnnN1q8paCymcB"}
    http_method => "post"
    url => "https://rcv.insightcat.com/api/v1/write"
  }
}
```
**Status Code** : `404 Not Found`

**Content Type** : `application/json`

**Condition** : `tenant company not found within the partner account`
```json
{"code":"TENANT_NOT_FOUND","message":"[always present; string]"}
```
**Status Code** : `412 Precondition Failed`

**Content Type** : `application/json`

**Condition** : `tenant company does not have any api keys`
```json
{"code":"NO_API_KEYS","message":"[always present; string]"}
```
**Status Code** : `404 Not Found`

**Content Type** : `application/json`

**Condition** : `no agent configs that match the supplied criteria`
```json
{"code":"AGENT_CONFIG_NOT_FOUND","message":"[always present; string]"}
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
