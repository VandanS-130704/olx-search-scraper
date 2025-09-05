# OLX Car Cover Scraper

A simple Python script to scrape search results from OLX (example: "Car Cover") and save them in a CSV file.

---

## 🚀 Features
- Scrapes OLX search results for a given query (default: `car-cover`).
- Extracts:
  - **Title**
  - **Price**
  - **Location**
  - **Link to the listing**
- Saves results into a structured CSV file (`olx_results.csv`).

---

## 📦 Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/VandanS-130704/olx-search-scraper.git
   cd olx-search-scraper

   ```

2. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## ▶️ Usage

Run the scraper with:
```bash
python scraper.py
```

This will create an output file:
```
olx_results.csv
```

---

## ⚙️ Custom Query

By default, the script searches for `car-cover`.  
You can modify the query by editing the `scrape_olx(query="your-search-term")` function call inside `scraper.py`.

Example for "bike-cover":
```python
if __name__ == "__main__":
    scrape_olx(query="bike-cover")
```

---
