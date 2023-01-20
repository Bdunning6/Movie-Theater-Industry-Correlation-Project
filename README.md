# Movie Theater Industry Correlation and Visualization Project


![blankenbaker-14](https://user-images.githubusercontent.com/115194266/211164070-aa772601-c268-49c7-aa1c-1e6de74502e3.jpg)
## Table of contents
## Introduction
Movie theaters have been a vital part of the motion picture industry for a long period of time, allowing producers to generate profit while introducing their movies to the general public. But due to the introduction of streaming services such as Netflix and the ramifications of a worldwide pandemic, the abillity of movie theaters to generate profit has been diminished. But what leads a movie to be profitable? Does a higher budget mean it's more likely a movie will profit? Do certain genre's and ratings of movies perform better than others? Or are the ratings of critics the most important? And most imporantly, can movie theaters adjust their strategy to adapt to a new environment? Through this project, I will analyze what makes a movie succesfull and develop a potential business statetgy that allows for theaters to adapt in order to remain profitable in the future. 

## Objectives

## Dataset ([Link to dataset](https://www.kaggle.com/datasets/danielgrijalvas/movies))
The data set was found on Kaggle and is a csv file. There are 7668 rows and 15 columns. The 15 columns are:
* **Name:** The name of the movie.
* **Rating:** The rating of the movie.
* **Genre:** The genre of the movie.
* **Year:** The year the movie was released.
* **Released:** The date the movie was released.
* **Score:** The IMDB user score of the movie.
* **Votes:** The number of votes a movie has recieved.
* **Director:** Director of the movie.
* **Writer:** Writer of the movie.
* **Star:** The main actors or actresses of the movie.
* **Country:** Country where the movie was produced.
* **Budget:** The budget of the movie.
* **Gross:** The gross profit of the movie.
* **Company:** The company that produced the movie.
* **Runetime:** Runtime of the movie.

## Preparing the Data

### Importing the libaries and importing the data set.

Importing the pandas, seaborn, numpy and matplotlib libaries. 
![Import Libaries Image](https://user-images.githubusercontent.com/115194266/211173986-a20effb5-10a5-4a46-bd06-3a8c95e85f7c.JPG)

Importing the data set.
![Pandas Data Import](https://user-images.githubusercontent.com/115194266/211174190-bd309ce2-8f29-4127-942d-1bc6fbd5573e.JPG)

## Overview of Data
In order to begin, we should seek to develop a basic understanding of the data that we are working with. Let's use the df head and tail methods to get a general overview of the dataframe. 
### Top 5 rows
![image](https://user-images.githubusercontent.com/115194266/211916457-1d0d36ee-f973-4e41-aada-8be02e4e433b.png)
### Bottom 5 rows
![Df Tail](https://user-images.githubusercontent.com/115194266/211174541-fab3bd72-51e2-4408-9600-b6af85bec25b.JPG)

## Data Cleaning
Beginning the data cleaning process by detecting missing values and summing them up based upon their column. 
![image](https://user-images.githubusercontent.com/115194266/211684627-fbcaacf2-343d-4608-b3b5-0d78198ea77e.png)
We can see there are 11 columns with missing values. Most of the columns have a relatively small amount of missing values besides the budget column. After doing a bit of research to find out why there were missing values, the owner of the Kaggle data stated that some of information for the movies on IMDB were blank. We will be using a few impuation methods in order to fill in these values. We need to first look at the data types before we move foward with any sort of imputation. 
![image](https://user-images.githubusercontent.com/115194266/211686216-52ae2ac4-15c6-4655-b78f-ad343df6b2da.png)

For the object/string variables, we will impute text strings that state no information was provided.
* For the rating column, the missing values can be replaced with "No rating provided".
![image](https://user-images.githubusercontent.com/115194266/211686877-f594635f-8d89-47cc-ad7a-44011eafdb0e.png)
* For the released column, the missing values can be replaced with "No release date provided".
![image](https://user-images.githubusercontent.com/115194266/211687681-4e1c2ba2-3774-4fa5-8b1f-41fd8cf5c7df.png)
* For the writers column, the missing values can be replaced with "No film writers provided".
![image](https://user-images.githubusercontent.com/115194266/211687627-971c3d60-ca9b-41d2-93b2-faf24ab3bcff.png)
* For the star column, the missing values can be replaced with "No star name provided".
![image](https://user-images.githubusercontent.com/115194266/211687843-e01c053a-6c16-4333-bcb3-f4b615f74615.png)
* For the country column, the missing values can be replaced with "No country of origin provided".
![image](https://user-images.githubusercontent.com/115194266/211916613-dc5a0884-5b3e-441b-b61e-0d7a34756c98.png)
* And lastly for the company column, the missing values can be replaced with "No production company provided".
![image](https://user-images.githubusercontent.com/115194266/211916657-9ac5149c-24a5-4de3-84dd-1b6c2876a20c.png)

Now that the missing object columns are taken care of, we can move onto the gross, budget,votes and runtime columns. Since the number of missing values in these columns are numeric and are more significant for our analysis, we will use KNN imputation to fill in the missing values for these columns. We need to find the optimal K value before we use any sort of imputation. In a seperate notebook we can use the Within Clusters Sum of Squares and the Elbow Method in order to determine and visualize what the optimal number of clusters should be.

### Utilizing the Elbow Method
Using a seperate notebook, the needed libaries and data can be imported.
![image](https://user-images.githubusercontent.com/115194266/212750593-ee7bcece-6b77-4c19-94f9-ff5851c6af3e.png)

A dataframe can be created containing the columns that have missing values. The missing values will be dropped from this data frame in order to find the opitmal K value.

![image](https://user-images.githubusercontent.com/115194266/212750920-4fc9d30c-9509-413d-b03d-770d4000a8c2.png)

To reduce a high level a varience, a standard scaler can be imported and fitted to the dataframe in order to standardize the data.
![image](https://user-images.githubusercontent.com/115194266/212751373-cc420a39-8d67-469e-a223-6df71a979f80.png)

Creating the Within Clusters Sum of Squares model. A for loop can be created with the range of 1-11 to test the number of clusters from 1-10. The results then will be plotted with the number of clusters on the X-axis and the WCSS (Within Cluster Sum of Squares) on the Y-axis.
![image](https://user-images.githubusercontent.com/115194266/212753178-e3244bc5-841a-4bb4-af20-4320a859ecee.png)

There are are two bends in the graph at K=2 and K=3. The lowest bend in the plot appears to be at 3, indicating that 3 is the optimal number of clusters. 
We will now return to the original workbook to use KNN imputation to impute the rest of the missing numeric values.
![image](https://user-images.githubusercontent.com/115194266/212780453-b967cddb-8eca-4afb-8e87-7b8796d40969.png)


Using the KNN imputer to impute the missing values for the score, budget, gross, votes and runtime columns. Using the 3 as the number for the number nearest neighbors or k-value.
![image](https://user-images.githubusercontent.com/115194266/212753911-0798f12b-2125-48cd-9964-b44cbc0bff31.png)

Reevaluating to see if there's any missing data. There is none.

![image](https://user-images.githubusercontent.com/115194266/212754150-3392feb5-5b98-4a17-b37d-821b94777fe4.png)


### Finishing the data cleaning process
There is no more missing data in any of the columns. 
![image](https://user-images.githubusercontent.com/115194266/211926177-1fe243b9-2acf-48b7-9dd7-b7d621312b5b.png)

For some of the rows, the year column is incorrect. The release date provides a more accurate description on what year the movie actually released. An extraction of the year from the released column can fix this.
![image](https://user-images.githubusercontent.com/115194266/212426983-4f4f8582-a728-4ef2-9340-5522951f08a3.png)

Finishing the data cleaning process by dropping duplicates rows.
![image](https://user-images.githubusercontent.com/115194266/212426701-68f4d554-f6de-4be0-ad71-21056e6c5e6a.png)

## Correlation
Now that the data is cleaned, we can begin to analyze the factor on what makes movies succesful and begin to develop a strategy for the movie theater industry to remain succesful in the future. By using correlation methods, we can and visualize the strength of a linear relationship between two variables. This is useful because we can see if certain movie factors are more likely to lead to a higher gross profit and a higher popularity among movie watchers. We can start by visualizing the correlation of Budget Vs Gross and IMDB Score Vs Gross to develop general a insight.

### Budget Vs Gross Earnings
![image](https://user-images.githubusercontent.com/115194266/212206526-3c54c5f8-7049-4b3b-a769-eefcf1b3f8c9.png)
According to the regression plot, there is an indication that a positive correlation between budget and gross profit exists. This demonstrates that movies with higher budgets tend to bring in more gross profit. Generally there's much more a company can do with a movie if it recieves a higher budget. A larger budget could mean that more expensive technology can be used, such as better cameras or more advanced CGI. An example of this is James Cameron's first Avatar movie, which at the time used state of the art CGI and motion capture technologies that factored into the movie costing over 230 million dollars. This paid off because the movie grossed a little over 2.9 billion dollars. With higher budgets, companies can hire more notable stars, market their movies more extensively and release their movies across more theaters and platforms. Let's continue with another scatter plot visualization using the score and gross Earning variables.

### IMDB Score Vs Gross Earnings
![image](https://user-images.githubusercontent.com/115194266/212781203-25ea2db4-3dd3-4489-b209-cb0422ce44c1.png)
The IMDB score is calculated through an aggregation of user ratings and then summarized as a single rating for the movie title. This metric can be used to gauge how well the audience favored a movie. In the second visualization, there appears to be a slight positive correlation between IMDB score and Gross, but the relationship between these two variables appears to be much weaker compared to the first scatter plot. This indicates that how favorably a movie was rated on IMDB has a smaller affect on how much gross earnings a movie produces. Movies that are favored by the audiences and critics will tend to perform better financially but the rating is not as an important contributing factor compared to a movies production budget. Next let's use a heat map to see how all the numeric variables correlate with each other.

### Heat Map of Numeric Variables 
![image](https://user-images.githubusercontent.com/115194266/213324575-ddddfe1a-de13-4666-ab83-885560e08533.png)
A heat map can be used to display correlations between multiple variables. By using a heat map, we can display the correlations between all the numeric variables in this data set.  A heat map uses color coding to represent lower and higher values. In this example, cooler colors such as purple and black represent lower correlations while the more hot colors such as orange and red represent higher correlations. It also allows us how to quantify how strong the correlation is between two variables rather than just visualizing it compared to the methods above. 

Looking at this heat map, we can see that the strongest correlational relationship is between budget and gross with a correlation of .75. We briefly went over why a higher budget might lead to higher gross earnings for a movie previously. The second strongest correlational relationship is between votes and gross with a correlation .63. Votes represents the total number of user ratings a movie has receieved. This is a much stronger relationship compared to score and gross, which only has a correlation of .19. Comparing these two correlations, it's clear that the number of votes/reviews are more indicative of gross profit than a movies IMDB score. Another noteworthy correlational relationship is between budget and votes with a correlation of .49, which is the third highest amongst all the numeric variables. This suggests that a higher budget also leads to a higher amount of exposure which in turn leads to more reviews and user votes. 

### Correlation of Non-Numeric and Numeric Variables 
![image](https://user-images.githubusercontent.com/115194266/213799950-62e7eb6d-4464-4cc2-bb7a-35ed5e4cfd2f.png)

To see the correlations between the non-numeric variables and numeric variables, we can convert the object variables into numerized catcodes. By doing this, we can see  if a movies genre is correlated to it's gross profit or if directors and IMDB scores are correlated.. Now that the object variables are converted, let's create a new heat map with all the columns to analyze the correlations. 

### Heatmap with Non-Numeric and Numeric Variables
![image](https://user-images.githubusercontent.com/115194266/213800193-f68c505e-785e-40ff-bf15-7b4eeb60f84c.png)
Looking at the new heat map, we can still see gross and budget has the strongest correlation of a .75. There is a moderate correlation between runtime and score, with a correlation of .40. This could suggest that there is an opitmal runtime for a movie a to be favored by viewers. There are also moderate negative correations as well. There is a negative correlation between genre and budget numbered at -.33. There is another negative correlation between genre and gross scored at a -.23. Both of these negative correlations could indicate that certain genre's of movies could receive a lower budget and gross profit compared to other genres. Certain genres such as action movies that have high budgets may draw in higher gross profits compared to a low budget comedy film. We can seek to determine which genres have higher and lower budgets and gross profits during the visualization part of this project. Before we move on, let's summarize which variables have the strongest correlations.

### Summary of Strongest Positive Correlations
![image](https://user-images.githubusercontent.com/115194266/213810624-b340cced-6efb-4b68-a2dd-d87b89af5df3.png)
![image](https://user-images.githubusercontent.com/115194266/213810742-528b82ce-8406-41c1-bebe-248b7ed0c7d9.png)
![image](https://user-images.githubusercontent.com/115194266/213810819-9a05b5ee-9065-4748-a80e-2aa5e84d4b2e.png)

## Visualizing with PowerBi




