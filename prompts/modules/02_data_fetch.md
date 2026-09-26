# Module: Data Fetch
Task: fetch_daily_data.py

Logic:
1. Get IST date: datetime.now(pytz.timezone('Asia/Kolkata')).strftime('%d-%b-%Y')
2. Try nsepython.nsefetch() for participant OI
3. Fallback to requests with headers: User-Agent Mozilla/5.0 + NSE cookie
4. Save to data/fao/YYYY-MM-DD.csv
5. Fetch Nifty close via yfinance or nsepython
6. Save to data/nifty/YYYY-MM-DD.json

Edge: If Saturday/Sunday, exit 0.
