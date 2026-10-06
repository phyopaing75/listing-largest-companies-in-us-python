# Largest Companies in the US: Web Scraping with Python

A Python web scraping project that collects the 100 largest US companies by revenue from Wikipedia and saves them as a CSV file. The notebook uses `requests` to download the page, `BeautifulSoup` to read the table, and `pandas` to build and export the dataset.

---

## Project Overview

* Source: Wikipedia, [List of largest companies in the United States by revenue](https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue)
* Tools and Technologies: Python, Requests, Beautiful Soup 4, pandas, Jupyter Notebook
* Output: `us-largest-companies.csv`, with 100 companies and 7 columns
* Files: `largest_companies_in_us.ipynb` (scraping notebook) and `us-largest-companies.csv` (scraped data)

---

## How the Scraper Works

| Step | What the notebook does |
|---|---|
| 1. Request the page | Sends a `GET` request with `requests` and a custom `User-Agent` header (`MyWebScraper/1.0`) |
| 2. Parse the HTML | Loads the response text into a `BeautifulSoup` object |
| 3. Find the table | Selects the table with class `wikitable sortable` |
| 4. Read the headers | Collects every `<th>` tag and strips the text to get the 7 column names |
| 5. Create an empty DataFrame | Builds a `pandas` DataFrame with those 7 columns |
| 6. Read the rows | Loops through each `<tr>` after the header, reads the `<td>` cells, strips the text and appends each row to the DataFrame |
| 7. Export | Saves the 100 rows to CSV with `to_csv(index=False)` |

---

## Dataset

100 rows and 7 columns, one row per company.

| Column | Description | Example |
|---|---|---|
| `Rank` | Position by revenue (1 to 100) | 1 |
| `Name` | Company name | Walmart |
| `Industry` | Industry as listed on Wikipedia | Retail |
| `Revenue (USD millions)` | Annual revenue in millions of US dollars | 680,985 |
| `Revenue growth` | Change in revenue from the previous year | 5.1% |
| `Employees` | Number of employees | 2,100,000 |
| `Headquarters` | City and state of the head office | Bentonville, Arkansas |

---

## What the Data Shows

All figures are calculated from `us-largest-companies.csv`.

1. **The 100 companies earn $13.05 trillion in total revenue** and employ about 16.2 million people.
2. **Revenue is concentrated at the top.** The top 10 companies make 32% of the total and the top 5 make 19%. Walmart ($681 billion) earns about 15 times as much as the 100th company, Eli Lilly ($45 billion).
3. **Financials is the biggest industry label by company count.** It has 16 of the 100 companies and $1.87 trillion in revenue. Petroleum has 9 companies and $1.21 trillion.
4. **Most companies grew.** 19 of the 100 companies had falling revenue. Nvidia grew the most (114.2%), followed by StoneX Group (64.1%) and Broadcom (46.4%). Deere (-15.6%), Boeing (-14.5%) and Valero Energy (-10.8%) fell the most.
5. **Headquarters cluster in a few states.** Texas has 17 of the 100 head offices, New York 15 and California 11.
6. **The largest employers are retailers and delivery firms.** Walmart (2,100,000), Amazon (1,556,000), The Home Depot (470,100), Target (440,000) and FedEx (422,100) have the most employees.

---

## Data Notes

* **All values are saved as text.** The scraper keeps each cell exactly as Wikipedia shows it, so `Revenue (USD millions)` and `Employees` contain commas and `Revenue growth` contains a `%` sign.
* **Industry labels are not consistent.** The CSV has 30 different labels, and some overlap (for example `Pharmaceutical` and `Pharmaceutical industry`, or `Technology` and `Technology and cloud computing`). The industry counts above use the labels exactly as they appear.
* **Hardcoded settings.** The `User-Agent` header still holds the placeholder email `your_email@example.com`, and the CSV is saved to a local Desktop path, so both need changing before running on another computer.
* **The scraper reads the table with class `wikitable sortable`.** If the Wikipedia page layout changes, the selector may need an update.

---

## Repository Contents

| File | Description |
|---|---|
| `largest_companies_in_us.ipynb` | Notebook that scrapes the table and exports the CSV |
| `us-largest-companies.csv` | Scraped dataset (100 companies, 7 columns) |
| `README.md` | Project documentation |
