
## Sector

Model of sector object.

> Sample object:

```json
{
    "id": "m8",
    "name": "Tower A",
    "shortName": "A",
    "status": "OPEN",
    "services": ["s9","s10","s30"]
}
```

### Fields

* **id** <span class="param-type">String</span> <br>Sector unique identifier.
* **name** <span class="param-type">String</span> <br>Complete name of the sector. <p>*Maximum length*: <code>120</code></p>
* **shortName** <span class="param-type">String</span> <br>Name to display in small devices. <p>*Maximum length*: <code>20</code></p>
* **status** <span class="param-type">Enum</span> <br>Current status of the sector. <p>*Possible values*: <ul><li><code>ACTIVE</code></li><li><code>INACTIVE</code></li></ul></p>
* **services** <span class="param-type">List\<String\></span> <br> List of ids of the services allowed at sector.<p>*Unique items:* <code>true</code><br>*Minimum items:* <code>1</code></p>
