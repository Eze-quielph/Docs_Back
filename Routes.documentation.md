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
    "Qr": "QR Code",
    "Tickets": "Tickets",
    "Role": "Role"
  }
  ```

- **Response Body(JSON):**
  ```json
  {
      {
        "token": "Authentication Token",
        "user": {
            // User data
        },
        "message": "User created successfully"
        }
    }
  ```

## ERRORS

- 400 Bad Request: User already exists.
- 500 Internal Server Error: Could not create the user

### User Login

- **URL:** `POST /user/login`
- **Description:** Log in to the application with the provided credentials.
- **Request Body (JSON):**

```json
{
  "Email": "Email Address",
  "Password": "Password"
}
```

- **Response Body(JSON):**

```json
{
  "user": {
    // User data
  },
  "token": "Authentication Token",
  "message": "User logged in successfully"
}
```

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
  "Capacity": 500
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
    "dataValues": {
        "id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
        "Name": "Ejemplo de Evento",
        "Description": "Una descripción de ejemplo para el evento",
        "Day": "2023-10-31T00:00:00.000Z",
        "Hour": "2023-10-31T14:00:00.000Z",
        "Age_min": 18,
        "Category": "Concierto",
        "Ubication": "Lugar de ejemplo",
        "Price": 25.99,
        "Image": "imagen.jpg",
        "Artist": "Artista Ejemplo",
        "Capacity": 500,
        "updatedAt": "2023-10-19T18:41:36.907Z",
        "createdAt": "2023-10-19T18:41:36.907Z"
    },
    "_previousDataValues": {
        "Name": "Ejemplo de Evento",
        "Description": "Una descripción de ejemplo para el evento",
        "Day": "2023-10-31T00:00:00.000Z",
        "Hour": "2023-10-31T14:00:00.000Z",
        "Age_min": 18,
        "Category": "Concierto",
        "Ubication": "Lugar de ejemplo",
        "Price": 25.99,
        "Image": "imagen.jpg",
        "Artist": "Artista Ejemplo",
        "Capacity": 500,
        "id": "8c81939a-0f1b-4332-a4d8-ef43e3cc41ab",
        "createdAt": "2023-10-19T18:41:36.907Z",
        "updatedAt": "2023-10-19T18:41:36.907Z"
    },
    "uniqno": 1,
    "_changed": [],
    "_options": {
        "isNewRecord": true,
        "_schema": null,
        "_schemaDelimiter": ""
    },
    "isNewRecord": false
}
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

```
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
    "_previousDataValues": {
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
    "_changed": [],
    "_options": {
        "isNewRecord": false,
        "_schema": null,
        "_schemaDelimiter": "",
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
```

## ERRORS

- 400 Bad Request: Incorrect credentials.
- 404 Not Found: NOT_FOUND: Event not found.
- 500 Internal Server Error: Could not log in the user.

## EVENT SearchByName

- **URL:** `GET /event/search?name=name`
- **Description** Search Event Detail
- **Request Query (?name='name'):**

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
            "_previousDataValues": {
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
            "_changed": [],
            "_options": {
                "isNewRecord": false,
                "_schema": null,
                "_schemaDelimiter": "",
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
            "_previousDataValues": {
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
            "_changed": [],
            "_options": {
                "isNewRecord": false,
                "_schema": null,
                "_schemaDelimiter": "",
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
        "_previousDataValues": {
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
        "_changed": [],
        "_options": {
            "isNewRecord": false,
            "_schema": null,
            "_schemaDelimiter": "",
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
