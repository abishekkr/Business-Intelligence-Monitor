# Business Intelligence Monitor

A Flask app that scrapes competitor prices, currency rates & news headlines on a schedule, stores data in MySQL, and delivers a live dashboard with automated email alerts. Built with BeautifulSoup, APScheduler & Chart.js.

---

## Project Architecture

```
bi_monitor/
│
├── app.py                  # Flask app entry point
│
├── scrapers/
│   ├── news_scraper.py     # Scrapes news headlines by keyword
│   ├── price_monitor.py    # Tracks product prices
│   ├── rates_fetcher.py    # Fetches USD/INR, GBP/INR rates
│   └── stock_tracker.py    # Pulls stock data via yfinance
│
├── scheduler/
│   └── jobs.py             # APScheduler — runs scrapers every N mins
│
├── database/
│   ├── models.py           # Table definitions (MySQL)
│   └── db.py               # DB connection handler
│
├── api/
│   ├── routes.py           # Flask REST endpoints
│   └── alerts.py           # Price/rate threshold logic
│
├── reports/
│   └── email_report.py     # Builds & sends daily HTML email
│
├── templates/
│   └── dashboard.html      # Main UI (Chart.js graphs)
│
├── static/
│   └── style.css
│
├── config.py               # API keys, email creds, thresholds
└── requirements.txt
```

---

## System Requirements

Make sure the following are installed on your machine before setup:

| Tool | Version | Notes |
|------|---------|-------|
| Python | 3.10+ | [python.org](https://python.org) — check "Add to PATH" |
| MySQL | 8.0+ | [mysql.com](https://mysql.com) — also install MySQL Workbench |
| pip | Latest | Comes with Python |
| Git | Any | [git-scm.com](https://git-scm.com) |

---

## Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/your-username/business-intelligence-monitor.git
cd business-intelligence-monitor
```

**2. Create and activate a virtual environment**
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Configure environment variables**

Create a `.env` file in the root directory:
```env
# Database
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=bi_monitor

# Email
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your@gmail.com
EMAIL_PASSWORD=your_app_password

# Alert thresholds
PRICE_DROP_THRESHOLD=5
RATE_ALERT_THRESHOLD=0.5
```

**5. Set up the MySQL database**
```bash
mysql -u root -p
CREATE DATABASE bi_monitor;
```

**6. Run the app**
```bash
python app.py
```

Visit `http://localhost:5000` to open the dashboard.

---

## Libraries & Tools

### Web Framework
- **Flask** — Core web framework for routing, REST API, and serving the dashboard

### Scraping & Data Collection
- **BeautifulSoup4** — Parses HTML to extract news headlines and product prices
- **Requests** — Handles HTTP calls to websites and currency APIs
- **requests-cache** — Caches API responses to avoid redundant calls
- **yfinance** — Fetches stock market data from Yahoo Finance
- **lxml** — Fast HTML/XML parser used with BeautifulSoup and XPath

### Scheduling
- **APScheduler** — Runs scrapers automatically in the background at set intervals

### Database
- **MySQL Connector Python** — Connects Flask to the MySQL database
- **SQLAlchemy** — ORM for defining and querying database models cleanly

### Data & Visualisation
- **Pandas** — Cleans and structures scraped data before storing
- **Chart.js** *(frontend)* — Renders live charts on the dashboard

### Reporting & Alerts
- **smtplib** *(built-in)* — Sends automated daily HTML email reports
- **Jinja2** — Templates the HTML email content (comes with Flask)

### Configuration & Utilities
- **python-dotenv** — Loads API keys and credentials from a `.env` file
- **logging** *(built-in)* — Tracks scraper runs, errors, and alert triggers

---

## Author

**Abishek KR** — Python Developer  
[abishekramlingam@gmail.com](mailto:abishekramlingam@gmail.com)
