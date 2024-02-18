# nosql-challenge
The UK Food Standards Agency evaluates various establishments across the United Kingdom and assigns them a food hygiene rating. In this project, I analyze some of the ratings data to assist journalists from a food magazine and food critics in deciding where to focus future articles. The code for this project has been written in a Jupyter Notebook and is divided into two parts:

## Part 1: Database and Jupyter Notebook Setup
Initially, I imported the data provided in the establishments.json file using the command line interface. I named the database uk_food, and the collection establishments. Next, I imported the PyMongo library for interacting with MongoDB and the pprint module for pretty-printing. For easier access and manipulation, I assigned the establishments collection to a variable named 'establishments'.

## Part 2: Update the Database
The magazine editors have requested modifications to the database before performing any queries or analysis. The changes to be made to the establishments collection are as follows: a new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked to include it in the analysis:

<img width="383" alt="new_resturant_info" src="https://github.com/MarcoN16/nosql-challenge/assets/150491559/749ed39e-56f8-423f-b859-33bea8b3c4ca">

I examined the dataset to locate the BusinessTypeID corresponding to "Restaurant/Cafe/Canteen" establishments. Subsequently, I extracted and returned solely the BusinessTypeID and BusinessType fields for further analysis. After successfully identifying the BusinessTypeID, I proceeded to update the information of the newly opened restaurant, ensuring that it was assigned the appropriate BusinessTypeID. 
Given the magazine's lack of interest in establishments located in Dover, I conducted a comprehensive assessment to determine the number of documents associated with the Dover Local Authority. Following this, I removed all establishments within the Dover Local Authority from the database, verifying the deletion process to confirm the removal of these documents.
Upon thorough inspection, I identified that certain numerical values were erroneously stored as strings instead of their correct numerical data type. To rectify this, I converted the latitude and longitude values to decimal numbers.
Furthermore, recognizing that the RatingValue field should ideally be stored as integer numbers for consistency and ease of analysis, I converted these values to their appropriate data type.

<img width="369" alt="from _string_to_numbers" src="https://github.com/MarcoN16/nosql-challenge/assets/150491559/050929b5-1ac4-4f54-8b07-37335865dada">

## Part 3: Exploratory Analysis
Eat Safe, Love magazine had specific questions they wanted to answer with this analysis, which will help them identify the locations they wish to visit and those to avoid.
The RatingValue refers to the overall rating determined by the Food Authority and ranges from 1 to 5. A higher value indicates a better rating. Note: This field may also contain non-numeric values such as 'Pass', indicating that the establishment passed inspection but was not assigned a numeric rating. I converted non-numeric values to nulls during the database setup before converting ratings to integers.
The scores for Hygiene, Structural, and ConfidenceInManagement work inversely. Therefore, a higher value indicates a poorer performance in these areas.
I used the following questions to delve into the database and extract the necessary information for the magazine editors:
- Which establishments have a hygiene score equal to 20?

<img width="772" alt="highest_hygiene_score" src="https://github.com/MarcoN16/nosql-challenge/assets/150491559/b170215b-ce57-46ca-a7a6-1810764e9dfc">

- Which establishments in London have a RatingValue greater than or equal to 4?

<img width="766" alt="highest_RatingValue_score" src="https://github.com/MarcoN16/nosql-challenge/assets/150491559/275eb016-be58-4881-acd9-2930adb44fe5">

- What are the top 5 establishments with a RatingValue of 5, sorted by the lowest hygiene score, nearest to the restaurant, "Penang Flavours"?

- How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and list the top ten local authority areas

<img width="206" alt="lowest_hygiene_score" src="https://github.com/MarcoN16/nosql-challenge/assets/150491559/281b8e8a-d3e0-4b7b-815d-77a85280132c">


![lowest_hygiene_score_plot](https://github.com/MarcoN16/nosql-challenge/assets/150491559/a54d72dc-5e86-4cd1-aabc-d2ea45a1abe1)


# References
UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).


