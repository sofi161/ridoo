# User Registration Endpoint Documentation

## Endpoint

**POST** `/register`

## Description

This endpoint registers a new user. It accepts user data, validates the input, and creates a new user in the database. Upon successful registration, it returns a JSON Web Token (JWT) and user details.

## Request Data

The request body should be in JSON format with the following structure:

```json
{
  "fullName": {
    "firstName": "John",
    "lastName": "Doe" // lastName is optional
  },
  "email": "john.doe@example.com",
  "password": "password123"
}
```

### Field Requirements

- **email**: Must be a valid email address.
- **fullName.firstName**: Required; should be at least 3 characters long.
- **password**: Required; must be at least 6 characters long.

## Response

### Successful Registration

- **Status Code**: 201 Created
- **Response Body**:

```json
{
  "token": "<JWT token>",
  "user": {
    "_id": "<User ID>",
    "fullName": {
      "firstName": "John",
      "lastName": "Doe"
    },
    "email": "john.doe@example.com",
    "password": "johnpassword"
  }
}
```

### Validation Error

- **Status Code**: 400 Bad Request
- **Response Body**:

```json
{
  "errors": [
    {
      "msg": "Validation error message",
      "param": "<field>",
      "location": "body"
    }
    // additional error objects
  ]
}
```

## Status Codes Summary

- **201**: User successfully registered.
- **400**: Bad request due to input validation errors.
