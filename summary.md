## Resolver

On startup the app should call this URL with the appropriate hostname parameter:

https://resolver.pinpacuba.com/resolver?hostname=beta.service2grow.com

```json
{
    "hostname": "beta.service2grow.com",
    "url": "https://core-beta.service2grow.com/v2",
    "header": "s-grow"
}
```

The result provides:
- url: the API url that will be used throughout the app
- header: the value of the x-app header that must be used in every request

## Brand configuration

Next we should query the API for the specific brand configuration

POST brand/config

```json
{
    "code": "s-grow",
    "footer": {
        "columns": []
    },
    "paypal": {
        "clientId": "Aas8pKwXJLlnhVxr4CB7qdxqq5bTjwo7ihP6mbBUXl-V0zHNw16W4RXExWqOX8m9c69cFlj8aaKsWfI_",
        "currency": "USD"
    },
    "mainUrl": "https://www.service2grow.com",
    "assetsUrl": "https://core.service2grow.com/assets/service2grow/",
    "headlines": [
        {
            "text": "Llama a Cuba con la mejor calidad y precio",
            "image": "habana_1.jpg",
            "title": "Llamadas"
        },
        {
            "text": "Ya tus amigos no tienen que esperar que les recargues, solo les envias dinero a su cartera virtual y ellos se recargan cuando quieran",
            "image": "nacional.jpg",
            "title": "Cartera virtual"
        }
    ],
    "languages": [
        {
            "id": "en-US",
            "name": "English"
        },
        {
            "id": "es-ES",
            "name": "Español"
        }
    ],
    "colorPrimary": "#1fc743",
    "defaultLanguage": "es-ES",
    "applicationTitle": "Service2Grow"
}
```

## Headers

- x-app: should be sent with every request (e.g. s-grow)
- x-invoker (optional): account ID of the user creating the request. Default value is the logged in user

## Authentication

The API supports basic authentication (username and password) and JWT authentication. For web applications it is recommended to use the token approach.

POST auth/token
```json
{
	"deviceId": "71be59fc4e81c01df0ea53651c6b6893",
	"login": "juanperez@pinpacuba.com",
	"password": "MyPassword1"
}
```
Response:

```json
{
	"tk": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE2MjgyMjkzMTQsImp0aSI6IjdBYU5naUM1cjM1elgzRVQ0MDlZRGRqTTUxdHQ4Y3Y5M1NRNlJmTEJcL1dFPSIsImlzcyI6Ind3dy5waW5wYWN1YmEuY29tIiwibmJmIjoxNjI4MjI5MzE0LCJleHAiOjE2MzAwMjkzMTQsImRhdGEiOnsiYWNjb3VudF9pZCI6ImJhYmE5ZGRkNzQ5YzQyYTI4ZGU4NjNhOWNiZjEzMTE1IiwibG9naW4iOiIiLCJkZXZpY2VfaWQiOiIiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwicm9sZXMiOltdfX0.VKil_NFjELA9dBpE2IfYaDpCkD-YKj4Nt82DypeddjE",
	"id": "baba9ddd749c42a28de863a9cbf13115",
	"alias": "juanperez",
	"firstName": "Juan",
	"lastName": "Perez",
	"languageId": "es-ES",
	"countryName": "United States",
	"countryIso2": "US",
	"countryPrefix": "1",
	"email": "juanperez@pinpacuba.com",
	"allowChildren": "0",
	"roles": []
}
```

Use the token by adding an Authorization header to every request:

Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE2MjgyMjkzMTQsImp0aSI6IjdBYU5naUM1cjM1elgzRVQ0MDlZRGRqTTUxdHQ4Y3Y5M1NRNlJmTEJcL1dFPSIsImlzcyI6Ind3dy5waW5wYWN1YmEuY29tIiwibmJmIjoxNjI4MjI5MzE0LCJleHAiOjE2MzAwMjkzMTQsImRhdGEiOnsiYWNjb3VudF9pZCI6ImJhYmE5ZGRkNzQ5YzQyYTI4ZGU4NjNhOWNiZjEzMTE1IiwibG9naW4iOiIiLCJkZXZpY2VfaWQiOiIiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwicm9sZXMiOltdfX0.VKil_NFjELA9dBpE2IfYaDpCkD-YKj4Nt82DypeddjE

## Create account (register)

POST account

```json
{
	"alias": "juanperez",
	"email": "juanperez@service2grow.com",
	"firstName": "Juan",
	"languageId": "es-ES",
	"lastName": "Perez",
	"password": "MyPassword1"
}
```

