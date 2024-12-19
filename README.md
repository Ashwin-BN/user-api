# User API

This is a Node.js-based RESTful API for user management. It provides endpoints for user registration, authentication using JSON Web Tokens (JWT), and functionalities for managing user favorites and history. The application uses MongoDB for data persistence and is deployed using Vercel.

---

## Features

- **User Registration**: Allows users to create an account with a username and password.
- **Authentication**: Secure login with JWT for session management.
- **Favorites Management**: Add, retrieve, and remove items from a user's favorites list.
- **History Management**: Add, retrieve, and remove items from a user's history list.
- **Security**: Passwords are hashed using `bcryptjs`. JWT is used for secure communication.
- **Database**: MongoDB is used to store user data.

---

## Prerequisites

To run this project locally, ensure you have the following installed:

- Node.js (v16 or above)
- MongoDB
- NPM or Yarn

---

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd user-api
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables:
   Create a `.env` file in the root directory and add the following:
   ```env
   PORT=8080
   MONGO_URL=<your-mongodb-connection-string>
   JWT_SECRET=<your-secret-key>
   ```

4. Start the server:
   ```bash
   npm start
   ```

5. Access the API at:
   ```
   http://localhost:8080
   ```

---

## Endpoints

### **User Authentication**

#### `POST /api/user/register`
Register a new user.

**Request Body**:
```json
{
  "userName": "exampleUser",
  "password": "password123",
  "password2": "password123"
}
```

**Response**:
- Success: `200 OK`
- Error: `422 Unprocessable Entity`

---

#### `POST /api/user/login`
Authenticate a user and generate a JWT token.

**Request Body**:
```json
{
  "userName": "exampleUser",
  "password": "password123"
}
```

**Response**:
- Success: 
  ```json
  {
    "message": "login successful",
    "token": "<jwt-token>"
  }
  ```
- Error: `422 Unprocessable Entity`

---

### **Favorites Management**

#### `GET /api/user/favourites`
Retrieve a list of the user's favorites.

**Authorization**: JWT required in the header.

**Response**:
- Success: Array of favorites.
- Error: `422 Unprocessable Entity`

---

#### `PUT /api/user/favourites/:id`
Add an item to the user's favorites.

**Authorization**: JWT required in the header.

**Response**:
- Success: Updated array of favorites.
- Error: `422 Unprocessable Entity`

---

#### `DELETE /api/user/favourites/:id`
Remove an item from the user's favorites.

**Authorization**: JWT required in the header.

**Response**:
- Success: Updated array of favorites.
- Error: `422 Unprocessable Entity`

---

### **History Management**

#### `GET /api/user/history`
Retrieve a list of the user's history.

**Authorization**: JWT required in the header.

**Response**:
- Success: Array of history items.
- Error: `422 Unprocessable Entity`

---

#### `PUT /api/user/history/:id`
Add an item to the user's history.

**Authorization**: JWT required in the header.

**Response**:
- Success: Updated array of history items.
- Error: `422 Unprocessable Entity`

---

#### `DELETE /api/user/history/:id`
Remove an item from the user's history.

**Authorization**: JWT required in the header.

**Response**:
- Success: Updated array of history items.
- Error: `422 Unprocessable Entity`

---

## Project Structure

```
user-api/
├── server.js           # Main entry point for the application
├── user-service.js     # Service layer for user-related database operations
├── package.json        # Project dependencies and scripts
├── .env                # Environment configuration
```

---

## Deployment

This application is deployed on [Vercel](https://vercel.com/).

### Steps to Deploy:
1. Push your code to a GitHub repository.
2. Import the repository into Vercel.
3. Add environment variables (e.g., `MONGO_URL`, `JWT_SECRET`) in the Vercel dashboard.
4. Deploy the project.

---

## Dependencies

- **express**: Web framework for Node.js.
- **dotenv**: Loads environment variables from a `.env` file.
- **bcryptjs**: For password hashing.
- **jsonwebtoken**: For generating and verifying JWT tokens.
- **mongoose**: MongoDB object modeling for Node.js.
- **passport**: Authentication middleware.
- **passport-jwt**: Passport strategy for authenticating with JWT.
