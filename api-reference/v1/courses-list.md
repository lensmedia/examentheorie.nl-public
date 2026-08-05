# Courses - List

To generate access codes, you will need a `course (label)` and a `locale`, otherwise we can't connect an access code to
a course. For each `course`, all `categories` and `category_items` are shown. Within `category_items` there is also an `url` 
which can be used for [deep linking](../../deep-linking/readme.md). 

### Example
#### Test
```http 
GET https://test.examentheorie.nl/api/v1/courses/list
```

#### Live
```http
GET https://examentheorie.nl/api/v1/courses/list
```

### Returns
Json response with all courses and categories/category_items. Depending on whether you can use the full functionalities of
our API, 2 more rows are visible with each `category_item`. These are `modified_at` and `download_url`, and serve for who 
are able to use/download the packages for ITEC.

So for regular users, response looks like below
```json
[
    {
        "title": "Theoriecursus Personenauto",
        "label": "B",
        "locale": {
            "locale": "nl",
            "label": "Nederlands"
        }, 
        "categories": [
            {
                "id": "01KG4H07YP19Q9JZZH2AM1EN3B",
                "name": "Examens",
                "category_items": [
                    {
                        "id": "01KG4H0XTDS69CPV1FFAAH6CEH",
                        "title": "Examen 1",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH"
                    },
                    {
                        "id": "01KG4H1190NB6AMZKPG7VSTTD5",
                        "title": "Examen 2",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H1190NB6AMZKPG7VSTTD5"
                    },
                    {
                        "id": "01KG4H14D33R8T82RZWE3G27SE",
                        "title": "Examen 3",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H14D33R8T82RZWE3G27SE"
                    }
                ]
            }
        ]
    }
]
```

For full API users, response looks like below. 

```json
[
    {
        "title": "Theoriecursus Personenauto",
        "label": "B",
        "locale": {
            "locale": "nl",
            "label": "Nederlands"
        }, 
        "categories": [
            {
                "id": "01KG4H07YP19Q9JZZH2AM1EN3B",
                "name": "Examens",
                "category_items": [
                    {
                        "id": "01KG4H0XTDS69CPV1FFAAH6CEH",
                        "title": "Examen 1",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH",
                        "modified_at": "2026-07-17T04:20:08+02:00",
                        "download_url": "examentheorie.nl/api/v1/lpm/download/01KG4H0XTDS69CPV1FFAAH6CEH"
                    },
                    {
                        "id": "01KG4H1190NB6AMZKPG7VSTTD5",
                        "title": "Examen 2",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H1190NB6AMZKPG7VSTTD5",
                        "modified_at": "2026-07-17T04:20:08+02:00",
                        "download_url": "examentheorie.nl/api/v1/lpm/download/01KG4H1190NB6AMZKPG7VSTTD5"
                    },
                    {
                        "id": "01KG4H14D33R8T82RZWE3G27SE",
                        "title": "Examen 3",
                        "url": "examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H14D33R8T82RZWE3G27SE",
                        "modified_at": "2026-07-17T04:20:08+02:00",
                        "download_url": "examentheorie.nl/api/v1/lpm/download/01KG4H14D33R8T82RZWE3G27SE"
                    }
                ]
            }
        ]
    }
]
```
