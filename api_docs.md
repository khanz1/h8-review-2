# Movie API Documentation

## Hosting Server

- [https://api.hacktiv8.khanz1.dev](https://api.hacktiv8.khanz1.dev)

## Endpoints

List of available endpoints:

- `POST /auth/sign-up`
- `POST /auth/sign-in`
- `GET /movies`
- `POST /movies`
- `DELETE /movies/:id`

&nbsp;

## 1. POST /auth/sign-up

Request:

- body:

```json
{
  "email": "string",
  "password": "string"
}
```

_Response (201 - Created)_

```json
{
  "message": "string"
  "access_token": "string"
}
```

_Response (400 - Bad Request)_

```json
{
  "message": "Email is required"
}
OR
{
  "message": "Invalid email format"
}
OR
{
  "message": "Email must be unique"
}
OR
{
  "message": "Name is required"
}
OR
{
  "message": "Password is required"
}
```

&nbsp;

## 2. POST /auth/sign-in

Request:

- body:

```json
{
  "email": "string",
  "password": "string"
}
```

_Response (200 - OK)_

```json
{
  "access_token": "string",
  "username": "string",
  "message": "string"
}
```

_Response (400 - Bad Request)_

```json
{
  "message": "Email is required"
}
OR
{
  "message": "Password is required"
}
```

_Response (401 - Unauthorized)_

```json
{
  "message": "Invalid email/password"
}
```

&nbsp;

## 3. GET /movies

Description:

- Get all movie from database

Request:

- headers:

```json
{
  "access_token": "string"
}
```

_Response (200 - OK)_

```json
[
  {
    "id": 1,
    "title": "Iron Man",
    "imgUrl": "https://yourwebsite.com/path/to/ironman.jpg",
    "synopsis": "After being held captive in an Afghan cave, billionaire engineer Tony Stark creates a unique weaponized suit of armor to fight evil.",
    "authorId": 1,
    "createdAt": "2023-07-26T22:20:04.562Z",
    "updatedAt": "2023-07-26T22:20:04.562Z",
    "User": {
      "id": 1,
      "email": "khanz1@gmail.com"
    }
  }
]
```

&nbsp;

## 4. POST /movies

Description:

- Create new movie

Request:

- headers:

```json
{
  "access_token": "string"
}
```

- body:

```json
{
  "title": "string (required)",
  "imgUrl": "string (required)",
  "synopsis": "string (required)"
}
```

_Response (201 - Created)_

```json
{
  "id": "integer",
  "title": "string",
  "imgUrl": "string",
  "synopsis": "string",
  "authorId": "integer",
  "createdAt": "date",
  "updatedAt": "date"
}
```

## 5. DELETE /movies/:id

Description:

- Delete movie by id

Request:

- headers:

```json
{
  "access_token": "string"
}
```

- params:

```json
{
  "id": "integer (required)"
}
```

_Response (200 - OK)_

```json
{
  "message": "Movie <name> deleted"
}
```

_Response (404 - Not Found)_

```json
{
  "message": "Movie not found"
}
```

&nbsp;

## Global Error

_Response (401 - Unauthorized)_

```json
{
  "name": "Unauthorized",
  "message": "No token provided"
}
```

_Response (500 - Internal Server Error)_

```json
{
  "message": "Internal server error"
}
```
