# DAPMS – Digital Academic Performance Management System

A modern web-based academic management platform that helps educational institutions manage students, teachers, courses, assessments, attendance, and results efficiently.

Built with **Flask** and **SQLite**, featuring role-based access for **Admin**, **Teacher**, and **Student**.

---

## Features

### Admin
- Create and manage academic terms
- Create / bulk import students, teachers & courses (Excel support)
- Create course sections and assign teachers
- Reset passwords & handle password reset requests
- Approve and publish final results

### Teacher
- Manage assigned sections
- Enroll students
- Create, edit & delete assignments (with file upload)
- Record attendance
- Post announcements & upload course materials
- Define grading components and enter marks
- Submit results for admin approval

### Student
- View enrolled courses
- Submit assignments
- Access course materials and announcements
- Track attendance and performance
- View final results and CGPA

### Common
- Secure role-based authentication
- Profile management
- Password change & forgot password flow
- Responsive modern UI (Tailwind CSS)

---

## Tech Stack

| Layer          | Technology              |
|----------------|-------------------------|
| Backend        | Flask 3.0.3             |
| Database       | SQLite                  |
| Authentication | Werkzeug                |
| File Import    | openpyxl                |
| Frontend       | HTML + Tailwind CSS     |
| Deployment     | Docker + Gunicorn       |

---

## Project Structure

```
dapms/
├── app/
│   ├── core/           # Security helpers
│   ├── managers/       # Business logic
│   ├── models/         # Data models
│   ├── routes/         # Auth, Admin, Teacher, Student routes
│   ├── services/       # ID generation, importers, results
│   ├── static/         # Assets
│   ├── templates/      # Jinja2 templates
│   ├── uploads/        # Uploaded files
│   ├── __init__.py
│   └── db.py
├── instance/           # SQLite database
├── Dockerfile
├── requirements.txt
└── run.py
```

---

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/Razin-7478/dapms_dp_1.git
cd dapms_dp_1
```

### 2. Create virtual environment
```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the application
```bash
python run.py
```

Open → [http://127.0.0.1:5000](http://127.0.0.1:5000)

---

## Docker

```bash
docker build -t dapms .
docker run -p 8000:8000 dapms
```

---

## Demo Accounts

| Role    | Email                 | Password     |
|---------|-----------------------|--------------|
| Admin   | admin@dapms.local     | admin123     |
| Teacher | teacher@dapms.local   | teacher123   |
| Student | student@dapms.local   | student123   |

---

## Key Workflows

1. **Admin** creates term → creates courses → creates sections → assigns teachers
2. **Teacher** enrolls students → posts assignments → records attendance → enters marks → submits results
3. **Admin** reviews and publishes results
4. **Student** submits work and views published results + CGPA

---

## Contributors

- [Mohammad Razin Masud](https://github.com/Razin-7478)
- [ALI ARMAN SULAIM](https://github.com/arman-sulaiman)

---

## License

This project is available for educational and demonstration purposes.
