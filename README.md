# ML_Unsupervised_Capstone_Netflix_Movies_and_TV_Shows_Clustering
# Introduction:-
Netflix is the world's leading streaming entertainment service with over 209 million paid memberships in over 190 countries enjoying TV series, documentaries and feature films across a wide variety of genres and languages. 

It is a streaming service that offers a wide variety of award-winning TV shows, movies, anime, documentaries and more – on thousands of internet-connected devices. Members can watch as much as they want, anytime, anywhere, on any internet-connected screen. 

# Project Overview:-
The dataset consists of tv shows and movies available on Netflix as of 2019. It has been collected from Flixable which is a third-party Netflix search engine.

In 2018, they released an interesting report which shows that the number of TV shows on Netflix has nearly tripled since 2010. The streaming service’s number of movies has decreased by more than 2,000 titles since 2010, while its number of TV shows has nearly tripled.

# Objective:-
In this project, we are required to do
1. Exploratory Data Analysis
2. Understanding what type content is available in different countries
3. Is Netflix has increasingly focus on TV rather than movies in recent years.
4. Clustering similar content by matching text-based features

# DATASET:-
The dataset consists of following columns:-
1) show_id : Unique ID for every Movie / Tv Show
2) type : Identifier - A Movie or TV Show
3) title : Title of the Movie / Tv Show
4) director : Director of the Movie
5) cast : Actors involved in the movie / show
6) country : Country where the movie / show was produced
7) date_added : Date it was added on Netflix
8) release_year : Actual release year of the movie / show
9) rating : TV Rating of the movie / show
10) duration : Total Duration - in minutes or number of seasons
11) listed_in : Genre
12) description: The Summary description

Our data set contains 7787 rows and 12 columns. We have 1 numeric and 11 categorical independent features.

# Workflow:-
The workflow of this problem is divided into following sections:-

### I. Data Study
First, we will import python libraries such as NumPy and Pandas to load the CSV file. Then we will import following Python libraries for different functions

- Matplotlib ,Seaborn and Plotly - For Visualization
- re and string- For Text Cleaning
- nltk- To import stop words
- sklearn – For all mathematical calculations and clustering

Later we will perform some operations to understand and analyze the data.

### II. Data Manipulation
Since director column has highest null values, 30.7% of data is missing and cast, country , date added , rating column has more than 10% null values. In order to treat missing values in the director column we can fill it with ‘unknown’ and in the cast column with 'No cast', country can be filled with mode value, null values of date added and rating are very less so they can be removed.

We have created new features to store date, day, month and year separately. We have handled outliers using the IQR method.

### III. EDA and Visualisation:-

### 1. Type of Content on Netflix

![download (44)](https://user-images.githubusercontent.com/110467640/213736113-fbda5e78-f33b-421c-abdb-c373a09341b7.png)

- 69.1% of the content available on Netflix are movies and the remaining 30.9% are TV Shows

### 2. Release year of Movies/TV Shows

![download (45)](https://user-images.githubusercontent.com/110467640/213736220-c9263e62-cecb-4390-86e0-5714a509f73e.png)

- Maximum number of Movies streaming on the platform were released in 2017.
- Most TV Shows streaming on the platform were released after 2015
- Since the number of movies releasing each year has started decreasing after 2017 whereas number of TV Shows have increased gradually after 2015

### 3. Number of Movies/TV Shows added per Year and per Month

![download (46)](https://user-images.githubusercontent.com/110467640/213736313-b6d71d7b-ecc1-454b-8208-5d70deb36b34.png)

- Number of movies added to the platform showed a deliberate increase from 2017 to 2019 and has decreased after that.
- TV Shows have been added continuously from 2015 and its number has been increased every year.

![download (47)](https://user-images.githubusercontent.com/110467640/213736514-71096c03-17ee-4789-8d72-67c592d8dec2.png)

- Most number of Movies and TV Shows are added between October and January

### 4. Top 10 Directors

![download (48)](https://user-images.githubusercontent.com/110467640/213736790-0dfb47c4-74c0-4b84-9a22-20f93d6d1fd0.png)

- Top 3 Directors are-
1. Jan Suter
2. Raul Campos
3. Marcus Raboy

### 5. Top 10 Actors

![download (49)](https://user-images.githubusercontent.com/110467640/213736953-d143d223-edde-45a9-b445-f3c2e7212ff4.png)

- Top 3 Actors are
1. Anupam Kher
2. Shah Rukh Khan
3. Om Puri

### 6. Top Genres on Netflix

![download (50)](https://user-images.githubusercontent.com/110467640/213737208-d0f0f3ed-637e-411a-9695-cd9144b18e21.png)
![download (51)](https://user-images.githubusercontent.com/110467640/213737311-9ea76fdc-e7c2-492f-be0f-f4ba7fcc48fb.png)

- In both Movies and TV Shows top genres are International Movies/TV Shows, Dramas and Comedies Movies/TV Shows.

### 7. Top 10 Countries producing content on Netflix

![download (52)](https://user-images.githubusercontent.com/110467640/213740241-0f7f7fb5-199a-426e-8a1f-d79baacd87f2.png)

- United States is the country producing maximum content on Netflix followed by India and UK.

### 8. What Type of content produced by Top 10 Countries

![download (53)](https://user-images.githubusercontent.com/110467640/213740526-672a8676-7b66-4e88-913f-0f307f89abc8.png)

- Drama, International Movies, and Comedies seem popular choices in most countries.
- British and International Tv Shows dominate in the United Kingdom.
- Regional specialties such as Anime in Japan, Spanish TV Shows in Spain and Korean Tv Shows in South Korea are more prominent in these countries.
- It is also observed that in the countries where the regional language is not English, International Tv Shows/Movies are more in demand.

### 9. Ratings of content

- TV-MA :for Mature Audiences
- R : Restricted
- PG-13 : Parents strongly cautioned. May be Inappropriate for ages 12 and under
- TV-14 : Parents strongly cautioned. May not be suitable for ages 14 and under
- TV-PG : Parental Guidance suggested
- NR : Not Rated
- TV-G : Suitable for General Audiences
- TV-Y : Designed to be appropriate for all children
- PG : Parental Guidance suggested
- G : Suitable for General Audiences
- NC-17 : the content isn't suitable for children under 17 and younger
- TV-Y7-FV : Suitable for ages 7 and up

![download (54)](https://user-images.githubusercontent.com/110467640/213740770-4747712c-a698-4f44-a79d-bb332a2d6405.png)

- Most content on Netflix is rated for Mature Audiences(MA) and over 14 years old

### 10. Duration of Movies/TV Shows

![download (55)](https://user-images.githubusercontent.com/110467640/213740851-7a7ab978-f252-4c29-a6aa-5a7993823141.png)

- Most movies on Netflix have a duration range from 80 to 120 minutes

![Screenshot 2023-01-07 185107](https://user-images.githubusercontent.com/110467640/213740946-49933576-2ce6-409b-92ce-fd7154138ef3.png)

- Most number of TV shows are having single season
- Grey's Anatomy is the longest TV Show with 16 Seasons

# Feature Engineering

Firstly, we add genres, rating and description of our dataset to form our target variable.

### I. Text Cleaning

We conerted all words in lowercase and remove everything except the alphabets.

### II. Word Tokenization

We converted the sentence into a token of words using the tokenization method.

### III. Punctuation Removal

We have applied a function to remove punctuation in the target variable.

### IV. Stop Word Removal

We have removed all the stop words using nltk library.

### V. Lemmatization

Applying Word Net Lemmatizer to extract meaningful words from the target variable.

### VI. TF-IDF-Term Frequency-Inverse Document Frequency

Term frequency-inverse document frequency is a text vectorizer that transforms the text into a usable vector.

# Clustering Algorithms

## K-Means Clustering

K-means is a centroid-based algorithm, or a distance-based algorithm, where we calculate the distances to assign a point to a cluster. The main objective of the K-Means algorithm is to minimize the sum of distances between the points and their respective cluster centroid.

![download (57)](https://user-images.githubusercontent.com/110467640/213743542-0860f027-0032-493e-8196-9daf971daa71.png)
![download (58)](https://user-images.githubusercontent.com/110467640/213743570-6bdf53f6-4d8e-4f36-b840-1d99b4f954fe.png)
![Screenshot 2023-01-12 141732](https://user-images.githubusercontent.com/110467640/213745018-6f5528fc-774d-459f-98d3-d4acf2417447.png)
![download (77)](https://user-images.githubusercontent.com/110467640/213743608-3e0d0614-0754-4a43-807c-112293b23be5.png)
![download (60)](https://user-images.githubusercontent.com/110467640/213743625-b9dafbef-2a4a-4729-8220-d6509df35054.png)

- From the Silhouette Analysis and Elbow method, the optimal cluster is 13. This gives a clustering score of 0.012

## Hierarchical Clustering

Hierarchical clustering is an unsupervised machine learning algorithm, which is used to group the unlabelled datasets into clusters. In this algorithm, we develop the hierarchy of clusters in the form of a tree, and this tree-shaped structure is known as the dendrogram.

![download (61)](https://user-images.githubusercontent.com/110467640/213743730-a69e3747-c2e0-4f8e-b5b1-200f00fc276a.png)
![download (62)](https://user-images.githubusercontent.com/110467640/213743760-2b032047-e1a1-455c-b78f-616bf70d8311.png)
![Screenshot 2023-01-08 003215](https://user-images.githubusercontent.com/110467640/213745508-faa4a548-eb82-4543-80ec-bcea5d37dc2b.png)

- Highest Silhouette Score of 0.671327 achieved at distance = 20 with 13 clusters

## DB SCAN

DBSCAN stands for Density-Based Spatial Clustering of Applications with Noise. It is a density-based clustering algorithm. The algorithm increases regions with sufficiently high density into clusters and finds clusters of arbitrary architecture in spatial databases with noise.

![download (63)](https://user-images.githubusercontent.com/110467640/213743987-042794a9-2fcf-4af7-919b-dd9afa81873a.png)

- Estimated number of clusters: 13
- Estimated number of noise points: 1039

## WORD CLOUD

![download (64)](https://user-images.githubusercontent.com/110467640/213744153-5988d0f6-04d2-4006-ac80-c688bfae7d36.png)
![download (65)](https://user-images.githubusercontent.com/110467640/213744171-9526882a-00c9-4627-802e-c15d920f96a4.png)
![download (66)](https://user-images.githubusercontent.com/110467640/213744204-82bad6d4-008e-4516-8465-5d3b0146a530.png)
![download (68)](https://user-images.githubusercontent.com/110467640/213744228-e84b402e-6f73-45ae-b89e-4efc2ec1bf40.png)
![download (69)](https://user-images.githubusercontent.com/110467640/213744243-b85632fd-f568-49d3-a26e-8365ebf27e57.png)
![download (70)](https://user-images.githubusercontent.com/110467640/213744261-30698bce-a892-4722-b033-3a71becc30f2.png)
![download (71)](https://user-images.githubusercontent.com/110467640/213744293-4b779375-7f39-4639-aacd-efcd5067ea73.png)
![download (72)](https://user-images.githubusercontent.com/110467640/213744316-4d90903f-bf74-4d45-9291-6de87059bc97.png)
![download (73)](https://user-images.githubusercontent.com/110467640/213744388-9f8e835a-b41f-4030-9cfc-5d55af451e0f.png)
![download (74)](https://user-images.githubusercontent.com/110467640/213744425-ca9a23de-f9fb-41f3-941d-e73fd963c61b.png)
![download (76)](https://user-images.githubusercontent.com/110467640/213744454-7fc7af71-4693-41d0-9941-d117a41e600d.png)

## CONCLUSION
- Majority of content on Netflix is movies. Netflix has 5372 movies and 2398 TV shows.
- The number of movies on Netflix is growing significantly faster than the number of TV shows.
- We saw a huge increase in the number of movies and TV Shows after 2015. Highest number of movies released in 2017.
- Less Number of movies released after 2017 whereas a greater number of TV shows were released in this period.
- Most of these contents are released either in the year ending or in the beginning.
- International Movies/TV Shows are the top most genre in Netflix which is followed by Drama and Comedy movies/TV shows.
- The United States is the major content producing country on the platform followed by India, UK, Japan, South Korea.
- Jan Suter and Raul Campos have directed the most content on Netflix.
- Also 6 of the actors among the top ten actors with maximum content are from India. Anupam Kher, Shah Rukh Khan, Om Puri are the top 3 Actors.
- TV-MA tops the rating chart, indicating that mature content is more popular on Netflix.
- Most of the movies have a duration between 80 to 120 minutes.
- Most TV shows have a single season. Grey's Anatomy is the longest TV Show with 16 Seasons.
- k=13 was found to be an optimal value for clusters using which we grouped our data into 13 distinct clusters.
