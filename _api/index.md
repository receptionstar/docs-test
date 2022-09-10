---
title: API Reference
has_children: false
nav_order: 1
---

# API Reference

The REST API provides access to the data you have access to across Reception Star.

The base address of the API is https://my.receptionstar.com/api/v3, which a set of [endpoints] to the various resources, each with its own unique path. The API requires authorization to access all endpoints except the `/heart` endpoint, which can be used to troubleshoot any connectivity issues you may be experiencing.


## Requests

The API is based on REST principles. Resources are accessed via standard HTTPS requests in UTF-8 format, using appropriate HTTP verbs for each action:

| Method | Action                        |
|--------|-------------------------------|
| GET    | Retrieves resources           |
| POST   | Creates resources             |
| PUT    | Changes or replaces resources |
| DELETE | Deletes resources             |


## Responses

API responses will include a JSON object.


## Timestamps

Timestamps are returned in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format as [Coordinated Universal Time (UTC)](https://en.wikipedia.org/wiki/UTC_offset) with a zero offset: `YYYY-MM-DDTHH:MM:SSZ`.


## Pagination

Some endpoints support a way of paging the dataset, taking an `offset` and `limit` as query parameters, and will be noted in the documentation for each endpoint that supports this:

```
curl -X GET \
  https://my.receptionstar.com/api/v1/clients/?offset=20&limit=10
```

In this example, the total number of clients may be 50, however the next 10 (`limit`) clients will be retrived, from the 20th (`offset`).


## Response Status Codes

The API uses the following response status codes:

| Status Code | Description |
|-------------|-------------|
| 200         | OK - The request succeeded. The client can read the result of the request in the body and the headers of the response. |
| 201         | Created - The request has been fulfilled and resulted in a new resource being created. |
| 202         | Accepted - The request has been accepted for processing, but the processing has not been completed. |
| 204         | No Content - The request succeeded but returns no message body. |
| 304         | Not Modified. Please use the already cached version. |
| 400         | Bad Request - The request could not be understood by the server due to malformed syntax. |
| 401         | Unauthorized - The request requires user authentication or, if the request included authorization credentials, authorization has been refused for those credentials. |
| 403         | Forbidden - The server understood the request, but is refusing to fultill it. |
| 404         | Not Found - The requested resource could not be found. This error can be due to a temporary or permanent condition. |
| 429         | Too Many Requests - Rate limiting has been applied. |
| 500         | Internal Server Error. Please report this to us if you see it. |
| 502         | Bad Gateway - The server was acting as a gateway or proxy and received an invalid response from the upstream server. |
| 503         | Service Unavailable - THe server is currently unable to handle the request due to a temporary condition which will be alleviated for some other day. Please resend your request. |

