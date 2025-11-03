# Inventory Management System - Backend API

Backend API untuk sistem manajemen inventori dengan fitur keamanan lengkap.

## Features

- ✅ JWT Authentication
- ✅ Role-Based Access Control (RBAC)
- ✅ Password Hashing (bcrypt)
- ✅ Rate Limiting
- ✅ Input Validation
- ✅ CORS Protection
- ✅ Secure Headers (Helmet)
- ✅ MongoDB Database
- ✅ RESTful API

## Tech Stack

- Node.js & Express.js
- MongoDB & Mongoose
- JWT for authentication
- bcryptjs for password hashing
- Helmet for security headers
- express-rate-limit for rate limiting

## Installation
```bash
# Clone repository
git clone https://github.com/username/inventory-backend.git
cd inventory-backend

# Install dependencies
npm install

# Setup environment variables
cp .env.example .env
# Edit .env with your configuration

# Start development server
npm run dev
```

## Environment Variables
```
PORT=5000
NODE_ENV=development
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=7d
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100
CORS_ORIGIN=http://localhost:3000
```

## API Endpoints

### Authentication
- POST /api/auth/register - Register new user
- POST /api/auth/login - Login user
- GET /api/auth/me - Get current user
- PUT /api/auth/profile - Update profile
- PUT /api/auth/change-password - Change password

### Products
- GET /api/products - Get all products
- GET /api/products/:id - Get single product
- POST /api/products - Create product (Admin/Staff)
- PUT /api/products/:id - Update product (Admin/Staff)
- DELETE /api/products/:id - Delete product (Admin)
- GET /api/products/low-stock - Get low stock products
- GET /api/products/stats/dashboard - Get dashboard statistics

## Deployment

Deployed on Render.com: https://inventory-backend.onrender.com

## License

MIT
