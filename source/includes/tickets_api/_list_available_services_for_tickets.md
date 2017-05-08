
## List available services for tickets

> Sample request:

```http
GET /v1/tickets/services HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "s8",
        "name": "Plataforma",
        "short_name": "Plataforma"
    }
]
```

Returns available services for the specified channel.

<aside class="warning">
    <strong>Caution:</strong> 
    You must consider the following:
    <ul>
        <li>This operation throw an error(404) when the referenced channel does not exist.</li>
        <li>An empty list is returned when not available services exist from the specified channel.</li>
    <ul>
</aside>

### Endpoint

`GET /v1/tickets/services`

### Query Params

* **channel_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value must be set in the client application.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Service](#service)\></span><br>
A list of services.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
