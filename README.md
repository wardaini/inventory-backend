# Inventory Management System - Backend API

Backend REST API untuk sistem manajemen inventori dengan fitur keamanan lengkap.

## 🚀 Live Demo

**Backend API:** https://inventory-backend-sis8.onrender.com

**Health Check:**
```bash
curl https://inventory-backend-sis8.onrender.com/
```

## ✨ Features

- ✅ JWT Authentication & Authorization
- ✅ Role-Based Access Control (Admin, Staff, Viewer)
- ✅ Password Hashing (bcrypt - 10 salt rounds)
- ✅ Rate Limiting (100 requests/15 min)
- ✅ Input Validation & Sanitization
- ✅ CORS Protection
- ✅ Secure Headers (Helmet.js)
- ✅ MongoDB Database with Mongoose ODM
- ✅ RESTful API Design

## 🛠️ Tech Stack

- **Runtime:** Node.js v18+
- **Framework:** Express.js
- **Database:** MongoDB (Atlas)
- **ODM:** Mongoose
- **Authentication:** JWT (jsonwebtoken)
- **Password:** bcryptjs
- **Security:** Helmet, CORS, express-rate-limit
- **Validation:** express-validator, Joi
- **Logging:** Morgan

## 📦 Installation

### Prerequisites

- Node.js v18 or higher
- npm v9 or higher
- MongoDB Atlas account

### Local Development
```bash
# Clone repository
git clone https://github.com/YOUR_USERNAME/inventory-backend.git
cd inventory-backend

# Install dependencies
npm install

# Setup environment variables
cp .env.example .env
# Edit .env with your configuration

# Start development server
npm run dev
```

Server akan berjalan di `http://localhost:5000`

## ⚙️ Environment Variables

Create `.env` file:
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Connection
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/inventory_db

# JWT Configuration
JWT_SECRET=your_super_long_random_secret_key_minimum_32_characters
JWT_EXPIRE=7d

# Rate Limiting
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100

# CORS
CORS_ORIGIN=http://localhost:5173
```

**Production `.env`:**
```env
NODE_ENV=production
CORS_ORIGIN=https://your-frontend-domain.vercel.app
```

## 📡 API Endpoints

### Authentication

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |
| GET | `/api/auth/me` | Get current user | Yes |
| PUT | `/api/auth/profile` | Update profile | Yes |
| PUT | `/api/auth/change-password` | Change password | Yes |

### Products

| Method | Endpoint | Description | Auth Required | Role |
|--------|----------|-------------|---------------|------|
| GET | `/api/products` | Get all products | Yes | All |
| GET | `/api/products/:id` | Get single product | Yes | All |
| POST | `/api/products` | Create product | Yes | Admin, Staff |
| PUT | `/api/products/:id` | Update product | Yes | Admin, Staff |
| DELETE | `/api/products/:id` | Delete product | Yes | Admin |
| GET | `/api/products/low-stock` | Get low stock products | Yes | All |
| GET | `/api/products/stats/dashboard` | Dashboard statistics | Yes | All |
| PATCH | `/api/products/:id/stock` | Update stock | Yes | Admin, Staff |

### Example Requests

**Register:**
```bash
curl -X POST https://inventory-backend-sis8.onrender.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123",
    "role": "staff"
  }'
```

**Login:**
```bash
curl -X POST https://inventory-backend-sis8.onrender.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "password": "password123"
  }'
```

**Get Products (with JWT token):**
```bash
curl https://inventory-backend-sis8.onrender.com/api/products \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

## 🔒 Security Features

### 1. Authentication & Authorization
- JWT-based stateless authentication
- Token expiration (7 days)
- Role-based access control (RBAC)

### 2. Password Security
- Bcrypt hashing (10 salt rounds)
- Password strength validation
- Secure password change flow

### 3. API Security
- HTTPS enforcement
- CORS configuration
- Rate limiting (prevent brute force)
- Helmet.js security headers
- Input validation & sanitization
- MongoDB injection prevention

### 4. Database Security
- Connection with authentication
- Network access control
- Encrypted connections (TLS/SSL)

## 🚀 Deployment

### Deploy to Render.com

1. **Push code to GitHub**
2. **Connect Render to GitHub**
3. **Create Web Service:**
   - Runtime: Node
   - Build: `npm install`
   - Start: `npm start`
   - Instance: Free

4. **Add Environment Variables:**
```
   NODE_ENV=production
   MONGODB_URI=your_connection_string
   JWT_SECRET=your_secret_key
   CORS_ORIGIN=https://your-frontend.vercel.app
```

5. **Deploy!**

Backend akan auto-deploy setiap push ke GitHub.

## 📁 Project Structure
```
backend/
├── config/
│   └── db.js                 # MongoDB connection
├── models/
│   ├── User.js               # User schema
│   └── Product.js            # Product schema
├── controllers/
│   ├── authController.js     # Auth logic
│   └── productController.js  # Product logic
├── routes/
│   ├── auth.js               # Auth routes
│   └── products.js           # Product routes
├── middleware/
│   ├── auth.js               # JWT verification
│   ├── validation.js         # Input validation
│   └── errorHandler.js       # Error handling
├── .env                      # Environment variables
├── .gitignore
├── package.json
├── server.js                 # Entry point
└── README.md
```

## 🧪 Testing
```bash
# Test with curl
curl https://inventory-backend-sis8.onrender.com/api/health

# Expected response
{
  "success": true,
  "message": "API is healthy",
  "timestamp": "2025-11-04T..."
}
```

## 🐛 Troubleshooting

### CORS Error
- Check `CORS_ORIGIN` environment variable
- Must match frontend URL exactly (include https://)

### MongoDB Connection Failed
- Verify connection string
- Check MongoDB Atlas Network Access (allow 0.0.0.0/0)
- Ensure database user has correct permissions

### Cold Start (Render Free Tier)
- First request after 15 min idle takes ~30 seconds
- Subsequent requests are fast (~200ms)

## 📊 Performance

- Average response time: ~200-500ms
- Rate limit: 100 requests/15 min per IP
- MongoDB connection pooling enabled
- Indexed queries for optimization

## 📄 License

MIT

## 👨‍💻 Author

Wardatul A'ani - [GitHub Profile](https://github.com/wardaini)

## 🔗 Links

- **Backend API:** https://inventory-backend-sis8.onrender.com
- **Frontend App:** https://inventory-frontend-tm8n.vercel.app
- **Documentation:** [API Docs](docs/API.md)
