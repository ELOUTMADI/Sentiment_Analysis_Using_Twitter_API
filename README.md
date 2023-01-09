# Twitter Sentiment Analysis

This code is for performing sentiment analysis on tweets using the Twitter API and Python. It includes two main functions: 

## `Construction_Du_TestSet(mot_clé)`

This function takes in a keyword (`mot_clé`) and searches for 100 tweets containing that keyword using the Twitter API. It then returns a list of dictionaries, where each dictionary represents a tweet and contains the keys "text" (the text of the tweet) and "label" (which is set to `None`).

## `Construire_Le_Training_Set(FichierCorpus, FichierTweets)`

This function takes in two file paths, `FichierCorpus` and `FichierTweets`. `FichierCorpus` should be a CSV file with three columns: "topic", "label", and "tweet_id". The "topic" and "label" columns are for categorizing the tweets, and the "tweet_id" column is the unique identifier for each tweet. This function uses the Twitter API to retrieve the tweets corresponding to the tweet IDs in `FichierCorpus` and stores them, along with the "topic" and "label" information, in a new CSV file at the file path specified by `FichierTweets`. It also returns a list of dictionaries, where each dictionary represents a tweet and contains the keys "tweet_id", "text", "label", and "topic".

## Preprocessing Tweet Text

The code also has some additional helper functions for preprocessing the tweet text, including `prétraitement_Du_Tweets(Data_to_process)`, which takes in a list of tweet dictionaries and performs the following preprocessing steps on each tweet:

1. Convert the tweet text to lowercase
2. Replace URLs with the string "URL"
3. Replace mentions of other users (e.g. "@user") with the string "AT_USER"
4. Remove hashtags (e.g. "#hashtag")
5. Tokenize the tweet text
6. Remove stopwords and punctuation from the tokenized tweet

## Dependencies

This code imports several libraries for use in the functions, including:

- `twitter`: a Python library for accessing the Twitter API
- `re`: a library for performing regular expression operations
- `nltk` (the Natural Language Toolkit): a library for working with human language data (e.g. tokenizing text)

## Getting Started

To use this code, you will need to have a Twitter developer account and create a new application. This will give you access to the necessary API keys and tokens.

Then, in the code, update the following lines with your own API keys and tokens:

```python
twitter_api = twitter.Api(consumer_key='YOUR_CONSUMER_KEY',
                        consumer_secret='YOUR_CONSUMER_SECRET',
                        access_token_key='YOUR_ACCESS_TOKEN_KEY',
                        access_token_secret='YOUR_ACCESS_TOKEN_SECRET')
                       
You will also need to specify the file paths for FichierCorpus and FichierTweets in the Construire_Le_Training_Set function. These file paths should be updated to point to the location of the corresponding CSV files on your local machine.

## Example Usage
Here is an example of how to use these functions:
# Search for 100 tweets containing the keyword "happy"
Data_To_Use_For_Testing = Construction_Du_TestSet("happy")

# Retrieve and store tweets from a CSV file of tweet IDs
FichierCorpus = "path/to/corpus.csv"
FichierTweets = "path/to/tweetDataFile.csv"
Data_To_Use_For_Training  = Construire_Le_Training_Set(FichierCorpus, FichierTweets)
```

## Additional Information
- The Construction_Du_TestSet function uses the twitter_api.GetSearch method to search for tweets containing the specified keyword.
- The Construire_Le_Training_Set function uses the twitter_api.GetStatus method to retrieve the tweets corresponding to the tweet IDs in FichierCorpus.
- The prétraitement_Du_Tweets function uses the stopwords list from the nltk library to remove common stopwords (e.g. "the", "a", "an") from the tokenized tweet. It also removes punctuation using the punctuation list from the string library.
