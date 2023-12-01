# Module 12 Challenge - NoSQL Databases
## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Challenge Instructions
This Challenge is divided into three parts: 
   - Part 1: Database and Jupyter Notebook Set Up
   - Part 2: Update the Database
   - Part 3: Exploratory Analysis

### Part 1: Database and Jupyter Notebook Set Up
-  Use NoSQL_setup_starter.ipynb for this section of the challenge.
- Import the data provided in the establishments.json file from your Terminal. Name the database uk_food and the collection establishments. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.
- Create an instance of the Mongo Client.
- Confirm that you created the database and loaded the data properly:
   - List the databases you have in MongoDB. Confirm that uk_food is listed.
   - List the collection(s) in the database to ensure that establishments is there.
   - Find and display one document in the establishments collection using find_one and display with pprint.
- Assign the establishments collection to a variable to prepare the collection for use.

### Part 2: Update the Database
- Use NoSQL_setup_starter.ipynb for this section of the challenge.
- The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:
   - An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:
   ``` 
   {
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
    }
   ```
   - Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.
   - Update the new restaurant with the BusinessTypeID you found.
   - The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.
   - Some of the number values are stored as strings, when they should be stored as numbers.
      - Use update_many to convert latitude and longitude to decimal numbers.
      - Use update_many to convert RatingValue to integer numbers.

### Part 3: Exploratory Analysis
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.
- Use NoSQL_analysis_starter.ipynb for this section of the challenge.
- Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.
1. Which establishments have a hygiene score equal to 20?

2. Which establishments in London have a RatingValue greater than or equal to 4?

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

## Challenge Solutions
- The solution for this challenge is under the nosql_challenge folder. The input CSV's are located under nosql_challenge/Resources folder.
- Run the jupyter notebooks
   - NoSQL_setup_starter.ipynb
   - NoSQL_analysis_starter.ipynb
- Answers to the four questions in Part 3 exploratory analysis section can be found in the NoSQL_analysis_starter.ipynb notebook.
   1. Which establishments have a hygiene score equal to 20?

      There are 41 establishments with a hygiene score of 20 from the uk_food dataset.
   2. Which establishments in London have a RatingValue greater than or equal to 4?

      There are 33 establishments in London that have a RatingValue greater than or equal to 4 from the uk_food dataset.
   3. What are the top 5 establishments with a RatingValue rating value of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

      The top 5 establishments with a RatingValue of '5' sorted by lowest hygiene score nearest to "Penang Flavours" are: "Volunteer", "Lumbini Grocery Ltd T/A Al-Iman", "Plumstead Manor Nursery", "Iceland", and "Howe and Co Fish and Chips - Van 17".
   4. How many establishments in each Local Authority area have a hygiene score of 0?

      There are 55 rows in the DataFrame. This is the preview of the first 10 rows:

| _id_      | count |
| ----------- | ----------- |
| Thanet      | 1130       |
| Greenwich   | 882        |
| Maidstone      | 713       |
| Newham   | 711        |
| Swale      | 686       |
| Chelmsford   | 680        |
| Medway      | 672       |
| Bexley   | 607        |     
| Southend-On-Sea      | 586       |
| Tendring   | 542        |
   

