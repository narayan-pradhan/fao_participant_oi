# Project: NSE F&O Participant OI Automation
Version: 1.0
Date: 2026-09-26
Status: Active
Author: You

## 1. ROLE
You are an expert Python automation and DevOps engineer specializing in NSE India data scraping, data visualization, and GitHub Actions automation.

## 2. OBJECTIVE
Build a 100% fully automated, zero manual intervention pipeline that:
- Daily downloads NSE F&O Participant OI data and Nifty 50 closing price
- Updates a self-contained HTML dashboard/documentation
- Publishes it to GitHub Pages with a Telegram notification link

Goal: No manual steps after initial setup.

## 3. CONTEXT & CURRENT PROBLEM
Current file: `index.html` - A static documentation/dashboard file.

Problem 1: Poor Co-relation
While reading documentation, user cannot co-relate explanation text with the corresponding graph or data table.

Solution Required:
- Refactor HTML to add clear anchor links, references, and interactivity.
- Every graph/table must have a unique ID (e.g., id="fii-long-graph").
- Every doc paragraph must link to its graph using <a href="#id">.
- On hover/click, highlight linked graph/table (CSS + minimal JS).
- Add tooltips.

Problem 2: Missing Layman Summary
At the end, add section: "Layman's Story: What Happened Today in the Market?"
- Auto-generated via Python based on today's data.
- Simple English, story-like, no jargon.

## 4. PHASES / TASKS

### PHASE 1 - Data Ingestion (fetch_daily_data.py)
- Download fao_participant_oi for CURRENT DAY from NSE. Save to data/fao/YYYY-MM-DD.csv
- Fetch Nifty 50 close. Save to data/nifty/YYYY-MM-DD.json
- Handle weekends/holidays gracefully.

### PHASE 2 - Execution + Versioning (Daily 8 PM IST)
- git pull -> python fetch_daily_data.py -> update HTML -> git push
- Provide Option A (Cloud GitHub Action - Recommended) and Option B (Local Windows Task Scheduler)

### PHASE 3 - Hosting & Notification
- GitHub Pages hosting
- Telegram notification with link after push

## 5. TECH STACK / CONSTRAINTS
- MUST USE: Python 3.10+, requests, pandas, nsepython, GitHub Actions
- MUST NOT: Hardcode dates, manual steps, paid APIs
- HTML must be single file, mobile responsive

## 6. DELIVERABLES
1. Refactored index.html
2. fetch_daily_data.py
3. generate_story.py
4. requirements.txt
5. .github/workflows/daily-publish.yml
6. setup_guide.md
7. run_daily.bat

## 7. OPEN QUESTIONS & HOW TO HANDLE THEM (QAD PATTERN)

### Q1: What is exact URL for fao_participant file?
- Status: OPEN
- Impact: High
- Instruction to AI: "If URL not confirmed, implement using `nsepython` as primary and requests with NSE headers as fallback. Keep URL as config variable NSE_FAO_URL at top of file for easy change. Do NOT hardcode inside logic."

### Q2: Local PC vs Cloud Automation at 8 PM?
- Status: OPEN
- Instruction to AI: "Implement BOTH. Option A (Cloud): .github/workflows/daily-publish.yml as default. Option B (Local): run_daily.bat + guide as optional."

### Q3: Telegram vs WhatsApp?
- Status: OPEN
- Instruction to AI: "Implement Telegram by default. Keep WhatsApp code commented as TODO."

### Q4: My HTML file structure?
- Status: OPEN
- Instruction to AI: "Create template index.html with dummy IDs and linking logic. Add comment `<!-- TODO: Replace with actual charts -->`"

## 8. ASSUMPTIONS (Use if OPEN questions not answered)

If any OPEN question is not answered, AI must use these safe defaults and log them in output:

1. OS = Windows 11
2. Python = 3.10+
3. Timezone = Asia/Kolkata (IST)
4. GitHub repo = PUBLIC, GitHub Pages enabled from root
5. NSE holiday = Exit 0, log "Market closed", don't push
6. Data storage = CSV for FAO, JSON for Nifty
7. Notification = Telegram

Example log AI must produce:
[ASSUMPTION LOG]
- Used nsepython because FAO URL not confirmed (Q1)
- Implemented Cloud as default (Q2)

## 9. DECISIONS LOG

| Date | Question | Decision | Reason | Status |
|------|----------|----------|--------|--------|
| 2026-09-26 | Notification channel | Telegram | Free, easy API. WhatsApp needs paid API | Decided |
| 2026-09-26 | Hosting | GitHub Pages | Free, integrated with repo | Decided |
| 2026-09-26 | Q1 FAO URL | Pending | Waiting for user to provide working URL | OPEN |
| 2026-09-26 | Q2 Local vs Cloud | Pending | User to confirm if PC stays ON at 8 PM | OPEN |
