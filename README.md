
# Smart Parking System Afghanistan v2.0
A complete production-ready automated vehicle plate recognition system for parking management in Afghanistan, featuring AI-powered license plate detection, OCR text recognition, ticket generation, and payment processing.

## Features

- **AI-Powered License Plate Detection**: YOLOv8 for real-time vehicle license plate detection
- **OCR Text Recognition**: EasyOCR for extracting plate numbers (supports English, Persian/Dari, Pashto)
- **Automatic Ticket Generation**: Barcode-based parking tickets with printable receipts
- **Vehicle Entry/Exit Management**: Automated gate control simulation
- **Payment Processing**: Multiple payment methods (cash, card, mobile)
- **Dashboard Analytics**: Real-time statistics and reporting
- **Admin Panel**: User management, parking rates, system logs
- **Watchlist System**: Monitor vehicles of interest with automatic alerts
- **Occupancy Tracking**: Real-time parking space monitoring
- **Event Feed**: Real-time system event streaming
- **Health Monitoring**: System health and performance metrics
- **Responsive Web Interface**: Modern UI with dark/light theme support

## Tech Stack

### Backend

- Python 3.12
- FastAPI
- SQLAlchemy ORM
- Pydantic
- Uvicorn
- MySQL 8.0

### AI/Computer Vision

- YOLOv8 (Ultralytics)
- EasyOCR
- OpenCV
- Pillow
- NumPy

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- Responsive Design

### Ticket System

- python-barcode
- Pillow

## Project Structure

```
smart-parking/
│
├── backend/
│   ├── ai/                     # AI/Computer Vision modules
│   │   ├── plate_detector.py   # YOLOv8 license plate detection
│   │   └── ocr_reader.py       # EasyOCR text recognition
│   ├── api/                    # API endpoints (empty - in main.py)
│   ├── database/               # Database configuration
│   │   └── config.py          # Connection and session management
│   ├── middleware/             # Custom middleware
│   │   └── rate_limiter.py    # Rate limiting middleware
│   ├── models/                 # Database models
│   │   └── database.py         # SQLAlchemy models
│   ├── services/               # Business logic services (empty)
│   ├── tickets/                # Ticket generation
│   │   └── ticket_generator.py # Barcode ticket generation
│   ├── static/                 # Static files (empty)
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
│   │   ├── base.css            # Base styles and variables
│   │   └── style.css           # Main stylesheet
│   ├── js/                     # JavaScript
│   │   ├── admin.js            # Admin panel logic
│   │   ├── ai-analytics.js     # AI analytics logic
│   │   ├── ai-history.js       # AI detection history
│   │   ├── common.js           # Shared utilities
│   │   ├── dashboard.js        # Dashboard logic
│   │   ├── demo.js             # Demo mode logic
│   │   ├── entry.js            # Entry logic
│   │   ├── events.js           # Event feed logic
│   │   ├── exit.js             # Exit logic
│   │   ├── health.js           # Health monitor logic
│   │   ├── login.js            # Login logic
│   │   ├── occupancy.js        # Occupancy tracking logic
│   │   ├── records.js          # Records logic
│   │   ├── reports.js          # Reports logic
│   │   └── watchlist.js        # Watchlist logic
│   ├── pages/                  # HTML pages
│   │   ├── admin.html          # Admin panel
│   │   ├── ai-analytics.html   # AI analytics dashboard
│   │   ├── ai-history.html     # AI detection history
│   │   ├── dashboard.html      # Dashboard
│   │   ├── demo.html           # Demo mode
│   │   ├── entry.html          # Vehicle entry
│   │   ├── events.html         # Event feed
│   │   ├── exit.html           # Vehicle exit
│   │   ├── health.html         # Health monitor
│   │   ├── login.html          # Login page
│   │   ├── occupancy.html      # Occupancy tracking
│   │   ├── records.html        # Parking records
│   │   ├── reports.html        # Reports
│   │   └── watchlist.html      # Watchlist
│   └── assets/                 # Frontend assets (empty)
│
├── trained_models/             # Trained AI models
│   └── best.pt                 # YOLOv8 model
├── .env                        # Environment variables (not in git)
├── .env.example               # Environment variables template
├── .gitignore                 # Git ignore rules
├── LICENSE                    # License file
├── README.md                  # This file
└── AUDIT_REPORT.md            # Enterprise audit report
```

## Installation

### Prerequisites

- Python 3.12 or higher
- MySQL 8.0 or higher
- pip (Python package manager)
- Git

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd smart-parking
```

### Step 2: Set Up Virtual Environment

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On Linux/Mac
source venv/bin/activate
```

### Step 3: Install Backend Dependencies

```bash
cd backend
pip install -r requirements.txt
```

### Step 4: Configure MySQL Database

1. Create a MySQL database:

```sql
CREATE DATABASE smart_parking;
```

1. Create a MySQL user (optional):

```sql
CREATE USER 'parking_user'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON smart_parking.* TO 'parking_user'@'localhost';
FLUSH PRIVILEGES;
```

### Step 5: Configure Environment Variables

1. Copy the example environment file:

```bash
cd ..
cp .env.example .env
```

1. Edit `.env` with your configuration:

```env
# Database Configuration
DB_HOST=localhost
DB_PORT=3306
DB_NAME=smart_parking
DB_USER=your_mysql_user
DB_PASSWORD=your_secure_password_here

# API Configuration
API_HOST=0.0.0.0
API_PORT=8000
API_DEBUG=False

# CORS Configuration (IMPORTANT: Restrict in production)
CORS_ORIGINS=http://localhost:3000,http://localhost:8000

# AI Model Configuration
YOLO_MODEL_PATH=trained_models/best.pt
USE_GPU=False
OCR_LANGUAGES=en,fa

# Security Configuration
SECRET_KEY=your_generated_secret_key_here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Default User Passwords (for initial database setup)
DEFAULT_ADMIN_PASSWORD=your_secure_admin_password_here
DEFAULT_OPERATOR_PASSWORD=your_secure_operator_password_here
```

**Important Security Notes:**
- Generate a strong SECRET_KEY using: `python -c "import secrets; print(secrets.token_urlsafe(48))"`
- Generate secure passwords using: `python -c "import secrets; print(secrets.token_urlsafe(16))"`
- Set DB_PASSWORD to a strong password
- Restrict CORS_ORIGINS to your actual frontend URLs in production

### Step 6: Initialize Database

```bash
cd backend
python -c "from database.config import init_database; init_database()"
```

Or run the initialization script:

```bash
python init_db.py
```

### Step 7: Start the Backend Server

```bash
cd backend
python main.py
```

Or using uvicorn directly:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

The API will be available at `http://localhost:8000`

### Step 8: Access the Frontend

Open your web browser and navigate to:

```
http://localhost:8000/frontend/pages/dashboard.html
```

Or serve the frontend files using a web server:

```bash
# Using Python's built-in server
cd frontend
python -m http.server 8080
```

Then access at `http://localhost:8080/pages/dashboard.html`

## API Endpoints

### Authentication

- `POST /auth/login` - Obtain a JWT access token (OAuth2 form fields: `username`, `password`)
- `GET /auth/me` - Get the current authenticated user's profile

> Default credentials are created during database initialization. Passwords are generated securely if not set via environment variables. **Change these passwords immediately after first login.**

### Admin (requires admin JWT)

- `GET|POST /admin/rates`, `DELETE /admin/rates/{id}` - Manage parking rates
- `GET|POST /admin/users`, `DELETE /admin/users/{id}` - Manage users
- `GET|DELETE /admin/logs` - View / clear system logs

### Vehicle Management

- `POST /vehicle/entry` - Process vehicle entry with image upload
- `POST /vehicle/exit` - Process vehicle exit with barcode scan
- `GET /vehicles` - Get all vehicles
- `GET /vehicles/{id}` - Get specific vehicle

### Parking Records

- `GET /records` - Get all parking records
- `GET /dashboard/stats` - Get dashboard statistics

### Reports

- `GET /reports/daily` - Get daily report
- `GET /reports/monthly` - Get monthly report

### Payments

- `POST /payment/process` - Process parking payment

### System

- `GET /` - API root
- `GET /health` - Health check endpoint

## Usage

### Vehicle Entry

1. Navigate to the Vehicle Entry page
2. Select vehicle type and gate number
3. Upload vehicle image or use live camera
4. Click "Process Entry"
5. System will:
   - Detect license plate using YOLOv8
   - Extract plate number using EasyOCR
   - Save to database
   - Generate ticket with barcode
   - Simulate gate opening

### Vehicle Exit

1. Navigate to the Vehicle Exit page
2. Scan or enter ticket barcode
3. System will:
   - Retrieve parking record
   - Calculate duration and fee
   - Display payment details
4. Process payment
5. Generate receipt
6. Simulate gate opening

### Dashboard

- View real-time statistics
- Monitor recent entries and exits
- Track revenue
- View recognition accuracy

### Reports

- Generate daily, weekly, monthly reports
- View revenue trends
- Export reports to CSV

### Admin Panel

- Manage parking rates
- Manage users and roles
- View system logs
- Configure system settings

## Training Custom YOLOv8 Model

### Prepare Dataset

1. Organize your dataset in YOLO format:

```
datasets/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
└── data.yaml
```

1. Create `data.yaml`:

```yaml
path: ../datasets
train: images/train
val: images/val
names:
  0: license_plate
```

### Train Model

```python
from backend.ai.plate_detector import PlateDetector

detector = PlateDetector()
detector.train_model(
    data_yaml='datasets/data.yaml',
    epochs=100,
    img_size=640
)
```

The trained model will be saved in `trained_models/plate_detector/`

## Configuration

### Parking Rates

Set default parking rates in the Admin Panel or directly in the database:

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

Configure supported languages in `.env`:

```env
OCR_LANGUAGES=en,fa,ps
```

Available languages:

- `en` - English
- `fa` - Persian/Farsi
- `ps` - Pashto

## Troubleshooting

### Database Connection Issues

1. Ensure MySQL is running
2. Check credentials in `.env`
3. Verify database exists

### Model Loading Issues

1. Ensure model file exists at specified path
2. Check if GPU is available (set `USE_GPU=False` if not)
3. Verify model compatibility

### OCR Not Working

1. Ensure EasyOCR is properly installed
2. Check language codes are valid
3. Verify image quality

### Frontend Not Loading

1. Ensure backend server is running
2. Check CORS configuration
3. Verify file paths are correct

## Security Considerations

### Implemented Security Measures

1. **Secure Password Generation**: Default passwords are no longer hardcoded. They are generated securely using Python's `secrets` module if not provided via environment variables.
2. **File Upload Validation**: File type and size validation implemented for image uploads (max 10MB, allowed types: JPEG, PNG).
3. **Rate Limiting**: In-memory rate limiting middleware implemented (100 requests per 60 seconds per IP).
4. **CORS Configuration**: CORS origins restricted from wildcard to specific origins (configurable via environment).
5. **Environment Variables**: All sensitive data stored in environment variables (.env is gitignored).

### Required Security Actions (Before Production)

1. **Set strong passwords** in `.env`:
   - `DB_PASSWORD` - Database password
   - `DEFAULT_ADMIN_PASSWORD` - Admin user password
   - `DEFAULT_OPERATOR_PASSWORD` - Operator user password
   - `SECRET_KEY` - JWT signing key

2. **Restrict CORS origins** to your actual frontend domain:
   ```env
   CORS_ORIGINS=https://yourdomain.com
   ```

3. **Use HTTPS** in production with a valid SSL certificate.

4. **Change default passwords** immediately after first login.

5. **Implement Redis-based rate limiting** for production (current implementation is in-memory).

6. **Regular database backups** and audit logging.

7. **Monitor system logs** for suspicious activity.

## Performance Optimization

1. **Use GPU** for YOLOv8 inference if available
2. **Implement caching** for frequently accessed data
3. **Use connection pooling** for database
4. **Optimize image sizes** before processing
5. **Implement async operations** where possible
6. **Use CDN** for static assets in production

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License.

## Support

For support and questions:

- Email: <info@smartparking.af>
- Phone: +93 700 000 000

## Acknowledgments

- YOLOv8 by Ultralytics
- EasyOCR
- FastAPI
- OpenCV
- Pillow

## Version History

- **2.0.0** - Enterprise Security Hardening (June 2026)
  - Removed hardcoded passwords
  - Implemented secure password generation
  - Added file upload validation
  - Implemented rate limiting middleware
  - Restricted CORS configuration
  - Removed Docker dependencies
  - Cleaned up dead code and unused files
  - Added comprehensive audit report

- **1.0.0** - Initial release
  - Vehicle entry/exit management
  - AI-powered license plate detection
  - OCR text recognition
  - Ticket generation
  - Payment processing
  - Dashboard and reporting
  - Admin panel



