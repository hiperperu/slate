
## List available services for tickets

> Sample request:

```http
GET /v1/tickets/channel/c10/services HTTP/1.1
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

Returns available services to generate tickets from the channel referenced.

<aside class="warning">
<strong>Caution: </strong> You should consider the following:
<ul>
<li>This operation throw a error(404) when the channel referenced not exists.</li>
<li>An empty list is returned when not exist services to generate tickets from the branch referenced.</li>
<ul>
</aside>

### Endpoint

`GET /v1/tickets/channel/{channelId}/services`

### Path Params

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Channel unique identifier.

### Responses

* **200** <span class="verb-description">Ok</span> *List\<[Service](#service)\>* <br>A list of services.
* **404** <span class="verb-description">Not Found</span> <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
