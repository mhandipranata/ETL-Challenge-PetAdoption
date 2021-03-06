# ETL Challenge: Pet Adoption

### Overview

Perform ETL (Extract, Transform, and Load) process on Pet Adoption data. Data will be extracted from 2 different data sources (API and Web Scraping). Then clean and filter data using pandas, and transform to dictionary to load the data to a database (MongoDB).

<b>Tools: </b> pandas, requests, json, BeautifulSoup, mongoDB
<br><br>
### Data Sources

I collected the data of pet adoptions from two websites.

- API: https://www.petfinder.com/developers/
- Web Scraping: http://dog.rescueme.org/California
<br><br>

### Extract

1. petfinder.com API has limitation of 1,000 call/day. Each call can collect 100 records per page (1 page, 1 API call). I called the data day by day and got a total of 209900 lines, put into pandas dataframe and stored the data in csv as a back up.

![petfinder_api_call](screenshots/petfinder_api_call.png)


2. dog.rescueme.org has 25 pages of pet adoption. I tried using splinter to go to each pages, but it did not work properly, so ended up looping through each pages and scrape. Put the scraped data into pandas dataframe and stored the data in csv as a back up.

![rescueme_scrape](screenshots/rescueme_scrape.png)
<br><br>

### Transform

Perform data cleaning for both data by joining all csv extracted from API call, filtering column, remove 'n/a' values and unsufficient data, then extracting necessary values from the column using pandas. Lastly, export to csv for back up.

![data_cleaning_1](screenshots/data_cleaning_1.png)
![data_cleaning_2](screenshots/data_cleaning_2.png)
![data_cleaning_3](screenshots/data_cleaning_3.png)
![data_cleaning_4](screenshots/data_cleaning_4.png)

<br>

### Load

From csv, we convert it to dictionary in a form of JSON to load them to MongoDB.
Create a new database in MongoDB ("pet_adoption_db") and load the API data and web scarping data to different collections.

Collections:
- petfinder.com API -> petfinder
- dog.rescueme.org Web Scraping -> pet_rescueme

![database_petfinder_data](screenshots/database_petfinder.png)
![database_rescueme_data](screenshots/database_rescueme.png)