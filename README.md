# Hey! A Data Collection & Management project is available here🩵


In this repo you will find **one case study** on building a **Data infrastruture** (storing, collecting with scrapping technic and data storage).
* The goal was to **select top 5 french cities** 🌇, from 35 in total, where **humitidy rate and temperature was ideal** for persons with **arthritis** (*nominatim API*) 🌥️ 🌤️. 
* After that city selection, I **scrapped Booking website** 🕷️in order to select **top 9 hotels for each of those 5 best cities**. 🏨
* Then the two Dataframes obtained has been merged and made accessible by **storing it into a S3 bucket**. 📂
* Finally, I **created a database** so that it can be directly available by others for analysis purposes.  ✅

---
## ➡️ The project is divided in two parts, please follow this order : 🤗

 * 🟡 🔗 **PART 1** :  Have a look at <ins>*Part_1_Top5_Cities_Weather_dorianedoyondousse.ipynb*</ins>  : top 5 french cities 🌇
   
    * 👉🏽 **Top5cities_forecast_weather.csv** is the dataframe obtained and *used for the rest of the project*. ⭐️ 
        * It's accessory but you can also check those obtained during the process : 
           * *all_cities_forecast.csv*  : all of the 35 cities weather infos
           * *all_cities_MEAN_weather_forecast.csv*  : mean of weather characterics for the 35 initial cities </br>


 * 🟢 🔗 **PART 2**: <ins>*Part_2_ScrapeBooking_dorianedoyondousse.ipynb*</ins> : scrapping Booking website 🕷️
   
    * 👉🏽 **scraped_hotels.json** is the json file obtained after scrapping the website. ⭐️ 
    * 👉🏽 **csv_scraping_kayak_project.csv** is the dataframe where all hotels infos collecting during the scrapping has been put.
    * 👉🏽 **merge_df** is the dataframe where I merged infos from top 5 cities weather and scrapped hotels, in order to create a unique file gathering data ⭐️ 
        * 🛜 **Link_s3_dataset_url.md** : merge_df has been stored in a S3 bucket, check the md file or click down bellow : 
            * https://project-scraping-doshdyndss-jedha-certification.s3.eu-west-3.amazonaws.com/merge_df.csv  
    * 👉🏽 **best_hotels.db**👈 is the database created, based on the merge_df, so that you can directly work on it with SQL ⭐️ 


---
      
 - 👇🏽 *Down here you have the full description of projects from Jedha, hope you enjoy them as did making them* 👇🏽


---
---
![Kayak](https://seekvectorlogo.com/wp-content/uploads/2018/01/kayak-vector-logo.png)

# Plan your trip with Kayak 

## Company's description 📇

<a href="https://www.kayak.com" target="_blank">Kayak</a> is a travel search engine that helps user plan their next trip at the best price.

The company was founded in 2004 by Steve Hafner & Paul M. English. After a few rounds of fundraising, Kayak was acquired by <a href="https://www.bookingholdings.com/" target="_blank">Booking Holdings</a> which now holds: 

* <a href="https://booking.com/" target="_blank">Booking.com</a>
* <a href="https://kayak.com/" target="_blank">Kayak</a>
* <a href="https://www.priceline.com/" target="_blank">Priceline</a>
* <a href="https://www.agoda.com/" target="_blank">Agoda</a>
* <a href="https://Rentalcars.com/" target="_blank">RentalCars</a>
* <a href="https://www.opentable.com/" target="_blank">OpenTable</a>

With over \$300 million revenue a year, Kayak operates in almost all countries and all languages to help their users book travels accros the globe. 


## Project 🚧

The marketing team needs help on a new project. After doing some user research, the team discovered that **70% of their users who are planning a trip would like to have more information about the destination they are going to**. 

In addition, user research shows that **people tend to be defiant about the information they are reading if they don't know the brand** which produced the content. 

Therefore, Kayak Marketing Team would like to create an application that will recommend where people should plan their next holidays. The application should be based on real data about:

* Weather 
* Hotels in the area 

The application should then be able to recommend the best destinations and hotels based on the above variables at any given time. 


## Goals 🎯

As the project has just started, your team doesn't have any data that can be used to create this application. Therefore, your job will be to: 

* Scrape data from destinations 
* Get weather data from each destination 
* Get hotels' info about each destination
* Store all the information above in a data lake
* Extract, transform and load cleaned data from your datalake to a data warehouse


## Scope of this project 🖼️

Marketing team wants to focus first on the best cities to travel to in France. According <a href="https://one-week-in.com/35-cities-to-visit-in-france/" target="_blank">One Week In.com</a> here are the top-35 cities to visit in France: 

```python 
["Mont Saint Michel",
"St Malo",
"Bayeux",
"Le Havre",
"Rouen",
"Paris",
"Amiens",
"Lille",
"Strasbourg",
"Chateau du Haut Koenigsbourg",
"Colmar",
"Eguisheim",
"Besancon",
"Dijon",
"Annecy",
"Grenoble",
"Lyon",
"Gorges du Verdon",
"Bormes les Mimosas",
"Cassis",
"Marseille",
"Aix en Provence",
"Avignon",
"Uzes",
"Nimes",
"Aigues Mortes",
"Saintes Maries de la mer",
"Collioure",
"Carcassonne",
"Ariege",
"Toulouse",
"Montauban",
"Biarritz",
"Bayonne",
"La Rochelle"]
```

Your team should focus **only on the above cities for your project**. 

## Helpers 🦮

To help you achieve this project, here are a few tips that should help you

### Get weather data with an API 

*   Use https://nominatim.org/ to get the gps coordinates of all the cities (no subscription required) Documentation : https://nominatim.org/release-docs/develop/api/Search/

*   Use https://openweathermap.org/appid (you have to subscribe to get a free apikey) and https://openweathermap.org/api/one-call-api to get some information about the weather for the 35 cities and put it in a DataFrame

*   Determine the list of cities where the weather will be the nicest within the next 7 days For example, you can use the values of daily.pop and daily.rain to compute the expected volume of rain within the next 7 days... But it's only an example, actually you can have different opinions on a what a nice weather would be like 😎 Maybe the most important criterion for you is the temperature or humidity, so feel free to change the rules !

*   Save all the results in a `.csv` file, you will use it later 😉 You can save all the informations that seem important to you ! Don't forget to save the name of the cities, and also to create a column containing a unique identifier (id) of each city (this is important for what's next in the project)

*   Use plotly to display the best destinations on a map

### Scrape Booking.com 

Since BookingHoldings doesn't have aggregated databases, it will be much faster to scrape data directly from booking.com 

You can scrap as many information asyou want, but we suggest that you get at least:

*   hotel name,
*   Url to its booking.com page,
*   Its coordinates: latitude and longitude
*   Score given by the website users
*   Text description of the hotel


### Create your data lake using S3 

Once you managed to build your dataset, you should store into S3 as a csv file. 

### ETL 

Once you uploaded your data onto S3, it will be better for the next data analysis team to extract clean data directly from a Data Warehouse. Therefore, create a SQL Database using AWS RDS, extract your data from S3 and store it in your newly created DB. 


## Deliverable 📬

To complete this project, your team should deliver:

* A `.csv` file in an S3 bucket containing enriched information about weather and hotels for each french city

* A SQL Database where we should be able to get the same cleaned data from S3 

* Two maps where you should have a Top-5 destinations and a Top-20 hotels in the area. You can use plotly or any other library to do so. It should look something like this: 

![Map](https://full-stack-assets.s3.eu-west-3.amazonaws.com/images/Kayak_best_destination_project.png)
