# New restaurant in the capital of Croatia/Europe? Let's try to sugest the best place!

## A description of the problem and a discussion of the background

I will try to sugest the best place for the restaurant in Zagreb. Zagreb is the capitol of the Croatia and Croatia is one small country in the European Union. Zagreb is the biggest town in the Croatia and it has almost 800 thousands people. Zagreb is devided in 17 parts and whole town area has 641 square kilometers. Some parts are residential and some parts are more industrial. I hope that type of these parts will be obvious.

## A description of the data and how it will be used to solve the problem

Croatia is not as digitized as Hong Kong or Canada, so I will have to extract some data manually. Fortunately, I have found map of Zagreb with added border layer of all parts. Here is the link:

https://geoportal.zagreb.hr/Karta

Next step is to find lattitude and longitude for significant border points of every part and put them in CSV files, upload files to https://cloud.ibm.com and find central point of every part of Zagreb. I will use some simple algorithm to find central point in Paython. I 

Next step will be getting data from Foursquare of recommended venues inside 1000 meters radius of every part of Zagreb, calculate the Top ten most common venues by its category as features. After that one-hot encoding to the vanues categories will be created and the mean of each category for every part of Zagreb will be calculated. Finaly, before clustering, the frequency of categories for each part will be calculated.

Clustering is the final part and the k-means will be used, because here we have a unlabelled dataset, so this belongs to unsupervisied learning. Clustering will help us to find out the pattern in dataset and identify the similar parts. The hyperparameter k will be set to k=6 and this means that town will be separated in 6 clusters.

