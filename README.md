# Global Banks Market Capitalization ETL Pipeline

An automated Python ETL (Extract, Transform, Load) pipeline designed to extract market capitalization metrics of top global banks from web sources, execute dynamic multi-currency conversions using foreign exchange matrices, and persist the processed results into both flat CSV format and an SQLite database.

## Technical Overview & Architecture

This pipeline automates quarterly financial reporting workflows by orchestrating four primary stages:

1. **Extraction:** Retrieves HTML table content from web archives using `requests` and parses relevant attributes via `BeautifulSoup` into a Pandas DataFrame.
2. **Transformation:** Ingests dynamic exchange rates from an external CSV mapping file to scale market cap figures across foreign currencies (GBP, EUR, INR) with 2-decimal point precision.
3. **Loading:** Dual-persists processed data structures into disk storage as CSV and relational tables (`Largest_banks`) in an SQLite database (`Banks.db`)[cite: 1, 6].
4. **Validation & Auditing:** Executes verification SQL queries directly on the SQLite database and logs timestamped execution stage transitions to `code_log.txt`.

---

## Tech Stack & Dependencies

* **Language:** Python 3.x
* **Libraries:**
  * `pandas` — DataFrame manipulation and SQL/CSV I/O operations
  * `beautifulsoup4` — Web page HTML parsing
  * `requests` — HTTP request handling
  * `numpy` — Mathematical precision rounding
  * `sqlite3` — Relational database connection and SQL query execution
  * `datetime` — Log event timestamping

---

## Repository Structure

```text
├── banks_project.py          # Primary ETL pipeline script
├── exchange_rate.csv         # Foreign currency exchange rates mapping
├── Largest_banks_data.csv    # Output: Extracted & transformed dataset
├── Banks.db                  # Output: SQLite relational database containing 'Largest_banks' table
├── code_log.txt              # Output: Execution stage status logging file
└── README.md                 # Documentation
