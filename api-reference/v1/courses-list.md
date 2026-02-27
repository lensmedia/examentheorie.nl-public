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
GET https://examtheorie.nl/api/v1/courses/list
```

### Returns
Json response with all courses and categories/category_items.
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
                        "url": "examentheorie.nl/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH"
                    },
                    {
                        "id": "01KG4H1190NB6AMZKPG7VSTTD5",
                        "title": "Examen 2",
                        "url": "examentheorie.nl/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H1190NB6AMZKPG7VSTTD5"
                    },
                    {
                        "id": "01KG4H14D33R8T82RZWE3G27SE",
                        "title": "Examen 3",
                        "url": "examentheorie.nl/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H14D33R8T82RZWE3G27SE"
                    }
                ]
            }
        ]
    }
]
```
