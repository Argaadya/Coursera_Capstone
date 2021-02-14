# Coursera_Capstone

The following report highlight the general finding from the data analysis. Full report can be seen at the [Notebook](https://github.com/Argaadya/Coursera_Capstone/blob/main/week4.ipynb).

# Introduction

Indonesia is a big and vast countries, ranked 4 in hte list of countries by population. Based on the [worldmeters.info](https://www.worldometers.info/world-population/indonesia-population/), currently Indonesia has a population of 275 millions people. 

![Indonesia](https://images.mapsofworld.com/earthquake/1482303515indonesia-map.gif)

Indonesia is divided into 34 different provinces, scattered in 5 main islands and thousands of small islands. One of the most popular province is the capital province of Jakarta which is also one of the main financial hub in Indonesia. Another popular province is the province of Bali, which is famous as a tourist attraction both for domestic and international tourist with total contribution of almost 29% of the national foreign exchange.

This project will explore and find different cluster of neighborhood both in Jakarta and Bali to see if there is certain characteristics that is associated with each province or if both provinces share the same characteristics based on various places and landmarks on its neighborhood.

# Data

The postal code and information about each province and city will be gathered from https://postcode.id/, which will give us the following fields from the data table:

- Propinsi (Province): The name of the province
- Jenis (City Type): Type of the city: either city or regency
- Kabupaten/Kota: The name of the city/regency
- Kecamatan: The name of district in the city/regency
- Keluarahan: The name of the neighborhood
- Postcode: The postal code of the neighborhood

I will also use the `geocoder` package to get the latitude and longitude information from each district/neighborhood. To get the list of places and landmarks in each area, I will use the `Foursquare API`.

With the mentioned data collection method, I will be able to extracts various places and landmarks, including the top venues or top neighborhood with the most venues. 

# Methodology

I will use the clustering analysis to find different characteristics of each city and the respective neighborhood to see if Jakarta and Bali has the same overall characteristics based on each province's main features. Another business perspective is to determine if it is better to open up a restaurant in Bali or in Jakarta. Is Bali as a tourist attraction more associated with restaurant than Jakarta? Is it better to setup a contractor office in Jakarta since Jakarta is a capital and an economic districts? We will find out in this project. Combined with Principal Component Analysis (PCA), we will find the unique feature of each cluster and if a cluster has some anomaly or exceptional neighborhood compared to other cluster.

# Result

Using the postal code data, we have collected 267 neighborhoods from Jakarta and 714 neighborhoods from Bali. Using the data from Foursquare API we have the following top 5 venues from Jakarta:

- Indonesian Restaurant
- Coffee Shop
- Convenience Store
- Asian Restaurant
- Chinese Restaurant

The following is the top 5 venues from Bali:

- Indonesian Restaurant
- Asian Restaurant
- Convenience Store
- Hotel
- Cafe

K-Means clustering is done with k (number of clusters) = 5 based on the within sum of squared distance from Elbow method.

# Discussion

## K-Means Clustering

The following is the result of the cluster generated from K-Means:

### Cluster 0: Residence Area (36 Neighborhoods)

This cluster has the highest proportion of Convenience Store and Asian Store. The cluster is dominated by neighborhood from Jakarta. Since we see less fancy venues in this cluster and more about daily needs convenience store and generic restaurant, we will call them as the residence area.

### Cluster 1: Food and Beverage (188 Neighborhoods)

This cluster is dominated by neighborhoods from Jakarta, which has a lot of public space for hanging out such as the fast food restaurant, noodle house, Cafe, and coffee shop.

### Cluster 2: Food Truck and Shopping (22 Neighborhoods)

This cluster has very high amount of food truck venues, followed by the presence of department store, and arcade. This cluster is also the mix of Jakarta and Bali neighborhood, with the highest number of neighborhood is located in the Jakarta Timur (East Jakarta). 

### Cluster 3: Bali Resort (5 Neighborhoods)

This cluster consists of neighborhood that only has resort and BBQ Joint venues and exclusively only has neighborhood from Bali and no Jakarta. We will call this cluster the Bali resort.

### Cluster 4: Local Food (74 Neighborhoods)

This cluster is also dominated neighborhood from Jakarta with the `Indonesian Restaurant` has the highest presence in this area. If you want to open a local food restaurant, this is a great area.

## Principal Component Analysis

Using the Principal Components Analysis, we have found that Cluster 1 and cluster 2 is a generic cluster that has no apparent uniqueness compared to other cluster, such as cluster 3 with its resort, cluster 0 with its high number of convenience store and cluster 4 with high number of Indonesian restaurant.

# Conclusion

I will highlight some finding based on our data analysis:

- Jakarta and Bali is not so different, both has high number of food and beverage venues
- Bali has exclusive resort neighborhood area which is has no significant presence in Jakarta
- Jakarta as a capital and the most populous city in Indonesia has a lot of FnB venues as a place for people to hang out
- If you want to open up a restaurant, espescially Indonesian restaurant, you can set up in neighborhood from cluster 4
- If you are a contractor, you can setup your office in Bali in the neighborhood from cluster 3
