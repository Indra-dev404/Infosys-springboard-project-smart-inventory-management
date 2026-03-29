# 🏢 Smart Inventory Management System

A comprehensive inventory management system for small businesses with user authentication, role-based access control, and real-time inventory tracking.

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Web Browser

### Installation & Setup

1. **Clone the repository**
```bash
git clone https://github.com/DhanushPadarthi/Smart-Inventory-Management-System.git
cd "Smart Inventory Management System"
```

2. **Create virtual environment**
```bash
python -m venv venv
venv\Scripts\activate  # Windows
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Run the application**
```bash
python app.py
```

5. **Open in browser**
```
http://localhost:5000
```

### Default Login Credentials
- **Username**: `admin`
- **Password**: `Admin@123`

## 📁 Project Structure

```
Smart Inventory Management System/
├── backend/              # Backend logic (authentication, inventory, reports)
├── database/            # Database schema and connection utilities
├── frontend/            # HTML/CSS/JS frontend files
│   ├── css/            # Stylesheets
│   ├── js/             # JavaScript files
│   └── *.html          # HTML pages
├── tests/              # Test files
├── docs/               # Documentation
│   ├── README.md       # Detailed setup guide
│   ├── PRD.md          # Product Requirements Document
│   ├── SETUP_GUIDE.md  # Complete installation guide
│   └── API_DOCUMENTATION.md
├── app.py              # Main Flask application
├── config.py           # Configuration settings
├── requirements.txt    # Python dependencies
└── .env.example        # Environment variables template
```

## ✨ Features

### ✅ Milestone 1 - Complete (Weeks 1-2)
- **User Authentication**: JWT-based login and registration
- **Role Management**: Admin and Employee roles
- **Password Security**: Bcrypt hashing
- **Session Management**: Token-based authentication
- **Profile Management**: Password reset functionality

### ✅ Milestone 2 - Complete (Weeks 3-4)
- **Product Management**: Full CRUD operations for products
- **SKU Management**: Unique product identification
- **Stock Tracking**: Real-time inventory levels
- **Stock Operations**: Stock-in, stock-out, and adjustments
- **Movement History**: Complete audit trail of stock changes
- **Categories & Suppliers**: Organized product classification
- **Search & Filters**: Advanced product search and filtering
- **Low Stock Detection**: Automatic identification of low stock items

### 🚧 Upcoming Milestones
- **Milestone 3** (Week 5): Low-Stock Alerts & Notifications
- **Milestone 4** (Weeks 6-7): Transaction Management
- **Milestone 5** (Week 8): Reports & Export

## 🛠️ Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Backend**: Python Flask
- **Database**: SQLite (Development) / MySQL (Production)
- **Authentication**: JWT (JSON Web Tokens)
- **Security**: Bcrypt password hashing

## 📖 Documentation

Detailed documentation is available in the `docs/` folder:
- [Setup Guide](docs/SETUP_GUIDE.md) - Complete installation instructions
- [Product Requirements](docs/PRD.md) - Full PRD with all milestones
- [API Documentation](docs/API_DOCUMENTATION.md) - API endpoints reference
- [Git Workflow](docs/GIT_WORKFLOW.md) - Contribution guidelines

## 🔐 Security Features

- JWT-based authentication with 24-hour token expiry
- Bcrypt password hashing
- Role-based access control (RBAC)
- Input validation and sanitization
- SQL injection prevention

## 🧪 Testing

Run tests:
```bash
python -m pytest tests/
```

## 📝 License

This project is part of academic coursework.

## 👥 Contributors

- Project Team

## 📞 Support

For issues or questions, please create an issue in the GitHub repository.

---

**Last Updated**: February 14, 2026  
**Current Milestone**: 1 - Authentication & Role Management ✅ Complete
