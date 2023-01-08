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
In order to begin, we should seek to develop a basic understanding of the data that we are working with. Let's use the df method to get a general overview of the dataframe. 
![DF](https://user-images.githubusercontent.com/115194266/211174285-5c468224-3253-4df1-8b75-5aee244bbff2.JPG)
### Top 5 rows
![Df Head](https://user-images.githubusercontent.com/115194266/211174507-88013fe4-a8bc-4d79-8999-a4b05092307e.JPG)
### Bottom 5 rows
![Df Tail](https://user-images.githubusercontent.com/115194266/211174541-fab3bd72-51e2-4408-9600-b6af85bec25b.JPG)

## Data Cleaning
Before any meaningfuly analysis can begin, we should detect any missing values and clean the data. We can start by checking the data type of the variables.

