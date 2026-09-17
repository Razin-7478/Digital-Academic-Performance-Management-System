# DAPMS – Digital Academic Performance Management System

**DAPMS** is a web-based academic management platform built with **Flask** and **SQLite**. It helps educational institutions manage courses, students, teachers, sections, assessments, attendance, materials, grading, and results with role-based access for Admins, Teachers, and Students.

## Features

### Admin
- Create and manage academic terms (semesters)
- Create / bulk-import students, teachers, and courses (Excel via openpyxl)
- Create course sections and assign teachers
- View students, teachers, and sections
- Reset user passwords and handle password-reset requests
- Approve and publish section results

### Teacher
- View assigned sections (current + archived)
- Enroll students by Student ID
- Create/edit/delete assignments (with optional file upload)
- Record and view attendance
- Post announcements and upload course materials
- Define grading components and enter marks
- Submit final results for admin approval
- Attendance reports

### Student
- View enrolled courses (current + archived)
- Submit assignments (with optional file + notes)
- View course materials, announcements, and attendance
- Check performance and final results (with CGPA)

### Common
- Role-based authentication
- Profile management and password change
- Forgot-password request flow
- File uploads for assignments and materials
- Modern responsive UI (Tailwind CSS)

## Tech Stack

| Component       | Technology          |
|----------------|---------------------|
| Backend        | Flask 3.0.3         |
| Database       | SQLite              |
| Auth / Security| Werkzeug            |
| Excel Import   | openpyxl            |
| Frontend       | HTML + Tailwind CSS |
| Deployment     | Docker + Gunicorn   |

## Project Structure

```
dapms_dp_1/
├── app/
│   ├── core/           # Security helpers
│   ├── managers/       # Business logic (Admin, Teacher, Student, Auth)
│   ├── models/         # Data models
│   ├── routes/         # Blueprints (auth, admin, teacher, student)
│   ├── services/       # ID generation, importers, results
│   ├── static/         # CSS, images, logo
│   ├── templates/      # Jinja2 templates
│   ├── uploads/        # Uploaded files
│   ├── __init__.py     # App factory
│   └── db.py           # Database setup & seeding
├── instance/           # SQLite database (created at runtime)
├── Dockerfile
├── requirements.txt
├── run.py
└── Password.txt
```

## Installation & Running Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/arman-sulaiman/dapms_dp_1.git
   cd dapms_dp_1
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**
   ```bash
   python run.py
   ```
   The app starts at `http://127.0.0.1:5000` (debug mode enabled).

## Docker

```bash
docker build -t dapms .
docker run -p 8000:8000 dapms
```
Access the app at `http://localhost:8000`.

## Default Demo Accounts

These accounts are automatically seeded on first run:

| Role    | Email                 | Password     |
|---------|-----------------------|--------------|
| Admin   | admin@dapms.local     | admin123     |
| Teacher | teacher@dapms.local   | teacher123   |
| Student | student@dapms.local   | student123   |

> **Note:** The `Password.txt` file in the repo may show different passwords. The actual seeded passwords are the ones listed above.

## Database

- SQLite database is automatically created at `instance/dapms.sqlite3` on first run.
- Tables, relationships, and seed data (demo users, one term, one course, one section) are handled by `app/db.py`.

## Key Workflows

1. **Admin** creates a term → creates courses → creates sections and assigns teachers → imports/creates students.
2. **Teacher** enrolls students → posts assignments/materials → records attendance → enters marks → submits results.
3. **Admin** reviews and approves results.
4. **Student** views courses, submits work, and checks published results/CGPA.

## License

This project is provided as-is for educational and demonstration purposes.
