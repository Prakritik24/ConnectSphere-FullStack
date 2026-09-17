# ConnectSphere-FullStack
# ConnectSphere — Campus Event Management System

## Quick Start (with MySQL database)

### Prerequisites
- Node.js v18+ installed
- MySQL server running with the database already created

### 1. Configure the database connection
Open `backend/.env` and confirm these match your MySQL setup:
```
DB_HOST=localhost
DB_USER=cs_user
DB_PASSWORD=cs_pass123
DB_NAME=connectsphere
JWT_SECRET=connectsphere_secret_key_2024
PORT=3000
```

### 2. Install dependencies
```bash
cd backend
npm install
```

### 3. Start the server
```bash
npm start
```
You should see:
```
✅ Database connection verified. Tables exist.
🚀 ConnectSphere server running at http://localhost:3000
```

### 4. Open the app
Visit: **http://localhost:3000**

---

## Demo Credentials (add via Register page, or insert manually)

To add demo users directly into MySQL:
```sql
-- password for all is: password123
INSERT INTO users (id, name, email, password, role) VALUES
('u1', 'John Student',    'student@example.com',   '$2a$10$N9qo8uLOickgx2ZMRZoMyeIjZAgcfl7p92ldGxad68LDRVONgJFFC', 'student'),
('u2', 'Alice Organizer', 'organizer@example.com', '$2a$10$N9qo8uLOickgx2ZMRZoMyeIjZAgcfl7p92ldGxad68LDRVONgJFFC', 'organizer'),
('u3', 'Admin User',      'admin@example.com',     '$2a$10$N9qo8uLOickgx2ZMRZoMyeIjZAgcfl7p92ldGxad68LDRVONgJFFC', 'admin');
```

Or simply use the Register page to create new accounts — they save directly to MySQL.

---

## What gets stored in MySQL

| Action | Table |
|--------|-------|
| Register / Login | `users` |
| Create Event | `events` |
| Register for Event | `registrations` |
| Unregister from Event | `registrations` (deleted) |

---

## Troubleshooting

**"Database table check failed"** — Make sure MySQL is running and you've created the tables from the SQL setup script.

**"Access denied for user 'cs_user'"** — Re-run the GRANT statement in MySQL:
```sql
GRANT ALL PRIVILEGES ON connectsphere.* TO 'cs_user'@'localhost';
FLUSH PRIVILEGES;
```

**Port 3000 already in use** — Change `PORT=3001` in `backend/.env`.

**Frontend shows no data / works offline** — The backend is not running. Start it with `npm start` from the `backend/` folder.
