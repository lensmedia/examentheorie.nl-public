# Access Codes - Info
When you want to check an access code for its disabled status or linked time frames, that is possible via the info route.
Below you will find the query parameters used in the url:

| Parameter | Example Value          |
|-----------|------------------------|
| code      | 1BtPQgJ714HMT5ZXrSLQ8i |

When access code provided in url is not valid or not found, and exception will be thrown.

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/access-code/info?code=1BtPQgJ714HMT5ZXrSLQ8i
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/info?code=1BtPQgJ714HMT5ZXrSLQ8i
```

### Returns
Json response with access code info.

```json
{
    "id": "01GMDGSD9DK3C7BM53V6R347N3",
    "created_at": "2022-12-16T13:08:15+00:00",
    "course": {
        "title": "Theoriecursus Personenauto",
        "label": "B",
        "locale": {
            "locale": "nl",
            "label": "Nederlands"
        }
    },
    "code": "1BtPQgJ714HMT5ZXrSLQ8i",
    "time_frames": [
        {
            "started_at": "2022-12-16T13:00:00+00:00",
            "ended_at": "2022-12-20T17:00:00+00:00"
        }
    ],
    "disabled": false
}
```
