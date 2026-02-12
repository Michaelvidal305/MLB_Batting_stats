# MLB Batting Stats (2015–2024)

## 📂Data source
  
  -- [View dataset MLB_batting_stats.csv](Dataset/MLB_Batting_stats) 
  
## 📝Description 
  
  This dataset contains scraped Major League Baseball (MLB) batting statistics from Baseball Reference for the seasons 2015 through 2024. It was collected using a custom Python scraping script and then cleaned and processed in SQL for use in analytics and machine learning workflows.
  
  The data provides a rich view of offensive player performance across a decade of MLB history. Each row represents a player’s season, with key batting metrics such as Batting Average (BA), On-Base Percentage (OBP), Slugging (SLG), OPS, RBI, and Games Played (G). This dataset is ideal for sports analytics, predictive modeling, and trend analysis.

## ⚙️Data Collection (Python)
  
  Data was scraped directly from Baseball Reference using a Python script that:
- Sent HTTP requests with browser-like headers to avoid request blocking.
- Parsed HTML tables with pandas.read_html().
- Added a Year column for each season.
- Cleaned player names by removing symbols (#, *).
- Kept summary rows for players who appeared on multiple teams/leagues.
- Converted numeric fields and filled missing values with zeros.
- Exported both raw and cleaned CSVs for each year.

## 🧹Data Cleaning (SQL)
After scraping, the raw batting tables were uploaded into BigQuery and further cleaned:
  
  - Null values removed – Rows missing key fields (Player, BA, OBP, SLG, OPS, Pos) were excluded.
  
  - Duplicate records handled – Identified duplicate player–year–league entries and kept only one instance.
  
  - Minimum playing threshold applied – Players with fewer than 100 at-bats were removed to focus on meaningful season-long contributions.
  
  - The final cleaned table (cleaned_batting_stats) provides consistent, duplicate-free player summaries suitable for analytics.


## 📊Dataset Structure
  
| Column | Description                                                       |
|--------|-------------------------------------------------------------------|
| Player | Name of the player |
| Year | Season year |
| Age | Age during the season |
| Team | Team code (2TM for multiple teams) |
| Lg | League (AL, NL, or 2LG) |
| G | Games played |
| AB, H, 2B, 3B, HR, RBI | Core batting stats |
| BA, OBP, SLG, OPS | Rate statistics |
| Pos | Primary fielding position |


## 🚀Potential Uses
  
  - League Trends: Compare batting averages and OPS across seasons.
  
  - Top Performer Analysis: Identify the best hitters in different eras.
  
  - Predictive Modeling: Forecast future player stats using regression or ML.
  
  - Clustering: Group players into offensive archetypes.# ## ## ##
  
  - Sports Dashboards: Build interactive Tableau/Plotly dashboards for fans and analysts.


## 📌Acknowledgments
  
  - Raw data sourced from Baseball Reference .

  
  - Inspired by open baseball datasets and community-driven sports analytics.
