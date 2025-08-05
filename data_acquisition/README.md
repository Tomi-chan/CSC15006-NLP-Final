# Data Acquisition for SinoNômBERT

This folder contains two Jupyter notebooks for collecting pre-modern Vietnamese texts (written in Chữ Nôm) from various online sources. The data is used for fine-tuning a language model on historical Vietnamese scripts.

---

## Notebooks Overview

### 1. `nomfoundation_crawling.ipynb`
- **Purpose:** Scrape data from the *History of Greater Vietnam* section on nomfoundation.org.
- **Functionality:**
  - Sends HTTP requests to retrieve page content.
  - Uses `Selenium` to handle JavaScript-rendered elements and pagination.
  - Parses HTML with `BeautifulSoup` and extracts structured data (characters, readings, meanings).
  - Saves extracted content to `.txt` files.

### 2. `HXH_TPNK_crawling.ipynb`
- **Purpose:** Crawl poetry by **Hồ Xuân Hương** and the **Trinh Phụ Ngâm Khúc**.
- **Functionality:**
  - Navigates through specific poem pages on nomfoundation.org.
  - Extracts poem titles, stanzas, and text content.
  - Normalizes formatting and removes unnecessary HTML tags.
  - Exports cleaned text data to `.txt` files.

---

## How to Use

1. Open the notebooks on Google Colab (recommended).
2. Run each cell sequentially to perform web scraping.
3. Download the output `.txt` files for further processing or training.

---

## Notes

- The HTML structure of the target website may change over time. Please verify and update the scripts if needed.
- An internet connection and browser driver are required when using `Selenium`.

---

## Suggestions for Improvement

- Implement multithreading or asynchronous crawling to speed up the process.
- Integrate structured storage using SQLite or MongoDB.
- Add deduplication and language detection filters for quality control.

---

## Files

- `nomfoundation_crawling.ipynb`: Crawl historical records from Nôm Foundation
- `HXH_TPNK_crawling.ipynb`: Crawl poetry by H.X.H and T.P.N.K
- `README.md`: This file
- `data_crawling_notes.docx`: Internal crawling notes and progress tracking