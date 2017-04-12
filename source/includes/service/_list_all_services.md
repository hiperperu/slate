
## List all services

> Sample request:

```http
GET /v1/services HTTP/1.1
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

Returns all available services that fulfill the filters.

<aside class="notice">
<strong>Order:</strong> The services are sorted by <code>shortName</code>.
</aside>

### Endpoint

`GET /v1/services`

### Query Params

* **channelId** <span class="recomended-param">recomended</span> *String* <br>Channel unique identifier.
* **isVirtual** *Boolean* <br>Indicator of virtual tickets enabled for the service.
* **isBookable** *Boolean* <br>Indicator of bookings enabled for the service.
* **fields** *List\<String\>* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,shortName`.
* **offset** *Integer* <br> Position in pagination.<p>*Default value:* <code>0</code><br>*Maximum value:* <code>9999</code></p>
* **limit** *Integer* <br> Number of items to retrieve.<p>*Default value:* <code>10</code><br>*Maximum value:* <code>50</code></p>

### Responses

* **200** <span class="verb-description">Ok</span> *List\<[Service](#the-service-object)\>* <br>A list of services.
* **400** <span class="verb-description">Bad Request</span> *[Error](#the-error-object)* <br>One or more parameters are not valid, returns a description of validation failed.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception.
