---
title: API Troubleshooting
nav_order: 3
---

# Troubleshooting

If you need to test your connectivity to the API, you can use the following endpoints to test an endpoint thats poblically available, and an endpoint that requires authentication first.


## Examples

### publically available

```sh
curl -v https://my.receptionstar.com/api/v1/heart
```

**Response 200**

The response will be a test string, rather than JSON like other endpoints.

```js
"The only true wisdom is in knowing you know nothing. ― Socrates"
```

