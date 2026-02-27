# Access Codes - Sessions

The way Examentheorie works is based on time registration. We keep that info in `sessions` in our database.
So if you are wondering how much time a user has practised already, you can gather that via this route.
Below you will find the query parameters used in the url:

| Parameter | Example Value          |
|-----------|------------------------|
| code      | 1BtPQgJ714HMT5ZXrSLQ8i |

When access code provided in url is not valid or not found, and exception will be thrown.

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/access-code/sessions?code=1BtPQgJ714HMT5ZXrSLQ8i
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/sessions?code=1BtPQgJ714HMT5ZXrSLQ8i
```

### Returns 
Json response, starting with total hours followed by al the sessions from that access code.
```json
{
    "total": [
        {
            "hours": "8"
        }
    ],
    "sessions": [
        [
            {
                "started_at": "2023-05-01T14:31:59+02:00",
                "ended_at": "2023-05-01T17:40:17+02:00"
            },
            "03:08:18"
        ],
        [
            {
                "started_at": "2023-05-01T18:48:02+02:00",
                "ended_at": "2023-05-01T19:44:48+02:00"
            },
            "00:56:46"
        ],
        [
            {
                "started_at": "2023-05-01T21:01:01+02:00",
                "ended_at": "2023-05-01T22:16:05+02:00"
            },
            "01:15:04"
        ],
        [
            {
                "started_at": "2023-05-02T10:30:41+02:00",
                "ended_at": "2023-05-02T10:30:41+02:00"
            },
            "00:00:00"
        ],
        [
            {
                "started_at": "2023-05-02T10:30:48+02:00",
                "ended_at": "2023-05-02T10:30:48+02:00"
            },
            "00:00:00"
        ],
        [
            {
                "started_at": "2023-05-02T10:30:52+02:00",
                "ended_at": "2023-05-02T10:55:29+02:00"
            },
            "00:24:37"
        ],
        [
            {
                "started_at": "2023-05-03T07:31:22+02:00",
                "ended_at": "2023-05-03T09:02:21+02:00"
            },
            "01:30:59"
        ]
    ]
}
```
