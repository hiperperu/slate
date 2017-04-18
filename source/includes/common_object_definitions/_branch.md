
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
    "status": "ACTIVE",
    "congestion": "MEDIUM",
    "lowEstimatedTime": 10,
    "highEstimatedTime": 14,
    "sectors": [
        {
            "id": "m9",
            "name": "Tower A",
            "shortName": "A",
            "status": "ACTIVE",
            "services": ["s8", "s9", "s10", "s30"]
        }
    ]
}
```

Model of branch object.

<aside class="warning">
    <strong>Caution:</strong> The <code>congestion</code>, <code>lowEstimatedTime</code> and <code>highEstimatedTime</code> are calculated using the configuration of the associated branch type. You need configure the next:
    <ul>
        <li>Time range to consider to calculate the waiting time.</li>
        <li>Desviation of waiting time.</li>
        <li>Minimal waiting time of medium congestion.</li>
        <li>Minimal waiting time of high congestion.</li>
    </ul>
    If the branch is <code>INACTIVE</code> this fields are not returned.
</aside>

### Fields

* **id** <span class="param-type">String</span><br>
Branch unique identifier (Configured from Bmatic configuration panel).

* **name** <span class="param-type">String</span><br>
Complete name of the branch.
<p>
    <span class="param-condition">Maximum length:</span> <code>50</code>
</p>

* **shortName** <span class="param-type">String</span><br>
Name to display in small devices.
<p>
    <span class="param-condition">Maximum length:</span> <code>20</code>
</p>

* **address** <span class="param-type">String</span><br>
Branch address.
<p>
    <span class="param-condition">Maximum length:</span> <code>100</code>
</p>

* **latitude** <span class="param-type">Float</span><br>
Latitude component of branch location.

* **longitude** <span class="param-type">Float</span><br>
Longitude component of branch location.

* **status** <span class="param-type">Enum</span><br>
Current status of the branch.
<p>
    <span class="param-condition">Possible values:</span>
        <ul>
            <li><code>ACTIVE</code>: At least one sector is <code>ACTIVE</code></li>
            <li><code>INACTIVE</code>: All sectors are <code>INACTIVE</code></li>
        </ul>
</p>

* **congestion** <span class="param-type">String</span><br>
Flag of branch congestion.
<p>
    <span class="param-condition">Possible values:</span>
        <ul>
            <li><code>LOW</code>: The average waiting time is lower to the minimal waiting time of medium congestion.</li>
            <li><code>MEDIUM</code>: The average waiting time is lower to the minimal waiting time of high congestion but equal or upper to the minimal waiting time of medium congestion.</li>
            <li><code>HIGH</code>: The average waiting time is equal or upper to the minimal waiting time of high congestion</li>
        </ul>
</p>

* **lowEstimatedTime** <span class="param-type">Integer</span><br>
Lower bound of the estimated waiting time. It's equal to the average waiting time minus the configured desviation.

* **highEstimatedTime** <span class="param-type">Integer</span><br>
Upper bound of the estimated waiting time. It's equal to the average waiting time plus the configured desviation.

* **sectors** <span class="param-type">List\<[Sector](#sector)\></span><br>
List of the branch's sectors. A correct configuration include at least one sector per branch.
<p>
    <span class="param-condition">Unique items:</span> <code>true</code><br>
    <span class="param-condition">Minimum items:</span> <code>1</code>
</p>
