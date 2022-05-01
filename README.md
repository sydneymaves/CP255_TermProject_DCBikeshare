# CP255 Urban Informatics Term Project: Increasing Equitable Access and Safety of Capital Bikeshare Station Locations in Washington, DC

Term Research Project for CP255 Urban Informatics + Visualization at UC Berkeley (Spring 2022)
_Created by Sydney Maves | 5.9.2022_

## Research Idea
Since the COVID-19 pandemic as more people have begun to work-from-home and and as leisure and social activities have changed, there has been more unpredictability in travel patterns. As modal shifts away from mass transportation have occured, bicycling around cities has become increasingly popular. With this, it is critical that folks of all backgrounds have adequate access to safe bicycling infrastructure and bikeshare stations.  

In this project, I will be exploring Washington D.C.'s Capital Bikeshare user data to examine how access to the system varies across throughout the city. This project will focus primarily on two important aspects of a bikeshare system - safety and equity - to understand if bikeshare locations are sited equitably and accessible to lower-income communities. While Capital Bikeshare has a program - Capital Bikeshare for All - geared towards improving system access, it is focused primarily on providing monetary assistance to lower-income folks. As you can see in the maps below which highlight geographic separation of high vs. low income households and percentage white vs. percentage black communities, Washington, DC is segregated, with the western parts of the city being more white and wealthy and the eastern parts of the city being more black and lower income. While this is a heavily simplified model to map equity, it begins to show a spatial pattern of where folks of differing levels of resources may be concentrated.  

![equity2](https://user-images.githubusercontent.com/95829239/166126866-372e6af9-cc94-440f-84aa-198a04473812.png)


This study hopes to provide data-driven support for expanding this program to begin constructing stations in communities that lack adequate access to the system. Secondly, it will explore where bikeshare users are likely riding to understand users are riding on the high injury network, ultimately highlighting where the city may consider putting additional resources towards bicycle-friendly infrastructure. 

While there are some bikeshare stations located outside of the District of Columbia (Figure XX), the vast majority of stations are located within the District. This scope of this analysis and data used in this study, therefore, uses only data for Washington, DC. 

https://github.com/sydneymaves/CP255_TermProject_DCBikeshare/blob/91be9912d685545d731387223278c3708efbecc4/explore_map.html

## Research Questions
This project is guided by four main guiding questions. The first two sets of questions (1) User Trends and (2) Station Data are geared towards exploring the dataset in a variety of ways to understand basic user characteristics and trends.  

_User Trends_
What are the fundamental ridership trends from DC's bikeshare users? 
    When are the most popular times to ride? 
    What is the average trip length?
  
_Station Data_ 
What bikeshare stations are utilized most? 

Ultimately, the second sets of questions (3) Equity Analysis and (4) Network Analysis hope to provide findings which may help the station improve system access and bicycle network safety. 

_Equity Analysis_
Where should Capital Bikeshare expand their operations to further equity priorities of the city? 

_Network Analysis_
What roads are most often taken by bikeshare users (utilizing shortest distance)? How can bikeshare data be used to prioritize certain roads for active pedestrian roadway improvements?

## Approach & Methodology (Finish this)

I will also be utilizing the OpenStreetMap (OSMnx) Shortest Path Algorithm to predict which cooridors are most frequently taken by bikeshare users. With this data, I hope to highlight where additional stations could be added to improve access to the bikeshare for more vulnerable populations. Using the results from my network analysis, active transportation planners in Washington, DC can prioritize facility improvements on high bikeshare (and likely traditional bike commuter) corridors. 

### Tools

### Datasets

_Capital Bikeshare Data:_ For the initial exploratory analysis, I am utilizing one year of data from March 2021 through February 2022. By using one year's worth of data, I will be able to explore seasonal variations in ridership patterns. For the mapping portions of this project, however, I am using data only from February 2022 due to the large size of the dataset.

_Capital Bikeshare Station Data:_ This dataset includes exact station location latitudes and longitudes as well as the docking capacity of each station. 

To conduct a basic equity indicators, I will be using two US Census datasets. 
1. Population and Race (ACS 2020 5-Year Table DP05)
2. Median Household Income (ACS 2020 5-Year Table S1901)

## Data Exploration & Local Context
![yearcount_biketype](https://user-images.githubusercontent.com/95829239/166126424-4bb00a7e-f367-4f82-9e03-ee73bb1e3ad1.png)

![users_day](https://user-images.githubusercontent.com/95829239/166126426-dcb68f05-7d30-4fb4-8e3a-d64434a95016.png)

![line_mem_cas](https://user-images.githubusercontent.com/95829239/166125226-f8ebef81-f16b-423f-af47-eb9974ed554a.png)

![weekday_classic_electric](https://user-images.githubusercontent.com/95829239/166125232-7d81b058-0802-4985-a7fa-a06dd87f7711.png)

![crosstab_heatmap_week](https://user-images.githubusercontent.com/95829239/166127681-e67c6c0a-51b0-4d5f-8fce-1b9543b6c722.png)

![weekday_cas_member](https://user-images.githubusercontent.com/95829239/166125761-11f6193e-4e3d-4b6b-b311-213e3208e65f.png)



## Key Findings

## References
