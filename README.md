# Task Management RESTful API

## Introduction
This project is a Task Management RESTful API built using Node.js, Express, MongoDB, and Swagger. It allows users to register with their email and password, and perform CRUD (Create, Read, Update, Delete) operations on tasks. The application uses JWT (JSON Web Token) for user authentication and WebSockets for real-time task updates.

## Features
- **User Registration**: Register with email and password.
- **Task Management**: Create, edit, get all tasks, get a single task, and delete tasks.
- **Authentication**: JWT-based authentication for secure access to task operations.
- **Real-time Updates**: WebSockets for real-time task updates rendered in the browser.
- **API Documentation**: Swagger for API documentation and testing.

## Technologies Used
- Node.js
- Express
- MongoDB
- JWT
- WebSockets
- Swagger
- Jest for testing

## Folder Structure
```
src/
  ├── config/          # Database and Swagger configuration
  ├── controllers/     # User and task controllers
  ├── middleware/      # Authentication setup
  ├── models/          # Database models
  ├── routes/          # API routes
  ├── socket.js        # WebSocket configuration
public/
  ├── index.html       # HTML template for real-time updates and JavaScript to handle WebSocket events
test/
  ├── dbController.test.js     # Unit tests for user
  ├── userController.test.js     # Unit tests for tasks
server.js                          # Main entry to the project
socket.js                           # configuration logic to handle WebSocket events
.env                   # Environment variables
```

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/ayowilfred95/RESTful-API-for-a-simple-task-management-system.git
   cd task-manager
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Create a .env File**
   Create a `.env` file in the root of the project and add the following variables:
   ```env
   PORT=4000
   MONGO_URI=mongodb+srv://username:password@cluster0.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
   JWT_SECRET=myjwtsecret12345
   ```

4. **Start the Server**
   ```bash
   npm start
   ```

5. **Access API Documentation**
   Open your browser and navigate to [http://localhost:4000/api-docs/](http://localhost:4000/api-docs/) to test the application using Swagger.

6. **Real-time Task Updates**
   Open a new tab on your browser and navigate to [http://localhost:4000/](http://localhost:4000/) to stream task data created in real-time.

## Usage

### User Registration
1. Create a new user by sending a POST request to `/api/user/register` with email and password.
2. A user value has been inputted in the swagger, no need to provide user email and password.
3. Just click on `try it out` on the User session on Register a new user and click `execute`
4. A JWT token will be generated upon successful registration.

### Authentication
1. Copy the generated token and paste it in the "Authorize" button in Swagger located at the top right of the page.

### Task Operations
1. Perform CRUD operations on tasks using the authenticated endpoints:
   - **Create Task**: POST `/api/task`
   - **Get All Tasks**: GET `/api/task`
   - **Get Single Task**: GET `/api/task/:id`
   - **Update Task**: PUT `/api/task/:id`
   - **Delete Task**: DELETE `/api/task/:id`


## Models

### User Model
The user model schema has two fields: `email` and `password`, both of which are required. Mongoose is used to connect to MongoDB. Validators ensure that the email format is correct and that the password is strong.

### Task Model
The task model schema has three fields: `title`, `description`, and `completed`. A user token ID generated during registration and login is used to authorize the user to perform CRUD operations on the task.

## Error Handling

Try and catch blocks are used extensively in the controllers to validate inputs and perform various checks to ensure the integrity and security of the operations.

## Testing
Run unit tests using Jest:
```bash
npm test
```

## Real-time Updates
- The HTML template and JavaScript in the `public` folder handle WebSocket events to render tasks in real-time.
- Whenever a task is created, updated, or deleted, a WebSocket event is emitted and rendered in the browser.

## Dependencies
- **express**: Web framework for Node.js
- **mongoose**: MongoDB object modeling tool
- **jsonwebtoken**: JWT implementation
- **socket.io**: Real-time bidirectional event-based communication
- **swagger-ui-express**: Swagger UI for API documentation
- **jest**: JavaScript testing framework


