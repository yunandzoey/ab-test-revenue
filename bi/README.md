# Power BI One-Pager

Import `../data/analytic.csv` and `../data/summary.csv`.  
Measures:
- Users = DISTINCTCOUNT(Users[user_id])
- Conversions = SUM(Users[converted])
- CVR = DIVIDE([Conversions], [Users])
- Revenue = SUM(Users[revenue])
- RPU = DIVIDE([Revenue], [Users])

Layout:
- Cards: CVR lift (95% CI, p), RPU lift (CI), SRM status
- Chart: CVR by arm (bar) or by date (line, if available)
- Chart: CVR by segment (exploratory)
- Slicers: arm, date/segment
- Notes: decision & next steps
