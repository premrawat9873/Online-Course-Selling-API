# Online-Course-Selling-API
CourseHub is a simple RESTful API for an online course selling platform. This project allows admins to create and manage courses, and users to sign up, browse, purchase, and view purchased courses. It features JWT-based authentication for secure access and uses MongoDB for persistent storage. Built with Node.js, Express, and Mongoose.
Here are step-by-step instructions for using your CourseHub - Online Course Selling API based on your provided code:

# CourseHub - Online Course Selling API

CourseHub is a RESTful API for an online course selling platform. This API allows admins to create and manage courses, and users to register, browse, purchase, and view purchased courses. It uses JWT for authentication and MongoDB for data storage. Built with Node.js, Express, and Mongoose.

## Features

- Admin registration & login
- Course creation and management (admin only)
- User registration & login
- Browse all courses
- Purchase courses
- View purchased courses
- JWT authentication for protected routes

## Technologies Used

- Node.js
- Express.js
- MongoDB (Mongoose)
- JSON Web Tokens (JWT)

## Getting Started

### Prerequisites

- Node.js and npm installed
- MongoDB connection string (e.g., from MongoDB Atlas)

### Installation

1. **Clone the repository:**

git clone [https://github.com/yourusername/coursehub-api.git](https://github.com/premrawat9873/Online-Course-Selling-API.git)
cd coursehub-api

text

2. **Install dependencies:**

npm install

text

3. **Create `config.js` in the root folder and add your JWT secret:**

// config.js
module.exports = {
JWT_SECRET: "your_secret_key"
};

text

4. **Ensure your MongoDB connection string is correct**  
(_Check `db.js` or `index.js` in your code._)

### Running the Server

node index.js

text

Server will start at `http://localhost:3000`

## API Endpoints

### Admin

- **POST /admin/signup**
  - Create a new admin.
  - Body: `{ "username": "admin", "password": "pass" }`

- **POST /admin/signin**
  - Login as admin, receive JWT.
  - Body: `{ "username": "admin", "password": "pass" }`

- **POST /admin/courses**
  - Add a course (requires JWT in `Authorization` header).
  - Body: `{ "title": "...", "description": "...", "imageLink": "...", "price": 100 }`

- **GET /admin/courses**
  - List all courses (requires JWT).

### User

- **POST /user/signup**
  - Create a new user.
  - Body: `{ "username": "user", "password": "pass" }`

- **POST /user/signin**
  - Login as user, receive JWT.
  - Body: `{ "username": "user", "password": "pass" }`

- **GET /user/courses**
  - Browse all courses.

- **POST /user/courses/:courseId**
  - Purchase a course (requires JWT).

- **GET /user/purchasedCourses**
  - View purchased courses (requires JWT).

## Authentication

For protected endpoints, set the `Authorization` header in your requests:
Authorization: Bearer <your_jwt_token>

text

## Example curl Command

Create a course as admin (after login):

curl -X POST http://localhost:3000/admin/courses
-H 'Authorization: Bearer <admin_jwt_token>'
-H "Content-Type: application/json"
-d '{"title":"Node.js Basics","description":"Learn Node","imageLink":"http://...","price":99}'

text

## Notes

- Passwords are stored in plain text for demo purposes. **Change this for production!**
- Update the MongoDB connection string and secrets before deploying.

---

Feel free to fork, open issues, or contribute!
