# School Management System - Setup Guide

## Quick Start (For Non-Technical Users)

### Windows Users

1. **Install Node.js**
   - Go to https://nodejs.org/
   - Download the LTS version (recommended)
   - Run the installer and follow the prompts
   - Restart your computer

2. **Extract the Project**
   - Extract `school-management-system.zip` to `C:\SchoolSMS\`

3. **Start the System**
   - Double-click on `start-server.bat`
   - Wait for the message "Server running on port: 3001"
   - Open your browser and go to: http://localhost:3001

4. **Login**
   - Username: `admin`
   - Password: `admin123`

### Linux/Mac Users

1. **Install Node.js**
   ```bash
   # Ubuntu/Debian
   sudo apt update
   sudo apt install nodejs npm

   # Mac (using Homebrew)
   brew install node
   ```

2. **Extract the Project**
   ```bash
   unzip school-management-system.zip -d ~/SchoolSMS
   cd ~/SchoolSMS
   ```

3. **Make script executable and run**
   ```bash
   chmod +x start-server.sh
   ./start-server.sh
   ```

4. **Open browser and go to:** http://localhost:3001

---

## Detailed Installation

### Step 1: Install Node.js

#### Windows
1. Download from https://nodejs.org/ (LTS version)
2. Run installer
3. Verify installation:
   ```cmd
   node -v
   npm -v
   ```

#### Linux (Ubuntu/Debian)
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

#### Mac
```bash
# Using Homebrew
brew install node

# Or download from https://nodejs.org/
```

### Step 2: Setup Backend

1. Open terminal/command prompt
2. Navigate to backend folder:
   ```bash
   cd school-management-system/backend
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Initialize database:
   ```bash
   npm run init-db
   ```

   This will:
   - Create the SQLite database
   - Create all required tables
   - Create default admin user

### Step 3: Setup Frontend

1. Navigate to frontend folder:
   ```bash
   cd ../frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build for production:
   ```bash
   npm run build
   ```

### Step 4: Start the Server

#### Development Mode (for testing)
```bash
# Terminal 1 - Backend
cd backend
npm start

# Terminal 2 - Frontend
cd frontend
npm run dev
```

#### Production Mode (recommended)
```bash
cd backend
npm start
```

The server will start on http://localhost:3001

---

## First Time Setup

### 1. Login with Default Credentials
- **URL:** http://localhost:3001
- **Username:** admin
- **Password:** admin123

### 2. Change Default Password
1. Click on your name in the sidebar
2. Go to Settings
3. Change your password

### 3. Configure School Information
1. Go to Settings
2. Update:
   - School Name
   - Address
   - Phone
   - Email
   - Academic Year

### 4. Create Users
1. Go to Users (Principal only)
2. Add:
   - Accountant (for fee management)
   - Teachers (for attendance and marks)

### 5. Setup Classes
1. Go to Classes
2. Add all your classes and sections
3. Assign class teachers

### 6. Add Staff
1. Go to Staff
2. Add all teachers and staff members
3. Set their basic salaries

### 7. Add Students
1. Go to Students
2. Add students one by one
3. Or use the export/import feature for bulk addition

---

## Daily Operations

### Taking Attendance
1. Go to Attendance
2. Select Class and Date
3. Mark each student as Present/Absent/Leave/Late
4. Click "Save Attendance"

### Collecting Fees
1. Go to Fees
2. Find the student (use search or filters)
3. Click the dollar icon
4. Enter amount and payment mode
5. Print receipt

### Paying Salaries
1. Go to Payroll
2. Click "Generate Payroll" for the month
3. Review the amounts
4. Click dollar icon to pay
5. Print salary slip

### Entering Exam Marks
1. Go to Exams
2. Create a new exam
3. Click on the chart icon
4. Enter marks for each student
5. Save results

---

## Backup & Restore

### Automatic Backups
- System creates daily backups at 11:59 PM
- Backups are stored in `backend/backups/`
- Keeps last 30 backups

### Manual Backup
1. Login as Principal
2. Go to Settings
3. Click "Create Backup Now"

### Restore from Backup
**WARNING: This will overwrite current data!**

1. Stop the server
2. Copy backup file to `backend/data/school.db`
3. Restart the server

---

## Troubleshooting

### Problem: "Port already in use"
**Solution:**
1. Change port in `backend/.env`:
   ```
   PORT=3002
   ```
2. Update frontend `.env`:
   ```
   VITE_API_URL=http://localhost:3002/api
   ```

### Problem: "Cannot find module"
**Solution:**
```bash
cd backend
npm install
cd ../frontend
npm install
```

### Problem: "Database is locked"
**Solution:**
1. Stop the server
2. Wait 10 seconds
3. Start again

### Problem: "Page not loading"
**Solution:**
1. Check if server is running
2. Clear browser cache (Ctrl+Shift+R)
3. Try different browser

### Problem: "Login not working"
**Solution:**
1. Reset database:
   ```bash
   cd backend
   npm run init-db
   ```
2. Use default credentials again

---

## System Requirements

### Minimum Requirements
- **OS:** Windows 7+, Ubuntu 18.04+, Mac OS 10.14+
- **RAM:** 4GB
- **Storage:** 1GB free space
- **Browser:** Chrome, Firefox, Edge (latest)
- **Node.js:** 18.x or higher

### Recommended
- **OS:** Windows 10/11, Ubuntu 22.04+
- **RAM:** 8GB
- **Storage:** 5GB free space
- **Browser:** Chrome (latest)

---

## Security Best Practices

1. **Change default password immediately**
2. **Create separate users** for each staff member
3. **Don't share login credentials**
4. **Regular backups** to external drive
5. **Keep computer in secure location**
6. **Lock screen** when away

---

## Getting Help

### Common Questions

**Q: Can I use this on multiple computers?**
A: Yes, but each computer needs its own installation. Data won't sync between them.

**Q: Can I access this from other devices on the network?**
A: Yes, use the computer's IP address instead of localhost.

**Q: How do I update the system?**
A: Backup your data, download the new version, and replace the files.

**Q: Can I import data from Excel?**
A: Yes, use the Reports → Export/Import feature.

**Q: What if the computer crashes?**
A: Your data is safe in the backups folder. Restore from the latest backup.

---

## Contact & Support

For technical issues or feature requests, contact your system administrator.

---

**Document Version:** 1.0  
**Last Updated:** February 2025
