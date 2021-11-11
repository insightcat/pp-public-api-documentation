# Metadata
Updateable InsightCat objects have a metadata parameter. You can use this parameter to attach key-value data to these InsightCat objects.

You can specify up to 50 keys, with key names up to 40 characters long and values up to 500 characters long.

Metadata is useful for storing additional, structured information on an object. As an example, you could store someone's full name and corresponding unique identifier from your system on an InsightCat object. Metadata is not used by InsightCat.

Do not store any sensitive information (bank account numbers, card details, etc.) as metadata.

## How updating metadata works
When updating metadata, InsightCat does not replace the existing object with the supplied one, but rather complements it.

Deleting metadata keys is done by setting them to `null`.

### Case #1
**Objective** : delete the `phoneNumber` key

**Given metadata**
```json
{
  "name": "Juan Marselo",
  "phoneNumber": "+4567890042"
}
```

**Metadata object that should be supplied**
```json
{
  "phoneNumber": null
}
```

**Result metadata**
```json
{
  "name": "Juan Marselo"
}
```

### Case #2
**Objective** : change the value of the `name` key

**Given metadata**
```json
{
  "name": "Juan",
  "lastName": "Marselo"
}
```

**Metadata object that should be supplied**
```json
{
  "name": "Ivan"
}
```

**Result metadata**
```json
{
  "name": "Ivan",
  "lastName": "Marselo"
}
```

### Case #3
**Objective** : add some new keys

**Given metadata**
```json
{
  "key1": "value1",
  "key2": "value2"
}
```

**Metadata object that should be supplied**
```json
{
  "key3": "value3"
}
```

**Result metadata**
```json
{
  "key1": "value1",
  "key2": "value2",
  "key3": "value3"
}
```

### Case #4
**Objective** : add some new keys, delete the `key1` key, change the value of the `key2` key 

**Given metadata**
```json
{
  "key1": "value1",
  "key2": "value2"
}
```

**Metadata object that should be supplied**
```json
{
  "newKey": "newValue",
  "key1": null,
  "key2": "newValueForKey2"
}
```

**Result metadata**
```json
{
  "newKey": "newValue",
  "key2": "newValueForKey2"
}
```