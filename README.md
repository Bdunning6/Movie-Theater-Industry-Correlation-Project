# Movie Theater Industry Correlation and Visualization Project


![blankenbaker-14](https://user-images.githubusercontent.com/115194266/211164070-aa772601-c268-49c7-aa1c-1e6de74502e3.jpg)
## Table of contents
## Introduction
Movie theaters have been a vital part of the motion picture industry for a long period of time, allowing film producers to generate profit while introducing their movies to the general public. But due to the introduction of streaming services such as Netflix and the ramifications of a worldwide pandemic, the abillity of movie theaters to generate profit has been diminished. But what leads a movie to be profitable? Does a higher budget mean it's more likely a film will profit? Do certain genre's and ratings of movies perform better than others? Or are the ratings of critics the most important? Through this project, I will analyze what makes a movie succesfull and develop a business statetgy that allows for theaters to adapt in order to remain profitable in the future. (Maybe some statistics about the rise of streaming services and closing theaters to make a more quantiative point?)

## Objectives

## Dataset ([Link to dataset](https://www.kaggle.com/datasets/danielgrijalvas/movies))
The data set was found on Kaggle and is a csv file. There are 7668 rows and 15 columns. The 15 columns are:
* **Name:** The name of the film.
* **Rating:** The rating of the film.
* **Genre:** The genre of the film.
* **Year:** The year the film was released.
* **Released:** The date the film was released.
* **Score:** The IMDB user score of the film.
* **Votes:** The number of votes a film has recieved.
* **Director:** Director of the film.
* **Writer:** Writer of the film.
* **Star:** The main actors or actresses of the film.
* **Country:** Country where the film was produced.
* **Budget:** The budget of the film.
* **Gross:** The gross profit of the film.
* **Company:** The company that produced the film.
* **Runetime:** Runtime of the film.

## Importing the Libaries and Dataset Into Python
Let's begin by importing the pandas, seaborn, numpy and matplotlib libaries. 
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
Before any meaningfuly analysis can begin, we should detect any missing values and clean the data. 
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

Now that the missing object columns are taken care of, we can move onto the gross, budget,votes and runtime columns. Since the number of missing values in these columns are numeric and are more significant for our analysis, we will use KNN imputation to fill in the missing values for these columns. We need to find the optimal K value before we use any sort of imputation. In a seperate notebook we can use the Elbow Method in order to determine and visualize what the optimal number of clusters should be.

## Utilizing the Elbow Method
Using a seperate workbook, we can use the elbow method to find the optimal number of clusters to use for our KNN imputation. First we must import the relevant modules  and the data. 
![image](https://user-images.githubusercontent.com/115194266/211922559-99a338e3-cd6c-419e-a3b5-2d53afaa8884.png)

Then we must drop all missing and infinite values from the dataframe. 
![image](https://user-images.githubusercontent.com/115194266/211919943-3062062c-5295-4532-a726-2bc97f53e24d.png)

Next a label encoder must be imported and used in order to convert the object columns into a numeric form which machine learning readable. 
![image](https://user-images.githubusercontent.com/115194266/211920254-9b57fe54-9020-4ddc-9e1d-d2669e15d82f.png)

We can then use the df.head() function to see if the label encoder was a success.
![image](https://user-images.githubusercontent.com/115194266/211920368-867108cd-7ea4-42a5-af7c-d1c999554b5e.png)

Now that the object columns have been encoded, we can begin to began by standardizing data using the standard scaler we imported earlier.
![image](https://user-images.githubusercontent.com/115194266/211923011-df75e28f-2bd0-4e0a-94a7-b3a84866af36.png)

From there we need to create the Kmeans parameters that will determine the optimal K-value. We will 10 for the total amount of clusters that we want to test.
![image](https://user-images.githubusercontent.com/115194266/211923408-ee81b167-1e36-4951-82ff-179dfcce0cea.png)

After we set up the parameters, we can then create a list that will determine the SSE values for each K-value. We use the list range 1-11 so that the created list will determine the SSE values for K 1-10. After running this code, we can then develop a visualization to use the elbow method to find the optimal amount of clusters to be use for imputation.
![image](https://user-images.githubusercontent.com/115194266/211924463-f65420a1-c206-4ac1-98cf-e866ba456c0d.png)

Developing the visualization to display the number clusters versus SSE.
![image](https://user-images.githubusercontent.com/115194266/211924863-b4fc9735-a301-4a7f-aecc-9cabc754ccf4.png)
Although it's a little difficult to see, the optimal number of clusters for this dataset seem to be 2 because that's where the line bends, similar to a elbow.. Let's return to the original workbook and finish cleaning the data by using KNN imputation.
![image](https://user-images.githubusercontent.com/115194266/211925703-1487a6e4-8daa-4a77-bfdb-6dde56ee106d.png)

We can see that there is no more missing data in any of the columns. 
![image](https://user-images.githubusercontent.com/115194266/211926177-1fe243b9-2acf-48b7-9dd7-b7d621312b5b.png)




## Correlation Analysis
Now that the data is cleaned, we can begin to analyze and develop insights on what makes movies succesful and begin to develop a strategy for the movie theater industry to remain succesful in the future. By using correlation methods, we can and visualize the strength of a linear relationship between two variables. This is useful because we can see if certain properties of movies are more likely to lead to a higher gross profit. We can start by visualizing the correlation of some of the variables using a regression plot. 

### Budget Vs Gross Earnings
![image](https://user-images.githubusercontent.com/115194266/212206526-3c54c5f8-7049-4b3b-a769-eefcf1b3f8c9.png)




