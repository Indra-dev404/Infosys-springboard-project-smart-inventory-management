# Smart Inventory Management System

A comprehensive web-based inventory management system built with Flask and SQLite to help businesses track products, manage stock levels, process orders, and generate insightful reports.

## 🎯 Features

- **User Authentication**: Secure login and registration system
- **Product Management**: Add, edit, delete, and search products
- **Inventory Tracking**: Real-time stock level monitoring
- **Low Stock Alerts**: Automatic notifications for low inventory
- **Order Management**: Create and track customer orders
- **Supplier Management**: Maintain supplier information and contacts
- **Reports & Analytics**: Sales reports, inventory summaries, and performance metrics
- **Dashboard**: Visual overview of key metrics and statistics

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Python 3.8+, Flask
- **Database**: SQLite
- **Version Control**: Git

## 📁 Project Structure

```
Smart Inventory Management System/
├── app.py                          # Flask application entry point
├── config.py                       # Configuration settings
├── requirements.txt                # Python dependencies
├── .env.example                    # Environment variables template
├── .gitignore                      # Git ignore rules
├── README.md                       # Project documentation
├── PRD.md                         # Product requirements
├── TEAM_ASSESSMENT.md             # Team assignments
│
├── backend/                        # Backend Python modules
│   ├── __init__.py                # Package initialization
│   ├── routes.py                  # API route definitions
│   ├── models.py                  # Database models
│   ├── auth.py                    # Authentication logic
│   ├── inventory.py               # Inventory management
│   ├── reports.py                 # Reports generation
│   └── utils.py                   # Helper utilities
│
├── database/                       # Database files
│   ├── database.py                # Database connection
│   ├── schema.sql                 # Database schema
│   └── seed_data.sql              # Sample data
│
├── frontend/                       # Frontend files
│   ├── index.html                 # Landing page
│   ├── login.html                 # Login page
│   ├── dashboard.html             # Dashboard
│   ├── inventory.html             # Inventory page
│   ├── reports.html               # Reports page
│   │
│   ├── css/                       # Stylesheets
│   │   ├── style.css
│   │   ├── dashboard.css
│   │   ├── inventory.css
│   │   └── reports.css
│   │
│   └── js/                        # JavaScript files
│       ├── main.js
│       ├── auth.js
│       ├── dashboard.js
│       ├── inventory.js
│       ├── reports.js
│       └── utils.js
│
├── static/                         # Static assets
│   └── images/
│
└── tests/                          # Test files
    ├── test_backend.py
    └── test_database.py
```

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- Git
- pip (Python package manager)

### Setup Steps

1. **Clone the repository**
```bash
git clone <repository-url>
cd "Smart Inventory Management System"
```

2. **Create virtual environment**
```bash
python -m venv venv
```

3. **Activate virtual environment**
```bash
# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

4. **Install dependencies**
```bash
pip install -r requirements.txt
```

5. **Set up environment variables**
```bash
# Copy the example file
copy .env.example .env  # Windows
cp .env.example .env    # Mac/Linux

# Edit .env and add your configuration
```

6. **Initialize database**
```bash
python -c "from database.database import init_db; init_db()"
```

7. **Run the application**
```bash
python app.py
```

8. **Access the application**
- Open your browser and navigate to: `http://localhost:5000`

## 📖 Usage

### For Users

1. **Registration**: Create a new account on the registration page
2. **Login**: Login with your credentials
3. **Dashboard**: View overview of inventory statistics
4. **Manage Products**: Add, edit, or delete products from inventory
5. **Track Orders**: Create and monitor customer orders
6. **View Reports**: Generate and export various reports
7. **Manage Suppliers**: Add and manage supplier information

### For Developers

See [TEAM_ASSESSMENT.md](TEAM_ASSESSMENT.md) for detailed team assignments and development guidelines.

## 🔗 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout

### Products
- `GET /api/products` - Get all products
- `POST /api/products` - Add new product
- `GET /api/products/<id>` - Get single product
- `PUT /api/products/<id>` - Update product
- `DELETE /api/products/<id>` - Delete product

### Orders
- `GET /api/orders` - Get all orders
- `POST /api/orders` - Create new order
- `PUT /api/orders/<id>` - Update order status

### Reports
- `GET /api/reports/sales` - Sales report
- `GET /api/reports/inventory` - Inventory summary
- `GET /api/reports/dashboard` - Dashboard statistics

## 👥 Team

- **Dhanush** - Project Lead & Backend (Core & Authentication)
- **Tharun** - Backend & Database (Inventory & Products)
- **Mageswari** - Backend & Database (Reports & Analytics)
- **Indra** - Backend & Database (Orders & Suppliers)
- **Akash** - Frontend (Dashboard & Inventory UI)
- **Kazi** - Frontend (Authentication & Reports UI)
- **Punyashree** - Frontend (Orders & Suppliers UI)

See [TEAM_ASSESSMENT.md](TEAM_ASSESSMENT.md) for detailed responsibilities.

## 🧪 Testing

Run the backend tests:
```bash
pytest tests/
```

## 📝 License

This project is created for educational purposes.

## 🤝 Contributing

1. Create your feature branch (`git checkout -b feature/AmazingFeature`)
2. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
3. Push to the branch (`git push origin feature/AmazingFeature`)
4. Open a Pull Request

## 📞 Support

For support and questions, please contact the team lead.

---

**Built with ❤️ by Team Dhanush**
