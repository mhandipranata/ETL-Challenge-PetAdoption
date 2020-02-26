# ETL-Challenge-PetAdoption

- Extract: original data sources and how the data was formatted (CSV, JSON, pgAdmin 4, etc).
- Transform: what data cleaning or transformation was required.
- Load: the final database, tables/collections, and why this was chosen.

## Data Sources

I collected the data of pet adoptions from two websites.

- API: https://www.petfinder.com/developers/
- Web Scraping: http://dog.rescueme.org/California

### Extract

1. petfinder.com API has limitation of 1,000 call/day. Each call can collect 100 records. I called the data day by day and got a total of 209900 lines, and stored the data in csv as a back up.
2. dog.rescueme.org has 25 pages of pet adoption. I tried using splinter to go to each pages, but it did not work properly, so ended up looping through each pages and scrape.

### Transform

Doing data cleaning for both data by filtering column, and extracting necessary values from the column.

