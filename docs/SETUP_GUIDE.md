# Smart Inventory Management System - Setup Guide

## 🚀 Milestones Complete

### ✅ Milestone 1: Authentication & Role Management (Weeks 1-2)
- User registration and login with JWT authentication
- Role-based access control (Admin/Employee)
- Password reset in user profile
- Secure session management

### ✅ Milestone 2: Product & Inventory Management (Weeks 3-4)
- Complete product CRUD operations
- Stock level tracking and updates
- Stock movement history
- Categories and suppliers management
- Advanced search and filtering
- Low stock detection

This guide covers the setup and running of the complete system with authentication and inventory management.

---

## 📋 Prerequisites

- Python 3.8 or higher
- Node.js 16 or higher
- MySQL 5.7 or higher
- Git

---

## 🛠️ Backend Setup (Python + Flask)

### 1. Install Python Dependencies

```bash
# Navigate to project directory
cd "d:\projects\Smart Inventory Management System"

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Configure Database

```bash
# Create .env file from example
copy .env.example .env

# Edit .env file and update database credentials
# DB_HOST=localhost
# DB_USER=root
# DB_PASSWORD=your-password
# DB_NAME=inventory_db
# DB_PORT=3306
```

### 3. Initialize Database

```bash
# Login to MySQL
mysql -u root -p

# Create database (or run schema.sql)
source database/schema.sql

# Or manually:
CREATE DATABASE inventory_db;
USE inventory_db;
# Copy and paste the contents of database/schema.sql
```

### 4. Run Backend Server

```bash
# Make sure virtual environment is activated
python app.py
```

The backend server will start at: **http://localhost:5000**

---

## � Testing the Application

### Default Admin Credentials

- **Email**: `admin@inventory.com`
- **Password**: `Admin@123`

### Test Flow

1. **Login**: 
   - Open http://localhost:5000
   - Use default admin credentials to login
   - You'll be redirected to the dashboard

2. **Register New User**:
   - Click "Register here" on login page
   - Fill in the registration form
   - Password requirements:
     - At least 8 characters
     - One uppercase letter
     - One lowercase letter
     - One number
     - One special character (!@#$%^&*)
   - Select role: Admin or Employee
   - Click Register

3. **Dashboard**:
   - View user information
   - See role badge (Admin/Employee)
   - Navigate to Products, Reports, or Profile
   - Logout functionality

4. **Profile & Password Reset**:
   - Click "👤 Profile" button in dashboard header
   - View complete user information
   - Change password with current password verification
   - Password must meet strength requirements

5. **Product Management** (New in Milestone 2):
   - Click "📦 Products" from dashboard
   - **Add Product**: Click "+ Add Product" button
     - Enter SKU (unique identifier), name, description
     - Select category and supplier
     - Set unit price, initial stock, min stock level
     - Choose unit of measure
   - **Search & Filter**: 
     - Search by product name or SKU
     - Filter by category or supplier
     - Show only low stock items checkbox
   - **Edit Product**: Update product details (except stock)
   - **Update Stock**: Record inventory movements
     - Stock-in (purchases/receipts)
     - Stock-out (sales/usage)
     - Adjustments (corrections)
     - Add reference numbers and notes
   - **View Details**: See full product info and stock movement history
   - **Delete Product**: Admin-only soft delete

---

## 📁 Project Structure

```
Smart Inventory Management System/
├── backend/
│   ├── auth.py              # Authentication logic (register, login)
│   ├── models.py
│   ├── routes.py
│   └── utils.py
├── database/
│   ├── database.py          # Database connection
│   └── schema.sql           # Database schema with users table
├── frontend-react/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Login.js     # Login component
│   │   │   ├── Register.js  # Registration component
│   │   │   ├── Dashboard.js # Dashboard component
│   │   │   ├── Auth.css
│   │   │   └── Dashboard.css
│   │   ├── services/
│   │   │   └── api.js       # API calls with axios
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── index.js
│   │   └── index.css
│   └── package.json
├── app.py                   # Flask main application
├── config.py                # Configuration settings
├── requirements.txt         # Python dependencies
├── .env.example            # Environment variables template
└── README.md
```

---

## 🔌 API Endpoints

### Authentication Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |
| GET | `/api/auth/me` | Get current user | Yes (JWT) |
| POST | `/api/auth/refresh` | Refresh access token | Yes (Refresh Token) |
| PUT | `/api/auth/change-role` | Change user role (Admin) | Yes (JWT) |
| PUT | `/api/auth/change-password` | Change password | Yes (JWT) |

### Product Management Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/products` | Get all products | Yes (JWT) |
| POST | `/api/products` | Create new product | Yes (JWT) |
| GET | `/api/products/<id>` | Get single product | Yes (JWT) |
| PUT | `/api/products/<id>` | Update product | Yes (JWT) |
| DELETE | `/api/products/<id>` | Delete product (Admin) | Yes (JWT) |
| PUT | `/api/products/<id>/stock` | Update stock | Yes (JWT) |
| GET | `/api/products/<id>/movements` | Get stock history | Yes (JWT) |

### Utility Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/categories` | Get all categories | Yes (JWT) |
| GET | `/api/suppliers` | Get all suppliers | Yes (JWT) |
| GET | `/api/health` | Health check | No |

### Request Examples

**Register:**
```json
POST /api/auth/register
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "SecurePass@123",
  "role": "employee",
  "first_name": "John",
  "last_name": "Doe",
  "phone": "+1234567890"
}
```

**Login:**
```json
POST /api/auth/login
{
  "username": "john_doe",
  "password": "SecurePass@123"
}
```

**Response:**
```json
{
  "message": "Login successful",
  "access_token": "eyJ0eXAiOiJKV1Q...",
  "refresh_token": "eyJ0eXAiOiJKV1Q...",
  "user": {
    "user_id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "role": "employee",
    "first_name": "John",
    "last_name": "Doe"
  }
}
```

---

## 🔒 Security Features

- **Password Hashing**: Using bcrypt for secure password storage
- **JWT Authentication**: Token-based authentication with 24-hour expiry
- **Refresh Tokens**: 30-day refresh tokens for extended sessions
- **Password Validation**: Strong password requirements enforced
- **SQL Injection Prevention**: Using parameterized queries
- **Role-Based Access**: Admin and Employee role separation

---

## ✅ Milestone 1 Completion Checklist

- [x] JWT-based authentication implemented
- [x] User registration with validation
- [x] Login functionality
- [x] Password hashing with bcrypt
- [x] Role-based access control (Admin/Employee)
- [x] React frontend with login/register pages
- [x] Token management and refresh
- [x] User session handling
- [x] Secure database schema
- [x] Error handling and validation

---

## 🐛 Troubleshooting

### Backend Issues

**Database Connection Error:**
```
Error connecting to database
```
- Check MySQL is running
- Verify .env credentials
- Ensure database `inventory_db` exists

**Module Not Found:**
```
ModuleNotFoundError: No module named 'flask'
```
- Activate virtual environment: `venv\Scripts\activate`
- Install requirements: `pip install -r requirements.txt`

### Frontend Issues

**Port Already in Use:**
```
Something is already running on port 3000
```
- Stop other React apps
- Use different port: `PORT=3001 npm start`

**API Connection Failed:**
```
Network Error
```
- Ensure backend is running on http://localhost:5000
- Check CORS configuration

---

## 📚 Next Steps (Upcoming Milestones)

- **Milestone 2 (Weeks 3-4)**: Product and Inventory Management
- **Milestone 3 (Week 5)**: Low-Stock Alerts
- **Milestone 4 (Weeks 6-7)**: Transaction Management
- **Milestone 5 (Week 8)**: Reports and Export

---

## 👥 User Roles

### Admin
- Full system access
- Can create/manage employee accounts
- Access all features and reports
- Manage system settings

### Employee
- Limited access
- Can perform stock operations
- View assigned inventory
- Generate reports (limited)

---

## 📝 License

This project is part of the Smart Inventory Management System development.

---

## 📞 Support

For issues or questions, please create an issue in the GitHub repository.

**Repository**: https://github.com/DhanushPadarthi/Smart-Inventory-Management-System.git

---

**Last Updated**: February 12, 2026  
**Milestone**: 1 - Authentication and Role Management  
**Status**: ✅ Complete
