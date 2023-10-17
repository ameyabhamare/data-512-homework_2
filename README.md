# Objective  
---  
In this study, I delved into the examination of bias within data by utilizing Wikipedia articles. I obtained data pertaining to searches for Wikipedia articles about various cities and towns throughout the United States, and I assessed the articles' quality using the ORES API. I conducted an analysis of significant metrics associated with the predicted article quality, such as identifying the states with the most comprehensive per capita coverage of articles. The primary objective was to gain insights into the regional patterns of article coverage and the prevalence of high-quality articles.

# Source Data
1. A csv file [**us_cities_by_state_SEPT.2023**](https://en.wikipedia.org/wiki/Category:Lists_of_cities_in_the_United_States_by_state). It contains state, page title and url. 

2. An excel file [**NST-EST2022-POP**](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html). This file contains the list of states and the 2022 population estimates for each state.

3. A csv file [**US States by Region - US Census Bureau**](https://docs.google.com/spreadsheets/d/14Sjfd_u_7N9SSyQ7bmxfebF_2XpR8QamvmNntKDIQB0/edit#gid=0). It contains regions (Northeast, Midwest etc.), divisions (New England, Middle Atlantic) and states (Connecticut, Vermont)

# Licensing    
---   
1. [Wikimedia Foundation REST API](https://www.mediawiki.org/wiki/API:REST_API#Terms_and_conditions)

2. [Creative Commons License](https://creativecommons.org/licenses/by/4.0/)

# Helpful API Documentation    
---    
1. [ORES Wiki](https://www.mediawiki.org/wiki/ORES)
   
2. [Wikipedia Content Assessment](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment)
   
3. [Wikimedia API Documentation](https://www.mediawiki.org/wiki/API:Info)

# Research Implications   
---    
This assignment provided intriguing insights into Wikipedia as a data source. I discovered the concept of article quality rankings and found that less populated states like Wyoming and Vermont had better per capita article coverage. Surprisingly, major city articles, like those for San Francisco, Seattle, and New York City, didn't have high quality ratings, likely due to their frequent and dynamic editing.

I noticed several biases in the data, including the significant influence of population centers on per capita rankings. Major cities exhibited varying article qualities likely due to frequent edits, and they often lacked state names in their titles, requiring special handling. Interestingly, I encountered no missing data after ORES calls, which exceeded my expectations, demonstrating the scalability and reliability of the ORES model. I'm keen to delve deeper into the ORES model's mechanics, understanding its article grading methodology, the significance of different parameters, and the mathematical aspects of probability score assignment.

Using open source data like Wikipedia for data science research poses inherent challenges. Online data is rife with biases, including geographical, racial, economic, and more. In our assignment, we witnessed how larger population centers influenced article quality, illustrating the potential skewing of results in algorithms trained on such biased datasets. Overrepresented groups or regions can significantly influence data-driven decisions, necessitating a cautious approach to avoid detrimental real-world effects in decision-making based on data science research.

Nonetheless, Wikipedia offers valuable support for data science research in numerous ways. It excels in providing reliable historical data, making it ideal for time series analytics. 

# Coding Process

1. In **data_acquisition.ipynb**, we make the Wikimedia API calls to get latest revision IDs for each article title. We use these generated revision IDs.

2. This final csv has following data fields as requested:

| Fields    |
| -------- |
| state  |
| regional_division |
| population    |
| article_title |
| revision_id |
| article_quality |

3. In **analysis.ipynb**, we generate all required tables. 