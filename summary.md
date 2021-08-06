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
url: the API url that will be used throughout the app
header: the value of the x-app header that must be used in every request

## Headers

x-app: should be sent with every request (e.g. s-grow)
x-invoker (optional): account ID of the user creating the request. Default value is the logged in user

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
