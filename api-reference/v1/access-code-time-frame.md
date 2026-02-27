# Access Codes - Time Frames
You can add time frames to an access code, within these time frames an access code user can make use of Examentheorie.
Below you can find the query parameters used in the url:

| Parameter | Example Value          |
|-----------|------------------------|
| code      | 1BtPQgJ714HMT5ZXrSLQ8i |
| start     | 2022121418             |
| start     | 2022122018             |

`start` and `end` are required parameters here. Format is same as with [generating](access-code-generate.md) access codes. 
First the system checks for RFC3339 format, then YmdH. If parameters are not provided or correct, an exception will be thrown.

When access code provided in url is not valid or not found, and exception will be thrown. 

### Example
#### Test 
```http 
GET https://test.examentheorie.nl/api/v1/access-code/add-time-frame?start=2022121418&end=2022122018&code=1BtPQgJ714HMT5ZXrSLQ8i
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/add-time-frame?start=2022121418&end=2022122018&code=1BtPQgJ714HMT5ZXrSLQ8i
```

### Returns
Json response with access code info including new time frame.

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
