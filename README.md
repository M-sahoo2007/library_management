````markdown
---
title: College Library Management System
emoji: 📚
colorFrom: blue
colorTo: purple
sdk: python
sdk_version: "3.10"
app_file: app.py
pinned: false
---

# College Library Management System

A comprehensive Flask-based library management system with role-based access control, student and admin portals, and secure authentication.

---

## 📋 Table of Contents

1. [Quick Start](#quick-start)
2. [System Overview](#system-overview)
3. [Features](#features)
4. [Installation](#installation)
5. [Configuration](#configuration)
6. [Security Architecture](#security-architecture)
7. [File Structure](#file-structure)
8. [Routes & Endpoints](#routes--endpoints)
9. [Database Schema](#database-schema)
10. [Testing Checklist](#testing-checklist)
11. [Troubleshooting](#troubleshooting)
12. [Deployment](#deployment)

---

## 🚀 Quick Start (Local Development)

### 1. Install Dependencies
```bash
pip install -r requirements.txt
````

### 2. Configure Secret Code

Edit `config.py`:

```python
ADMIN_SECRET_CODE = "ADMIN2025"  # change this
```

### 3. Run Application

```bash
python app.py
```

### 4. Access System

* Local URL: [http://localhost:5000](http://localhost:5000)
* Admin Registration: Admin → Register (secret code required)
* Student Management: Admin → Students

---

## 🌐 Hugging Face Deployment (Important)

This project is deployed on **Hugging Face Spaces**.

Key points:

* Flask runs on **port 7860**
* Host must be **0.0.0.0**
* SQLite database is **ephemeral** (resets on restart)

The app is started automatically by Hugging Face using:

```python
app.run(host="0.0.0.0", port=7860)
```

No Gunicorn is required on Hugging Face.

---

## 📊 System Overview

### Architecture

* Flask backend (app.py)
* SQLite database (auto-created)
* Jinja2 templates
* Bootstrap-based UI
* Role-based access control

### Key Components

* **Flask Application**: Routing, authentication, business logic
* **SQLite Database**: Students, admins, books, issues, reports
* **Templates**: 20+ HTML pages
* **Static Assets**: Bootstrap + custom CSS

---

## ✨ Features

### 🔐 Security

* Admin registration protected by secret code
* Student registration restricted to admin
* Password hashing using Werkzeug
* Role-based route protection
* Session-based authentication

### 📚 Core

* Student dashboard
* Book borrowing and return
* Admin book inventory management
* Issue reporting and resolution
* Audit logs for admin actions

---

## 💾 Installation

### Prerequisites

* Python 3.8+
* pip

### Setup

```bash
pip install -r requirements.txt
python app.py
```

Database (`library.db`) is auto-created on first run.

---

## ⚙️ Configuration

### Secret Code

Defined in `config.py`:

```python
ADMIN_SECRET_CODE = "YOUR_SECRET_CODE"
```

Used only for admin registration.

### Environment Notes

| Environment  | Port | Notes            |
| ------------ | ---- | ---------------- |
| Local        | 5000 | Development      |
| Hugging Face | 7860 | Production Space |

---

## 🔒 Security Architecture

* Password hashing with Werkzeug
* Session-based authentication
* Decorators for role enforcement
* Parameterized SQL queries
* No plaintext passwords stored

---

## 📁 File Structure

```
library_management/
├── app.py
├── config.py
├── requirements.txt
├── library.db        (auto-created)
├── templates/
│   ├── index.html
│   ├── student_login.html
│   ├── admin_login.html
│   └── ...
└── static/
    └── style.css
```

---

## 🔗 Routes & Endpoints

### Public

* `/`
* `/student/login`
* `/admin/login`
* `/admin/register`

### Student

* `/student/dashboard`
* `/student/books`
* `/student/borrow/<id>`
* `/student/return/<id>`
* `/student/reports`

### Admin

* `/admin/dashboard`
* `/admin/students`
* `/admin/books`
* `/admin/reports`
* `/admin/audit`

---

## 🗄️ Database Schema

Tables:

* students
* admin
* books
* book_issues
* reports
* admin_actions

All tables are auto-created on startup.

---

## ✅ Testing Checklist

* App starts without errors
* Database auto-creates
* Admin registration works
* Student login works
* Borrow / return works
* Role protection enforced

---

## 🐛 Troubleshooting

### App not starting on Hugging Face

* Ensure `README.md` contains YAML config
* Ensure `app.run(host="0.0.0.0", port=7860)`
* Check Logs tab in Space

### Missing module

```bash
pip install -r requirements.txt
```

---

## 🚀 Deployment

### Hugging Face Spaces

* Python SDK
* Auto build & run
* No Gunicorn
* Port 7860 only

### Local Production (Optional)

```bash
gunicorn app:app
```

(Not used on Hugging Face)

---

## 📝 Version History

| Version | Date       | Notes                  |
| ------- | ---------- | ---------------------- |
| 3.0     | 2025-11-11 | Admin security & audit |
| 2.0     | 2025-11-11 | Bug fixes              |
| 1.0     | 2025-11-11 | Initial release        |

---

**Status**: ✅ Deployed on Hugging Face
**Platform**: Hugging Face Spaces
**Backend**: Flask + SQLite

````

---

## ✅ FINAL STEPS (DO THIS NOW)

Run:

```bash
git add README.md
git commit -m "Fix Hugging Face README configuration"
git push hf main
````

Then:

* Open your Space
* The **Configuration error will be gone**
* Build will start automatically

---

### If the app does not turn **Running**

Open **Logs**, copy the error text, paste it here.
We are now past 90% — only small runtime fixes remain.
