# ETL Challenge: Pet Adoption

### Data Sources

I collected the data of pet adoptions from two websites.

- API: https://www.petfinder.com/developers/
- Web Scraping: http://dog.rescueme.org/California

### Extract

1. petfinder.com API has limitation of 1,000 call/day. Each call can collect 100 records. I called the data day by day and got a total of 209900 lines, put into pandas dataframe and stored the data in csv as a back up.
2. dog.rescueme.org has 25 pages of pet adoption. I tried using splinter to go to each pages, but it did not work properly, so ended up looping through each pages and scrape. Put the scraped data into pandas dataframe and stored the data in csv as a back up.

### Transform

Doing data cleaning for both data by joining all csv extracted from API call, filtering column, remove 'n/a' values and unsufficient data, then extracting necessary values from the column using pandas. Lastly, export to csv for back up.

### Load

From csv, we convert it to dictionary in a form of JSON to load them to MongoDB.
Create a new database in MongoDB ("pet_adoption_db") and load the API data and web scarping data to different collections.

Collections:
- petfinder.com API -> petfinder
- dog.rescueme.org Web Scraping -> pet_rescueme

