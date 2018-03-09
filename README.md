# twitter-sentiment-analysis

Analysis on Twitter data using R and PIG to know the sentiments of public towards a particular topic. Helps in knowing the recent trends and its positive and negative effects.

Installing TwitterR project:

First of all install this package in your VM (cloudera)
sudo yum install libcurl-devel
After that open RStudio and install the following packages;
pkgs <-c('twitteR','ROAuth','httr','plyr','stringr','ggplot2','plotly')
for(p in pkgs) suppressPackageStartupMessages(library(p, quietly=TRUE, character.only=TRUE))
# ^^ Loading the packages silently. Altough please check which packages were not installed before executing this.

Now you have to create a Twitter account if you don’t have one and then create an app on it by going to apps.twitter.com Fill in the details accordingly (You can put in dummy URL right now for all URL fields).
After creating the app go to Keys and Access Tokens. There you will find the Consumer keys and Consumer secret. Now for access token and access secret you have to scroll down and find the button genrerate token access click on it and that will generate your access token copy both token and secret. Now keep these 4 token and keys somewhere because we will be needing them later.

# Set API Keys

# FILL THESE KEYS

api_key <- "   "

api_secret <- "  "

access_token <- "  "

access_token_secret <- "  "

setup_twitter_oauth(api_key, api_secret, access_token, access_token_secret)

If this goes well you have successfully installed TwitterR.





Things to remember for sentiment analysis:

We can perform some basic operations on the data  like GSUB for cleaning

tweet = gsub('https://','',tweet) # removes https://

tweet = gsub('http://','',tweet) # removes http://

tweet = gsub('[[:punct:]]', '', tweet) # removes punctuation 

tweet = gsub('[[:cntrl:]]', '', tweet) # removes control characters

tweet = gsub('\\d+', '', tweet)	# removes numbers

----
TOKENIZE- It splits the string
FLATTEN – It remove and brackets and expand the content inside it.

tokens = foreach extract_details generate id,text, FLATTEN(TOKENIZE(text)) As word;
-----
this command will create a table with words splitted.

Ex: 
2,this is me

Will become

2,this is me,this

2,this is me,is

2,this is me,me
------------
Replicated Joins: These kind of joins are used when there are many small joins that are small enough to fit into the main memory, in such cases we will use replicated joins.

Left Outer Join: List all the rows from left side irresspcetive of the fact there was any relation with other table or not. Here means all tweets will be there even if no match was there in AFINN dictionary.
-------------


----------
HELP: https://pig.apache.org/docs/r0.7.0/piglatin_ref2.html
--------


