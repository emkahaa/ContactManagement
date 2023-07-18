# User API Spec

## Register User

Endpoint : POST /api/users

Request Body :

```json
{
  "username" : "maskho",
  "password" : "rahasia",
  "name" : "Mas Kholil"
}
```

Response Body (Success) :

```json
{
  "data" : "OK"
}
```

Response Body (Fail) :

```json
{
  "errors" : "Username must not blank, ???"
}
``` 

## Login User

Endpoint : POST /api/auth/login

Request Body :

```json
{
  "username" : "maskho",
  "password" : "rahasia"
}
```

Response Body (Success) :

```json
{
  "data" : {
    "token" : "TOKEN",
    "expiredAt" : 192837192387 // milliseconds
  }
}
```

Response Body (Fail, 401) :

```json
{
  "errors" : "Username or Password wrong"
}
``` 

## Get User

Endpoint : GET /api/user/current

Request Header :
 - X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "data" : {
    "username" : "maskho",
    "name" : "Mas Kholil"
  }
}
```

Response Body (Fail, 401) :

```json
{
  "errors" : "Unauthorized"
}
```

## Update User

Endpoint : PATCH /api/users/current

Request Header :
- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
  "name" : "Mamas Kholil", // put if only want to update name
  "password" : "rahasia baru" // put if only want to update password
}
```

Response Body (Success) :

```json
{
  "data" : {
    "token" : "TOKEN",
    "expiredAt" : 192837192387 // milliseconds
  }
}
```

Response Body (Fail, 401) :

```json
{
  "errors" : "Username or Password wrong"
}
```

## Logout User

Endpoint : DELETE /api/auth/logout

Request Header :
- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "data" : "OK"
}
```