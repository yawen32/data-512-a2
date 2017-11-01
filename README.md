# data-512-a2: Bias in data

## Goal
The goal of this project is to explore the concept of bias by analyzing the data of policical articles from different countries on Wikepidia. The project is supposed to perform an analysis from two aspects: existence and quality of policial articles for each country.

## License of the source data and Wikimedia Foundation terms of use
1. Wikimedia REST API is licensed under the CC-BY-SA 3.0 and GFDL licenses
CC-BY-SA 3.0: `https://creativecommons.org/licenses/by-sa/3.0/`
GFDL: `https://www.gnu.org/copyleft/fdl.html`
2. Wikimedia's Terms of Use: `https://wikimediafoundation.org/wiki/Terms_of_Use/en`
3. Wikimedia's Privacy Policy: `https://wikimediafoundation.org/wiki/Privacy_policy`

## API documentation
1. The legacy Pagecounts API: `https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts`
2. The Pageviews API: `https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews`
3. Wekimedia REST API: `https://www.mediawiki.org/wiki/REST_API`
4. Wekimedia REST API endpoint: 

The legacy Pagecounts API:
`https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end`

The Pageviews API:
`https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end`

## Data file description
### After removing the rows that do not have matching data, there are five fields in the final data file (final_data.csv):
* country: country names
Field Type: String
* article_name:
Field Type: String
* revision_id：
The values of this field are integers which indicate the number of views from the legacy Pagecounts API on both desktop and mobile during given months.
* article_quality:
Field Type: String
* population:
The values of this field are integers which indicate the number of views from the legacy Pagecounts API on mobile during given months.


## Special considerations of data
In the process of collecting the data from Pageview API, we only focus on organic (user) traffic. Thus, traffic data by web crawlers or spiders was excluded by filtering agent type to user, while data from the Pagecounts API does not filter on agent.

## Writeup
Please check the notebook.
