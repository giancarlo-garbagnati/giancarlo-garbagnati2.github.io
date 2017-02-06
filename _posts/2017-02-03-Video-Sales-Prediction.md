---
layout: post
title: Video Soup
---

I recently tried my hand at building a web scraper to gather movie data and using a basic model to predict video sales. Let's find out how that went!

<!-- more -->

## Webscraping (without APIs)

In order to build a model for movie video sales, one needs data. Although it would very likely be easier and simplier to find databases with APIs, the data collected for this project was all scraped using the Python package [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/). I gathered information such as box office domestic total gross, release date, genres, directors, MPAA rating, runtime, etc from three sources: [BoxOfficeMojo](http://www.boxofficemojo.com/), [The-Numbers](http://www.the-numbers.com/), and [Rotten Tomatoes](https://www.rottentomatoes.com/).

The top 200 grossing movies from each year from 2006-2016 were gathered and scraped from BoxOfficeMojo, and then movie title information gathered from there was used to search for the same movies on the other two websites (The-Numbers and Rotten Tomatoes) for the scrapings there. (Here's my apology to Rotten Tomatoes for calling you all sorts of unpleasant names during the late hours of the night. Turns out if wasn't you, it was poor code on my end.)

## Data

As mentioned above, the top 200 movies were collected from 2006-2016. After cleaning the data, the number of movies in the dataset was ~1600. The movies from 2006-2015 were used for a training/test set and cross-validation and the 2016 movies were separated into what's called a 'hold out' set. The initial idea of this project was to predict video sales for 2016 movies, but in hindsight it would have probably have been better to just include the 2016 set in the train/test set for a more robust model.

The target variable was to predict video sales (dvd+blu-ray). After eye-balling the data, it appeared many movies had the majority of the sales by the 8 week mark after video release, so the sales data was collected at the 8 week mark to try to normalize the sales. Also since some of these numbers could get rather large, this was transformed on a log scale.

## Modeling and Results

Models were built using linear regression, random forest regression, and gradient boosted regression, and was compared against each other by looking at (10^) mean squared error.

## Observations

## Conclusions
