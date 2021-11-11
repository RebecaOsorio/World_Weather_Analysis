# Module 6 Challenge. World_Weather_Analysis

## Project

### Background
My Trip is a top travel technology company that specializes in internet related services in the hotel and lodging industry. Thought the module we worked with more than 500 random (latitudes and longitudes), find the nearest city, used linear regression to predict the best time of the year for people to plan their vacation and filter based on the users preferred travel criteria in order to find their ideal hotel anywhere.

### Overview of  the Challenge
For this Challenge, the Beta Users want to take the app to the next level. To achieve this, they want to be able to see the **weather description** in the weather data we've already retrieved in this module. Then, using the weather descriptions, the users will **input statements to filter the data for their weather preferences**, which will be used to **identify potential travel destinations and nearby hotels**. To finally, **create a list of four potential travel destinations**, and using the Google Maps Directions API, the user will see a **travel route between the four cities** as well as a marker layer map.


##  Resources

* **Data Source:** In this module, we worked with API's retrieved data from [Weather API](https://openweathermap.org/api), [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript/overview#Loading_the_Maps_API), [Places API](https://developers.google.com/maps/documentation/places/web-service/overview), and [Google Directions API](https://developers.google.com/maps/documentation/directions/overview).

* **Software:** Jupyter Notebook, Python 3.7.7, Matplotlib 2.2.2, Numpy 1.19.1, Requests 2.24.0, Pandas 1.1.3, Gmaps 0.9.0.


## Summary

### Retrieve Weather Data
In the `Weather_Database` Notebook, we created a New DataFrame that contains:
-   Latitude and longitude
-   Maximum temperature
-   Percent humidity
-   Percent cloudiness
-   Wind speed
-   Weather description (for example, clouds, fog, light rain, clear sky) 

We started generating a set of 2,000 random latitudes and longitudes, retrieve the nearest city for each combination using the `citipy` module, and perform an API call with the OpenWeatherMap so we could end with a DataFrame as the following:

![image](https://user-images.githubusercontent.com/90414330/141238792-b60c56b5-0399-4dc0-8598-41edbfd59820.png)


### Customer Travel Destinations Map
With input statements we retrieve customer weather preferences, then use those preferences to:
1.  Identify potential travel destinations. *Filtering the `WeatherPy_Database.csv`*
2.  Nearby hotels. *Using nearbysearch API*

To finally, show those destinations on a marker layer map with pop-up markers.![image](https://user-images.githubusercontent.com/90414330/141239400-68ecd32b-7922-4c12-8f25-2142794a363c.png)


### Create a Travel Itinerary Map
Use the Google Directions API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, create a marker layer map with a pop-up marker for each city on the itinerary.
|  |  |
|--|--|
| ![WeatherPy_travel_map_closeup](https://user-images.githubusercontent.com/90414330/141245693-aae46ae3-b933-4942-9af0-687c1e7177d9.png) | ![WeatherPy_travel_map_markers](https://user-images.githubusercontent.com/90414330/141245705-79bf746e-40f2-4936-aa96-2d14fc201bc4.png) |

## Additional Adjustment
### 	Import from a Parallel Directory.
```
## --- 📝 NOTE --- ##

- 🌳 Working Directory Tree -

└───World_Weather_Analysis
    │   .gitignore
    │   config.py
    │   README.md
    │   VacationPy.ipynb
    │   WeatherPy.ipynb
    │   Weather_Database.ipynb
    │
    ├───Vacation_Search
    │       Vacation_Search.ipynb
    │
    ├───weather_data
    │       cities.csv
    │       Fig1.png
    │       Fig2.png
    │       Fig3.png
    │       Fig4.png
    │
    ├───Weather_Database
    │       WeatherPy_Database.csv
    │
    └───__pycache__
            config.cpython-37.pyc
            
Notice that we can't import the `g_key` if we are in the
Vacation_Search Directory. For that reason, we used `sys`
and `os` modules to help importing the `g_key`
```
Retrieved from [DataCamp](https://www.datacamp.com/community/tutorials/modules-in-python?utm_source=adwords_ppc&utm_medium=cpc&utm_campaignid=14989519638&utm_adgroupid=127836677279&utm_device=c&utm_keyword=&utm_matchtype=b&utm_network=g&utm_adpostion=&utm_creative=278443377095&utm_targetid=aud-517318241987:dsa-429603003980&utm_loc_interest_ms=&utm_loc_physical_ms=1010043&gclid=Cj0KCQiA-K2MBhC-ARIsAMtLKRvn_CZvfMJtYiGnJj8vF-B4w3IRrrx2tUAgC1EljLjMVBrrdz9BfSIaAvexEALw_wcB):
 ![image](https://user-images.githubusercontent.com/90414330/141230282-5dab2e9a-e0d8-4901-bca1-923f9a5c4e4d.png)

This means that we can't import the key because in the system we don't have listed the `World_Weather_Analysis` Directory.
|  |  |
|--|--|
| ![image](https://user-images.githubusercontent.com/90414330/141231529-eaedcfb3-b99e-47f6-9617-4601d54c306a.png) | ![image](https://user-images.githubusercontent.com/90414330/141231802-622eb2a5-d0a1-4ce2-94b2-df15e6b07929.png) |


To solve this, we'll add the directory, with help of the `os` module.![image](https://user-images.githubusercontent.com/90414330/141232116-4067d592-dd67-4bdb-936f-a472c140c4e8.png)

And now, appending the directory where `config.py` file lives to the `sys.path`, we should be able to configure the API key.
![image](https://user-images.githubusercontent.com/90414330/141232241-3ac0fbbe-6ab8-4f2f-9d56-b8af54501fd6.png)

> Written with [StackEdit](https://stackedit.io/).
