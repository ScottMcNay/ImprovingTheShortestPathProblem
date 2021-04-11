# ImprovingTheShortestPathProblem
By Scott McNay, 2021-04-06. Licensed under MIT license.

The various algorithms for determining the best path (A* Search, Bellman-Ford, Dijkstra’s, Floyd-Warshall, Johnson’s) all seem to have mathematical graphs in mind and one-time use. Real-world maps, though, have some specific features which should allow optimization, including:

* Start points tend to cluster, such as in cities.
* Connections between regions tend to bottleneck, especially when there are features such as rivers and mountains.
* The same maps will be reused many times, yet are too complex to store all possible start/end pairs.

With this in mind, it should be possible to determine the best path more efficiently by breaking maps into regions at a number of size levels, then pre-calculating, for each region, the shortest path to each location on the border of the region. Note that sometimes this path may go outside the region (curving mountain roads, for example). After that, you only need to check the intersection of the list of paths from starting point A, to the border of the region A is in, and the list of paths from the border of the region B is in, to ending point B. The fastest results will probably be when A and B are in adjacent large regions.

For example, if you are traveling from New York to San Francisco, the best route will generally bottleneck to a small number of highways. Similarly, city, county, and state borders and rivers, may make good region borders. So, you’d only need to determine the combined shortest route from a list of approximately 7:

1. from point A to the county border (since New York City covers multiple counties)
2. from the county border to the city limits of New York City, 
3. from there to the border of New York State, 
4. from there to the Mississippi River, 
5. from there to the border of California, 
6. from there to the border of the City and County of San Francisco, and 
7. from there to point B.

Judging from the time some trips take to calculate, it appears that modern mapping systems do not break down by region as described above, which is why this is proposed.

Disclaimer: I did a cursory search for information about optimized Shortest Path algorithms and only found the algorithms listed above.

Request: Please link implementations (or links to implementations) to this repository.
