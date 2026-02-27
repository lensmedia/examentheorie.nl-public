# Access Codes - Generate

Access codes can be generated on both servers, live and test. 
Below are the different query parameters used in the url:

| Parameter         | Example Value                       |
|-------------------|-------------------------------------|
| amount (optional) | 5 (defaults to 1 when not provided) |
| course            | B                                   |
| locale            | nl                                  |
| start (optional)  | 2022121418                          |
| start (optional)  | 2022122018                          |

`start` & `end` are optional parameters, but do come in pairs. So when you provide `start` you also have to provide `end`.
When both parameters are provided, a time frame will be added while generating the access code. 
Timestamps can be provided in 2 ways, system first checks for `RFC3339` format (https://www.php.net/manual/en/class.datetimeinterface.php#datetimeinterface.constants.rfc3339), 
then in format as above `YmdH`. So in format as above `2022121418` gives us `2022, december 14th, 18h`.
If `start` and `end` are not provided, access code will be generated but will not have access yet because there is no time 
frame linked to the access code. To add a time frame to an access code, check [Access Code - Time Frames](access-code-time-frame.md).

If combination of `course` and `locale` doesn't match a valid course, an exception will be thrown.

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/access-code/generate?amount=5&course=B&locale=nl
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/generate?amount=5&course=B&locale=nl
```

### Returns 
Json response with created access code.

```json
[
    {
        "id": "01GMDKM82DQ5HV3AABV5XAHYCK",
        "created_at": "2022-12-16T13:57:52+00:00",
        "code": "1BtPUTi7GSnH72UQgRoAqY",
        "time_frames": [
            {
                "started_at": "2022-12-14T18:00:00+00:00",
                "ended_at": "2022-12-20T18:00:00+00:00"
            }
        ]
    },
    {
        "id": "01GMDKM82EAHBWMFF4WP033XR9",
        "created_at": "2022-12-16T13:57:52+00:00",
        "code": "1BtPUTi7R9hp5mTYMZAziL",
        "time_frames": [
            {
                "started_at": "2022-12-14T18:00:00+00:00",
                "ended_at": "2022-12-20T18:00:00+00:00"
            }
        ]
    },
    {
        "id": "01GMDKM82EAHBWMFF4WP033XRB",
        "created_at": "2022-12-16T13:57:52+00:00",
        "code": "1BtPUTi7R9hp5mTYMZAziN",
        "time_frames": [
            {
                "started_at": "2022-12-14T18:00:00+00:00",
                "ended_at": "2022-12-20T18:00:00+00:00"
            }
        ]
    },
    {
        "id": "01GMDKM82EAHBWMFF4WP033XRD",
        "created_at": "2022-12-16T13:57:52+00:00",
        "code": "1BtPUTi7R9hp5mTYMZAziQ",
        "time_frames": [
            {
                "started_at": "2022-12-14T18:00:00+00:00",
                "ended_at": "2022-12-20T18:00:00+00:00"
            }
        ]
    },
    {
        "id": "01GMDKM82EAHBWMFF4WP033XRF",
        "created_at": "2022-12-16T13:57:52+00:00",
        "code": "1BtPUTi7R9hp5mTYMZAziS",
        "time_frames": [
            {
                "started_at": "2022-12-14T18:00:00+00:00",
                "ended_at": "2022-12-20T18:00:00+00:00"
            }
        ]
    }
]
```
