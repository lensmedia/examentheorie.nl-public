# Access Codes - Disable & Enable
Access codes can be disabled and enabled, so when an access code is disabled the user gets an error logging in. 
The error states that their access code is disabled, and they should contact their supplier. 
This comes in handy when for instance the use of the platform by the user is used wrong or something else.
Below you will find the query parameters to use in the url: 

| Parameter | Example Value          |
|-----------|------------------------|
| code      | 1BtPQgJ714HMT5ZXrSLQ8i |

When access code provided in url is not valid or not found, and exception will be thrown. 

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/access-code/disable?code=1BtPQgJ714HMT5ZXrSLQ8i
GET https://test.examentheorie.nl/api/v1/access-code/enable?code=1BtPQgJ714HMT5ZXrSLQ8i
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/disable?code=1BtPQgJ714HMT5ZXrSLQ8i
GET https://examtheorie.nl/api/v1/access-code/enable?code=1BtPQgJ714HMT5ZXrSLQ8i
```

### Returns
Json response with access code info and updated status `disabled`.

```json
{
    "id": "01GMB7V2XDYQTQGX2ZSZ6NX1FE",
    "created_at": "2022-12-15T15:53:24+00:00",
    "course": {
        "title": "Theoriecursus Personenauto",
        "label": "B",
        "locale": {
            "locale": "nl",
            "label": "Nederlands"
        }
    },
    "code": "1BtMjToeScfX9NcwCtmiUV",
    "time_frames": [
        {
            "started_at": "2022-12-16T16:00:00+00:00",
            "ended_at": "2022-12-20T18:00:00+00:00"
        }
    ],
    "disabled": true
}
```

