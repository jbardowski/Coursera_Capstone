# A Comparison of Museums and Cultural Arts Scenes Between Metropolises


**Introduction**

A small tour-guide company that focuses on museums, historical sites, and the cultural and performing arts is looking to expand by opening a new office in a new city somewhere in the US or Western Europe. From a short list of preferred locations, the company has tasked us to determine in which city is the most appropriate to open an office.

Specifically, between four pre-selected cities (New York, Paris, London, and Toronto), the company would like to know which metropolis has ***(i)*** the highest number of museums, arts centers, and historic sites, ***(ii)*** the highest concentration of museums, as well as in which neighborhoods they are located, and ***(iii)*** a comparison of the surrounding neighborhoods (i.e., what venues are around the museums).


**Describe the data**

To facilitate the client’s request, we leverage data from ***(a)*** Wikipedia, which we scrape to *[i]* find the neighborhood names and addresses for Paris ([link](https://en.wikipedia.org/wiki/Arrondissements_of_Paris)), London ([link](https://en.wikipedia.org/wiki/List_of_areas_of_London)), and Toronto ([link](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M)), and *[ii]* find the total area for each city that we used to scale our dataset ([link](https://en.wikipedia.org/wiki/List_of_largest_cities)), ***(b)*** a local JSON file downloaded from Coursera for the neighborhood names and addresses in New York, and ***(c)*** FourSquare's API to search for and download venues in each city's neighborhoods.


**Methodology section**

[which represents the main component of the report where you discuss and describe any exploratory data analysis that you did, any inferential statistical testing that you performed, if any, and what machine learnings were used and why.
]

Using the sources described above, we downloaded the necessary neighborhood names and areas for each city from the web into pandas dataframes, formatting to single out addressess for each neighborhood. Then, utilizing the geocode python library, we determined the geographical coordinates for each city and their respective neighborhoods. 

With the coordinates of each neighborhood from geocode, we accessed FourSquare's API to get all venues within half mile radius. Keeping only the neighborhoods that contained historical sites, museums, and cultural and performing arts centers, we visualized those neighborhoods on a map using the folium library (***Exhibits 1-4***).

**Exhibit 1: New York Neighborhoods with Museums/Arts Centers**
![New York Neighborhoods with Museums/Arts Centers](Images/nyc_hoods_museums.png)

**Exhibit 2: Paris Neighborhoods with Museums/Arts Centers**
![Paris Neighborhoods with Museums/Arts Centers](Images/paris_hoods_museums.png)

**Exhibit 3: London Neighborhoods with Museums/Arts Centers**
![London Neighborhoods with Museums/Arts Centers](Images/london_hoods_museums.png)

**Exhibit 4: Toronto Neighborhoods with Museums/Arts Centers**
![Toronto Neighborhoods with Museums/Arts Centers](Images/toronto_hoods_museums.png)

Furthermore, we analyzed the aggregate number of museums, historic sites, and arts centers between each city (***Exhibit 5***). 

**Exhibit 5: Absolute Number of Museums/Arts Centers Between Cities**
![Museums/Arts Centers per City](Images/unscaled_count.png)

The natural problem we faced, however, is how do we adjust for differences between cities so that we could analyze on a equal footing? In response, we selected to scale each city by its respective area. That is, we again used Wikipedia to downloaded the area, in squared kilometers, for each city. 

We then divided the matrix of the aggregate number of museums, historic sites, and arts centers for each city by the vector of each city's square-kilometer area (***Exhibit 6***).

**Exhibit 6: Scaled Number of Museums/Arts Centers Between Cities**
![Museums/Arts Centers per City Scaled](Images/scaled_count.png)

In order to describe the neighborhoods that surround located museums, historical sites, and cultural/performing arts centers in each city, we opted to cluster the neighborhoods based on the venue categories in each. Specifically, we used pandas onehot encoding method to segment the targeted neighborhoods by FourSquare's venue category feature, then ran scikit-learn's k-means clustering algorithm.


**Results section**

In this section, we discuss the results of our analysis by each city. 

- New York

In ***Exhibit 7***, we map New York City's 
......ny cluster mapped + cluster value counts + cluster breakout

**Exhibit 7: **
![ny_cluster_map](Images/ny_clustered_map.png)

**Exhibit 8: **
![ny_museum_counts](Images/ny_cluster_count.png)

**Exhibit 9: **
![ny_cluster_breakout](Images/ny_cluster_breakout.png)



- summarize the most common venues appearing in neighborhoods with museums/arts


**Discussion section**

[Discussion section where you discuss any observations you noted and any recommendations you can make based on the results.
Conclusion section where you conclude the report.]

- recommend which city our client should select for expansion