**# Express User Management API

A complete user management system built with Express.js, MongoDB, and EJS templating engine.

## 📦 Required Packages

Install the following packages before running the application:

```bash
npm install express ejs bcrypt mongoose path
```

### Package Details:
- **express**: Web framework for Node.js
- **ejs**: Embedded JavaScript templating engine
- **bcrypt**: Password hashing library
- **mongoose**: MongoDB object modeling tool
- **path**: Node.js built-in module for file paths

## 🚀 Getting Started

1. Install dependencies:
```bash
npm install
```

2. Make sure MongoDB is running on your system

3. Create a `models/userModel.js` file with your user schema

4. Create a `views` folder and place the `login.ejs` file inside

5. Create a `public` folder for static files

6. Start the server:
```bash
node app.js
```

The server will run on `http://localhost:3000`

## 📝 API Endpoints

### 1. Create User
**Endpoint**: `POST /user/create`  
**Content-Type**: `application/json`

**Request Body**:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "mypassword123"
}
```

**Success Response**:
```json
{
  "success": true,
  "message": "User successfully created!",
  "redirectUrl": "/login"
}
```

### 2. User Login
**Endpoint**: `POST /login`  
**Content-Type**: `application/json`

**Request Body**:
```json
{
  "email": "john@example.com",
  "password": "mypassword123"
}
```

**Success Response**:
```json
{
  "success": true,
  "message": "Successfully Logged In",
  "redirectUrl": "/profile/:user"
}
```

**Error Response**:
```json
{
  "message": "No User Found!",
  "redirectUrl": "/user/create"
}
```

### 3. Update User
**Endpoint**: `POST /user/update`  
**Content-Type**: `application/json`

**Request Body**:
```json
{
  "id": "60f1b2b3c4d5e6f7g8h9i0j1",
  "name": "John Updated",
  "email": "john.updated@example.com"
}
```

**Success Response**:
```json
{
  "success": true,
  "message": "User updated successfully!",
  "user": {
    "_id": "60f1b2b3c4d5e6f7g8h9i0j1",
    "name": "John Updated",
    "email": "john.updated@example.com",
    "password": "hashedpassword"
  }
}
```

### 4. Delete User
**Endpoint**: `DELETE /user/delete/:id`  
**URL Parameter**: User ID

**Example**: `DELETE /user/delete/60f1b2b3c4d5e6f7g8h9i0j1`

**Success Response**:
```json
{
  "success": true,
  "message": "User deleted successfully!"
}
```

**Error Response**:
```json
{
  "success": false,
  "message": "User not found!"
}
```

### 5. Get Single User
**Endpoint**: `GET /user/:id`  
**URL Parameter**: User ID

**Example**: `GET /user/60f1b2b3c4d5e6f7g8h9i0j1`

**Success Response**:
```json
{
  "success": true,
  "user": {
    "_id": "60f1b2b3c4d5e6f7g8h9i0j1",
    "name": "John Doe",
    "email": "john@example.com",
    "password": "hashedpassword"
  }
}
```

### 6. Get All Users
**Endpoint**: `GET /users`  
**Method**: GET

**Success Response**:
```json
{
  "success": true,
  "users": [
    {
      "_id": "60f1b2b3c4d5e6f7g8h9i0j1",
      "name": "John Doe",
      "email": "john@example.com",
      "password": "hashedpassword"
    },
    {
      "_id": "60f1b2b3c4d5e6f7g8h9i0j2",
      "name": "Jane Smith",
      "email": "jane@example.com",
      "password": "hashedpassword"
    }
  ]
}
```

### 7. Login Page
**Endpoint**: `GET /login`  
**Method**: GET  
**Response**: Renders the login page (`login.ejs`)

## 🧪 Testing the API

### Using cURL:

**Create User**:
```bash
curl -X POST http://localhost:3000/user/create \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","password":"testpass123"}'
```

**Login**:
```bash
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"testpass123"}'
```

**Update User**:
```bash
curl -X POST http://localhost:3000/user/update \
  -H "Content-Type: application/json" \
  -d '{"id":"USER_ID_HERE","name":"Updated Name","email":"updated@example.com"}'
```

**Delete User**:
```bash
curl -X DELETE http://localhost:3000/user/delete/USER_ID_HERE
```

**Get User**:
```bash
curl -X GET http://localhost:3000/user/USER_ID_HERE
```

**Get All Users**:
```bash
curl -X GET http://localhost:3000/users
```

### Using Postman:

1. Set method to POST/GET/DELETE as required
2. Set URL to the endpoint
3. For POST requests, set Headers: `Content-Type: application/json`
4. Add JSON body as shown in examples above

## 📁 Project Structure

```
project/
├── app.js              # Main application file
├── models/
│   └── userModel.js    # User schema (create this)
├── views/
│   └── login.ejs       # Login page template
├── public/
│   └── login.css       # Login page styles
├── package.json        # Dependencies
└── README.md          # This file
```

## 🗂️ Setup Project Structure

Create the following folders and files:

1. **Create views folder and add login.ejs**:
```bash
mkdir views
# Add login.ejs file in views folder
```

2. **Create public folder and add login.css**:
```bash
mkdir public
# Add login.css file in public folder
```

## 🔐 Security Features

- **Password Hashing**: Uses bcrypt with salt rounds
- **Input Validation**: Basic validation on required fields
- **Error Handling**: Proper error responses for failed operations

