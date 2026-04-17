##  Dataset Description

This dataset provides a comprehensive view of games available on the Steam platform, combining information about game metadata, market performance, and player engagement.

It enables analyzing how different factors contribute to a game's success in terms of popularity, user satisfaction, and retention.

---
##  Data Cleaning & Analysis Workflow

This project follows a structured data analysis pipeline starting from raw data inspection to extracting insights.

---

###  Initial Data Exploration

* Loaded the dataset and explored its structure
* Checked:

  * Number of rows and columns
  * Data types of each feature
  * Summary statistics
* Identified potential issues:

  * Missing values
  * Skewed distributions
  * Presence of extreme values

---

###  Data Cleaning

####  Handling Missing Values

* Checked missing values across all columns
* Observed missing entries mainly in:

  * developer
  * publisher
* Decided on appropriate handling (dropping or keeping based on relevance)

---

####  Removing Duplicates

* Checked for duplicate rows
* Removed duplicates to ensure data consistency

---

####  Data Type Corrections

* Converted columns to proper data types:

  * Dates → datetime format
  * Numerical columns → numeric types

---

####  Owners Column Transformation

* The **owners** column was originally stored as ranges (e.g., "20,000 - 50,000")
* Steps performed:

  * Extracted lower and upper bounds
  * Converted them into numeric values
  * Calculated the average (**owners_avg**) for analysis

---

###  Feature Engineering

* Created new features to improve analysis:

####  Engagement & Satisfaction

* total_ratings = positive + negative
* satisfaction_score = positive / total

---

####  Time-Based Features

* Extracted:

  * release_year
  * release_month

---

####  Platform Encoding

* Converted platform availability into binary variables:

  * windows, mac, linux

---

###  Outlier Detection

* Used statistical and visual methods:

  * Boxplots
  * IQR method

* Applied on:

  * positive_ratings
  * negative_ratings
  * average_playtime

* Investigated whether outliers represent:

  * Errors → handled
  * Real high-performing games → retained

---

###  Exploratory Data Analysis (EDA)

####  Distribution Analysis

* Visualized distributions of:

  * Ratings
  * Playtime

---

####  Relationship Analysis

* Studied relationships between:

  * Playtime vs Ratings
  * Positive vs Negative ratings

---

####  Performance Analysis

* Identified:

  * Top games by ratings
  * Most engaging games (high playtime)

---

####  Trend Analysis

* Analyzed game releases over time
* Studied patterns across years and months

---

###  Key Observations

* Highly engaging games tend to receive more positive ratings
* Data is heavily skewed with extreme outliers
* A small number of games dominate user engagement

---

###  Final Output

A clean, enriched dataset ready for:

* Advanced analytics
* Machine learning
* Business insights


##  Data Structure

Each row in the dataset represents a single game, while columns describe different attributes related to that game.

---

##  Features Description

###  Identification & Basic Info

* **appid**: A unique identifier assigned to each game
* **name**: The official title of the game
* **release_date**: The date when the game was launched

---

###  Development & Publishing

* **developer**: The company or individual who developed the game
* **publisher**: The entity responsible for distributing the game

These features help in analyzing whether certain developers or publishers consistently produce successful games.

---

###  Game Characteristics

* **genres**: Defines the category of the game (e.g., Action, Adventure, Strategy)
* **categories**: Additional classifications (e.g., Single-player, Multi-player)
* **achievements**: Number of achievements available in the game

These variables help understand how game design influences engagement.

---

###  Platform Availability

* **platforms** were transformed into binary columns:

  * **windows**
  * **mac**
  * **linux**

This allows analyzing platform availability as a factor in game success.

---

###  User Engagement Metrics

* **positive_ratings**: Number of users who liked the game
* **negative_ratings**: Number of users who disliked the game
* **average_playtime**: Average time spent playing the game
* **median_playtime**: Median playtime (less sensitive to outliers)

These variables are central to understanding player satisfaction and engagement.

---

###  Market Performance

* **owners**: Represents estimated ownership range of the game
* **price**: Game price in USD

Since the owners column was stored as ranges (e.g., "20,000 - 50,000"), it was transformed into a numeric feature during preprocessing.

---

##  Feature Engineering

To improve analysis quality, several new variables were created:

* **total_ratings** = positive_ratings + negative_ratings
* **satisfaction_score** = positive_ratings / total_ratings

This metric provides a normalized measure of user satisfaction.

---

###  Time-Based Features

From the release date, the following were extracted:

* **release_year**
* **release_month**

These help identify trends over time.

---

###  Owners Transformation

The **owners** feature was converted from a range into a numeric approximation:

* Extracting lower and upper bounds
* Computing an average value (**owners_avg**)

This step was crucial for enabling numerical analysis.

---

##  What This Dataset Captures

This dataset uniquely combines:

* **User Behavior** → ratings and playtime
* **Game Design** → genres, categories, achievements
* **Business Performance** → owners and price

This allows for a multi-dimensional analysis of game success.

---

##  Data Quality Challenges

Several issues were identified and handled:

* Missing values in developer and publisher columns
* Outliers in:

  * ratings
  * playtime
* Owners stored as ranges instead of numeric values
* Potential skewness in engagement metrics

These were addressed through preprocessing and statistical techniques.

---

##  Analytical Value

This dataset supports answering complex analytical questions such as:

* What factors influence a game's success?
* Is there a relationship between playtime and user satisfaction?
* Do certain genres perform better than others?
* How does pricing affect engagement?

It forms a strong foundation for both **EDA and predictive modeling**.
