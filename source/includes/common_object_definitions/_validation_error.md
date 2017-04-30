
## Validation Error

> Sample object:

```json
{
    "code": "40003",
    "message": "Customer 'c9mas9js' has a ticket on hold",
    "field":"customerId"
}
```

Model of validation error object.

### Fields

* **code** <span class="param-type">String</span><br>
Error code, used to identify the error.

* **message** <span class="param-type">String</span> <span class="required-param">required</span><br>
Simple description of the error.

* **field** <span class="param-type">String</span> <span class="required-param">required</span><br>
Field associated to the error.
