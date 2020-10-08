
## DATA 512 A1: Data Curation

The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2020.We will combine data about Wikipedia page traffic from two different Wikimedia REST API endpoints into a single dataset, perform some simple data processing steps on the data, and then analyze the data visually.


### Step 1: Gathering the data

In this step, in order to measure Wikipedia traffic from 2008-2020, we collect data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API.

* The Legacy Pagecounts API provides access to desktop and mobile traffic data from December 2007 through July 2016.
* The Pageviews API provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

The output of this step are saved as the following JSON files
pagecounts_desktop-site_200712-202008.json
pagecounts_mobile-site_200712-202008.json
pageviews_desktop_200712-202008.json
pageviews_mobile-app_200712-202008.json
pageviews_mobile-web_200712-202008.json


### Step 2: Processing the data

Given the outputs from API calls, we perform the following
* For data collected from the Pageviews API, combine the monthly values for mobile-app and mobile-web to create a total mobile traffic count for each month.
* For all data, separate the value of timestamp into four-digit year (YYYY) and two-digit month (MM) and discard values for day and hour (DDHH).
* Combine the above data into a single CSV file

The output is a CSV file saved as en-wikipedia_traffic_200712-202008.csv

The csv file has the following headers
 
| Column                  | Value     | Datatype |
|-------------------------|-----------|----------|
| year                    | YYYY      | int64   |
| month                   | MM        | int64   |
| pagecount_all_views     | num_views | int64    |
| pagecount_desktop_views | num_views | int64    |
| pagecount_mobile_views  | num_views | int64    |
| pageview_all_views      | num_views | int64    |
| pageview_desktop_views  | num_views | int64    |
| pageview_mobile_views   | num_views | int64    |

### Step 3: Analyze the data

In this step, we create a visualization that will track three traffic metrics: mobile traffic, desktop traffic, and all traffic (mobile + desktop) using matplotlib.

The output is a trend chart image file saved as en_wikipedia_traffic_visualization_200712-202008.png


### Data sources

* [Wikimedia REST API](https://www.mediawiki.org/wiki/Wikimedia_REST_API)
* Legacy Pagecounts API
([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end))
* Pageviews API
([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end))
* [Wikimedia Foundation REST API terms of use](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions)
* Text is available under the [Creative Commons Attribution-ShareAlike License](https://creativecommons.org/licenses/by-sa/3.0/)


### Important Notes
* The Pageview API (but not the Pagecount API) allows us to filter by agent=user. Since we're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders, we have applied this filter
* There was about 1 year of overlapping traffic data between the two APIs. We have used the data from both APIs for this period of time.


### Dependencies

* numpy
* pandas >= 1.0.0
* matplotlib
* json
* requests
* datetime



