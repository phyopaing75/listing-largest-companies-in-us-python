# Listing Largest US Companies by Revenue

An automated Python web scraping pipeline that extracts, parses, and structures corporate financial data from Wikipedia's list of the top 100 largest United States companies by revenue.

## Project Overview

This project uses Python to scrape publicly available corporate performance records directly from Wikipedia. The script handles HTTP requests with custom client headers, parses DOM elements to isolate target tables, strips irregular formatting, and structures the records into a clean Pandas DataFrame exported to CSV for downstream analytics.

## Features and Implementation

* Custom HTTP Headers: Configured user-agent identification to adhere to standard web etiquette and prevent request blocking.
* Targeted DOM Parsing: Leverages Beautiful Soup to isolate the target Wikitable class (`wikitable sortable`) and extract header and row nodes.
* Data Sanitization: Cleans trailing whitespace, line breaks, and raw HTML formatting from extracted table headers and row values.
* DataFrame Transformation and Export: Dynamically compiles the extracted records into a Pandas DataFrame and exports the final dataset to a structured CSV file (`us-largest-companies.csv`).

## Dataset Schema

The resulting dataset captures 100 enterprise records with 7 core fields:

| Column Name | Data Type | Description |
| ----- | ----- | ----- |
| `Rank` | Integer / String | Company position ranked by total revenue. |
| `Name` | String | Legal corporate enterprise name. |
| `Industry` | String | Primary business and operating sector. |
| `Revenue (USD millions)` | String / Numeric | Total annual revenue reported in millions of USD. |
| `Revenue growth` | String / Percentage | Year-over-year revenue percentage growth. |
| `Employees` | String / Numeric | Total full-time global workforce count. |
| `Headquarters` | String | City and state of corporate headquarters. |

## Tech Stack and Libraries

* Language: Python
* Web Scraping: BeautifulSoup4 (`bs4`), requests
* Data Structuring and Export: pandas

## Output Sample

```
Rank  Name                Industry                    Revenue (USD millions)  Revenue growth  Employees  Headquarters
1     Walmart             Retail                      680,985                 5.1%            2,100,000  Bentonville, Arkansas
2     Amazon              Retail and cloud computing  637,959                 11.0%           1,556,000  Seattle, Washington
3     UnitedHealth Group  Healthcare                  400,278                 7.7%            400,000    Minnetonka, Minnesota
4     Apple               Technology                  391,035                 2.0%            164,000    Cupertino, California
5     CVS Health          Healthcare                  372,809                 4.2%            259,500    Woonsocket, Rhode Island
```
