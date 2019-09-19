# twitter-movie-personalities

## Project Goal: 

Long-form: To leverage personality insights derived from a user’s twitter profile in conjunction with fictional dialogue to craft robust, interactive and completely personalized narratives.

Short-form: To successfully create an MVP generative model that marries a user’s big five personality profile with a fictional character and generates a short paragraph or tweet.

## Data and Process: 

Data was pulled from a massive film corpus from the University of California Santa Cruz. The corpus is broken down by genre and contains 960 film scripts where the dialog in the film has been separated from the scene descriptions. 

The process was to clean and preprocess the data such that I was left with a pandas dataframe broken down by character and all dialogue instances as rows. Next I filtered the dataframe for characters that had 100 lines or more and each line consisting of at least 3 words. 

From here, I created a relational database that included the following information in a nested structure: film genre, film title, film character, and then all dialogue from each character.

Next, I created a script that ran each individual character's dialogue through the IBM Watson Personality Insights program and returned back their detailed big five personality profile.

At this point, I had a 3,000+ database of characters and their associated personality profiles, so I moved on to Twitter where I used Tweepy to pull the last 200 tweets from any given user and wrote a similar script to also run their personality through IBM.

The Twitter profile was then compared to all characters in the relational database and using cosine similarity, I printed out the character in each genre that was most similar to the user. 

For the final step, I leveraged OpenAI's GPT-2 architecture to generate a short tweet from each character. The GPT-2 instance was trained using the GPT-2 Simple python library created by Max Woolf, was trained individually on each character's dialogue and was fine-tuned to print out a tweet length of original content.

## Conclusions and Next Steps:

While this project was fascinating (and successful in it's own right) this is simply the calibration for a much larger, long-form narrative delivery that I hope to roll out in the near-ish future. Long-form text generation is a difficult problem to solve, however, so for now I am satisfied in generating short samples in the speaking style of fictional characters and creating a storytelling calibration device that meets each user specifically at their personality profile.
