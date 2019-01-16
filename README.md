# MongoDB-Textual-Spatial-Searching
The required task is to write two functions, which will perform some textual and spatial searching on MongoDB. Details are explained below.

## Setup Instructions:
 
1. Install MongoDB 2.6.11.   

2. Install pymongo to act as helper interface with MongoDB.   

3. Run the tester file to check everything runs and nothing fails. 

4. Now, Implement the function provided in Interface.py to perform the operations as listed below: 

a. **FindBusinessBasedOnCity**(cityToSearch, saveLocation1, collection) 

This function searches the ‘collection’ given to find all the business present in the city provided in ‘cityToSearch’ and save it to ‘saveLocation1’. For each business you found, you should store name Full address, city, state of business in the following format. 
Each line of the saved file will contain, Name$FullAddress$City$State. ($ is the separator and must be present) 

b. **FindBusinessBasedOnLocation**(categoriesToSearch, myLocation, maxDistance, saveLocation2, collection) 

This function searches the ‘collection’ given to find name of all the business present in the ‘maxDistance’ from the given ‘myLocation’ that covers all the given categories (please use the distance algorithm given below) and save them to ‘saveLocation2’. Each line of the output file will contain the name of the business only. 

-- categoriesToSearch: a list of categories need to be covered   
-- ‘myLocation’ will be given with format [“40.3”,“51.6”]           
-- maxDistance: the search distance   
-- saveLocation2: output location   

## Files:

Interface.py – Has the function implementations
testData.json – This is the json file whose data is inserted in MongoDB. The structure of one record of this file is
 < Key value pair>: - 
{ 
'type': 'business', 
'business_id': (encrypted business id), 
'name': (business name), 
'neighborhoods': [(hood names)], 
'full_address': (localized address), 
'city': (city), 
'state': (state), 
'latitude': latitude, 
'longitude': longitude, 
'stars': (star rating, rounded to half-stars), 
'review_count': review count, 
'categories': [(localized category names)] 
'open': True / False (corresponds to permanently closed, not business hours), 
}

 
## Example: - 
{
"city": "Ahwatukee",  
"review_count":3,  
"name": "McDonald's",
"neighborhoods": [],  
"type": "business",  
"business_id": "LNdwp-9Isnd6xmBKUz4K_A",  
"full_address": "10823 S 51st St\nAhwatukee, AZ 85044",  
"state": "AZ",  
"longitude": -111.975004,  
"stars": 2.0,  
"latitude": 33.348560900000003,  
"open": true,  
"categories": ["Burgers", "Fast Food", "Restaurants"]  
}   

tester.py – To test the functions FindBusinessBasedOnCity and FindBusinessBasedOnLocation

## Distance Algorithm used:
Given two pair of latitude and longitude as [lat2, lon2] and [lat1, lon1], you can calculate the distance between them using the formula given below: 

![distance_algo](https://user-images.githubusercontent.com/44238315/51229005-f9f47300-1917-11e9-9f2f-a85f33352472.PNG)
