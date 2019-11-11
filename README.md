# New restaurant in the capital of Croatia/Europe? Let's try to sugest the best place!

## A description of the problem and a discussion of the background

I will try to sugest the best place for the restaurant in Zagreb. Zagreb is the capital of the Croatia and Croatia is one small country in the European Union. Zagreb is the biggest city in the Croatia and it has almost 800 thousands people. Zagreb is devided in 17 districts and whole city area has 641 square kilometers. Some districts are residential and some are more industrial. I hope that type of these districts will be obvious. You can find the list of districts: https://en.wikipedia.org/wiki/Zagreb#City_districts

![The list of districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/1.png)

## A description of the data and how it will be used to solve the problem

Croatia is not as digitized as Hong Kong or Canada, so I will have to extract some data manually. Fortunately, I have found the map of Zagreb with added border layer of all districts. Here is the link:

https://geoportal.zagreb.hr/Karta
![Map of Zagreb with districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/2.png)

Next step is to find lattitude and longitude for significant border points of every district and put them in CSV files, upload files to https://cloud.ibm.com and find central point of every district of Zagreb. I will use one simple algorithm to find central point in Python.

Next step will be getting data from Foursquare of recommended venues inside 1000 meters radius of every district of Zagreb, calculate the Top ten most common venues by its category as features. After that one-hot encoding to the vanues categories will be created and the mean of each category for every district of Zagreb will be calculated. Finaly, before clustering, the frequency of categories for each part will be calculated.

Clustering is the final part and the k-means will be used, because here we have an unlabelled dataset, so this belongs to unsupervisied learning. Clustering will help us to find out the pattern in dataset and identify the similar districts. The hyperparameter k will be set to k=6 and this means that city will be separated in 6 clusters. 

On the end I hope that I will be able to recommend in which district to open a new restaurant!

_________________________________________________________________________________________________________

# ...so let's see what have I done... :-)

## Data

I have known that Croatia is not so digitized like western European countries or USA and as I expected, some tasks had to be done manualy. 
First step was to find central point of every district in Zagreb. I used geoportal on the web adress: https://geoportal.zagreb.hr/Karta , so I made 17 CSV file with 10 to 20 points that define district polygon. These points were defined by longitude and letitude. Here is the figure of one CSV file open in Notepad++.

![Longitude and letitude of 10 district points](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/29.png)

After that I used some python code from this gist (https://gist.github.com/tlhunter/0ea604b77775b3e7d7d25ea0f70a23eb) to find central point of every district. Final result of this is table with central points of every district in Zagreb. Here is the figure:

![Tabli with letitude and longitude of districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/3.png)

Another source of data is Foursquare service and I decided to get data of recommended venues inside 1500 meters radius of every district, calculate the top ten most common venues by its category as features.

## Methodology

# Explore area and data

I used folium library to mark central points of every district in Zagreb. It can be seen in the next figure:

![Central point of districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/4.png)

From Foursqare service I have got more than five huderts venues in Zagreb, so here is the list:

![List of venues](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/5.png)

In the next table it can be seen how many venues can be found in every district if you ask Foursqare:

![Number of venues by district](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/6.png)

One-hot encoding table based on the vanues categories, gets mean of each category for every district.

![One-hot encoding table](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/7.png)

In one moment i have realised that one district is missing. It was district called Brezovica and in this district was without any venue. I deleted it from table. It is the district with the lowest population density by square kilometer.

# Clustering

k-means is a clustering algorithm that has been used in the project. This is an unsupervisied learning project because we have an unlabelled dataset. K-means clustering group data into k clusters so we can find a pattern in them. On the begining I tought that 6 clasters will be enough but finaly I chose 3 clasters. So here are results in the table:

![Table with clusters](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/8.png)

## Results

In the next picture you can se distribution of clasters.

![Distribution of clusters](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/9.png)

There are one main claster with 13 districts and two clasters with one and two districts. When you analyse picture you can see that red circles are in the hilly part of Zagreb as well as the green circle near the upper border of the picture. In the next three tables you can find five most common venues in every cluster. 

# CLUSTER1

![Cluster 1](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/91.png)

# CLUSTER2

![Cluster 2](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/92.png)

# CLUSTER3

![Cluster 3](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/93.png)

# Discusion and conclusion

Final result is accurate but not so precise. More information like average income and population density will be helpful to rise quality of the result. On the other hand we get results and we can conclude that the biggist cluster is the best for the new restaurant mostly because other clusters are mostly in the filly and afforested part of Zagreb.


