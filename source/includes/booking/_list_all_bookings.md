
## List all bookings

> Sample request:

```http
GET /customer/v1/bookings?customer_id=m809a31n HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "a90mos70om",
        "code": "UxMa01m",
        "channel": "mobile",
        "status": "ACTIVE",
        "phone": "+51987776576",
        "branch": {
            "id": "27b6",
            "name": "Hiper Central",
            "short_name": "Hiper",
            "code": "AG001",
            "address": "Calle Beta 181 - 195, Callao",
            "latitude": -12.049919,
            "longitude": -77.0845193,
            "status": "OPEN",
            "opening_time": "2017-02-20T14:00:00.000Z",
            "closing_time": "2017-02-20T23:00:00.000Z",
            "congestion_level": "MEDIUM"
        },
        "service": {
            "id": "7b6",
            "name": "Plataforma",
            "short_name": "Plataforma"
        },
        "start_time": "2017-02-20T14:00:00.000Z",
        "end_time": "2017-02-20T15:00:00.000Z",
        "created_at": "2017-02-10T14:00:00.000Z",
        "updated_at": "2017-02-10T14:00:00.000Z"
    }
]
```

Returns all tickets created by a specific customer.

<aside class="notice">
<strong>Order:</strong> The bookings are sorted descendantly by the field : <code>created_at</code>.
</aside>

<aside class="warning">
<strong>Caution: </strong> You have to consider the following:
<ul>
<li>

</li>
For this operation its necesary indicate a specific customer, You have two options, send the <code>customer_id_type</code> and the <code>customer_id_number</code> or only send the <code>customer_id</code>. If you send all parameters, the API just consider the parameter <code>customer_id</code>.
</ul>
</aside>

### Endpoint

`GET /customer/v1/bookings`

### Query Params

| |
|:---|
|**customer_id** *string* <span class="recomended-param">recomended</span><br>Customer unique identifier used in your company. <p>*Validation pattern*: <code>^[0-9A-Za-z]{1,20}$</code></p> |
|**customer_id_type** *string* <br>Type of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,2}$</code></p> |
|**customer_id_number** *integer* <br>Number of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,16}$</code></p> |
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,code`. |

### Responses

| |
|:---|
|**200** *array[[Booking](#ticket)]* <br>A list of bookings. |
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
