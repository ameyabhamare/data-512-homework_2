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

Wikipedia stands out as a valuable data source due to its extensive information repository. This assignment focused on extracting metadata from articles, revealing the vast potential for in-depth analysis. Despite being widely regarded as a reliable resource, its open-source nature allows public edits, leading to potential inaccuracies. Instances of edit wars have resulted in certain articles, like San Francisco, being locked. Nevertheless, I believe Wikipedia remains a valuable resource for diverse analyses. The previous assignment explored page views, while this one delved into article qualities, showcasing the numerous possibilities for data analysts.

Wikipedia offers extensive opportunities for supporting data science research. Its reliability in historical data makes it ideal for time series analytics, representing a significant use case. Being a primary online information source due to its vast content, Wikipedia is widely accessible. Additionally, the Wikimedia Foundation now provides comprehensive APIs and models, enhancing access to various data and metadata aspects. These resources make conducting data science analysis on Wikipedia data highly appealing.

# Workflow

In **data_acquisition.ipynb**, I make a Wikimedia API calls to get latest revision IDs for each article title. I used these generated revision IDs to makes ORES API calls for each article title. The ORES response is a multilevel dictionary.    
      
The score level gives a data structure of the form:   
           
"Abbeville, Alabama": {   
&nbsp;&nbsp;&nbsp;&nbsp;"prediction": "C",   
&nbsp;&nbsp;&nbsp;&nbsp;"probability": {   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"B": 0.31042252456158204,   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"C": 0.5979200965294227,   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"FA": 0.025186220917133947,   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"GA": 0.04952133645299354,   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"Start": 0.013573873336789355,   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"Stub": 0.0033759482020785892   
&nbsp;&nbsp;&nbsp;&nbsp;}    

All the ORES responses are saved to 'consolidated-ores.json'
           
Additionally, I created a dataframe for state with its corresponding regional division and population called 'combined_region_population.csv'.
     
Finally, to create 'wp_scored_city_articles_by_state.csv', I merged the entries from consolidated-ores.json and combined_region_population.csv based on matched 'state'.    
     
This final csv has following data fields:

| Fields    |
| -------- |
| state  |
| regional_division |
| population    |
| article_title |
| revision_id |
| article_quality |

3. In **analysis.ipynb**, we generate all required tables. 
