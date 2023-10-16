**Objective**
---
The goal of this assignment is to construct, analyze, and publish a dataset of monthly article traffic for a select set of pages from English Wikipedia from July 1, 2015 through September 30, 2023. 

**Usage**      
---   
[Terms of use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)    
English Wikipedia’s text can be used under the terms of the [Creative Commons Attribution Share-Alike license](https://en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License)

**API usage**
---
[API usage documentation](https://wikimedia.org/api/rest_v1/#/Pageviews%20data)

**Data files desciption**
---
The graphs folder contains all required graphs - 
* 1_page_requests_graph.png
* 2_top_articles_page_views_graph.png 
* 3_fewest_months_data_graph.png

The json_files folder contains the 3 json files - 
* academy_monthly_mobile_201507-202309.json
* academy_monthly_desktop_201507-202309.json
* academy_monthly_cumulative_201507-202309.json

An example row in the json file - 
[{"12 Years a Slave (film)": [{"project": "en.wikipedia", "granularity": "monthly", "timestamp": "2015070100", "views": 138151}, {"project": "en.wikipedia", "granularity": "monthly", "timestamp": "2015080100", "views": 122993}, {}]

The data structure is a list of dictionaries (outer is for article level) within a list of dictionaries (inner is the time series data for each article)

Here, project is the name of the project, granulairty refers to the time duration for which web traffic is montiored, timestamp is a YYYYMMDD00 format, agent refers to who accessed it and views is the number of monthly visits.
