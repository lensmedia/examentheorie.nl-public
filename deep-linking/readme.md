# Deep Linking

In our system students can practice exams, exercises etc. But to be able to practice, a student has to log in first, 
then go to the correct category and then select the exam or exercises they want to take. Let's say you have a system/platform
where you have all the exams and exercises listed, and you don't want the hassle for your students to constantly log in and 
search again in our platform for that exam/exercise.
With deep linking we offer the possibility to send a user directly to an exam or exercise. With a query parameter/JWT token 
we can log them in, and they enter directly the selected exam/exercise (if correct url was used).


## Let's get started
<i>For this to work you need authentication to our API, so if you don't have access please make sure you do (contact us for
access to our api).</i>

So, first we need an url to begin with. With this url we send a user to the exam/exercise you want to send them to. 
Check our API reference for [courses](../api-reference/v1/courses-list.md) to know what url belongs to what exam/exercise.

Let's take the following `course list` json as example, and select `Examen 1`
(**please note**: this is just an example, ids/urls have different values on live and test server).

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

`Examen 1` has the following url:
```http
GET https://examentheorie.nl/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH
```
This is our base, what's left to do is add a query parameter which consists of a JWT Token so our systems recognizes that 
you want to deep link to that exam.

## access_token
To let our system know that we are deep linking, we need to add `access_token` as query parameter to our url.
So our urls looks like this ('foobar' as example value):
```http
GET https://examentheorie.nl/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH?access_token=foobar
```

## JWT Token
Now that our system knows we are deep linking to that exam, we need a value for our access token.
This consists of a JWT token, so we don't have any public data (for instance the users access code) in the url itself.

The only thing that is different about the normal use of JWT tokens, is that you generate that token yourself. 'Normal' 
workflow with JWT tokens would be for us to generate a token and provide that to you, but since we only put a few 
parameters in the token data it is perfectly fine this way.

Tip! for trying out encoding/decoding you can always check out https://www.jwt.io/. This site provides a JWT Decoder &
Encoder, where you can put your own parameters/secret to the test. 

### PHP Library
For PHP, we use https://github.com/firebase/php-jwt to encode/decode tokens.

### Parameters
Below you will find the parameters we encode in the JWT token:

| Parameter  | Example Value            |
|------------|--------------------------|
| accessCode | 1BtPQgJ714HMT5ZXrSLQ8i   |
| returnUrl  | https://examentheorie.nl |

Both parameters are required! We need the `accessCode` to log the user in, and we need `returnUrl` to redirect the user 
to that url after exam/exercise is completed.

### Encoding
Using firebase/php-jwt library we can create a token bij using `JWT::encode`, so generating a token looks like this:
```php
private const string ACCESS_TOKEN_KEY = 'foobar';
private const string ACCESS_TOKEN_ALGORITHM = 'foobar';
 
public static createAccessToken(): string
{
    return JWT::encode(array_merge([
            'accessCode' => '1BtPQgJ714HMT5ZXrSLQ8i',
            'returnUrl' => 'https://examentheorie.nl'
        ]), self::ACCESS_TOKEN_KEY, self::ACCESS_TOKEN_ALGORITHM
    );
}
```
Now there are 2 constants: `ACCESS_TOKEN_KEY` and `ACCESS_TOKEN_ALGORITHM`. Those are not meant for this public wiki, so 
you get those parameters bij contacting us.

This generates a string which we use as `access_token` in the url. So that gives us 
```http
GET https://examentheorie.nl/studie/categorie/01KG4H07YP19Q9JZZH2AM1EN3B/item/01KG4H0XTDS69CPV1FFAAH6CEH?access_token=generated_access_token
```

### Decoding
In our system we decode that `access_token`. If for some reason the token can't be decoded, an exception will be thrown.
If the token is decoded, but for instance the user doesn't have access anymore (so we can't log the user in since there
is no valid time frame), we redirect to the provided returnUrl with 3 query parameters:

| Parameter | Example Value             |
|-----------|---------------------------|
| error     | 401002                    |
| message   | Access Code has no access |
| token     | provided token returned   |

This way you can handle that error via the url. So for example when using `https://examentheorie.nl` as `returnUrl`, and 
an error pops up  and the token can be decoded normally we redirect to the following url:
```http
GET https://examentheorie.nl?error=401002&message=access%20code%20has%20no%20access&token=generated_access_token
```

There are multiple error codes, check the list below with possible errors you can expect:

| Error code | Message                   |
|------------|---------------------------|
| 401001     | Access Code not found     |
| 401002     | Access Code has no access |
| 401006     | Invalid signature         |
| 401007     | Token not valid yet       |
| 401008     | Token has expired         |
| 401009     | Token is invalid          |

Since you generate that token yourself, you should for exampel not get the error `401007` since that results from 
putting an `nbf` parameter in the token while encoding. Since we do not use that, you should not be getting that error. 
More info on these default claims/parameters can be found on https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-token-claims#registered-claims.





