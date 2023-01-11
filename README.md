## Table of contents
# Movie Theater Industry Analysis and Correlation Project


![blankenbaker-14](https://user-images.githubusercontent.com/115194266/211164070-aa772601-c268-49c7-aa1c-1e6de74502e3.jpg)
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

# Overview of Data
In order to begin, we should seek to develop a basic understanding of the data that we are working with. Let's use the df head and tail methods to get a general overview of the dataframe. 
### Top 5 rows
![Df Head](https://user-images.githubusercontent.com/115194266/211174507-88013fe4-a8bc-4d79-8999-a4b05092307e.JPG)
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
* And lastly for the company column, the missing values can be replaced with "No production company provided".
Now that the missing object/string columns are taken care of, we can move onto the gross and budget columns. 
