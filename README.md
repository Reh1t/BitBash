# 🧮 Job Board - Full Stack App

🚀 **Demo Video:** [Watch on Vimeo](https://vimeo.com/your-demo-link) *(replace this with your actual link)*

This is a full-stack Job Board application built with **Flask (backend)** and **React (frontend)**. It scrapes actuarial job listings from [actuarylist.com](https://www.actuarylist.com/) using **Selenium**, stores them in a **SQLite** database, and displays them in a **responsive React UI** with full CRUD functionality and search filters.

---

## 🧩 Tech Stack

- **Frontend:** React 19, Bootstrap 5
- **Backend:** Python 3.x, Flask, Flask-SQLAlchemy, REST API
- **Database:** SQLite
- **Scraping:** Selenium + ChromeDriver

---

## 📂 Project Structure

```

job-board/
├── backend/
│   ├── app/
│   ├── scrape/
│   ├── run.py
│   └── requirements.txt
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── README.md (optional)
└── README.md (you are here)

````

---

## ⚙️ Setup Instructions

### 🔧 Backend (Flask API + Scraper)

1. **Clone the repo**
```bash
git clone https://github.com/reh1t/job-board-backend.git
cd job-board-backend/backend
````

2. **Set up virtual environment**

```bash
python -m venv venv
# Activate:
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate
```

3. **Install dependencies**

```bash
pip install -r requirements.txt
```

4. **Initialize database**

```bash
python scrape/init_db.py
```

5. **Run the backend**

```bash
python run.py
```

API will run at: `http://localhost:5000`

6. **(Optional) Clear job table**

```bash
python scrape/delete_all_jobs.py
```

7. **Run the Selenium Scraper**

```bash
python scrape/scraper.py
```

> ✅ Make sure Chrome and [ChromeDriver](https://chromedriver.chromium.org/downloads) are installed.

---

### 💻 Frontend (React)

1. **Clone frontend repo**

```bash
cd ../../frontend
# or if cloning separately:
git clone https://github.com/reh1t/job-board-frontend.git
cd job-board-frontend
```

2. **Install dependencies**

```bash
npm install
# OR
yarn
```

3. **Start the React app**

```bash
npm start
```

App will run at: `http://localhost:3000`
Ensure backend is running at `http://localhost:5000`.

---

## 🔌 API Overview

**Base URL:** `http://localhost:5000`

| Endpoint     | Method | Description               |
| ------------ | ------ | ------------------------- |
| `/jobs`      | GET    | Get all jobs with filters |
| `/jobs/<id>` | GET    | Get job by ID             |
| `/jobs`      | POST   | Create a new job          |
| `/jobs/<id>` | PUT    | Update a job              |
| `/jobs/<id>` | DELETE | Delete a job              |

**Query Filters:**

* `title`, `company`, `location`, `tag`
* `job_type`: Onsite | Remote
* `date_filter`: 24h, 7d, 30d
* `sort`: posting\_date\_asc / posting\_date\_desc
* `page`: pagination page

---

## 🧪 Scraper Features

* ✅ Extracts: title, company, location, tags, date
* ✅ Deduplicates based on title + company + location
* ✅ Adds jobs to SQLite via SQLAlchemy
* ✅ Handles pagination and skips ads
* ✅ Works with popups

---

## 🖼️ Frontend Features

* 🔍 Filter by title, company, job type, date
* 🆕 Add new jobs via modal
* 📝 Edit & delete existing jobs
* 📱 Responsive UI with sticky filters
* 🗃️ Pagination (handled on frontend)
* 🛠️ Fully integrated with live backend

---

## 📌 Notes

* `.env` example for backend:

```env
FLASK_ENV=development
DATABASE_URI=sqlite:///jobs.db
```

* Update API base URL in `frontend/src/hooks/useFilters.js` if different.
* Posting date is generated automatically on new job creation.

---

## 🧠 Future Improvements

**Backend:**

* Convert relative dates (e.g., "6d ago") to ISO timestamps
* Add logging and error handling
* Export data to CSV
* Background scraping with Celery (optional)

**Frontend:**

* Tag-based filtering
* Detail view per job
* Toast notifications
* Auth panel (admin only, optional)

---

## ✍️ Author

Full-stack development, architecture & scraping by **Rehan**

---

## 📄 License

This project is open-sourced under the **MIT License**.
