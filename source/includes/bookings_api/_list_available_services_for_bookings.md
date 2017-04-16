
## List available services for booking

> Sample request:

```http
GET /v1/services/s8 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "s8",
    "name": "Plataforma",
    "shortName": "Plataforma"
}
```

Returns a specific service requested by ID.

### Endpoint

`GET /v1/services/{serviceId}`

### Path Params

* **serviceId** *string* <span class="required-param">required</span> <br>Unique identifier of service.

### Query Params

* **fields** *List\<String\>* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,shortName`.

### Responses

* **200** <span class="verb-description">Ok</span> *[Service](#the-service-object)* <br>A service.
* **404** <span class="verb-description">Not Found</span> *[Error](#the-error-object)* <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception.
