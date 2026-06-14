<div align="center">

# 🚗 Smart Parking System Afghanistan v2.0

**AI-Powered License Plate Recognition for Modern Parking Management**

[![Python 3.12](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104-green.svg)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status: Production Ready](https://img.shields.io/badge/Status-Production%20Ready-success.svg)]()

A complete production-ready automated vehicle plate recognition system for parking management in Afghanistan, featuring AI-powered license plate detection, OCR text recognition, ticket generation, and payment processing.

[Features](#-features) • [Installation](#-installation) • [API Documentation](#-api-endpoints) • [Security](#-security-considerations) • [Contributing](#-contributing)

</div>

## ✨ Features

### Core Functionality
- 🤖 **AI-Powered License Plate Detection** - YOLOv8 for real-time vehicle license plate detection
- 🔍 **OCR Text Recognition** - EasyOCR for extracting plate numbers (supports English, Persian/Dari, Pashto)
- 🎫 **Automatic Ticket Generation** - Barcode-based parking tickets with printable receipts
- 🚗 **Vehicle Entry/Exit Management** - Automated gate control simulation
- 💳 **Payment Processing** - Multiple payment methods (cash, card, mobile)

### Advanced Features
- 📊 **Dashboard Analytics** - Real-time statistics and reporting
- 👥 **Admin Panel** - User management, parking rates, system logs
- ⚠️ **Watchlist System** - Monitor vehicles of interest with automatic alerts
- 🅿️ **Occupancy Tracking** - Real-time parking space monitoring
- 📡 **Event Feed** - Real-time system event streaming
- 🏥 **Health Monitoring** - System health and performance metrics
- 🎨 **Responsive Web Interface** - Modern UI with dark/light theme support

## 🛠 Tech Stack

### Backend
[![Python](https://img.shields.io/badge/Python-3.12-blue)](https://www.python.org/) [![FastAPI](https://img.shields.io/badge/FastAPI-0.104-green)](https://fastapi.tiangolo.com/) [![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0-red)](https://www.sqlalchemy.org/) [![MySQL](https://img.shields.io/badge/MySQL-8.0-orange)](https://www.mysql.com/)

- Python 3.12
- FastAPI
- SQLAlchemy ORM
- Pydantic
- Uvicorn
- MySQL 8.0

### AI/Computer Vision
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-purple)](https://github.com/ultralytics/ultralytics) [![EasyOCR](https://img.shields.io/badge/EasyOCR-latest-blue)](https://github.com/JaidedAI/EasyOCR) [![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)](https://opencv.org/)

- YOLOv8 (Ultralytics)
- EasyOCR
- OpenCV
- Pillow
- NumPy

### Frontend
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5)](https://developer.mozilla.org/en-US/docs/Web/HTML) [![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3)](https://developer.mozilla.org/en-US/docs/Web/CSS) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

- HTML5
- CSS3
- Vanilla JavaScript
- Responsive Design

### Ticket System
[![python-barcode](https://img.shields.io/badge/python--barcode-latest-blue)](https://github.com/WhyNotHugo/python-barcode) [![Pillow](https://img.shields.io/badge/Pillow-10.x-blue)](https://python-pillow.org/)

- python-barcode
- Pillow

---

## 📁 Project Structure

```
smart-parking/
│
├── backend/
│   ├── ai/                     # AI/Computer Vision modules
│   │   ├── plate_detector.py   # YOLOv8 license plate detection
│   │   └── ocr_reader.py       # EasyOCR text recognition
│   ├── database/               # Database configuration
│   │   └── config.py          # Connection and session management
│   ├── middleware/             # Custom middleware
│   │   └── rate_limiter.py    # Rate limiting middleware
│   ├── models/                 # Database models
│   │   └── database.py         # SQLAlchemy models
│   ├── tickets/                # Ticket generation
│   │   └── ticket_generator.py # Barcode ticket generation
│   ├── uploads/                # Uploaded images
│   │   ├── vehicles/           # Vehicle images
│   │   ├── plates/             # License plate images
│   │   └── tickets/            # Generated tickets
│   ├── auth.py                 # Authentication utilities
│   ├── init_db.py              # Database initialization
│   ├── main.py                 # FastAPI application
│   └── requirements.txt        # Python dependencies
│
├── frontend/
│   ├── css/                    # Stylesheets
│   ├── js/                     # JavaScript modules
│   └── pages/                  # HTML pages
│
├── trained_models/             # Trained AI models
│   └── best.pt                 # YOLOv8 model
├── .env.example               # Environment variables template
├── .gitignore                 # Git ignore rules
├── LICENSE                    # MIT License
├── README.md                  # This file
└── AUDIT_REPORT.md            # Enterprise audit report
```

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [API Documentation](#-api-endpoints)
- [Usage](#-usage)
- [Configuration](#-configuration)
- [Security](#-security-considerations)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🚀 Installation

### Prerequisites

| Requirement | Version | Notes |
|-------------|---------|-------|
| Python | 3.12+ | [Download](https://www.python.org/downloads/) |
| MySQL | 8.0+ | [Download](https://dev.mysql.com/downloads/mysql/) |
| pip | Latest | Included with Python |
| Git | Latest | [Download](https://git-scm.com/downloads) |

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/smart-parking-afghanistan.git
cd smart-parking-afghanistan
```

### Step 2: Set Up Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate on Windows
venv\Scripts\activate

# Activate on Linux/Mac
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
cd backend
pip install -r requirements.txt
```

### Step 4: Configure Database

```sql
-- Create database
CREATE DATABASE smart_parking;

-- Create user (optional)
CREATE USER 'parking_user'@'localhost' IDENTIFIED BY 'your_secure_password';
GRANT ALL PRIVILEGES ON smart_parking.* TO 'parking_user'@'localhost';
FLUSH PRIVILEGES;
```

### Step 5: Environment Configuration

```bash
# Copy example environment file
cd ..
cp .env.example .env

# Edit .env with your configuration
```

**Required Environment Variables:**

```env
# Database
DB_HOST=localhost
DB_PORT=3306
DB_NAME=smart_parking
DB_USER=your_mysql_user
DB_PASSWORD=your_secure_password

# Security (IMPORTANT: Generate strong values!)
SECRET_KEY=your_generated_secret_key_here
DEFAULT_ADMIN_PASSWORD=your_secure_admin_password_here
DEFAULT_OPERATOR_PASSWORD=your_secure_operator_password_here

# CORS (IMPORTANT: Restrict in production)
CORS_ORIGINS=http://localhost:3000,http://localhost:8000
```

> ⚠️ **Security Warning**: Generate strong secrets using:
> ```bash
> python -c "import secrets; print(secrets.token_urlsafe(48))"  # For SECRET_KEY
> python -c "import secrets; print(secrets.token_urlsafe(16))"  # For passwords
> ```

### Step 6: Initialize Database

```bash
cd backend
python init_db.py
```

### Step 7: Start the Server

```bash
# Development mode with auto-reload
python main.py

# Or using uvicorn
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

The API will be available at `http://localhost:8000`

---

## ⚡ Quick Start

After installation, access the application:

1. **Dashboard**: `http://localhost:8000/frontend/pages/dashboard.html`
2. **Vehicle Entry**: `http://localhost:8000/frontend/pages/entry.html`
3. **Vehicle Exit**: `http://localhost:8000/frontend/pages/exit.html`
4. **Admin Panel**: `http://localhost:8000/frontend/pages/admin.html`

**Default Login**: Use credentials generated during database initialization (check logs)

## 📚 API Documentation

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/login` | Obtain JWT access token |
| GET | `/auth/me` | Get current user profile |

> 💡 **Note**: Default credentials are generated during database initialization. Check logs for generated passwords.

### Admin Endpoints (Requires Admin JWT)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/admin/rates` | List parking rates |
| POST | `/admin/rates` | Create parking rate |
| DELETE | `/admin/rates/{id}` | Delete parking rate |
| GET | `/admin/users` | List users |
| POST | `/admin/users` | Create user |
| DELETE | `/admin/users/{id}` | Delete user |
| GET | `/admin/logs` | View system logs |
| DELETE | `/admin/logs` | Clear system logs |

### Vehicle Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/vehicle/entry` | Process vehicle entry |
| POST | `/vehicle/exit` | Process vehicle exit |
| GET | `/vehicles` | List all vehicles |
| GET | `/vehicles/{id}` | Get vehicle details |

### Parking Records

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/records` | List parking records |
| GET | `/dashboard/stats` | Get dashboard statistics |

### Reports

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/reports/daily` | Daily report |
| GET | `/reports/monthly` | Monthly report |

### Payments

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/payment/process` | Process payment |

### System

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API root |
| GET | `/health` | Health check |
| GET | `/health/monitor` | System health metrics |
| GET | `/health/history` | Health history |

---

## 📖 Usage

### Vehicle Entry Workflow

1. Navigate to **Vehicle Entry** page
2. Select vehicle type and gate number
3. Upload vehicle image or use live camera
4. Click **"Process Entry"**
5. System automatically:
   - 🤖 Detects license plate using YOLOv8
   - 🔍 Extracts plate number using EasyOCR
   - 💾 Saves to database
   - 🎫 Generates ticket with barcode
   - 🚪 Simulates gate opening

### Vehicle Exit Workflow

1. Navigate to **Vehicle Exit** page
2. Scan or enter ticket barcode
3. System retrieves parking record
4. Review duration and fee
5. Process payment
6. Generate receipt
7. Gate opens automatically

### Dashboard Features

- 📊 Real-time statistics
- 🚗 Recent entries/exits monitoring
- 💰 Revenue tracking
- 🎯 Recognition accuracy metrics

### Reports

- 📅 Daily, weekly, monthly reports
- 📈 Revenue trend analysis
- 📄 CSV export capability

### Admin Panel

- 💵 Manage parking rates
- 👤 Manage users and roles
- 📋 View system logs
- ⚙️ Configure system settings

## ⚙️ Configuration

### Parking Rates

Set default parking rates via Admin Panel or directly:

```python
from backend.models.database import ParkingRate, VehicleType
from backend.database.config import get_db_context

with get_db_context() as db:
    rate = ParkingRate(
        vehicle_type=VehicleType.CAR,
        hourly_rate=10.0,
        daily_rate=50.0
    )
    db.add(rate)
    db.commit()
```

### OCR Languages

Configure in `.env`:

```env
OCR_LANGUAGES=en,fa,ps
```

**Available Languages:**
- `en` - English
- `fa` - Persian/Farsi
- `ps` - Pashto

---

## 🔒 Security Considerations

### ✅ Implemented Security Measures

| Measure | Status | Description |
|---------|--------|-------------|
| Secure Password Generation | ✅ | Uses `secrets` module for password generation |
| File Upload Validation | ✅ | Type and size validation (max 10MB) |
| Rate Limiting | ✅ | 100 requests/60s per IP |
| CORS Configuration | ✅ | Restricted to specific origins |
| Environment Variables | ✅ | All secrets in `.env` (gitignored) |

### ⚠️ Required Actions Before Production

1. **Set Strong Passwords** in `.env`:
   ```env
   DB_PASSWORD=your_strong_password
   DEFAULT_ADMIN_PASSWORD=your_strong_password
   DEFAULT_OPERATOR_PASSWORD=your_strong_password
   SECRET_KEY=your_strong_secret_key
   ```

2. **Restrict CORS Origins**:
   ```env
   CORS_ORIGINS=https://yourdomain.com
   ```

3. **Enable HTTPS** with valid SSL certificate

4. **Change default passwords** after first login

5. **Implement Redis-based rate limiting** for production

6. **Regular database backups** and audit logging

7. **Monitor system logs** for suspicious activity

> 📖 See [AUDIT_REPORT.md](AUDIT_REPORT.md) for detailed security analysis.

---

## 🔧 Troubleshooting

### Database Connection Issues

**Problem**: Cannot connect to MySQL

**Solutions**:
- ✅ Ensure MySQL is running
- ✅ Check credentials in `.env`
- ✅ Verify database exists
- ✅ Check firewall settings

### Model Loading Issues

**Problem**: YOLOv8 model fails to load

**Solutions**:
- ✅ Ensure model file exists at `trained_models/best.pt`
- ✅ Set `USE_GPU=False` if no GPU available
- ✅ Verify model compatibility

### OCR Not Working

**Problem**: EasyOCR fails to extract text

**Solutions**:
- ✅ Ensure EasyOCR is properly installed
- ✅ Check language codes are valid
- ✅ Verify image quality and lighting

### Frontend Not Loading

**Problem**: Web interface not accessible

**Solutions**:
- ✅ Ensure backend server is running
- ✅ Check CORS configuration
- ✅ Verify file paths are correct
- ✅ Check browser console for errors

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

**Development Guidelines:**
- Follow PEP 8 for Python code
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 Support

For support and questions:

- 📧 Email: [info@smartparking.af](mailto:info@smartparking.af)
- 📱 Phone: +93 700 000 000
- 🐛 Issues: [GitHub Issues](https://github.com/yourusername/smart-parking-afghanistan/issues)

---

## 🙏 Acknowledgments

Special thanks to:

- [YOLOv8](https://github.com/ultralytics/ultralytics) by Ultralytics
- [EasyOCR](https://github.com/JaidedAI/EasyOCR)
- [FastAPI](https://fastapi.tiangolo.com/)
- [OpenCV](https://opencv.org/)
- [Pillow](https://python-pillow.org/)

---

## 📜 Version History

### [2.0.0] - June 2026

**Security Hardening Release**
- ✅ Removed hardcoded passwords
- ✅ Implemented secure password generation
- ✅ Added file upload validation
- ✅ Implemented rate limiting middleware
- ✅ Restricted CORS configuration
- ✅ Removed Docker dependencies
- ✅ Cleaned up dead code and unused files
- ✅ Added comprehensive audit report

### [1.0.0] - Initial Release

**Core Features**
- Vehicle entry/exit management
- AI-powered license plate detection
- OCR text recognition
- Ticket generation
- Payment processing
- Dashboard and reporting
- Admin panel

---

<div align="center">

**Made with ❤️ for Afghanistan**

[⬆ Back to Top](#-smart-parking-system-afghanistan-v20)

</div>



