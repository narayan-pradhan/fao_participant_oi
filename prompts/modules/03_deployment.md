# Module: Deployment & Notification
Task: GitHub Actions + Telegram

Workflow: .github/workflows/daily-publish.yml
Cron: 30 14 * * 1-5 (8:00 PM IST = 2:30 PM UTC, Mon-Fri)

Steps:
1. checkout
2. setup-python
3. pip install -r requirements.txt
4. python fetch_daily_data.py
5. python generate_story.py (updates story in index.html or creates data/story.json that index.html reads)
6. git config, git add ., git commit, git push
7. Send Telegram via curl: https://api.telegram.org/bot${{ secrets.TELEGRAM_BOT_TOKEN }}/sendMessage

Secrets needed: TELEGRAM_BOT_TOKEN, TELEGRAM_CHAT_ID
