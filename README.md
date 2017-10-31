# data-512-a2: Bias in data

## Goal
The goal of this project is to explore the concept of bias by analyzing the data of policical articles from different countries on Wikepidia. The project is expected to in two aspects: 

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
### There are eight fields in the final data file (en-wikipedia_traffic_200801-201709.csv):
#### year:
The values of this field are integers in four-digit format (YYYY)
#### month:
The values of this field are integers in two-digit format (MM)
#### pagecount_all_views：
The values of this field are integers which indicate the number of views from the legacy Pagecounts API on both desktop and mobile during given months.
#### pagecount_desktop_views:
The values of this field are integers which indicate the number of views from the legacy Pagecounts API on the desktop during given months.
#### pagecount_mobile_views:
The values of this field are integers which indicate the number of views from the legacy Pagecounts API on mobile during given months.
#### pageview_all_views：
The values of this field are integers which indicate the number of views from the the Pageviews API on both desktop and mobile during given months.
#### pageview_desktop_views：
The values of this field are integers which indicate the number of views from the the Pageviews API on the desktop during given months.
#### pageview_mobile_views：
The values of this field are integers which indicate the number of views from the the Pageviews API on mobile during given months.

## Special considerations of data
In the process of collecting the data from Pageview API, we only focus on organic (user) traffic. Thus, traffic data by web crawlers or spiders was excluded by filtering agent type to user, while data from the Pagecounts API does not filter on agent.
