#  {description}
**Path** : `{path}`

**Method** : `{method}`

**Auth required** : {YES/NO}

**Headers**
```
Content-Type: application/json
Authorization: [string; required]
```

**Body Constraints**
```json
{
  "key": "[required; string; up to 50 characters]"
}
```
**Body Sample**
```json
{"key": "value"}
```

##  Response

**Status Code** : `{success code}`

**Content Type** : `application/json`

**Condition** : `{success condition}`
```json
{
  "key": "value"
}
```
