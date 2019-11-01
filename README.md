# New restaurant in the capital of Croatia/Europe? Let's try to sugest the best place!

## A description of the problem and a discussion of the background

I will try to sugest the best place for the restaurant in Zagreb. Zagreb is the capital of the Croatia and Croatia is one small country in the European Union. Zagreb is the biggest city in the Croatia and it has almost 800 thousands people. Zagreb is devided in 17 districts and whole city area has 641 square kilometers. Some districts are residential and some are more industrial. I hope that type of these districts will be obvious. You can find the list of districts: https://en.wikipedia.org/wiki/Zagreb#City_districts

![The list of districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/1.png)

## A description of the data and how it will be used to solve the problem

Croatia is not as digitized as Hong Kong or Canada, so I will have to extract some data manually. Fortunately, I have found the map of Zagreb with added border layer of all districts. Here is the link:

https://geoportal.zagreb.hr/Karta

![Map of Zagreb with districts](https://raw.githubusercontent.com/kristian1971/kristian1971.github.io/master/pictures/2.png)

Next step is to find lattitude and longitude for significant border points of every district and put them in CSV files, upload files to https://cloud.ibm.com and find central point of every district of Zagreb. I will use one simple algorithm to find central point in Paython.

Next step will be getting data from Foursquare of recommended venues inside 1000 meters radius of every district of Zagreb, calculate the Top ten most common venues by its category as features. After that one-hot encoding to the vanues categories will be created and the mean of each category for every district of Zagreb will be calculated. Finaly, before clustering, the frequency of categories for each part will be calculated.

Clustering is the final part and the k-means will be used, because here we have an unlabelled dataset, so this belongs to unsupervisied learning. Clustering will help us to find out the pattern in dataset and identify the similar districts. The hyperparameter k will be set to k=6 and this means that city will be separated in 6 clusters. 

On the end I hope that I will be able to recommend in which district to open a new restaurant!

