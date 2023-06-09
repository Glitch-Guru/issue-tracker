# GlitchGuru Issue Tracker

## API Reference

## Authentication

In order to authenticate with the API, you must first register a user.  
The API will return a JWT token that you can use to authenticate with the API.  
The token must be sent in the `Authorization` header as a `Bearer` token.  

### `POST /api/v1/auth/register`

#### Parameters

| Name        | Type     | Description                             |
|-------------|----------|-----------------------------------------|
| `firstName` | `string` | **Required**. First name of the user.   |
| `lastName`  | `string` | **Required**. Last name of the user.    |
| `email`     | `string` | **Required**. Email of the user.        |
| `password`  | `string` | **Required**. The password of the user. |

#### Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiVVNFUiIsImFjY291bnRfaWQiOjEsInN1YiI6ImR1cGFmc2Rkc2ZzZGFmZjEyM0BlbWZkc2ZzZGFpbC5wbCIsImlhdCI6MTY4MDk4MTgxNSwiZXhwIjoxNjgwOTgzMjU1fQ.UN349pq51V0yFduI9aar--7pPbhWEchdAfJt_SJt_Qs"
}
```

### `POST /api/v1/auth/authenticate`

#### Parameters

| Name       | Type     | Description                             |
|------------|----------|-----------------------------------------|
| `email`    | `string` | **Required**. Email of the user.        |
| `password` | `string` | **Required**. The password of the user. |

#### Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiVVNFUiIsImFjY291bnRfaWQiOjEsInN1YiI6ImR1cGFmc2Rkc2ZzZGFmZjEyM0BlbWZkc2ZzZGFpbC5wbCIsImlhdCI6MTY4MDk4MTg3NSwiZXhwIjoxNjgwOTgzMzE1fQ.F5qaaJaO7ndDtSR11AFAlraa_ZlVMFQNCaRC4b5U5i0"
}
```

## Tickets

This API allows you to create and list tickets.  
In order to create a ticket, you must be authenticated as a user.  
The token must be sent in the `Authorization` header as a `Bearer` token.

### `POST /api/v1/tickets`

#### Parameters

| Name          | Type     | Description                                                |
|---------------|----------|------------------------------------------------------------|
| `title`       | `string` | **Required**. Title of the ticket.                         |
| `description` | `string` | **Required**. Content of the ticket.                       |
| `status`      | `string` | Status of the ticket. Default value: Open                  |
| `assigneeId`  | `number` | Assignee of the ticket. Default value: id of the requester |

#### Response

```json
{
  "id": 1,
  "title": "Test ticket 1",
  "description": "Test ticket 1 description",
  "status": "Open",
  "assigneeId": 1,
  "reporterId": 1
}
```

### `GET /api/v1/tickets`

#### Response

```json
[
  {
    "id": 1,
    "title": "Test ticket 1",
    "description": "Test ticket 1 description",
    "status": "Open",
    "assigneeId": 1,
    "reporterId": 1
  },
  {
    "id": 2,
    "title": "Test ticket 2",
    "description": "Test ticket 2 description",
    "status": "Open",
    "assigneeId": 1,
    "reporterId": 1
  }
]
```

### `GET /api/v1/tickets/{id}`

#### Response

```json
{
"id": 1,
"title": "Test ticket 1",
"description": "Test ticket 1 description",
"status": "Open",
"assigneeId": 1,
"reporterId": 1
}
```

### `PUT /api/v1/tickets/{id}`

#### Parameters

| Name          | Type     | Description                                                |
|---------------|----------|------------------------------------------------------------|
| `title`       | `string` | Title of the ticket.                                       |
| `description` | `string` | Content of the ticket.                                     |
| `status`      | `string` | Status of the ticket. Default value: Open                  |
| `assigneeId`  | `number` | Assignee of the ticket. Default value: id of the requester |

### `DELETE /api/v1/tickets/{id}`

## Users

This API allows you to list users.
In order to list users, you must be authenticated as a user.  
The token must be sent in the `Authorization` header as a `Bearer` token.

### `GET /api/v1/users`

#### Response

```json
[
  {
    "id": 1,
    "firstName": "testFirstName",
    "lastName": "testLastName",
    "email": "testEmail",
    "role": "USER"
  },
  {
    "id": 2,
    "firstName": "testFirstName",
    "lastName": "testLastName",
    "email": "testEmail2",
    "role": "USER"
  }
]
```

### `GET /api/v1/users/{id}`

#### Response

```json
{
  "id": 1,
  "firstName": "testFirstName",
  "lastName": "testLastName",
  "email": "testEmail",
  "role": "USER"
}
```

### `GET /api/v1/users/current`

#### Response

```json
{
  "id": 1,
  "firstName": "testFirstName",
  "lastName": "testLastName",
  "email": "testEmail",
  "role": "USER"
}
```