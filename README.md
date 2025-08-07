# Online-Course-Selling-API
CourseHub is a simple RESTful API for an online course selling platform. This project allows admins to create and manage courses, and users to sign up, browse, purchase, and view purchased courses. It features JWT-based authentication for secure access and uses MongoDB for persistent storage. Built with Node.js, Express, and Mongoose.
Here are step-by-step instructions for using your CourseHub - Online Course Selling API based on your provided code:

1. Prerequisites
Node.js and npm installed.

MongoDB Atlas connection string (already used in your code).

Clone this repository and navigate to the project directory.

2. Setup
Install dependencies:

bash
npm install
Create a config.js file in your project root with your JWT secret:

js
// config.js
module.exports = {
  JWT_SECRET: "your_secret_key"
};
3. Start the Server
bash
node index.js
The server will run on http://localhost:3000

4. API Endpoints
Admin
POST /admin/signup
Create a new admin.
Body: { "username": "admin", "password": "pass" }

POST /admin/signin
Login as admin to receive a JWT token.
Body: { "username": "admin", "password": "pass" }

POST /admin/courses
Create a new course (JWT Bearer token required in Authorization header).
Body: { "title": "Course", "description": "Desc", "imageLink": "URL", "price": 100 }

GET /admin/courses
Get all courses (JWT Bearer token required).

User
POST /user/signup
Register a new user.
Body: { "username": "user", "password": "pass" }

POST /user/signin
Login as user to receive a JWT token.
Body: { "username": "user", "password": "pass" }

GET /user/courses
List all available courses.

POST /user/courses/:courseId
Purchase a course (JWT Bearer token required).

GET /user/purchasedCourses
View purchased courses (JWT Bearer token required).

5. Using API Requests
Use a tool like Postman, Insomnia, or curl to send HTTP requests to these endpoints.

For protected routes, set the Authorization header:

text
Authorization: Bearer <your_jwt_token>
Example curl command to create a course after logging in as admin:

bash
curl -X POST http://localhost:3000/admin/courses \
  -H 'Authorization: Bearer <admin_jwt_token>' \
  -H 'Content-Type: application/json' \
  -d '{"title": "Node.js Basics", "description": "Learn Node", "imageLink": "http://...png", "price": 99}'
6. Notes
Passwords are stored as plain text in this sample. For production, use hashing and validation.

Update connection strings and secrets for your own deployment.

This guide should help you set up and use your online course selling API quickly. If you need example requests, feel free to ask!
