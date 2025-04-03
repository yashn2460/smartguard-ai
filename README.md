# SmartGuard AI Backend

A TypeScript-based Node.js server for the SmartGuard AI application.

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)
- MongoDB (v4.4 or higher)

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create a `.env` file in the root directory and add your environment variables:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/smartguard
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRES_IN=24h
API_PREFIX=/api/v1
```

## Development

To run the server in development mode with hot-reload:
```bash
npm run dev
```

## Production

To build and run the server in production mode:
```bash
npm run build
npm start
```

## Available Scripts

- `npm run dev`: Start the development server with hot-reload
- `npm run build`: Build the TypeScript code
- `npm start`: Start the production server
- `npm test`: Run tests (to be implemented)

## API Documentation

The API documentation is available using Swagger UI at:
```
http://localhost:3000/api-docs
```

This interactive documentation allows you to:
- Browse all available endpoints
- See request/response schemas
- Test API endpoints directly from the browser
- Understand authentication requirements

## API Endpoints

### Authentication
- `POST /api/v1/auth/register`: Register a new user
  ```json
  {
    "email": "user@example.com",
    "password": "password123",
    "name": "John Doe"
  }
  ```
- `POST /api/v1/auth/login`: Login user
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```

### Users
- `GET /api/v1/users`: Get all users (requires authentication)
- `POST /api/v1/users`: Create a new user (requires authentication)
  ```json
  {
    "name": "John Doe"
  }
  ```
- `GET /api/v1/users/:id`: Get a specific user (requires authentication)

## Project Structure

```
.
├── src/                    # Source code
│   ├── config/            # Configuration files
│   │   └── database.ts    # Database configuration
│   ├── controllers/       # Request handlers
│   │   ├── authController.ts
│   │   └── userController.ts
│   ├── docs/              # Documentation
│   │   └── swagger.ts     # Swagger API documentation
│   ├── interfaces/        # TypeScript interfaces
│   │   └── apiResponse.ts # API response interface
│   ├── middleware/        # Express middleware
│   │   └── errorHandler.ts # Error handling middleware
│   ├── models/            # Mongoose models
│   │   ├── Auth.ts        # Authentication model
│   │   └── User.ts        # User model
│   ├── routes/            # API routes
│   │   ├── authRoutes.ts  # Authentication routes
│   │   └── userRoutes.ts  # User routes
│   ├── services/          # Business logic
│   │   ├── authService.ts # Authentication service
│   │   └── userService.ts # User service
│   ├── utils/             # Utility functions
│   │   └── apiError.ts    # API error utility
│   └── server.ts          # Main application file
├── dist/                  # Compiled JavaScript
├── package.json           # Dependencies and scripts
├── tsconfig.json          # TypeScript configuration
└── README.md              # This file
``` 