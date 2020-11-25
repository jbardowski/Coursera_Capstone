# Cultural Arts Scene Comparison

A small tour-guide company that focuses on museums and cultural arts centers is looking to expand by opening a new office in a new city somewhere in the US or Western Europe. From a short list of preferred locations, the company has tasked us to determine in which city is the most appropriate to expand.

Specifically, the company would like to know which metropolis has (i) the most number of museums and cultural arts centers, (ii) the highest concentration of museums, as well as where they are located, and (iii) a comparison of the surrounding neighborhoods.

To facilitate this request, we leverage (a) open source data to find neighborhoods (e.g., Wikipedia) and determine their specific coordinates (we use geopy where possible), and (b) FourSquare's API to search for venues in a given city's neighborhoods, which we use to find museums and cultural arts centers. 

We then, for each city, tally the number of museums and cultural arts centers, plot their coordinates on a map for visualization, and cluster the venues in each neighbo.

<GET DISTANCE> .... then take the average distance between each venue as a measure of concentration.
...The cities are then ordered by most museums/concentration ...and our conclusions are submitted to the company.