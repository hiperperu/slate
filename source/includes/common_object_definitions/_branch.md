
## Branch

> Sample object:

```json
{
    "id": "27b6",
    "name": "Hiper Central",
    "shortName": "Hiper",
    "address": "Calle Beta 181 - 195, Callao",
    "latitude": -12.049919,
    "longitude": -77.0845193,
    "status": "OPEN",
    "isVirtual": true,
    "isBookable": true,
    "congestion": "MEDIUM",
    "lowEstimatedTime": 10,
    "highEstimatedTime": 14,
    "sectors": [
        {
            "id": "m8",
            "name": "Tower A",
            "shortName": "A",
            "status": "OPEN",
            "services": ["s9","s10","s30"]
        }
    ]
}
```

Model of branch object.

<aside class="warning">
<strong>Caution:</strong> The fields <code>congestion</code>, <code>lowEstimatedTime</code>, <code>highEstimatedTime</code> are undefined when the branch is closed.
</aside>

### Fields

* **id** <span class="param-type">String</span> <br>Branch unique identifier.
* **name** <span class="param-type">String</span> <br>Complete name of the branch. <p>*Maximum length*: <code>120</code></p>
* **shortName** <span class="param-type">String</span> <br>Name to display in small devices. <p>*Maximum length*: <code>20</code></p>
* **address** <span class="param-type">String</span> <br>Branch address. <p>*Maximum length*: <code>100</code></p>
* **latitude** <span class="param-type">Float</span> <br>Latitude component of branch location.
* **longitude** <span class="param-type">Float</span> <br>Longitude component of branch location.
* **status** <span class="param-type">Enum</span> <br>Current status of the branch. <p>*Possible values*: <ul><li><code>ACTIVE</code></li><li><code>INACTIVE</code></li></ul></p>
* **isVirtual** <span class="param-type">Boolean</span> <br>Possibility to create virtual tickets.
* **isBookable** <span class="param-type">Boolean</span> <br>Possibility to book.
* **congestion** <span class="param-type">String</span> <br>Congestion of the branch. <p>*Possible values*: <ul><li><code>LOW</code></li><li><code>MEDIUM</code></li><li><code>HIGH</code></li></ul></p>
* **lowEstimatedTime** <span class="param-type">Integer</span> <br>Lower bound of the estimated waiting time.
* **highEstimatedTime** <span class="param-type">Integer</span> <br>Upper bound of the estimated waiting time.
* **sectors** <span class="param-type">List\<[Sector](#sector)\></span> <br> List of the branch's sectors.<p>*Unique items:* <code>true</code><br>*Minimum items:* <code>1</code></p>
