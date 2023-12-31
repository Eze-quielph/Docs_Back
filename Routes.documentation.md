# User API

This API provides endpoints for user registration and user authentication.

- **URL BASE:** `https://eventbackend-production.up.railway.app/api/`

## Routes

### User Registration

- **URL:** `POST /user/register`
- **Description:** Register a new user in the application.
- **Request Body (JSON):**

  ```json
  {
    "FirstName": "First Name",
    "LastName": "Last Name",
    "Username": "Username",
    "Adress": "Address",
    "Birthdate": "Date of Birth",
    "Email": "Email Address",
    "Password": "Password",
    "Image": "Image URL",
    "Role": "CREATOR O USER DEPENDE EL CASO"
  }
  ```

- **Response Body(JSON):**
  ```json
  {
    "user": {
      "id": "36512882-26ec-4795-ba30-118549f80aeb",
      "FirstName": "First Name",
      "LastName": "Last Name",
      "Username": "Username",
      "Adress": "Address",
      "Birthdate": "2004-04-07T03:00:00.000Z",
      "Email": "Ema@gmail.com",
      "Password": "$2b$10$3RzD6dw1D/avxi8jLDJmNeIJyb.koV5hSp2naOBpSGXddjwFZp6wC",
      "Image": "Image URL",
      "updatedAt": "2023-11-07T00:32:58.420Z",
      "createdAt": "2023-11-07T00:32:58.420Z"
    },
    "message": "Usuario creado exitosamente"
  }
  ```

## ERRORS

- 400 Bad Request: User already exists.
- 500 Internal Server Error: Could not create the user

````

-**User Login**

- **URL:** `POST /auth/login`
- **Description:** Log in to the application with the provided credentials.
- **Request Body (JSON):**

```json
{
  "Email": "Email Address",
  "Password": "Password"
}


- **Response Body(JSON):**

```json
{
  "jwt": {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI3ZjZkODBkMy1lYzEwLTQ3NjItYTQ4MS1iNzkzNTM1NzE0OTQiLCJyb2xlIjpudWxsLCJpYXQiOjE2OTkzMTcwMDAsImV4cCI6MTY5OTMyMDYwMH0.MobNbKAXl7EM85F_2YFQkZhnjfUPY4u6tqkKBigaGGE",
    "dataValues": {
      "id": "7f6d80d3-ec10-4762-a481-b79353571494",
      "FirstName": "First Name",
      "LastName": "Last Name",
      "Username": "Username",
      "Adress": "Address",
      "Birthdate": "2004-07-04T03:00:00.000Z",
      "Email": "example@outlook.com",
      "Password": "$2b$10$Gb6v1mIEMcFnPCKunLh3beCYzo8fGUj8rjTZs6.U5NahAn0ihsW9O",
      "Image": "Image URL",
      "Qr": null,
      "Tickets": null,
      "Role": null,
      "createdAt": "2023-11-07T00:11:19.000Z",
      "updatedAt": "2023-11-07T00:11:19.000Z",
      "deletedAt": null
    }
  },
  "message": "Usuario logueado exitosamente"
}
````

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: User not found.
- 500 Internal Server Error: Could not log in the user.

## EVENT CREATE

- **URL:** `POST /event/create`
- **Description** Create Event in to the application
- **Request Body (JSON):**

```json
{
  "Name": "Ejemplo de Evento",
  "Description": "Una descripción de ejemplo para el evento",
  "Day": "2023-10-31",
  "Hour": "2023-10-31T14:00:00",
  "Age_min": 18,
  "Category": "Concierto",
  "Ubication": "Lugar de ejemplo",
  "Price": 25.99,
  "Image": "imagen.jpg",
  "Artist": "Artista Ejemplo",
  "Capacity": 500,
  "UserId": "ID del usuario que crea"
}
```

- **Request Header"**

```
  {
    .....
    "access_token": "token de JWT"
  }
```

- **Response Body(JSON):**

```
[
    {
        "id": "67656e79-2813-4d1b-aca5-0ea21cf88201",
        "Name": "Concierto Danilo Montero",
        "Description": "dasdfdafda",
        "Day": "2023-11-07T03:00:00.000Z",
        "Hour": "2023-11-07T03:00:00.000Z",
        "Age_min": 10,
        "Category": "Concierto",
        "Ubication": "Argentina, Palermo",
        "Price": 500,
        "Image": "https://th.bing.com/th/id/R.97587721349a5be9d7e0c2f80cf9bf86?rik=Kfynk9ck4dnRHw&riu=http%3a%2f%2fcdn.hallels.com%2fdata%2fimages%2ffull%2f11346%2fdanilo-montero.jpg%3fw%3d620&ehk=DNXOmOvgDOaltRP0UnCgBk%2b1SWY28%2fvSuTh90%2f9%2b%2bS4%3d&risl=&pid=ImgRaw&r=0",
        "Artist": "Danilo Montero",
        "Capacity": 10,
        "userId": null,
        "createdAt": "2023-11-08T01:51:01.361Z",
        "updatedAt": "2023-11-08T01:51:01.361Z",
        "deletedAt": null
    }
]
```

## EVENT SearchById

- **URL:** `GET /event/search/:id`
- **Description** Search Event Detail
- **Request Param (ID):**

- **Request Header"**

```
  {
    .....
    "access_token": "token de JWT"
  }
```

- **Response Body(JSON):**

````
{
    "id": "98b00183-3e1d-42b2-8974-fc813595f324",
    "Name": "Concierto Danilo Montero Rosario",
    "Description": "dasdfdafda",
    "Day": "2023-11-07T03:00:00.000Z",
    "Hour": "2023-11-07T03:00:00.000Z",
    "Age_min": 10,
    "Category": "Concierto",
    "Ubication": "Argentina, Rosario",
    "Price": 500,
    "Image": "https://th.bing.com/th/id/R.97587721349a5be9d7e0c2f80cf9bf86?rik=Kfynk9ck4dnRHw&riu=http%3a%2f%2fcdn.hallels.com%2fdata%2fimages%2ffull%2f11346%2fdanilo-montero.jpg%3fw%3d620&ehk=DNXOmOvgDOaltRP0UnCgBk%2b1SWY28%2fvSuTh90%2f9%2b%2bS4%3d&risl=&pid=ImgRaw&r=0",
    "Artist": "Danilo Montero",
    "Capacity": 10,
    "userId": "9fa175e8-9eb2-4769-953a-61e99d08b989",
    "createdAt": "2023-11-08T02:16:18.816Z",
    "updatedAt": "2023-11-08T02:16:18.816Z",
    "deletedAt": null
}```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found.
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByName

- **URL:** `GET /event/search?name=name`
- **Description** Search Event Detail
- **Request Query (?name='name'):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

````

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON):**

```

{
"count": 2,
"rows": [
{
"dataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejemplooooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-19T17:50:49.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejemplooooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-19T17:50:49.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT UpdateEvent

- **URL:** `GET /event/update/:id`
- **Description** Update Event
- **Request Param, Body (Id, JSON):**

```

{
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31",
"Hour": "2023-10-31T14:00:00",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 25.99,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100
}

```

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON):**

```

{
"updatedEvent": [
1
],
"event": {
"dataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-19T18:58:22.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-19T18:58:22.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
}

```

## EVENT SearchByCategory

- **URL:** `GET /event/filter/category?category=Concierto`
- **Description** filter Event
- **Request Query (?category='category'):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 2,
"rows": [
{
"dataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByPrice

- **URL:** `GET /event/filter/price?min_price=number&max_price=number`
- **Description** filter Event
- **Request Query (?min_price=number&max_price=number):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 1,
"rows": [
{
"dataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByDay

- **URL:** `GET /event/filter/day?min_day=2023-08-31T00:00:00.000Z&max_day=2023-11-31T00:00:00.000Z`
- **Description** filter Event
- **Request Query (?min_price=number&max_price=number):**
- **FORMAT TIME: 2023-08-31T00:00:00.000Z**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 3,
"rows": [
{
"dataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByCategoryAndPrice

- **URL:** `GET /event/filter/category_price?category=Comercial&min_price=1&max_price=20
- **Description** filter Event
- **Request Query (?category=string&min_price=number&max_price=number):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 1,
"rows": [
{
"dataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "7df60ffa-07dd-4e73-aa4f-1adaad9b13ab",
"Name": "Ejempooo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Comercial",
"Ubication": "Lugar de ejemplo",
"Price": 2,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 100,
"createdAt": "2023-10-19T16:27:54.000Z",
"updatedAt": "2023-10-20T07:12:19.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByCategoryAndDay

- **URL:** `GET /event/filter/category_day?category=Concierto&min_day=2023-08-31T00:00:00.000Z&max_day=2023-11-31T00:00:00.000Z
- **Description** filter Event
- **Request Query (?category=string&min_day=Date&max_day=Date):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 2,
"rows": [
{
"dataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByDayAndPrice

- **URL:** `GET /event/filter/price_day?min_price=25&max_price=500&min_day=2023-08-31T00:00:00.000Z&max_day=2023-11-31T00:00:00.000Z
- **Description** filter Event
- **Request Query (?min_price=number&max_price=number&min_day=Date&max_day=Date):**
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{
.....
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"count": 2,
"rows": [
{
"dataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
"Name": "Ejemplo de Evento",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T14:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-19T18:41:36.000Z",
"updatedAt": "2023-10-19T18:41:36.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{
"dataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "8c8a2d83-68b3-4555-a5b1-00ad9cb9aa39",
"Name": "Ejemplo",
"Description": "Una descripción de ejemplo para el evento",
"Day": "2023-10-31T00:00:00.000Z",
"Hour": "2023-10-31T17:00:00.000Z",
"Age_min": 18,
"Category": "Concierto",
"Ubication": "Lugar de ejemplo",
"Price": 26,
"Image": "imagen.jpg",
"Artist": "Artista Ejemplo",
"Capacity": 500,
"createdAt": "2023-10-20T06:33:28.000Z",
"updatedAt": "2023-10-20T06:33:28.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT GetAllEvents

- **URL:** `GET /event`
- **Description** get all events
- **Query Optional pagination (limit=number&off-set=number)**
    - **Default pagination: limit=20, off-set=0**

- **Request Header"**

```

{.
.......
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**
In this example, there are a total of 32 rows, but only 20 are shown. This is due to the default values (limit=20, offset=0).
```

{
"count": 32,
"rows": [
{
"dataValues": {
"id": "009ee05f-564f-4e50-b9aa-1607b5153dfc",
"Name": "Consumer Services59",
"Description": "Lion",
"Day": "2018-05-23T15:53:00.000Z",
"Hour": "2021-09-23T09:20:00.000Z",
"Age_min": 69,
"Category": "Hard Tile & Stone",
"Ubication": "Vicente Guerrero",
"Price": 45,
"Image": "https://wikimedia.org",
"Artist": "W√°",
"Capacity": 85,
"createdAt": "2021-09-23T09:20:00.000Z",
"updatedAt": "2021-09-23T09:20:00.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "009ee05f-564f-4e50-b9aa-1607b5153dfc",
"Name": "Consumer Services59",
"Description": "Lion",
"Day": "2018-05-23T15:53:00.000Z",
"Hour": "2021-09-23T09:20:00.000Z",
"Age_min": 69,
"Category": "Hard Tile & Stone",
"Ubication": "Vicente Guerrero",
"Price": 45,
"Image": "https://wikimedia.org",
"Artist": "W√°",
"Capacity": 85,
"createdAt": "2021-09-23T09:20:00.000Z",
"updatedAt": "2021-09-23T09:20:00.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{...},
{
"dataValues": {
"id": "2756c20f-d710-4f9c-bd26-fb323df8d202",
"Name": "Miscellaneous88",
"Description": "Thayne",
"Day": "2016-06-23T15:53:00.000Z",
"Hour": "2020-10-23T09:20:00.000Z",
"Age_min": 85,
"Category": "Retaining Wall and Brick Pavers",
"Ubication": "Los Boquerones",
"Price": 38,
"Image": "http://dot.gov",
"Artist": "Ma√Øwenn",
"Capacity": 32,
"createdAt": "2020-10-23T09:20:00.000Z",
"updatedAt": "2020-10-23T09:20:00.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "2756c20f-d710-4f9c-bd26-fb323df8d202",
"Name": "Miscellaneous88",
"Description": "Thayne",
"Day": "2016-06-23T15:53:00.000Z",
"Hour": "2020-10-23T09:20:00.000Z",
"Age_min": 85,
"Category": "Retaining Wall and Brick Pavers",
"Ubication": "Los Boquerones",
"Price": 38,
"Image": "http://dot.gov",
"Artist": "Ma√Øwenn",
"Capacity": 32,
"createdAt": "2020-10-23T09:20:00.000Z",
"updatedAt": "2020-10-23T09:20:00.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
}
]
}

```

## ERRORS

- 400 Bad Request: BAD_REQUEST: Validation failed (numeric string is expected.
- 404 Not Found: NOT_FOUND: Event not found
- 500 Internal Server Error: Could not log in the user.

## EVENT GetUpcommingEvents

- **URL:** `GET /event/upcoming`
- **Description** get upcoming events
- **Query Optional pagination (limit=number)**
    - **Default pagination: limit=6**

- **Request Header"**

```

{.
.......
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**
```

{
"count": 6,
"rows": [
{
"dataValues": {
"id": "d0fac699-53b5-4b21-8550-cd7a981cc902",
"Name": "Technology58",
"Description": "Davidson",
"Day": "2023-10-26T10:57:30.000Z",
"Hour": "2023-10-18T10:57:30.000Z",
"Age_min": 75,
"Category": "Construction Clean and Final Clean",
"Ubication": "Beni Khiar",
"Price": 6,
"Image": "https://miibeian.gov.cn",
"Artist": "L√≥ng",
"Capacity": 64,
"createdAt": "2023-10-18T10:57:30.000Z",
"updatedAt": "2023-10-18T10:57:30.000Z",
"deletedAt": null
},
"\_previousDataValues": {
"id": "d0fac699-53b5-4b21-8550-cd7a981cc902",
"Name": "Technology58",
"Description": "Davidson",
"Day": "2023-10-26T10:57:30.000Z",
"Hour": "2023-10-18T10:57:30.000Z",
"Age_min": 75,
"Category": "Construction Clean and Final Clean",
"Ubication": "Beni Khiar",
"Price": 6,
"Image": "https://miibeian.gov.cn",
"Artist": "L√≥ng",
"Capacity": 64,
"createdAt": "2023-10-18T10:57:30.000Z",
"updatedAt": "2023-10-18T10:57:30.000Z",
"deletedAt": null
},
"uniqno": 1,
"\_changed": [],
"\_options": {
"isNewRecord": false,
"\_schema": null,
"\_schemaDelimiter": "",
"raw": true,
"attributes": [
"id",
"Name",
"Description",
"Day",
"Hour",
"Age_min",
"Category",
"Ubication",
"Price",
"Image",
"Artist",
"Capacity",
"createdAt",
"updatedAt",
"deletedAt"
]
},
"isNewRecord": false
},
{...},
{...},
{...},
{...},
{...}
]
}

````

##  Create shopping-cart

- **URL:** `POST /shopping-cart`
- **Description** create shopping-cart
- **Body: **
   ```json
   {
    "creationDate":"2023:11:08",
    "total":0,
    "idUser":"32d39d0a-6b2a-4d5c-8c2c-eed24fe4f1c1"
    }
```

- **Request Header"**

````

{.
.......
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**

```

{
"id": "3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
"creationDate": "2023-01-01T14:08:00.000Z",
"total": "0.00",
"idUser": "32d39d0a-6b2a-4d5c-8c2c-eed24fe4f1c1"
}

````

##  Create item-cart

- **URL:** `POST /item-cart`
- **Description** create item
- **Body: **
   ```json
  {
    "quantity":1,
    "unitPrice":100,
    "idShoppingCart":"3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
    "idEvent":"d6f330b2-1031-4c47-a096-1ad0224636ab"
}
````

- **Request Header"**

````

{.
.......
"access_token": "token de JWT"
}

```

- **Response Body(JSON)**
```json
  {
    "item": {
        "id": "79e0f62f-b8d1-4a8f-922c-36eb1c22e4d1",
        "quantity": 1,
        "unitPrice": "100.00",
        "idShoppingCart": "3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
        "idEvent": "d6f330b2-1031-4c47-a096-1ad0224636ab"
    },
    "updateShop": {
        "id": "3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
        "creationDate": "2023-01-01T14:08:00.000Z",
        "total": "100.00",
        "idUser": "32d39d0a-6b2a-4d5c-8c2c-eed24fe4f1c1"
    }
}
```

##  Create item-cart

- **URL:** `PUT /item-cart`
- **Description** create item
- **Query: ?id=idItem**
- **Body: **
   ```json
 {
  "quantity": 5
}
```

- **Request Header"**

````

{.
.......
"access_token": "token de JWT"
}

````

- **Response Body(JSON)**

```json
 {
    "shop": {
        "id": "3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
        "creationDate": "2023-01-01T14:08:00.000Z",
        "total": "500.00",
        "idUser": "32d39d0a-6b2a-4d5c-8c2c-eed24fe4f1c1"
    },
    "itemCart": [
        1
    ],
    "detail": {
        "id": "79e0f62f-b8d1-4a8f-922c-36eb1c22e4d1",
        "quantity": 5,
        "unitPrice": "100.00",
        "idShoppingCart": "3ae7bdf2-a462-4ca1-93fb-e64c68245d36",
        "idEvent": "d6f330b2-1031-4c47-a096-1ad0224636ab"
    }
}
````
