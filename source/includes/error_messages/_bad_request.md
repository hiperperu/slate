
## Bad Request

> Sample response:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

[
    {
        "code": 40003,
        "message": "Customer 'c9mas9js' has a ticket on hold",
        "field":"customerId"
    }
]
```

HTTP response when an validation error occurred. The field <code>code</code> is not returned when the error is originated by validation of contract.

<aside class="success">
<strong>Remember:</strong>
All operations that return a error with code assigned contain the list of possible errors in their documentation.
</aside>

The errors with a code assigned are the next:

Code| Field |Message
---|---|---
40001|channelId|Channel not exists.
40002|serviceId|Service not exists.
40003|branchId|Branch not exists.
40004|sectorId|Sector not exists.
40005|categoryId|Customer category not exists.
40006|serviceId|Service not supported by the channel.
40007|serviceId|Service not supported by the branch.
40008|serviceId|Service not supported by the sector.
40009|branchId|Branch is not the sector owner.
40010|customerId|Customer has another ticket.
40011|categoryId|Customer category has no configured queue type for the service and  channel.
40012|customerId|Customer has another valid booking for the same service.
40013|startTime|Booking start time not valid.
40014|endTime|Booking end time not valid.
40015|serviceId|Service not available in the requested time.
