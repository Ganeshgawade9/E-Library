# E-Library
The E-Library Management System is a full-stack web application built with Python and Django that digitizes traditional library operations. It allows users to browse, search, borrow, and read books online, while administrators can manage the entire catalog, users, and transactions from a central dashboard.


# 📚 E-Library Management System
> Built with Python & Django | Full Stack Project

---

## 🚀 Features
- ✅ User Registration & Login
- ✅ Browse & Search Books (by title, author, category)
- ✅ Borrow & Return Books
- ✅ Due Date Tracking & Fine Calculation (₹5/day)
- ✅ Admin: Add / Edit / Delete Books
- ✅ Admin: Upload Cover Image & PDF
- ✅ Admin Dashboard with Borrow Records
- ✅ User Dashboard with Borrow History

---

## 🛠️ Tech Stack
| Layer | Technology |
|-------|-----------|
| Language | Python 3.x |
| Framework | Django 4.x |
| Database | SQLite (default) / MySQL / PostgreSQL |
| Frontend | HTML, CSS, Bootstrap 5 |
| File Storage | Django Media Files |

---

## ⚙️ Setup Instructions

### Step 1 — Clone / Download the Project
```bash
cd Desktop
# Place the elibrary_project folder here
```

### Step 2 — Create Virtual Environment
```bash
python -m venv venv
```

### Step 3 — Activate Virtual Environment
```bash
# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### Step 4 — Install Requirements
```bash
pip install -r requirements.txt
```

### Step 5 — Run Migrations
```bash
cd elibrary_project
python manage.py makemigrations
python manage.py migrate
```

### Step 6 — Create Admin (Superuser)
```bash
python manage.py createsuperuser
# Enter: username, email, password
```

### Step 7 — Run Server
```bash
python manage.py runserver
```

### Step 8 — Open in Browser
```
http://127.0.0.1:8000/          ← Home Page
http://127.0.0.1:8000/admin/    ← Django Admin
http://127.0.0.1:8000/admin-panel/ ← Custom Admin Panel
```

---

## 📁 Project Structure
```
elibrary_project/
├── manage.py
├── requirements.txt
├── elibrary/
│   ├── settings.py
│   ├── urls.py
├── books/
│   ├── models.py       → Book, Category, BorrowRecord
│   ├── views.py        → All book & admin views
│   ├── forms.py        → BookForm
│   ├── urls.py
│   ├── admin.py
│   └── templates/books/
│       ├── home.html
│       ├── book_list.html
│       ├── book_detail.html
│       ├── add_book.html
│       └── admin_dashboard.html
├── users/
│   ├── models.py       → CustomUser
│   ├── views.py        → Login, Register, Dashboard
│   ├── forms.py        → RegisterForm
│   ├── urls.py
│   └── templates/users/
│       ├── login.html
│       ├── register.html
│       └── dashboard.html
├── templates/
│   └── base.html
├── static/
│   └── css/
└── media/
    ├── book_covers/
    └── book_pdfs/
```

---

## 🗄️ Database Models

### Book
| Field | Type |
|-------|------|
| title | CharField |
| author | CharField |
| category | ForeignKey |
| description | TextField |
| cover_image | ImageField |
| pdf_file | FileField |
| available_copies | IntegerField |

### BorrowRecord
| Field | Type |
|-------|------|
| user | ForeignKey |
| book | ForeignKey |
| borrow_date | DateField |
| due_date | DateField |
| return_date | DateField |
| status | CharField |
| fine | DecimalField |

---

## 👤 User Roles
| Role | Access |
|------|--------|
| Guest | View books only |
| Registered User | Borrow/Return books, view dashboard |
| Admin/Staff | Add/Edit/Delete books, view all records |

---

## 📌 To Use MySQL Instead of SQLite
In `settings.py`, replace DATABASES with:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'elibrary_db',
        'USER': 'root',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```
Then install: `pip install mysqlclient`

---

**Made with ❤️ using Python & Django**
