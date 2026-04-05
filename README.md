# Business-Intelligence-Monitor
A Flask app that scrapes competitor prices, currency rates &amp; news headlines on a schedule, stores data in MySQL, and delivers a live dashboard with automated email alerts. Built with BeautifulSoup, APScheduler &amp; Chart.js.

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
