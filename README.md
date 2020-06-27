# sinhala-song-data-scraper
Simple web scraper built using Scrappy that scrapes sinhala song data and meta data. Then the scraped data is sent into Elastic Search. Some of the above scraped data may empty or not organized due to different html formats in the website.

## Getting Started
1. Install python 3.x version and pip version 3
2. Install required python packages by running the following command in the project home directory.
  `pip install -r requirements.txt`
3. `sinhalasongs/settings.py` should be modified with following configurations file as required.
```
# Configure a delay 
DOWNLOAD_DELAY = 9

# The download delay setting will honor only one of:
CONCURRENT_REQUESTS_PER_DOMAIN = 2
CONCURRENT_REQUESTS_PER_IP = 1

# Cookies Disabled
COOKIES_ENABLED = False
```
> Check here for additional configurations (https://docs.scrapy.org/en/latest/topics/settings.html).
4. Documents will be sent to Elastic Search using following configurations.
```
# Configure ScrapeElasticSearch

ELASTICSEARCH_SERVERS = ['http://127.0.0.1:9200']
ELASTICSEARCH_INDEX = 'sinhala_songs'
ELASTICSEARCH_TYPE = 'items'
ELASTICSEARCH_UNIQ_KEY = 'url'
```

## Running the Crawler
Go to `sinhalasongs` folder and run the following command.

`scrapy crawl sinhalasongbook_scraper -o <filename>.json`

## Scraped data 
Following data will be scraped by the crawler.

1. `songName`: Name of the song
2. `artist`: All the relevant artists
3. `genre`: Genres of the song
4. `lyric`: Lyrics with newline characters
5. `views`: Views from original page for the song
6. `lyricWriter`: Writers of the song
7. `musicDirector`: Music directors of the song
8. `beat`: Beat of the song
9. `url`: URL of the original lyric page
10. `key`: Key of the song
11. `shares`: Shares from original page for the song


