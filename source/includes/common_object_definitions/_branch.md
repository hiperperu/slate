
## Branch

> Sample object:

```json
{
    "id": "27b6",
    "name": "Hiper Central",
    "short_name": "Hiper",
    "address": "Calle Beta 181 - 195, Callao",
    "latitude": -12.049919,
    "longitude": -77.0845193,
    "status": "ACTIVE",
    "congestion": "MEDIUM",
    "low_estimated_time": 10,
    "high_estimated_time": 14,
    "sectors": [
        {
            "id": "m9",
            "name": "Tower A",
            "short_name": "A",
            "status": "ACTIVE"
        }
    ]
}
```

Model of branch object.

<aside class="warning">
    <strong>Caution:</strong> The <code>congestion</code>, <code>low_estimated_time</code> and <code>high_estimated_time</code> are calculated using the configuration of the associated branch type. You need configure the next:
    <ul>
        <li>Time range to take for calculate the waiting time.</li>
        <li>Desviation of estimated waiting time.</li>
        <li>Minimal waiting time of medium congestion.</li>
        <li>Minimal waiting time of high congestion.</li>
    </ul>
    If the branch is <code>INACTIVE</code> these fields will not return.
</aside>

### Fields

* **id** <span class="param-type">String</span><br>
Branch unique identifier (Configured from Bmatic configuration panel).

* **name** <span class="param-type">String</span><br>
Complete name of the branch.
<p>
    <span class="param-condition">Maximum length:</span> <code>50</code>
</p>

* **short_name** <span class="param-type">String</span><br>
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
Current status of branch.
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
            <li><code>HIGH</code>: The average waiting time is equal or upper to the minimal waiting time of high congestion.</li>
        </ul>
</p>

* **low_estimated_time** <span class="param-type">Integer</span><br>
Lower bound of the estimated waiting time. It's equal to the average waiting time minus the configured desviation.

* **high_estimated_time** <span class="param-type">Integer</span><br>
Upper bound of the estimated waiting time. It's equal to the average waiting time plus the configured desviation.

* **sectors** <span class="param-type">List\<[Sector](#sector)\></span><br>
List of the branch's sectors. A correct configuration include at least one sector per branch.
<p>
    <span class="param-condition">Unique items:</span> <code>true</code><br>
    <span class="param-condition">Minimum items:</span> <code>1</code>
</p>
