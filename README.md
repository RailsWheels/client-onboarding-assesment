# 🧑‍💻 Intern Task: Client Onboarding System (Foundational App)

Welcome to your first official task as an intern!

Your mission is to build the **foundation of a Client Onboarding System** for our future SaaS-based software product. This system will eventually grow into a full-featured client/invoice/payment management tool. Your job is to design a well-structured, modular backend that we can build on top of.

---

## 🚀 Task Overview

You will build a **Client Onboarding System** that includes:

1. **User Authentication (Login/Logout)**
2. **Client Management**
3. **Status Tracking**
4. **Database Integration with MySQL**
5. *(Optional)* HTML report for viewing client list

You are allowed to choose between **FastAPI** or **Django** as your web framework.

---

## 🛠️ Tech Stack Options

You can choose one of the following frameworks based on your comfort level:

### Option 1: FastAPI (Recommended if you're new to frameworks)
- Lightweight and modern
- Great for building APIs quickly
- Clean structure and auto-generated docs
- You can optionally add a simple HTML view using `Jinja2` or generate a static HTML file

### Option 2: Django
- Full-stack framework with built-in admin panel and authentication
- Can build both frontend + backend together
- More features out-of-the-box

Use **MySQL** as the database with either framework.

---

## 📂 Functional Requirements

### 🔐 User Authentication
- Secure login/logout functionality
- Passwords must be hashed
- Optional: Roles like `admin` and `employee`

### 👥 Client Onboarding
- Logged-in users can:
  - Add new clients
  - View client list
  - Update client status
- Client data is stored in a MySQL database

### 📈 Status Tracking
Client onboarding status can be:
- `Pending`
- `In Progress`
- `Completed`
- `On Hold`
- `Cancelled`

### 🧾 (Optional Bonus) HTML Report
Generate a `report.html` file or endpoint that shows the current list of clients with their statuses.

---

## 🗃️ Database Schema (MySQL)

### `users` table
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    role ENUM('admin', 'employee') DEFAULT 'employee',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
### `clients` table
```sql
CREATE TABLE clients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(20),
    company VARCHAR(100),
    onboarding_date DATE,
    status ENUM('Pending', 'In Progress', 'Completed', 'On Hold', 'Cancelled') DEFAULT 'Pending',
    services_required TEXT,
    created_by INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (created_by) REFERENCES users(id)
);
```

## 📊 Evaluation Criteria

Your work will be reviewed based on the following key areas:

| Category | Description | Weight |
|----------|-------------|--------|
| 📦 **Code Structure & Modularity** | Proper separation of concerns (auth, DB, routes, etc.). Reusable and clean functions. | 20% |
| 🔐 **Authentication Logic** | Secure login/logout, hashed passwords, proper user session/token handling. | 20% |
| 🗃️ **MySQL Integration & Schema Usage** | Correct usage of MySQL tables, constraints, and schema design based on given structure. | 20% |
| 👥 **Client Onboarding Features** | Ability to create, view, and update client details with status tracking. | 20% |
| 🧾 **HTML Report (Optional Bonus)** | Static or dynamic HTML report of clients with basic styling and filtering. | 10% |
| 📘 **Git Usage, README & Clean Code** | Descriptive README, good Git commit practices, clear file naming and documentation. | 10% |

### 💡 Bonus points for:
- Using environment variables for DB credentials
- Clean exception handling
- Future-readiness (extensible invoice/payment support)

---

## 📝 Submission Instructions

Please follow the steps below to submit your task:

1. **Create a GitHub Repository**  
   - Use a clear name like `client-onboarding-system`  
   - Initialize with a `README.md` and push regularly with meaningful commit messages

2. **Include the Following in Your Repo**:
   - All source code
   - A `README.md` with:
     - Setup instructions
     - How to run the app
     - Sample test login credentials (optional)
   - A `schema.sql` or SQL dump file to set up the MySQL database
   - `requirements.txt` listing all dependencies

3. **Optional (Bonus)**  
   - A `report.html` file or `/report` route showing the client list  
   - Screenshots or GIF of the working system

4. **Share the GitHub Repository Link**  
   Send the public repo link to your manager or mentor for review.

---

### 📌 Deadline

Please complete and submit this task within **3 days** from the day it was assigned. Let us know if you need an extension — communication is key.

---

We look forward to seeing how you approach this challenge! Build it like it's going into production 🚀
