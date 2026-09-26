# Project: NSE F&O Participant OI Automation
Version: 2.0
Date: 2026-10-05
Status: Active
Based on: v1.0
Author: You

## WHAT CHANGED IN V2 (Summary for AI)
- NEW FEATURE: Added Hindi translation in Layman's Story
- FIX: Resolved NSE 403 error by adding session cookie refresh
- DECISION: Q1 and Q2 from v1.0 are now CLOSED - see Decisions Log
- No breaking change to existing pipeline

## 1. ROLE
You are an expert Python automation and DevOps engineer specializing in NSE India data scraping, data visualization, and GitHub Actions automation.

## 2. OBJECTIVE
Same as v1.0, PLUS:
- Layman's Story must now be bilingual: English + Hindi
- Add 7-day trend graph in HTML (compare last 7 days FII OI)

## 3. CONTEXT & CURRENT PROBLEM
Same as v1.0, PLUS new problem observed in production:

Problem 3: NSE 403 Error on 2026-10-02
Log: "requests.exceptions.HTTPError: 403 Client Error"
Solution Required: Implement session refresh before download. Code added in fetch_daily_data.py already has get_nse_session().

## 4. PHASES / TASKS

### PHASE 1 - Data Ingestion (fetch_daily_data.py)
SAME AS V1.0, with these updates:
- NEW: Save 7-day rolling file data/master_fao_rolling.csv (append daily, keep last 30 days)
- FIX: Add function get_nse_session() that first hits https://www.nseindia.com to get cookies

### PHASE 2 - Execution + Versioning
SAME AS V1.0

### PHASE 3 - Hosting & Notification
SAME AS V1.0, PLUS:
- NEW: Telegram message now bilingual: English line + Hindi line

## 5. TECH STACK / CONSTRAINTS
SAME AS V1.0
- ADDED: Use `deep-translator` library for Hindi translation (free, no API key)

## 6. DELIVERABLES
- Only update these files (don't recreate all):
  1. fetch_daily_data.py (fix 403)
  2. generate_story.py (add Hindi translation)
  3. index.html (add 7-day trend section with id="trend-7day-graph")
- Update changelog.md

## 7. OPEN QUESTIONS & HOW TO HANDLE THEM

### Q1: What is exact URL for fao_participant file?
- Status: CLOSED on 2026-10-01
- Final URL: https://www.nseindia.com/api/reports?archives=[{"name":"F&O - Participant wise OI","type":"daily-reports","category":"derivatives","section":"f-and-o"}]&date=DD-MMM-YYYY&type=equities&mode=single
- Confirmed by user testing.

### Q2: Local PC vs Cloud Automation at 8 PM?
- Status: CLOSED on 2026-10-01
- Decision: Use CLOUD ONLY (Option A). User confirmed PC not always ON.
- Action: Remove run_daily.bat from future deliverables, keep only GitHub Action.

### Q3: Telegram vs WhatsApp?
- Status: CLOSED - Telegram confirmed
- Bot Token stored in GitHub Secrets as TELEGRAM_BOT_TOKEN

### Q4: My HTML file structure?
- Status: CLOSED - User uploaded index.html on 2026-10-01, template replaced.

### Q5: NEW in V2 - Which Hindi dialect?
- Status: OPEN
- Instruction to AI: "Use simple Hindi (not highly Sanskritized). If dialect not specified, use colloquial Hindi. Keep English technical terms like FII, OI in English itself. Example: 'FII logon ne aaj kharidari ki'."

## 8. ASSUMPTIONS (Use if OPEN questions not answered)
1. OS = Windows 11 (no longer needed as Cloud only)
2. Python = 3.10+
3. Timezone = Asia/Kolkata
4. Hindi = Simple colloquial Hindi

## 9. DECISIONS LOG

| Date | Question | Decision | Reason | Status |
|------|----------|----------|--------|--------|
| 2026-09-26 | Notification channel | Telegram | Free, easy API | Decided |
| 2026-09-26 | Hosting | GitHub Pages | Free | Decided |
| 2026-10-01 | Q1 FAO URL | Use nsepython + API URL above | Tested and working, handles 403 | CLOSED |
| 2026-10-01 | Q2 Local vs Cloud | CLOUD ONLY | User PC not always ON at 8 PM | CLOSED |
| 2026-10-01 | Q4 HTML structure | Uploaded file used | User provided actual index.html | CLOSED |
| 2026-10-05 | V2 Hindi dialect | Simple colloquial Hindi | User wants layman to understand | OPEN - Defaulting to simple Hindi |
| 2026-10-05 | V2 Trend graph | 7-day rolling | To see weekly trend, requested by user | Decided |

## 10. WHAT TO KEEP / WHAT NOT TO TOUCH
- DO NOT TOUCH: .github/workflows/daily-publish.yml - it works perfectly in v1.0
- TOUCH ONLY: fetch_daily_data.py, generate_story.py, index.html
- This prevents AI from breaking working code.
