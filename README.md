# Citi Bike Tableau Challenge
This Tableau workbook uses Citi Bike data gathered in March, 2024 from Jersey City. Using this data, we will be attempting to address the following questions:
1.	Are riders using the service leaving Jersey City?
2.	How long are riders using their bike rental?
3.	When are people taking Citi Bike rentals?
https://public.tableau.com/app/profile/eric.zhou1441/viz/Module18Challenge_17142374801400/Story?publish=yes# Tableau Story
## Map 1
This map simply displays the starting positions of each ride. Each ride is color coded, and these colors will be referenced in Map 2.
## Map 2
This map displays the ending positions of each ride. Each point is color coded based on the station from which the ride started. The size of each point is sized based on the number of riders ending at each station. From here, we can see that there are riders that went into New York City. However, from this map alone, it is difficult to quantify how many rides went from Jersey City to New York City.
## Dashboard 1
In this dashboard, we will first create a bar graph to display the number of rides ending at each station. Each bar is then color coded based on whether the end station is a Jersey City station. From here, we see that the most popular stations outside of the city are in Columbus Drive, Grand St & 14 St, and Washington St. The second bar graph displays the number of rides starting at each station. Here, the bars are split by number of rides ending inside or outside of Jersey City. We can see here that most riders are staying within Jersey City across all stations.
A set was necessary for creating the sheets used in this dashboard. To do this, the set simply selects all stations in Jersey City as “In” and other stations or null values as “Out”.
## Dashboard 2
Next, we are visualizing the ride duration and distance of rides. Some calculated values were necessary before creating visualization. 
This video guide was used to determine distances between starting and ending stations.
https://www.youtube.com/watch?v=HiRGubVsvi4
The following calculations were created to create a “distance” value in miles for each ride.
Origin = MAKEPOINT([Start Lat],[Start Lng])
Destination = MAKEPOINT([End Lat],[End Lng])

Distance = Distance([Origin],[Destination],'mi')
The following calculation was created to determine the duration of the ride in minutes.
Ride Time = DATEDIFF('minute',[Started At],[Ended At])

Now when we plot for number of rides along time and distance, we see that rides skew heavily on the shorter side, especially in ride time. However, when plotting for number of rides for each duration of the ride, we can color code the line plot by distance travel. Using this, we can see that longer ride times aren’t resulting in longer distances travelled. To investigate this further, a scatterplot comparing distance and time of rides is created. The highest R squared value fit was a logarithmic fit at an R squared value of 0.18. This indicates a weak logarithmic correlation. While one might expect that longer ride times lead to longer distances travelled, this is clearly not the case. It is very possible that riders are stopping at places along the way or are not travelling directly between start and end points.
## Dashboard 3
In this dashboard, we are examining when riders are renting Citi Bikes. From the bar chart showing the number of rides per day of the week, we can see that Friday and Sunday are the most popular days to ride. This is somewhat surprising as I expected either the weekend (Friday through Sunday) or the work week (Monday through Friday) to dominate the number of rides. Saturday is especially surprising for how low the number of rides is. From the line chart showing the number of rides taken at each hour of the day, we can see a peak between 7-9 AM and 4-6 PM. This corresponds to the expected morning and afternoon rush hours. Finally, a bar chart plots the number of rides starting at each station and splits each bar day of the week. For the most part, distribution of rides per day of the week seem to reflect the overall number of rides per day of the week.
