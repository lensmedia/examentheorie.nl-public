# Access Codes - Results
When a user completes an exercise/exam, we save that result to our database. Those results can be gathered. 
Below you will find the query parameters to use in the url:

| Parameter | Example Value          |
|-----------|------------------------|
| code      | 1BtPQgJ714HMT5ZXrSLQ8i |

When access code provided in url is not valid or not found, and exception will be thrown. 

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/access-code/results?code=1BtPQgJ714HMT5ZXrSLQ8i
```

#### Live
```http
GET https://examtheorie.nl/api/v1/access-code/results?code=1BtPQgJ714HMT5ZXrSLQ8i
```

### Returns
Json response with results from access code.

```json
[
    {
        "completed_at": "2022-12-08T13:24:30+00:00",
        "passed": false,
        "item_title": "Examen 1",
        "context": {
            "data": {
                "subscription": "1Bt6BAi1CybNpYtzSMbBuX"
            },
            "passed": false,
            "mapped_score": 65,
            "subject_count": {
                "B0": 25,
                "B1": 3,
                "B2": 3,
                "B3": 9,
                "B4": 5,
                "B5": 4,
                "B6": 6,
                "B7": 5,
                "B8": 5
            },
            "achieved_score": 0,
            "subject_errors": {
                "B0": 25,
                "B1": 3,
                "B2": 3,
                "B3": 9,
                "B4": 5,
                "B5": 4,
                "B6": 6,
                "B7": 5,
                "B8": 5
            }
        }
    },
    {
        "completed_at": "2022-12-08T13:25:06+00:00",
        "passed": false,
        "item_title": "Examen 60",
        "context": {
            "data": {
                "subscription": "1Bt6BAi1CybNpYtzSMbBuX"
            },
            "passed": false,
            "mapped_score": 65,
            "subject_count": {
                "B0": 25,
                "B1": 1,
                "B2": 2,
                "B3": 8,
                "B4": 7,
                "B5": 4,
                "B6": 4,
                "B7": 9,
                "B8": 5
            },
            "achieved_score": 0,
            "subject_errors": {
                "B0": 25,
                "B1": 1,
                "B2": 2,
                "B3": 8,
                "B4": 7,
                "B5": 4,
                "B6": 4,
                "B7": 9,
                "B8": 5
            }
        }
    }
]
```
