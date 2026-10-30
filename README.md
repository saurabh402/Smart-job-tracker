# 💼 Smart Job Tracker

A full-stack, responsive job application tracking and career command center designed to streamline your job search. Features include end-to-end application lifecycle management, automated follow-up reminders, visual status & monthly pipeline analytics, CSV data exports, and an ATS-style skill-matching **Resume Analyzer**.

---

## ✨ Features

- **📊 Career Command Centre & Dashboard**
  - Real-time pipeline metrics: Total Applications, Interviews, Offers, Rejections, and Pending Follow-ups.
  - Interactive status bars with visual progress tracking.
- **📝 Job Application Management (CRUD)**
  - Track company, role, location, job type, application date, status, job URLs, and custom notes.
  - Interactive search and filter by company, role, or application status.
  - Edit or delete applications with instant database sync.
- **⏰ Tasks & Follow-up Reminders**
  - Dedicated follow-up date tracking with overdue, due today, upcoming, and completed categories.
  - Quick action to mark reminders as done or reopen them.
- **📄 AI & ATS Resume Analyzer**
  - Upload resumes in **PDF**, **DOCX**, or **TXT** format (up to 5 MB).
  - Paste any target Job Description to extract skill keywords.
  - Computes an estimated **Skill Match Score (%)**, highlights **Matched Skills**, identifies **Missing Skills**, and provides actionable tailoring suggestions.
- **📈 Pipeline Analytics**
  - Status distribution breakdowns.
  - 6-month monthly application trend charts.
  - Application-to-interview conversion funnel statistics.
- **💾 Data Portability & Fallback**
  - One-click **CSV Export** for backing up your application history.
  - Automatic migration from browser `localStorage` to PostgreSQL upon initial connection.

---

## 🛠️ Tech Stack

### **Frontend**
- **HTML5 & Vanilla CSS3**: Modern design system, responsive grid layouts, custom modal dialogs, and smooth micro-interactions.
- **JavaScript (ES6+)**: Dynamic DOM rendering, asynchronous REST API communication, and state management without external framework overhead.

### **Backend**
- **FastAPI**: High-performance Python async web framework with automatic OpenAPI documentation.
- **PostgreSQL (`psycopg` v3)**: Relational database with automatic table creation, migrations, and dictionary row mapping.
- **Document Text Extractors**:
  - `pypdf` for PDF parsing.
  - `python-docx` for Word document parsing.
- **Pydantic**: Request validation and structured data serialization.
- **python-dotenv**: Environment configuration management.

---

## 📁 Project Structure

```text
Smart-job-tracker/
│
├── backend/
│   ├── .env                 # Database credentials & configuration (ignored by git)
│   ├── .env.example         # Example environment template
│   └── main.py              # FastAPI server, endpoints, and resume analyzer logic
│
├── frontend/
│   └── index.html           # Single-page application (UI, CSS styles, & client logic)
│
├── docs/                    # Additional documentation and assets
├── .gitignore               # Git ignore rules for virtual environments & secrets
└── README.md                # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites
- **Python 3.9+** installed
- **PostgreSQL** instance (local or hosted, e.g., Neon, Supabase, ElephantSQL, or Docker)
- A modern web browser (Chrome, Firefox, Edge, Safari)

---

### 2. Backend Setup

1. **Navigate to the backend directory:**
   ```bash
   cd backend
   ```

2. **Create and activate a virtual environment:**
   - **Windows:**
     ```powershell
     python -m venv venv
     .\venv\Scripts\activate
     ```
   - **macOS / Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. **Install dependencies:**
   ```bash
   pip install fastapi uvicorn psycopg[binary] python-dotenv pydantic pypdf python-docx python-multipart
   ```

4. **Configure Environment Variables:**
   Create a `.env` file inside the `backend/` directory:
   ```env
   DATABASE_URL=postgresql://username:password@localhost:5432/job_tracker_db
   ```
   *(Note: The database tables will be created automatically when FastAPI starts.)*

5. **Start the API Server:**
   ```bash
   uvicorn main:app --reload --host 127.0.0.1 --port 8000
   ```
   - API Root: `http://127.0.0.1:8000`
   - Interactive Swagger Docs: `http://127.0.0.1:8000/docs`

---

### 3. Frontend Setup

1. The frontend is built as a lightweight single-page application.
2. Open [frontend/index.html](file:///c:/Users/Saurabh%20Kumar/OneDrive/Documents/Smart%20Job%20Tracker/frontend/index.html) directly in any web browser, or serve it using an HTTP server:
   - **Using Python:**
     ```bash
     cd frontend
     python -m http.server 3000
     ```
   - **Using VS Code Live Server extension** or opening `frontend/index.html` in your browser.
3. Access the dashboard at `http://localhost:3000` (or `http://127.0.0.1:5500` if using Live Server).

---

## 🔌 API Endpoints Summary

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | API status message |
| `GET` | `/api/health` | Health check & database connection probe |
| `GET` | `/api/applications` | Retrieve all tracked applications |
| `POST` | `/api/applications` | Create a new job application |
| `PUT` | `/api/applications/{id}` | Update an existing application |
| `DELETE` | `/api/applications/{id}` | Delete an application |
| `POST` | `/api/resume/analyze` | Parse resume (`.pdf`, `.docx`, `.txt`) against a job description |

---

## 🛡️ License

This project is licensed under the [MIT License](LICENSE) (or applicable open-source license).