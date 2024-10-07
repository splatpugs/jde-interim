# Analysis of Netflix Data (Genres)

This project aims to simulate an ETL process using Python & PostgreSQL to clean, analyse & visualize Netflix data from 2018 to 2021.

![Data Architecture Diagram](https://raw.githubusercontent.com/splatpugs/jde-interim/refs/heads/main/2.%20Data%20Architecture%20Diagram/interimdiagram.drawio_blackarrows.png)

## Problem Statement
Netflix, as a leading global streaming service, continuously expands its content library to cater to a diverse and growing audience. To stay ahead of the competition, it is essential for Netflix to understand the distribution of genres within its catalog and how these genres have evolved over time. By analyzing genre trends, Netflix can make informed decisions on content acquisition, production, and recommendation strategies.  

## Project Objectives
The primary objective of the report is to analyze the distribution and trends of genres in Netflix's catalog over time. The analysis aims to answer key questions such as: 
* Which genres have become more or less popular over the years? 
* What are the most common genres in Netflix's catalog? 
* How do genre preferences vary across different countries? 
* Which countries are producing the most diverse set of genres? 
* How can these insights inform Netflix’s content strategy, including content acquisition, production, and regional marketing efforts? 

## Conceptual Models & Entity Relationship Diagrams
This is how the conceptual model will look after 3rd Normalisation:

![3NF Netflix Diagram](https://raw.githubusercontent.com/splatpugs/jde-interim/refs/heads/main/3.%20Entity%20Relationship%20Diagrams/Conceptuals/3NF.png)

And the entity-relationship diagram auto-generated within PostgreSQL (PgAdmin) after the primary key/foreign key constraints and table relationships are established in Python (via SQLAlchemy):

![Netflix ERD Diagram](https://raw.githubusercontent.com/splatpugs/jde-interim/refs/heads/main/3.%20Entity%20Relationship%20Diagrams/Final/ERD_Final.jpg)

## Data Structure & Assumptions
The dataset also consists of the following columns:

| Column Name   | Description   |
| ------------- |-------------|
| show_id       | Unique ID for every movie/tv show |
| type          | A type of identifier – whether it is `movie` or `tv show`|
| title         | Title of the movie/tv show     |
| director      | Director of the movie/tv show (can have one director or more) |
| cast          | Actors involved in the movie/tv show (can have one actor or more)      |
| country       | Countries which the movie/tv show was produced (can have one or more)      |
| date_added    | Date it was added on Netflix |
| release_year  | Actual release year of movie/tv show      |
| rating        | TV rating of the movie/tv show*     |
| duration      | Total duration in minutes or number of seasons* |
| listed_in     | Genre of the movie/tv show (can have one or more)      |
| description   | Summary of the movie/tv show     |

**_Note:_**
* For rating it refers to the TV ratings not user or viewer ratings.
  * For example, `PG-13`, `TV-MA`, `TV-14` and so on.
* For duration, TV shows are generally given the value as the number of seasons.
  * For example, 3 season.
  * Whereas Movies are in the total runtime in minutes (e.g. 60 min).

### Assumptions:
1.	The Netflix dataset consists of popular titles (Movies/TV shows) from 2018 to 2021.
2.	There is existing demand for the titles if it is already streaming on Netflix.
3.	Missing dates (NaT) found for date_added assumed to be “2018-12-31”.
4.	Missing ratings for show_id: 5542, 5795, 5814 assumed to be the same “TV-MA”.

## Overview of Findings
The insights from this analysis suggest that Netflix should continue to invest in diverse content offerings, particularly in emerging genres and international movies:
![Trends in Genre Popularity](https://raw.githubusercontent.com/splatpugs/jde-interim/refs/heads/main/4.%20Data%20Visualisations/Trends%20in%20Genre%20Popularity%20Over%20Years.png)

Regional preferences should guide content curation and marketing efforts, ensuring that Netflix remains a leader in the global streaming market. For example, Countries like India and France are among the top consumers of international movies, reflecting a growing interest in diverse global content:
![Top Countries Watching International Movies](https://raw.githubusercontent.com/splatpugs/jde-interim/refs/heads/main/4.%20Data%20Visualisations/Top%2010%20Countries%20Watching%20International%20Movies.png)

Netflix can further expand its international content offerings to cater to these markets, enhancing localization efforts to appeal to a global audience.

For more context on the findings/chart, refer to: [Interim Project Report](https://github.com/splatpugs/jde-interim/blob/main/1.%20Final%20Submission/Interim%20Project%20Report%20-%20ZetaZenith.docx)

## Summary 
 The insights gained from this analysis offer several strategic directions for Netflix:
 
- **Content Acquisition and Production:**
  - Increase investment in producing and acquiring popular genres, especially **documentaries** and **international movies**.
  - This strategy will help Netflix stay relevant and appeal to evolving global audience tastes.

- **Regional Content Strategies:**
  - Tailor content offerings and marketing strategies to match **regional genre preferences**.
  - Focus on genres that resonate most in specific countries to enhance **viewer engagement and satisfaction**.

- **Promoting Content Diversity:**
  - Highlight countries with diverse genre productions in Netflix’s global catalog.
  - This approach caters to various audience preferences and promotes **lesser-known genres and titles**.

- **Expanding Global Reach:**
  - Capitalize on the strong demand for international movies by increasing the **availability and visibility** of this content.
  - Consider localized content production and strategic partnerships in key markets to broaden Netflix’s **global reach**. 

## What’s Next?
Further research could involve analysing viewership data to better understand audience engagement with different genres, exploring the impact of global events on genre popularity, and investigating the role of Netflix Originals in shaping genre trends.

Additionally, given a longer period of time frame to work with we can also include DataFrames from web scraping. A prototype web scraper for IMDB listicles was coded in Python/Jupyter Notebook. The scraper uses  BeautifulSoup & requests packages. Which will test the website for it's status code, and then parse the website’s HTML code. 

The scraper will then proceed to find all ‘h3’ titles (which are movie titles), append them into an empty list and then converted into a DataFrame with the columns title and count, with count representing the number of times the title has been mentioned by users across different listicles on IMDB. This is to compensate for the lack of user ratings within the Netflix dataset. 


