# LPM - Download

Within our API, you can download the packages used for ITEC if you are eligible.
By each `category_item` on the list of [courses](courses-list.md) you will see a `download_url` which can be used the download the package under the `category_item` id.

Also on each `category_item` entry there is a `modified_at` timestamp, which can be used to check whether your downloaded package is outdated or not.
Simply just save the timestamp to your own database, get the list of [courses](courses-list.md) and check for each id you saved whether you're outdated.

### Example 

#### Test
```http 
GET https://test.examentheorie.nl/api/v1/lpm/download/01KG4H0XTDS69CPV1FFAAH6CEH
```

#### Live
```http
GET https://examtheorie.nl/api/v1/lpm/download/01KG4H0XTDS69CPV1FFAAH6CEH
```

### Returns
A zip for ITEC use.

## Important!
It can be that a download link refers to our Belgium domain, but that is only on the Belgium course.
LPM download route works in both cases, you can choose to edit the `.be` to `.nl` or leave it as is.
