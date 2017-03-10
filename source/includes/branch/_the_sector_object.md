
## The Sector object

Model of sector object.

> Sample object:

```json
{
    "id": "s8",
    "name": "Tower A",
    "short_name": "A",
    "status": "OPEN",
    "services": ["s9","s10","s30"]
}
```

### Fields

| |
|:---|
|**id** *string* <br>Sector unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{2,6}$</code></p> |
|**name** *string* <br>Complete name of the sector. <p>*Maximum length*: <code>120</code></p> |
|**short_name** *string* <br>Name to display in small devices. <p>*Maximum length*: <code>20</code></p> |
|**status** *enum* <br>Current status of the sector. <p>*Possible values*: <ul><li><code>OPEN</code></li><li><code>CLOSE</code></li></ul></p> |
|**services** *array[string]* <br> List of ids of the services allowed at sector.<p>*Unique items:* <code>true</code><br>*Minimun items:* <code>1</code></p>|
