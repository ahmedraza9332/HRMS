# HRMS - Human Resource Management System 💼

A comprehensive Human Resource Management System built with the PERN stack, featuring automated attendance tracking, messaging, leave management, and payroll processing.

## 📋 Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Database Configuration](#database-configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### Core HR Functions
- **👥 Employee Management**: Complete employee profiles and records
- **⏰ Attendance Tracking**: Automated daily attendance monitoring
- **💸 Payroll Management**: Automated salary calculations and processing
- **📝 Leave Management**: Leave request submission and approval workflow
- **💬 Internal Messaging**: Employee communication system
- **📊 Reporting**: Comprehensive HR analytics and reports

### Automation Features
- **🔄 Automated Attendance**: Daily attendance record generation
- **💰 Automated Payroll**: Monthly salary processing
- **⏱️ Cron Jobs**: Scheduled background tasks for HR operations
- **📈 Real-time Updates**: Live data synchronization

## 🛠️ Tech Stack

- **Frontend**: React.js
- **Backend**: Node.js + Express.js
- **Database**: PostgreSQL
- **Architecture**: PERN Stack (PostgreSQL, Express, React, Node)
- **Automation**: PostgreSQL Cron Jobs
- **Styling**: CSS/Bootstrap (assumed)

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14.0 or higher)
- **npm** (v6.0 or higher)
- **PostgreSQL** (v12.0 or higher)
- **Git**

Check your versions:
```bash
node --version
npm --version
psql --version
```

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/ahmed9332/hrms.git
cd hrms
```

### 2. Database Setup
1. **Create a new PostgreSQL database**:
   ```sql
   CREATE DATABASE hrms_db;
   ```

2. **Run DDL commands** to create tables:
   ```bash
   psql -d hrms_db -f server/creation_queries.sql
   ```

3. **Setup stored procedures** for automation:
   ```bash
   psql -d hrms_db -f server/procedures.sql
   ```

4. **Configure cron jobs** for automated tasks:
   ```bash
   psql -d hrms_db -f server/cron_setup.sql
   ```

### 3. Install Dependencies

**Backend Dependencies**:
```bash
cd server
npm install
```

**Frontend Dependencies**:
```bash
cd ../client
npm install
```

### 4. Environment Configuration

1. **Database Configuration**: Update your database credentials in `server/db.json`:
   ```json
   {
     "host": "localhost",
     "port": 5432,
     "database": "hrms_db",
     "username": "your_username",
     "password": "your_password"
   }
   ```

2. **Environment Variables** (create `.env` file in server folder):
   ```env
   PORT=5000
   DB_HOST=localhost
   DB_PORT=5432
   DB_NAME=hrms_db
   DB_USER=your_username
   DB_PASSWORD=your_password
   JWT_SECRET=your_jwt_secret
   ```

### 5. Start the Application

**Start Backend Server**:
```bash
cd server
node index
# Server runs on http://localhost:5000
```

**Start Frontend (in new terminal)**:
```bash
cd client
npm start
# Client runs on http://localhost:3000
```

## 🗄️ Database Configuration

### Local Setup
Follow the installation steps above for local PostgreSQL setup.

### Cloud Database (Recommended)
For a hassle-free setup with automated cron jobs and cloud hosting, we recommend **Supabase**:

1. **Create Account**: Visit [Supabase](https://supabase.com)
2. **Create Project**: Set up a new PostgreSQL project
3. **Import Schema**: Upload the SQL files from the `server/` folder
4. **Get Credentials**: Copy the connection details to your `db.json`
5. **Enable Extensions**: Make sure `pg_cron` extension is enabled

### Database Schema
The system includes the following main tables:
- `employees` - Employee information
- `attendance` - Daily attendance records
- `leaves` - Leave requests and approvals
- `payroll` - Salary and payment records
- `messages` - Internal messaging system

## 📖 Usage

### For Administrators
1. **Employee Management**: Add, edit, and manage employee records
2. **Attendance Monitoring**: View real-time attendance data
3. **Leave Approvals**: Process leave requests
4. **Payroll Processing**: Generate and manage salary payments

### For Employees
1. **Clock In/Out**: Mark daily attendance
2. **Leave Requests**: Submit and track leave applications
3. **Messaging**: Communicate with colleagues and management
4. **Payroll View**: Check salary slips and payment history

## 🏗️ Project Structure

```
hrms/
│
├── client/                    # React frontend
│   ├── public/
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── pages/           # Page components
│   │   ├── services/        # API services
│   │   └── styles/          # CSS files
│   └── package.json
│
├── server/                   # Node.js backend
│   ├── routes/              # API routes
│   ├── controllers/         # Business logic
│   ├── middleware/          # Custom middleware
│   ├── creation_queries.sql # Database schema
│   ├── procedures.sql       # Stored procedures
│   ├── cron_setup.sql      # Cron job configuration
│   ├── db.json             # Database config
│   ├── index.js            # Server entry point
│   └── package.json
│
└── README.md
```

## 🔧 API Endpoints

### Authentication
- `POST /api/auth/login` - User login
- `POST /api/auth/register` - User registration
- `POST /api/auth/logout` - User logout

### Employee Management
- `GET /api/employees` - Get all employees
- `POST /api/employees` - Add new employee
- `PUT /api/employees/:id` - Update employee
- `DELETE /api/employees/:id` - Delete employee

### Attendance
- `GET /api/attendance` - Get attendance records
- `POST /api/attendance/checkin` - Clock in
- `POST /api/attendance/checkout` - Clock out

### Leave Management
- `GET /api/leaves` - Get leave requests
- `POST /api/leaves` - Submit leave request
- `PUT /api/leaves/:id` - Update leave status

### Payroll
- `GET /api/payroll` - Get payroll records
- `POST /api/payroll/generate` - Generate payroll

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **Ahmed** - *Initial work* - [ahmedraza9332](https://github.com/ahmedraza9332)

## 🙏 Acknowledgments

- Built with the PERN stack
- Inspired by modern HR management needs
- Special thanks to the open-source community

---

**Note**: This HRMS system is designed for small to medium-sized organizations. For enterprise-level requirements, additional scalability considerations may be needed.
