---
toc: true
layout: post
description: 
categories: [misc]
title: Project 
comments: true
---

# Songs

## Overview

The music recommender utilizes **item-item collaborative filtering** within **collaborative based filtering**. In other words, the program analyzes the music that users like. It then calculates a similarity score (using the Jaccard Index) and populates it into a cooccurence matrix. The similarity in the cooccurence matrix then calculates a score.

## Introduction

To make the music recommender, there are two types of recommendation systems. The first is content based filtering, and the second is **collaborative based filtering**. The music recommender uses **collaborative** based filtering.

Collaborative based filtering consists of two parts:

* Item-Item collaborative filtering
* User item collaborative filtering

The music recommender uses **item-item collaborative filtering**. Item-item collaborative filtering will find items that a user liked based on other items that they like. In other words, it is "Users who liked this item also liked..."

Next, a cooccurrence matrix is created. What is a cooccurrence matrix? These are matrices found in item-item filtering. An example is this:

![]({{ site.baseurl }}/images/cooMatrix.jpg)

Afterwards, we want to calculate the **similarity**. What is similarity? Going back to item-item collaborative filtering, it requires a user-item matrix to be created. In this case, the user is the user, while the item is the song. After a user-item matrix is created, the similarity can be calculated to create a similarity matrix. 

In item-item filtering, the similarity includes 2 items, and many users (whereas in user-item filtering, the similarity includes 2 *users*, and many *items*). 

Looks something like this:

![]({{ site.baseurl }}/images/itemitemsimilarity.jpg)

There is something called **cosine similarity** which is used as a distance metric. "The similarity is calculated based on the angle between these vectors". Honestly I have no idea what that means and the calculations involves a lot of math that I can't understand, so we'll leave it at that :) But yeah, just know that a lot of math stuff occurs here to calculate similarity. 


## Reflection

One of the biggest limitation in our project is the dataset that we used. Our dataset came from Million Songs Dataset, which had enough data. However, the songs were pretty old (before 2010), so our program was limited to recommending pretty old songs. 



## The code

[Code file](https://github.com/Lychee80/fourWsBackend/blob/main/Recommenders.py)

### The data

The data comes from two datasets: `10000.txt` and `song_data.csv`. `10000.txt` contains the user id, song id, and number of times a user listened to a song. `song_data.csv` consists of the song id, song name (title), album name (release), artist's name, and year.

### Data cleaning

Throughout the code, there are lines that help filter the data. This is an important step in order to make sure that the data is clean so that the format is consistent throughout the entire file. 

**Instances of data cleaning**: 

* Line (#): 

  ```
  song_df = pandas.merge(song_df_1, song_df_2.drop_duplicates(['song_id']), on="song_id", how="left")
  ```

  `song_df_2.drop_duplicates(['song_id'])` removes all duplicate song ids. This ensures that the file with the song info does not contain rows with duplicate songs.


### init




`10000.txt` is read by Pandas into a dataframe, and assigned columns consisting of a user id, song id, and listen count. `song_data.csv` is also read by Pandas into a dataframe. 

The next step is to combine the two datasets. However, notice how both `10000.txt` and `song_data.csv` includes the song id? If the two datasets were combined, they would have duplicate entries. Therefore, they merge on the `song_id` column, while keeping the first dataset's `song_id` column.

<code>
song_df = pandas.merge(song_df_1, song_df_2.drop_duplicates(['song_id']), on="song_id", how="left") 
</code>

Afterwards, the dataset is created with a `song` column. This column consists of the combination of the `title` column and the `artist_name`. Therefore, when the format of the data when being entered is `Song name - Artist name`. 


After that, we want to split the dataset into testing and training data. 

<code>
train_data, test_data = train_test_split(song_df, test_size = 0.20, random_state=0)
</code>

This uses the `scikit-learn` library. In this case, the testing data's size is 20% of the dataset, while the remaining 80% is the training data. 

## Constructor

Since the code uses OOP, the class is called and the following instance variables are initalized: the training data (`train_data`). 

In addition, `user_id` is assigned to the string "user_id", and `item_id` is assigned to the string "song". Therefore, in this case, it is important to note that the **item is the song** (which makes sense because the recommendation really focuses on the user and their ratings for the songs).


The next piece of code passes in a list of songs that the user inputs:

<code>
df = is_model.get_similar_items(songList)
</code>


## get_similar_items(songList)

`get_all_items_train_data()` is called and assigned to `all_songs`. This function returns a list of the training data with the `song` column with unique values.

Next, a cooccurrence matrix is created. 


cooccurence_matrix = self.construct_cooccurence_matrix(user_songs, all_songs)

To create the coccurrence matrix, the `construct_cooccurence_matrix` function is called, passing in the `songList` and `all_songs` (training data unique songs).

## construct_cooccurence_matrix()

A list called `user_songs_users` is created. For each element in `songList`, the training data with values that are the same as the song are returned **as the user id**. (Additionally, the data is filtered to be unique).

Afterwards, we want to create a cooccurence matrix using numpy. The matrix originally consists of all zeros, with a row number that is equal to the number of songs in `songList`, and a column number equal to the number of songs in `all_songs` (training data that consists of unique values in `songList`). 


Afterwards, we want to calculate **simlarity**.


The code that calculates similarity does the following: it assigns the all of the training data (specifically the `song` column) that are unique into a variable called `songs_i_data`. It then uses this variable to get unique user ids and adds it in `users_i`. (`users_i`'s type is a set).

The user ids are then compared with each user id that listened to the songs in songList (**intersection**). If there are matches, the union of `users_i` and the id that lsitened to the songs in songList are recorded. The quotient of the length of the intersection and the union are added into the cooccurence matrix. 

<mark>Possible changes</mark>: Change the format from `Song - Artist` to just `Song`. 


## generate_top_recommendations()

Last piece of code in `get_similar_items()` is `generate_top_recommendations()`, which passes in the coocurrence matrix, `all_songs`, and `user_songs` (`songList`). 

Using the cooccurence matrix, a score is calculated by dividng the sum of the values in each column with the num of rows. These scores are then converted into an array and converted to a list. 

Using this list of scores, a new list is created that sorts the scores from highest to lowest and includes their corresponding index. 

A new dataframe is then created that contains the user id, song, score, and rank. 

<mark>Possible change</mark>: The code then loops through the sorted list of scores and checks if the top values actually have numbers and checks if these values are different from the song that the user inputs. Lastly, the dataframe adds in the name of the song (based on the index in `sort_index`), and its score. 





