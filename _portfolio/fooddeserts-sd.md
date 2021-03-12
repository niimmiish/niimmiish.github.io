---
title: " " # provide a title here if you want a link to show in the grid on the "Portfolio" landing page.
header:
  overlay_image: /assets/images/martijn-baudoin-unsplash.jpg
  caption: "Photo credit: [**Martijn Baudoinr**](https://www.unsplash.com)"
permalink: /portfolio/fooddeserts-sd/
date: 2021-02-24
toc: true
toc_label: "Contents"
---

# Identifying Food Deserts in South Dakota
*December 17, 2009*

## Summary
Many U.S. residents face an abundance of food choices in a traditional supermarket. Yet for many others, access to healthy and affordable food is limited or even non-existent. Population decline in rural communities due to shrinking economies results in fewer grocery outlets serving larger areas. A <span style="color: #4b6584; background-color: #ecf0f1">**region with diminished or non-existent geographic access to retail food is considered a food desert**</span> (Morton et al., 2005).

The term **“food desert”** is believed to have originated in the U.K. in the 1990s to describe the lack of access to retail food due to the closure of grocery stores in deteriorating neighborhoods of large cities. In the U.S., however, absence of grocery stores is an insufficient measure. The large presence of convenience stores and mini-marts does provide for access to food but clouds the importance of access to quality and healthy food at competitive prices. 

Alternately, a food desert community in the U.S. is more appropriately defined based on travel distance to large food retailers (Morton and Blanchard, 2007). In this project, I have used the food desert definition generally accepted in the literature to identify and characterize food deserts in South Dakota.

This summary [presentation]({{ site.baseurl }}/assets/pdfs/SDFoodDeserts.pdf){: style="color: #2980b9"} provides the complete analysis.

## Goals
The purpose of this project was to <span style="color: #4b6584; background-color: #ecf0f1">identify and characterize food deserts --- regions with **limited or non-existent access to healthy and affordable retail food** in South Dakota, a large rural state.</span> A Geographic Information Systems (GIS) approach is presented for the necessary manipulation and analysis of spatial and demographic data resulting in the visualization of food deserts. Finally, characterization of food deserts using demographic data presents insights into the socio-economic disparities evidenced in such areas.

## Objectives
For the current analysis, the food desert metaphor is considered equivalent to the degree of geographic access to retail food for the population in South Dakota. To measure such access, the following are the objectives:
- Obtain residential locations, census tracts, cities, counties, state, roads, and supermarket data for South Dakota.
- Calculate distance from residential locations to supermarkets and aggregate by census tract.
- Locate cities, counties, and major roads in the state to visualize the relative locations of supermarkets and food deserts.

## Data
**Reference Data:** The Mastering ArcGIS, 4th Ed., (MGIS) exercise data CD provided boundary shapefiles for the state of South Dakota and its counties, as well as a point layer of cities. [Original Geographic Coordinate System (GCS): NAD 1983]

**Residential locations:** Since I was not able to readily obtain a point layer for individual residential locations across South Dakota I chose to use census block centroids as a proxy for residential units within a block. To calculate block centroids, I obtained the census block boundary shapefile from the U.S. Census Bureau. [Original GCS: NAD 1983]

**Supermarket locations:** Supermarket data was obtained from ReferenceUSA. The data was restricted to North American Industry Classification System code 451100 [Supermarket and other Grocery (except Convenience) Stores] and 2,500+ square feet of space. I chose to ignore convenience stores as they typically reflect poor food choices in terms of nutrition and price (Morton and Blanchard, 2007).

**Census Tracts:** I obtained a shapefile of census tracts and tract-level demographic data for South Dakota from the U.S. Census Bureau. [Original GCS: NAD 1983]

**Roads:** The South Dakota Department of Transportation (SDDOT) website provided a shapefile of statewide roads. [Original GCS: NAD 1983].

**Projection:** South Dakota is a large state with a longer east-west extent. Since my analysis required distance calculations, I chose to use a state plane coordinate system projection, which would preserve distances well. I specifically chose the NAD83 StatePlane South Dakota South FIPS 4002 zone as some of the data I planned to use from MGIS were already in this coordinate system.

## Analysis
I began by converting the state, county, tracts, blocks, roads, and cities shapefiles into the State Plane projection mentioned earlier and imported them into a personal geodatabase. Then, I plotted the supermarkets data using the latitude/longitude coordinates and the NAD 1983 GCS, exported the resultant layer as a shapefile, and then imported it into the geodatabase with the aforementioned State Plane projection. Data for residential point locations could not be readily sourced. Therefore, as a proxy for residential locations, I used centroids of census blocks, which I calculated using the Calculate Field Geometry option in ArcMap, and saved the output in the geodatabase. 

The next step was to calculate the closest supermarket to each census block centroid. For this, I used a Simple Distance join with block centroids as the target layer, obtaining the distance to the closest supermarket (Output 1). Using the census tracts as the target, I performed a Summarized Inside join with Output 1, to obtain the mean distance to supermarkets by census tract (Output 2). Using Output 2, I displayed mean distance to supermarkets by census tracts via a choropleth map. 

A series of maps in this [presentation]({{ site.baseurl }}/assets/pdfs/SDFoodDeserts.pdf){: style="color: #2980b9"} provides a visual documentation of the food desert categorization process. Finally, I analyzed tract level demographic data in Excel and ArcMap to characterize the food desert and non-food desert tracts. 

## Results
South Dakota is a large rural Midwestern state. According to the 2000 U.S. Census it had a population of 754,844 people and a land area of 75,885 square miles. The mean per capita money income was $17,562 and the poverty rate was 13.2%.

Morton and Blanchard (2007) used a 10-mile threshold to determine food desert tracts based on the 1995 National Transportation Survey (NTS) finding that the average U.S. resident traveled 8 miles for grocery trips. Accounting for longer travel distances in a rural state and a Euclidean distance calculation, I picked a threshold of 12 miles i.e., 1.5 times the NTS finding. Therefore, any tract with a mean travel distance of over 12 miles to supermarkets was classified as a food desert.

Based on this approach, 75 out of 235 (or 31.9%) tracts are classified as food deserts, which account for 16.9% of the state population. In food desert tracts, the mean distance to food retailers is 17.5 miles while in non-food deserts it is 6.3 miles. Table 1 shows a comparison of some key characteristics between food deserts and non food deserts, with the shaded cells highlighting the demographic disparity of food deserts.

<caption><span style="font-size: 15px; font-weight: bold">Table 1. Characteristics of Food Desert and Non-Food Desert Tracts</span></caption>

|----------------+--------------------+------------------------|
| Characteristic | Food Desert Tracts | Non-Food Desert Tracts |
|:----|------------:|-----------------:|
| Median Household Income         | <font color="red">26,156</font>    | 34,600    |
| Population 18 and over          | <font color="red">75,321</font>    | 473,450   |
|---------------------------------+------------------------------------+-----------|
| Percent population 20 to 34     | <font color="red">14.4</font>      | 19.8      |
| Percent population 65 and up    | <font color="red">15.1</font>      | 14.2      |
| Percent rural population        | <font color="red">93.7</font>      | 40.4      |
|---------------------------------+------------------------------------+-----------|
| Total Housing Units             | 49,109    | 274,099   |
| Percentage of people with High School diploma or more, age 25 and more     | <font color="red">78.3</font>     | 84.0    |
| Percent disabled, 21-64 years   | <font color="red">18.6</font>      | 15.1      |
| Percent disabled, 65 and over   | 39.4      | 39.6      |
| Percent families in poverty     | <font color="red">16.4</font>      | 8.1       |
| Percent individuals in poverty  | <font color="red">22.1</font>      | 11.6      |
| Percent 65 and over in poverty  | <font color="red">22.0</font>    | 11.0      |
|---------------------------------+------------------------------------+-----------|
{: rules="groups"}

- Of the 20 poorest census tracts (based on rate of individual poverty), 15 are identified as food deserts. Five of these 15 tracts are also among the 20 tracts with the lowest educational attainment (based on percentage of population age 25 and up with a High School diploma or more).
- Of the 20 tracts with the lowest educational attainment, 14 are identified as food deserts.
- Of the 20 food desert tracts with the greatest distance from supermarkets: 
  - 4 are among the top 20 tracts with greatest rate of individual poverty.
  - 3 are among the top 20 tracts with the least educational attainment.
  - 2 are among the top 20 tracts with the least median household Income.

## Conclusions
- The Morton and Blanchard study (2007) identified 31 of 66 counties in South Dakota as food deserts. Using a simple and replicable GIS approach for determining food deserts based on generally accepted criteria in the literature and proxies for residential locations, my analysis yielded 31.9% of census tracts as food deserts.
- The characteristics of food desert tracts show that a significant portion of South Dakota’s rural population lacks access to healthy and affordable food. Moreover, populace which is already demographically disadvantaged, at or below poverty limits, and with less than a high school diploma is inherently at greater risk for further socio-economic hardship, exposure to an unhealthy diet, and potential health consequences.

## Future Research
This project has some evident limitations. First, the analysis is conducted within a state boundary, but residents are not restricted by such a boundary in accessing retail food. Second, using supermarkets precludes consideration of community gardens and farmers markets.

Future research could aim to address these issues and others: using accurate residential locations in calculating true travel distances along a road network; examination of economic (affordability) and informational (nutritional knowledge) access; health consequences of food deserts.

## References
- Morton, L.W. and Blanchard, T.C. (2007). “Starved for Access: Life in Rural America’s Food Deserts.” Rural Realities 1 (4): 1-10.
- Morton, L.W. et al., (2005). “Solving the Problems of Iowa Food Deserts: Food Insecurity and Perceptions of Civic Structure.” Rural Sociology 70 (1): 94-112.
- Price, M. Mastering ArcGIS, 4th Edition.
- [ReferenceUSA](www.referenceusa.com). *Accessed November 2009*.
- [South Dakota Department of Transportation (SDDOT)](https://arcgis.sd.gov/IMS/DOT/DOTweb/Default.spx). *Accessed November 2009*.
- [U.S. Census Bureau](https://www.census.gov). *Accessed November 2009*.
