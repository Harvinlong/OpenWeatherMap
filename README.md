# Weather API

## Purpose of this project:
This project aims to enhance the PlanMyTrip app by adding weather descriptions to the weather data and allowing beta testers to filter the data for their weather preferences to identify potential travel destinations and nearby hotels. 
The testers will then select four cities from the list to create a travel itinerary, and a travel route between the cities will be created using the Geoapify Routing API, along with a marker layer map.

## Retrieve Weather Data:
I used the numpy library to generate 2000 random latitudes and longitudes using the np.random.uniform() function. 
Next, I used the citipy module to find the nearest city for each latitude and longitude pair.
To retrieve the weather data for each city, 
I imported my OpenWeatherMap API key and assembled the API call URL as a string variable. I made sure to edit the config.py file to include my API key, and avoided publishing it on my GitHub repository.
Using the API call URL, I retrieved the following information: latitude and longitude, maximum temperature, percent humidity, percent cloudiness, wind speed, and weather description (e.g., clouds, fog, light rain, clear sky). I added this data to a new DataFrame for further analysis.

![data-6-1-current-weather-description](https://user-images.githubusercontent.com/111480084/225201001-95f50bd5-9896-4462-9e7c-a53f8b681d0f.png)

## Create a Customer Travel Destinations Map
In the Vacation_Search.ipynb file, I ensured that the dependencies and the Geoapify API key were imported correctly.
First, I wrote two input statements that prompted the user to enter their minimum and maximum temperature criteria for their vacation.

Then, I created a new Pandas DataFrame by using the loc to filter the DataFrame for temperature criteria collected. These parameters were the same as the ones used in the module; I used them to search for a hotel for each city.

In the end, I added a for loop to iterate through, in order to retrieve the latitude and longitude of each city and used the Geoapify API to find the nearest hotel based on the search parameters provided, then added the hotel name to the DataFrame. If a hotel wasn't found, I set the hotel name as "No hotel found".

Dropped all the rows in the DataFrame where a hotel name was not found and stored the resulting data into a new DataFrame
![data-6-1-pop-up-markers-for-each-city](https://user-images.githubusercontent.com/111480084/225201238-9194794a-9f10-46a9-b55f-dccf3e44b622.png)

## Create a Travel Itinerary Map
First, I imported the necessary dependencies and the Geoapify API key. Then, I created a map using GeoViews that displayed cities with temperature and location information.

From the map, I selected four cities that were close together and in the same country, and used the loc method to create separate DataFrames for each city.

Using the Geoapify Routing API, I retrieved the route's directions for my itinerary and stored the legs' coordinates in a variable named legs. I looped through the legs' coordinates to fetch latitude and longitude values for each step, storing them in two Python lists named longitude and latitude.

Finally, I used the asterisk operator to display a composed plot that showed the itinerary's route over the map containing the cities.
![data-M6-challenge-itinerary-map](https://user-images.githubusercontent.com/111480084/225203973-cc949d2d-5d5d-40bf-add4-aff530255850.png)

