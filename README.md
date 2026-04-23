# 🎓 Smart Education Tools

A full-stack educational web platform built with **Python (Flask)**, **SQLite**, and **Vanilla JavaScript** — providing separate role-based portals for students and teachers.

---

## 📌 Description

Smart Education Tools is a web application that connects students and teachers through a unified platform. Students take timed quizzes, track performance, and compete on leaderboards. Teachers create quizzes, monitor student progress, and manage records — all in real time.

---

## ✨ Features

### 👨‍🎓 Student Portal
- Timed quizzes across 8 subjects with Easy / Medium / Hard difficulty
- Streak tracking, instant feedback, and score history
- Analytics dashboard with per-subject performance breakdown
- Global leaderboard ranked by best quiz score
- Marks analyzer and Health & Wellness page

### 👩‍🏫 Teacher Portal
- Create quizzes that appear live on the student quiz page
- Per-subject student performance table with status badges
- Student records with scores, join dates, and activity status
- Quiz management — view, filter, and delete quizzes
- Platform-wide stats and leaderboard overview

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python 3.10+, Flask |
| Database | SQLite + SQLAlchemy ORM |
| Templating | Jinja2 |
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Security | Werkzeug password hashing |
| Charts | Chart.js |
| External API | OpenTDB (quiz questions) |
| Fonts | Google Fonts (Plus Jakarta Sans, Bricolage Grotesque) |

---

## 🗂️ Project Structure

```
smart-education-tools/
│
├── app.py                  # Main Flask app — all routes, models, DB logic
├── eduboard.db             # SQLite database (auto-created on first run)
├── requirements.txt        # Python dependencies
│
└── templates/
    ├── login.html          # Combined student/teacher login & signup
    ├── dashboard.html      # Student dashboard
    ├── quiz_select.html    # Quiz engine — selection, timer, results
    ├── analytics.html      # Student analytics with Chart.js
    ├── leaderboard.html    # Platform-wide leaderboard
    ├── marks_analyzer.html # Marks analysis
    ├── health.html         # Health & wellness page
    ├── teacher_dashboard.html   # Teacher overview
    ├── my_subject.html          # Per-subject student performance
    ├── quiz_management.html     # Quiz creation & management
    └── student_records.html     # Student registry
```

---

## ⚙️ Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/your-username/smart-education-tools.git
cd smart-education-tools
```

### 2. Create a virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the application
```bash
python app.py
```

### 5. Open in browser
```
http://localhost:5000
```

The database (`eduboard.db`) is created automatically on first run.

---

## 📦 Requirements

Create a `requirements.txt` with:

```
flask
flask-sqlalchemy
werkzeug
requests
```

Or generate it automatically:
```bash
pip freeze > requirements.txt
```

---

## 🔑 Usage

### Creating a Student Account
1. Go to `http://localhost:5000`
2. Select **Student** and click **Sign Up**
3. Fill in your details and register
4. You will be redirected to the student dashboard

### Creating a Teacher Account
1. Go to `http://localhost:5000`
2. Select **Teacher** and click **Sign Up**
3. Fill in your name, email, subject, and staff ID
4. You will be redirected to the teacher dashboard

### Creating a Quiz (Teacher)
1. Go to **Create Quiz** in the sidebar
2. Click **＋ Create Quiz**
3. Fill in the quiz name, subject, difficulty, and number of questions
4. Click **Create Quiz** — students will see it immediately on their quiz page

---

## 🗄️ Database Models

| Model | Description |
|-------|-------------|
| `User` | Stores both students and teachers; `role` field distinguishes them |
| `QuizAttempt` | Every quiz attempt — subject, difficulty, score, percentage, time |
| `QuizQuestion` | Individual questions and student answers per attempt |
| `TeacherQuiz` | Quizzes created by teachers; shown live to students |

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/login` | Authenticate user |
| POST | `/api/signup` | Register new user |
| POST | `/api/submit-quiz` | Save completed quiz attempt |
| GET | `/api/leaderboard` | Get top quiz scores |
| GET | `/api/user-stats` | Get current user stats |
| POST | `/api/teacher-quiz` | Create a teacher quiz |
| DELETE | `/api/teacher-quiz/<id>` | Delete a teacher quiz |
| GET | `/api/student/<id>` | Get student stats (teacher only) |

---

## 🚀 Deployment

### Deploy on Render (Recommended — Free)
1. Push your project to GitHub
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your GitHub repository
4. Set **Build Command:** `pip install -r requirements.txt`
5. Set **Start Command:** `python app.py`
6. Click **Deploy**

> **Note:** SQLite is file-based and resets on Render's free tier. For persistent data, switch to **Render PostgreSQL** (free) by updating the `SQLALCHEMY_DATABASE_URI` in `app.py`.

### Deploy on PythonAnywhere (Always-on Free)
1. Sign up at [pythonanywhere.com](https://pythonanywhere.com)
2. Upload your project files
3. Create a new web app → select Flask → point to `app.py`
4. Install requirements in the bash console

---

## 🔒 Security Notes

- Passwords are hashed using **Werkzeug's `generate_password_hash`** — never stored in plain text
- All teacher routes have server-side **role guards** — students cannot access teacher pages
- SQLAlchemy ORM **prevents SQL injection** through parameterized queries
- Change the `secret_key` in `app.py` before deploying to production:
  ```python
  app.secret_key = 'your-secure-random-key-here'
  ```

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👤 Author

**Smart Education Tools** — Built as an academic project demonstrating full-stack web development with Python Flask.
