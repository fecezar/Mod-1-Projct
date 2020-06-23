# Read Me

## Project Briefing:

"Microsoft sees all the big companies creating original video content, and they want to get in on the fun. They have decided to create a new movie studio, but the problem is they don’t know anything about creating movies. They have hired you to help them better understand the movie industry. Your team is charged with doing data analysis and creating a presentation that explores what type of films are currently doing the best at the box office. You must then translate those findings into actionable insights that the CEO can use when deciding what type of films they should be creating."

## Data Overview

The datasets used in this notebook include a wide range of related data

- Box Office Mojo:
  - bom.movie_gross.csv.gz
  

- IMDB:
  - imdb.title.crew.csv.gz
  - imdb.title.akas.csv.gz
  - imdb.title.ratings.csv.gz
  - imdb.name.basics.csv.gz
  - imdb.title.basics.csv.gz
  - imdb.title.principals.csv.gz



- TMDB:
  - tmdb.movies.csv.gz



- The Numbers:
  - tn.movie_budgets.csv.gz

After initial analysis and some data cleaning, the datasets which ultimately were used to draw conclusion were:
- imdb_title_basics_gz
- tn_movie_budgets_gz
- imdb_name_basics_gz

# Questions and Assumptions

This notebook explores and cleans the raw data in order to answer the following questions:


- **What is the relationship between movie grossings and the people who take part in the project?**
  - the underlying assumption is that even though there is a two way relationship between the success of a movie and that of a professional (one thing promotes the other), outlier professionals will have an outsized impact in the movie's results.
<br>
<br>
- **Do directors, actors and producers have the same impact on the financial results of a movie?**
  - the underlying assumption in this case is that roles with bigger responsabilities (directors, producers) have a larger impact than others (actors, for example)
<br>
<br>  
- **Are any genres more risky than other in terms of financial performance?**
  - the underlying assumption is that there will be differences among differnt genres
<br>
<br>
  
- **What part does genre play in the financial results of a movie?**
  - the underlying assumption is that some genres will generate better results than others  

 # Data Cleaning and Exploration

- **Deletion of  all duplicate rows from all data sets**
  - **tn_movie_budgets_gz**: Changing data stored as strings into floats (financial figures) or into datetime (release date)

- **Cleaning columns with numerical data, but stored as strings**
  - Changing data stored as string to datetime format for the column release_date

- **First Merge**
  - By merging **imdb_title_akas_gz** with **tn_movie_budgets_gz we can** we can cross **imdb** data with the financials from **tn**
  - New Features : additionally, we can calculate profits  for the new merged table

- **imdb_name_basics_gz**: 
This data set gives us a list of people and lists their professions and movies which they participated in

  - Increasing readability of listed professions: first we make the professions list more readable and accessible for further treatment and analysis. We can also eliminate empty values so we only have rows that are useful for the desired analysis
  - Deletion of rows: Rows with NaN either on known_for_titles column or on primary_profession were excluded
  - New Features - Professions: Adding new columns that tell if the person is an actor, a director or a producer
    - Deletion of rows: cleans away rows of people who are neither a director, an actor nor a producer
  - New Features - cross reference with financial figures: since we have access to financial information about several movies, we can cross reference that with the movies listed for each professional in imdb_name_basics_gz
    - Deleton of Rows
Drops rows where avg_grossing is zero



- **imdb_title_basics_gz**

  - Data Type Cleaning: splits the string values in genres into a list of genres
  - Row Deletions Deleting rows where column genre is empty
  - Subdividing: creates a DF for genres and their frequency



- **Second Merge**:  
Merges   **imdb_title_basics_gz**   with information data from  **df_imdb_financials**

# Questions Investigated



## What is the relationship between movie grossings and the people who take part in the project?

We can see no significant divergence in the composition of the distribution curves. 

![image.png](attachment:image.png)

![image.png](attachment:image.png)

However, we can note that:
- the bottom 25% of professionals present worse financial performances than the bottom 25% of all movies. We can thus infer that low performing professionals have an outsized negative impact on the financial performance of a movie


## Do directors, actors and producers have the same impact on the financial results of a movie?

![image.png](attachment:image.png)

The charts show an almost identical distribution for all three professions. From that we can infer that no professional has a larger impact on the financial result than the others

## Are any genres more risky than other in terms of financial performance?

![image.png](attachment:image.png)

The data show that some genres are more risky then others. A Drama is roughly 4 times more likely to fail than a documentary, for example

## What part does genre play in the financial results of a movie?

![image.png](attachment:image.png)

![image.png](attachment:image.png)

**Conclusion**
- The value creation is not equal among all genre types

**Recommendation**
- Proper allocation of resources into genres that create most values will benefit the company by allowing to take part in the biggest slices of profit in the market 

## Future Work

- A possible path for further exploration would be to dive into the relationships of professionals and genres.

- Additionally, further analysis into 


```python

```
