# Role-Based User Management API

A FastAPI-based REST API that implements role-based authentication and user management with MongoDB as the database backend. The system supports user registration, authentication, and role-based access control (RBAC) with admin and regular user roles.

## Features

- User registration and authentication
- JWT-based token authentication
- Role-based access control (Admin and User roles)
- Secure password hashing using bcrypt
- MongoDB integration for data persistence
- RESTful API endpoints

## Prerequisites

- Python 3.8 or higher
- MongoDB installed and running
- pip (Python package manager)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd role-base-user-2
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up MongoDB:
- Ensure MongoDB is installed and running on your system
- The application will automatically connect to the default MongoDB instance

## Running the Application

Start the FastAPI server using uvicorn:

```bash
uvicorn app.main:app --reload
```

The API will be available at `http://localhost:8000`

## API Endpoints

### Authentication

#### Register a New User
- **POST** `/register`
- Creates a new user account
- Body:
  ```json
  {
    "email": "user@example.com",
    "password": "strongpassword",
    "role": "user"  // "admin" or "user"
  }
  ```

#### Login
- **POST** `/token`
- Authenticates user and returns JWT token
- Form data:
  - username (email)
  - password

### User Management

#### Get Current User Info
- **GET** `/users/me`
- Returns information about the currently authenticated user
- Requires authentication

#### List All Users (Admin Only)
- **GET** `/users`
- Returns a list of all registered users
- Requires admin role

## Security

- Passwords are hashed using bcrypt
- JWT tokens are used for authentication
- Role-based access control for protected endpoints
- Input validation using Pydantic models

## Dependencies

- FastAPI: Web framework for building APIs
- PyMongo: MongoDB driver for Python
- Python-Jose: JWT token handling
- Passlib: Password hashing
- Python-multipart: Form data parsing
- Uvicorn: ASGI server

## Error Handling

The API uses standard HTTP status codes:
- 200: Success
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

## Development

For development purposes, the server can be started with auto-reload:

```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

## API Documentation

FastAPI automatically generates interactive API documentation:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`