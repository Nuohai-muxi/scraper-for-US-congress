# Congressional Record Scraper

This package contains functions to scrape, parse, and analyze the Congressional Record. It provides tools to extract metadata from congress.gov and download the text of the Congressional Record.

## Features

1. **Scrape metadata** from congress.gov
2. **Download text** of the Congressional Record
3. **Analyze** the Congressional Record (functionality to be implemented)

## Main Functions

### 1. `get_cr_df(date, section)`

Scrapes metadata for all subsections of the Congressional Record for a specific date and section.

- **Parameters:**
  - `date`: Date object
  - `section`: String (e.g., "senate-section", "house-section")
- **Returns:** DataFrame with metadata including headers and URLs to raw text

### 2. `get_cr_htm(row, output_dir)`

Downloads the raw text of each subsection as an .htm file.

- **Parameters:**
  - `row`: DataFrame row containing metadata
  - `output_dir`: Directory to save the downloaded files

## Usage

```python
from datetime import datetime
from congressional_record_scraper import get_cr_df, get_cr_htm

# Scrape metadata
date = datetime(2007, 3, 1)
cr_metadata = get_cr_df(date, section="senate-section")

# Download raw text
for _, row in cr_metadata.iterrows():
    get_cr_htm(row, "data/htm")
```

## Requirements

- Python 3.6+
- requests
- BeautifulSoup4
- pandas
- tqdm

## Data Storage

By default, the script creates a `data` directory to store:
- `cr_metadata.csv`: CSV file containing scraped metadata
- `htm` subdirectory: Contains downloaded raw text files

## Note

This scraper is designed to respect the terms of service of congress.gov. Please use responsibly and avoid overloading their servers with too many requests in a short time.

## Reference

[judgelord‘s projcet](https://github.com/judgelord/congressionalrecord)

