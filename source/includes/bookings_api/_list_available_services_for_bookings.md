
## List available services for booking

> Sample request:

```http
GET /v1/bookings/channel/c10/services HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "s8",
        "name": "Plataforma",
        "shortName": "Plataforma"
    }
]
```

Returns available services to book from the channel used.

<aside class="warning">
<strong>Caution:</strong>
You should consider the following:
<ul>
    <li>This operation throw a error(404) when the channel referenced not exists.</li>
    <li>An empty list is returned when not exist bookable services from the channel used</li>
<ul>
</aside>

### Endpoint

`GET /v1/bookings/channel/{channelId}/services`

### Path Params

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value should to be fixed in the client application.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Service](#service)\></span><br>
A list of services.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
