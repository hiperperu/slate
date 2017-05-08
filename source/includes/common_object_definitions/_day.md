
## Day

> Sample object:

```json
{
    "day": "2017-02-20T00:00:00.000Z",
    "ranges": [
        {
            "start_time": "2017-02-20T14:00:00.000Z",
            "end_time": "2017-02-20T15:00:00.000Z"
        }
    ]
}
```

Model of day object.


### Fields

* **day** <span class="param-type">Date</span><br>
Date with available ranges.
<p>
    <span class="param-condition">Standard:</span> <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code>
</p>

* **ranges** <span class="param-type">List\<[Range](#range)\></span><br>
List of available time ranges.
