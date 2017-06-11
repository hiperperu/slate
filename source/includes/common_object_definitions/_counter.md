
## Counter

> Sample object:

```json
{
    "id": "v10",
    "name": "V10",
    "teller": "achavez",
    "type": {
        "id": "v2002",
        "name": "Ventanilla"
    }
}
```

Model of counter object.

### Fields

* **id** <span class="param-type">String</span><br>
Counter unique identifier (Configured from Bmatic configuration panel).

* **name** <span class="param-type">String</span><br>
Name of the counter.
<p>
    <span class="param-condition">Maximum length:</span> <code>20</code>
</p>

* **teller** <span class="param-type">String</span><br>
Account name of teller in counter.
<p>
    <span class="param-condition">Maximum length:</span> <code>30</code>
</p>

* **type** <span class="param-type">[CounterType](#counter-type)</span><br>
Associated counter type.
