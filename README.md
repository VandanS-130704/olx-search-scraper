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

## 📦 Script
 ```bash
   import requests
from bs4 import BeautifulSoup
import csv

def scrape_olx(query="car-cover", filename="olx_results.csv"):
    url = f"https://www.olx.in/items/q-{query}"
    headers = {"User-Agent": "Mozilla/5.0"}
    response = requests.get(url, headers=headers)

    if response.status_code != 200:
        print(f"Failed to fetch OLX page. Status code: {response.status_code}")
        return

    soup = BeautifulSoup(response.text, "html.parser")

    with open(filename, "w", newline="", encoding="utf-8") as f:
        writer = csv.writer(f)
        writer.writerow(["Title", "Price", "Location", "Link"])

        for item in soup.select("li.EIR5N"):
            title = item.select_one("span._2tW1I").get_text(strip=True) if item.select_one("span._2tW1I") else "N/A"
            price = item.select_one("span._89yzn").get_text(strip=True) if item.select_one("span._89yzn") else "N/A"
            location = item.select_one("span._2Vp0i").get_text(strip=True) if item.select_one("span._2Vp0i") else "N/A"
            link = "https://www.olx.in" + item.a["href"] if item.a else "N/A"

            writer.writerow([title, price, location, link])

    print(f"Results saved to {filename}")

if __name__ == "__main__":
    scrape_olx()

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
