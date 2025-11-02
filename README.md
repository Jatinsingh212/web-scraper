Job Scraper ML
----------------
Personal, open‑source Flask app that scrapes LinkedIn and Indeed, enriches results with ML (salary/experience inference and GPT‑2 summaries), rotates free proxies to avoid 403s, and exports clean CSVs. Built for Indian software roles; runs locally without paid APIs.


Features
- Multi‑site: Indeed + LinkedIn (up to ~750 jobs/run).
- Anti‑block: validated free proxies, random UA/viewport, human delays, 403 retries.
- AI extras: CRNN CAPTCHA solver (.pth), GPT‑2 summarization, TF‑IDF + Linear Regression for salary/experience inference.
- Data quality: duplicate removal, accuracy metrics, skills extraction, sentiment; CSV export.
- Caching: SQLite cache (scraping_cache.db) speeds repeat searches.
- UI + API: Web form with live logs; simple POST endpoint.

API Usage
- POST /scrape_multi with fields:
  url, max_pages, sites (repeat for indeed/linkedin), search_term,
  use_keywords=1, detail_scrape=1, headless=1, use_cache=1
- GET /progress for JSON; /download/<filename> for CSV.

Output Columns
job_title | company_name | location | salary (₹X–Y LPA) | experience (X–Y years) | description (summarized) | skills | sentiment_score | posted_time | job_link | source

.gitignore (recommended)
extracted_jobs/
*.csv
*.pth
*.pkl
scraping_cache.db
__pycache__/
chromedriver*
.DS_Store

License
MIT License. Personal/educational use; respect site ToS and robots guidelines. No PII scraping.
"""
    return Response(
        content,
        mimetype='text/plain',
        headers={'Content-Disposition': 'attachment; filename=README.txt'}
    )
