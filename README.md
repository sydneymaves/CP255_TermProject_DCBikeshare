# CP255 Urban Informatics Term Project: Increasing Equitable Access of Capital Bikeshare Station Locations in Washington, D.C.

Term Research Project for CP255 Urban Informatics + Visualization at UC Berkeley (Spring 2022)
_Created by Sydney Maves | 5.9.2022_

## Research Idea
Since the COVID-19 pandemic, as more people have begun to work-from-home and as leisure and social activities have changed, the unpredictability of travel behaviors has increased. As modal shifts away from mass transportation have occurred, bicycling around cities has become increasingly popular. With this, it is critical that folks of all backgrounds and incomes have adequate access to safe bicycling infrastructure and bikeshare stations.  

In this project, I will be exploring Washington D.C.'s Capital Bikeshare user data to examine how access to the system varies throughout the city. This project will focus primarily on one important aspects of a bikeshare system - equity - to understand if bikeshare locations are sited equitably and accessible to lower-income communities. While Capital Bikeshare has a program - Capital Bikeshare for All - geared towards improving system access, it is focused primarily on providing monetary assistance to lower-income folks. As you can see in the maps below which highlight geographic separation of high vs. low income households and percentage white vs. percentage black communities, Washington, D.C. is segregated. The western parts of the city are more white and wealthy, while the eastern parts of the city have a higher proportion of black and lower income folks. While this is a heavily simplified model for mapping equity, it begins to show a spatial pattern of where folks of differing levels of resources may be concentrated.  

![equity_pop_income2](https://user-images.githubusercontent.com/95829239/167484542-34a5d4ac-7f5b-4e4e-8cda-9367501203ea.png)
![equity_black_white2](https://user-images.githubusercontent.com/95829239/167484557-1b31ef31-ac0b-4e51-b8ae-ea16c3f88573.png)

This study hopes to provide data-driven support for constructing stations in communities that lack adequate access to the system as part of the Capital Bikeshare For All program. Unfortunately, I was unable to perform an OSMnx and NetworkX analysis to identify routes heavily used by bikeshare users as well as create isochrone maps to show which neighborhoods have inadequate access to the bikeshare. Initially, this study also intended to identify where bikeshare users are likely riding (using OSMnx's shortest_path) to understand which roads are heavily utilized by bikeshare users and to determine if these routes align with the city's high injury network. This work ultimately sought to highlighting where the city may consider putting additional resources towards bicycle-friendly infrastructure. Due to time constraints and knowledge gaps this portion of the analysis will be completed in future work. 

While there are some bikeshare stations located outside of the District of Columbia (see map below), the vast majority of stations are located within the District. The scope of this analysis and data used in this study, therefore, focuses only on datapoints within Washington, DC. Only the points within the dotted line (District of Columbia region) on the map below are included in subsequent analyses. Click on the link below to learn more about where bike stations are located throughout the region. 

[Click Here to View the Interactive Introductory Map](https://sydneymaves.github.io/CP255_TermProject_DCBikeshare/explore_map.html)
![IntroMap_ScreenShot](https://user-images.githubusercontent.com/95829239/167264130-09d75709-2684-495f-9f42-bd73ef9e5ddf.png)

## Research Questions
This project is guided by four main questions. The first two sets of questions, (1) User Trends and (2) Station Data, are geared towards exploring the dataset in a variety of ways to understand basic user characteristics and trends.  

_User Trends_
What are the fundamental ridership trends from D.C.'s bikeshare users? 
    When are the most popular times to ride? 
    What is the average trip length?
  
_Station Data_ 
What bikeshare stations are utilized most? 

Ultimately, the second sets of questions, (3) Equity Analysis and (4) Network Analysis, hope to provide findings which may help the station improve system access and bicycle network safety. Unfortunately, I was unable to complete my OSMnx analysis to fully respond to question four. This will be a future areas of study. 

_Equity Analysis_
Where should Capital Bikeshare expand their operations to further equity priorities of the city? 

_Network Analysis (Future Work)_
What roads are most often taken by bikeshare users (utilizing shortest distance)? How can bikeshare data be used to prioritize certain roads for active transportation roadway improvements?

## Approach & Methodology

This project was completed using Python in Jupyter notebooks. Data was downloaded to CSV, shapefile, or loaded into Jupyter Notebooks via an API from various sources listed below (and in the references section). Python packages used in this analysis are described in the tools section below. The main data used in this analysis is from Capital Bikeshare's open data site (see reference). They share monthly ridership data on the start/end locations, time traveled, membership status, and bike type for each and every ride taken in the system. The first step of this research was to clean and process Capital Bikeshare's for one year (2021) to get rid of outliers. As part of this, I eliminated rides that started and ended at the same station. I also eliminated rides that were in the top and bottom standard deviation in ride duration. This information was combined with American Communities Survey data to begin to understand station location in the context of (in)equities. ACS data was pulled into Jupyter Notebook using the Census API. 

I also attempted to utilizing the OpenStreetMap (OSMnx) and NetworkX to sum all rides taken from each station pair to then highlight corridors most frequently used by bikeshare users and then identify the edges which connect the nearest ox_nodes to those stations. Using the results from my network analysis, active transportation planners in Washington, D.C. can prioritize facility improvements on high bikeshare traffic (and likely traditional bike commuter) corridors. I was also attempting to create isochrone maps using two, four, and six minute walking distances along the pedestrian network to highlight which neighborhoods are inadequately served. With this information, I was hoping to highlight where additional stations could be added to improve access to the bikeshare system for more vulnerable populations. 

### Tools & Packages
* CSV & APIs: Utilized to import data into Jupyter Notebook
* QGIS: Utilized to inspect shapefile data before loading into Jupyter Notebook
* Python Packages
    * Seaborn
    * Matplotlib
    * Plotly Express
    * Pandas
    * Geopandas
    * Contextly
    * OSMnx
    * NetworkX
* Maps Integrated - Used to geographically place my maps into the Washington, DC context.
    * CARTO 
    * MapBox GL
    * Leaflet 
    * Folium

### Datasets

_Capital Bikeshare Data:_ For the initial exploratory analysis, I am utilizing one year of data from January 2021 through December 2021. By using one year's worth of data, I will be able to explore seasonal variations in ridership patterns. For the mapping portions of this project, however, I am using data only from October 2022 due to the large size of the dataset.

_Capital Bikeshare Station Data:_ This dataset includes exact station location latitudes and longitudes as well as the docking capacity of each station. 

To conduct a basic equity indicators, I will be using two US Census datasets. 
1. Population and Race (ACS 2020 5-Year Table DP05)
2. Median Household Income (ACS 2020 5-Year Table S1901)

## Data Analysis & Mapping

Firstly, I'd like to present numerous exploratory charts which highlight basic bikeshare user trends for the 2021 calendar year. 

In 2021, approximately 2.4 million people road a Capital Bikeshare bicycle. Of which, approximately 267,000 (11%) were taken on an e-bike and 2,120,000 (89%) were taken on a classic docking bike.

![yearcount_biketype](https://user-images.githubusercontent.com/95829239/167280730-28bf4510-eba6-4e44-a0eb-440f92bf3d09.png)

Unsurprisingly, the most popular day to ride a Capital Bikeshare bike is Saturday, followed by Sunday. Monday is the least common day to ride. This map highlights that people may most often be utilizing Capital Bikeshare for leisure on non-work days. This may provide support for bolstering the network in common places of recreation and leisure, for example, along Rock Creek Park, the National Mall, Georgetown, and near the Arboretum.

![users_day](https://user-images.githubusercontent.com/95829239/166126426-dcb68f05-7d30-4fb4-8e3a-d64434a95016.png)

Casual riders also tend to ride for much longer time lengths (between 20-23 minutes, on average) than members (11-12 minutes). This may be because they're paying a flat rate for each ride and they want to maximize the value of that ride. Again we see that rides taken on Saturday and Sunday are longest. 

![weekday_cas_member](https://user-images.githubusercontent.com/95829239/167281073-b25a6b32-0691-4618-b040-ea215ede9068.png)

The bar graph below shows the top 10 most utilized stations. As shown on the chart, the most utilized station was the start location for approximately 29,000 trips in 2021. Although not shown on this visual, some stations were the start location of even just one to two rides. This may be because they are in an undesirable location or were put out of commission. It would be valuable for bikeshare planners to study why these stations are underutilized and consider placing them in more opportune areas. On average, each station was the start location for approximately 3,400 rides in 2021.

![Top_10_Stations](https://user-images.githubusercontent.com/95829239/167320938-0180ec2e-9a43-4759-b063-9462734da031.png)

During the weekdays, the peak times to ride are 5-6pm. On the weekends, the most common time to ride is between 11am-3pm. In future iterations of this work, I would like to figure out how to index through the days of the week to order them consecutively.

![crosstab_heatmap_week](https://user-images.githubusercontent.com/95829239/166127681-e67c6c0a-51b0-4d5f-8fce-1b9543b6c722.png)

When looking at a count of rides by members and casual riders, we see that the most common time to ride is in the summer months, peaking in October. This trend remains consistent for both rider types. Ridership numbers dip significantly in the winter months, likely due to the cold weather and fewer daylight hours. 

![line_mem_cas](https://user-images.githubusercontent.com/95829239/166125226-f8ebef81-f16b-423f-af47-eb9974ed554a.png)

Interestingly, the number of rides taken each month on an electric bike remains pretty consistent over the year (approximately 25,000 rides/month). This may be due to the extra cost of riding these bikes or due to the system's capacity. After a certain number of miles, an e-bike will be out of commission while it recharges. Similarly to what we saw in the previous line graph, the most popular month to ride is in October, petering off through the winter months. It is interesting to see that August had a small dip in ridership, and this may be due to hot, humid weather or rainfall. 

![weekday_classic_electric](https://user-images.githubusercontent.com/95829239/166125232-7d81b058-0802-4985-a7fa-a06dd87f7711.png)

Next, I wanted to explore spatially where people are riding to and from on different days of the week. Below are six heatmaps which show, in column one, which stations were most commonly used to start and end rides. The middle column looks at where riders are going to/from on weekdays. The right-most column looks at where riders are going to/from on the weekends. Surprisingly, there is almost no variation between these maps. I thought I would see that on the weekends, for example, there would be a high concentration (shown in yellow) of bike starts/ends along the National Mall. In future OSMnx analyses, I would be able to shed additional light on where a large number of riders are commuting to and from. 

![heatmap_startloc2](https://user-images.githubusercontent.com/95829239/167267500-a81f1c70-c53a-4026-abc6-ee01154086f1.png)
![heatmap_endloc2](https://user-images.githubusercontent.com/95829239/167269906-ccd534d7-279d-4207-828f-765200584ff1.png)

The final map, shown below, overlays a count of the number of rides _starting_ from each station with a cloropleth map of the percent of the tract that is black. This map begins to highlight the degree to which rides (and to some degree, stations) are located in the more affluent, whiter northwest parts of D.C. (areas shown in light yellow). The size of the bubble reveals how many bike rides were _started_ from a particular station. The smallest bubbles show where as few as three rides were started and the largest bubbles show where as many as 1,600 rides were started. Factors which may contribute to low ridership in part some parts of the city, particularly the southwestern area to the east of the Anacostia river, include low frequency of stations, inadequate bike redistribution, lower membership, and geographic barriers (e.g. the river). To promote equitable access and usage of the bikeshare system, Capital Bikeshare should consider these factors and continue building out stations in the southeast and northest portions of the city after consulting the community on how to best do this, assuming it is of interested to them (shown in dark red and red, respectively).

![bubble_blackpop_overlay4](https://user-images.githubusercontent.com/95829239/167484081-3b299134-2963-469c-a820-99f7060075cc.png)

Please also use the below interactive map to see exactly how many rides were taken at each station througout the city. Please note that some stations especially in the southeast portion of the city do not even have visible bubbles for stations due to low ridership. Capital Bikeshare may also benefit from community outreach geared towards the communities east of the Anacostia to see how this system could better serve their needs (and if it even is a system that they'd like to see more of). 

[Click Here to View the Interactive Bubble Map](https://sydneymaves.github.io/CP255_TermProject_DCBikeshare/count_start_bubble.html)
![Screen Shot 2022-05-07 at 9 24 18 PM](https://user-images.githubusercontent.com/95829239/167281676-e9d28ab7-8f86-487a-b9d4-15efe0c50ebe.png)


## Next Steps

As I mentioned previously, I would really like to spend more time learning how to use OSMnx and NetworkX to find the shortest path between two nodes and to create isochrone maps. I was able to aggregate the number of rides going from one station to every combination of end locations for a given month and then locate the nearest ox_node to each of those start and end station locations. I have, however, had difficulty iterating through this list of unique origin-destination pairs to identify the shortest path traveled. 

I also came close to being able to being able to create an isochrone map which shows which areas of the city are within two, four, or six minute walking distances of a station. I had difficulty when iterating through each of the 675 bikeshare stations that exist in the region. I will continue to trouble shoot this for future work. The map below shows the isochrone network for one station location. 

![Screen Shot 2022-05-07 at 9 47 06 PM](https://user-images.githubusercontent.com/95829239/167282259-f9052c53-b827-49b9-823b-395068740fe9.png)

## References
Anderson, Karl, Samuel D. Blanchard, Derek Cheah, and Drew Levitt. 2017. “Incorporating Equity and Resiliency in Municipal Transportation Planning: Case Study of Mobility Hubs in Oakland, California.” Transportation Research Record: Journal of the Transportation Research Board 2653 (1): 65–74. https://doi.org/10.3141/2653-08.

Boeing, G. "OSMnx: New Methods for Acquiring, Constructing, Analyzing, and Visualizing Complex Street Networks." Computers, Environment and Urban Systems 65 (2017), pp. 126-139.

Boeing, Geoff. (2017) 2022. OSMnx Examples. Jupyter Notebook. https://github.com/gboeing/osmnx-examples/blob/4ad81595cf7ac1a5898c2d88abae792839f40330/notebooks/13-isolines-isochrones.ipynb.

Brown, Brytanee. 2017. “OakMob 101: A Case Study in Expanding Access to Shared Mobility.” TransForm. July 10, 2017. https://www.transformca.org/transform-report/oakmob-101-case-study-expanding-access-shared-mobility.

Capital Bikeshare. 2022. “System Data.” Capital Bikeshare. 2022. http://ride.capitalbikeshare.com/system-data.

McNeil, Nathan, John MacArthur, Joseph Broach, Austin Cummings, Rae-Leigh Stark, Rebecca Sanders, and Adrian Witte. 2019. “National Scan of Bike Share Equity Programs: Approaches and Best Practices for Promoting Equity in Bike Share.” TREC Final Reports, July. https://doi.org/10.15760/trec.224.
Open Data DC. 2022. “Open Data DC.” 2022. https://opendata.dc.gov/.

United States Census Bureau. 2020a. “DP05: ACS Demographic and Housing Estimates (ACS 5-Year Estimates).” 2020. https://data.census.gov/cedsci/table?q=dp05.

———. 2020b. “S1901: Income in the Past 12 Months (in 2020 Inflation-Adjusted Dollars) (ACS 5-Year).” 2020. https://data.census.gov/cedsci/table?q=s1901&tid=ACSST5Y2020.S1901.
