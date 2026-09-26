# Prompt Changelog

This file tracks every change to your master prompt. Always add an entry when you update.

Format:
### vX.Y - YYYY-MM-DD
- Type: Added / Fixed / Changed / Removed / Decided
- What: Description
- Why: Reason
- Impact: Files affected

---

### v1.0 - 2026-09-26
- Type: Created
- What: Initial master prompt created for NSE F&O automation
- Why: First version covering HTML co-relation, data fetch, GitHub hosting, Telegram notification
- Files: index.html refactor, fetch_daily_data.py, GitHub Actions workflow
- Open Questions: Q1 FAO URL, Q2 Local vs Cloud, Q3 Telegram vs WhatsApp, Q4 HTML structure

### v2.0 - 2026-10-05 [EXAMPLE - HOW TO WRITE YOUR NEXT VERSION]
- Type: Added + Fixed + Decided
- What: 
  1. Added bilingual Layman Story (English + Hindi)
  2. Added 7-day trend graph
  3. Fixed NSE 403 error with session refresh logic
  4. Closed Q1, Q2, Q4 - moved to Decisions Log
- Why:
  1. User feedback: Hindi needed for wider audience
  2. Production bug: 403 error on 2026-10-02
  3. User confirmed: Cloud only, FAO URL working
- Impact: fetch_daily_data.py, generate_story.py, index.html updated. Workflow NOT touched.
- Decisions Closed: Q1, Q2, Q4
- New Open Question: Q5 Hindi dialect
- Lesson: Always isolate fix to only broken files to avoid regression.

### v2.1 - TEMPLATE FOR YOUR REAL UPDATE
- Type: 
- What:
- Why:
- Impact:

