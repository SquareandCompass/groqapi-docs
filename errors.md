---
description: The following are error messages that you may run into and their meanings.
---

# Error Messages

## Maintenance Mode

If the service is in maintenance mode, the service will return the following:

```json
{
  "error": {
    "code": 9999,
    "message": "service offline for maintenance"
  }
}
```

## Queue is Full

If the queue is full, the API will return a `HTTP/503` and the following:

```json
{
  "error": {
    "code": 14,
    "message": "ErrorQueueFull",
    "details": []
  }
}
```

## Get Place In Queue Fails

If you try to get place in queue, but the request is no longer available, the API will return a `HTTP/404` and the following:

```json
{
  "error": {
    "code": 5,
    "message": "ErrorRequestNotFound",
    "details": []
  }
}
```

## If Bearer Token is Missing or Invalid

The API will return a `HTTP/401`.

## Rate Limit Reached

The API will return a `HTTP/429`.
