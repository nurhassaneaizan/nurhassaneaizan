# 🏫 Visitor Management System (VMS)
> A full-stack web application built for SMK Agama Sultan Muhammad to digitally manage school visitor access.

---

## 📌 Overview

This system replaces manual paper-based visitor logbooks with a structured, role-based digital platform. Visitors can submit visitation requests online, admins can approve or reject them, and security guards can monitor status and record checkouts — all in real time.

---

## 🚀 Features

### 👤 Visitor Portal
- Self-registration and login with hashed password authentication
- Submit visitation requests targeting a specific Student ID or Staff ID
- Choose visit purpose, date, time, and optional vehicle plate number
- View all personal visit history with live approval status (Pending / Approved / Rejected)
- Update personal details or delete account

### 🛡️ Admin Portal
- Review all pending visitation requests with full visitor details
- Approve or reject each request individually
- Manage student, staff, and security guard records (full CRUD)
- Monthly analytics report — total visits, student vs staff breakdown, purpose ranking
- Printable report statement via browser print function

### 🔒 Security Guard Portal
- View all visitation requests and their verification status
- Search visitor records by IC number
- Record visitor exit times via checkout module with modal popup
- Update personal account details

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | PHP (procedural, session-based) |
| Database | MySQL (via PDO) |
| Local Server | XAMPP (Apache + MySQL) |

---

## 🗄️ Database Design

Normalised relational schema with **7 tables**:

```
visitor          — registered visitor accounts
student          — student records managed by admin
staff            — staff records managed by admin
studentvisitation — visit requests targeting a student
staffvisitation   — visit requests targeting a staff member
verification     — approval status per visit (linked by VisitID)
securityguard    — security guard accounts and shift info
admin            — admin account
```

Key design decisions:
- `verification` table links to a specific `VisitID` (not just visitor IC), allowing accurate per-visit status tracking even when a visitor has multiple visit records
- `UNION ALL` query merges both visitation tables with `LEFT JOIN` on verification to produce a unified visit history view

---

## 📐 System Design Documentation

- ✅ Context Diagram
- ✅ Level 0 Data Flow Diagram (DFD)
- ✅ Entity Relationship Diagram (ERD)
- ✅ Process Flowcharts (per role)

---

## ⚙️ Installation & Setup

> Requires XAMPP (or any Apache + PHP + MySQL environment)

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/visitor-management-system.git
   ```

2. **Move to your XAMPP web root**
   ```bash
   mv visitor-management-system/ C:/xampp/htdocs/vms/
   ```

3. **Import the database**
   - Open `phpMyAdmin` → Create a new database named `visitormanagementsystem`
   - Import the provided `vms_database.sql` file

4. **Configure database connection**
   - Open `db_connection.php`
   - Update credentials if needed (default: host `localhost`, user `root`, password empty)

5. **Run the app**
   - Start Apache and MySQL in XAMPP Control Panel
   - Open your browser and go to: `http://localhost/vms/`

---

## 👥 User Roles & Login

| Role | Login Page | Default Credentials |
|---|---|---|
| Visitor | `visitor_login.html` | Register a new account |
| Admin | `admin_login.html` | Set via phpMyAdmin |
| Security Guard | `security_login.html` | Set via Admin panel |

---

## 📸 Screenshots

> *(Add screenshots of your dashboard, status cards, and admin notifications page here)*

---

## 🧠 What I Learned

- Designing a **normalised relational database** and writing complex `UNION ALL` + `LEFT JOIN` SQL queries
- Building **multi-role authentication** using PHP sessions with separate access control per portal
- Implementing **secure password hashing** with `password_hash()` and `password_verify()`
- Structuring a full-stack project with clear separation between frontend, backend logic, and database layer
- Producing complete **system documentation** (DFD, ERD, flowcharts) before and during development

---

## 👨‍💻 Author

**Nur Hassan Bin Nor Eaizan**  
Diploma in Computer Science — Universiti Teknologi MARA (UiTM)  
📧 nurhassaneaizan@gmail.com

---

## 📄 License

This project was developed as a university assignment. Feel free to use it as a reference for learning purposes.
