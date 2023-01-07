# Toxic-Comment-Analysis
This is a programme to scrape tweets from twitter.com and train a model using BERT, analysing the scraped data from Twitter to classify the data into toxic, severe_toxic, obscene, threat, insult, identity_hate. The AUC score for the 5 models used in this project was 98.86, indicating a high level of accuracy in the classification process. This notebook is presented in three parts. Due to memory constraints in Kaggle, I divided the ML model into two parts.You can run either Part 2 or Part 3 independently.

A lot of the work in this notebook is inspired by the work of Izzy Analytics and Farzaneh F.

Part 1 is the Twitter scrapper, where the tweet_text and the handle of the user are taken.
NOTE: I used Chrome, so it has a "driver = Chrome()." Change them as required. Change the get_username, get_pass, and get_topic values, as well as the name of the .csv file containing tweet data. After the first installation, comment out the selenium installation line.

To run part 2 and 3 you will need to download the bert base uncased model (https://huggingface.co/bert-base-cased).
Part 2 is the preparation of the data and the model training using BERT. The model in this part runs only for one distribution of train sets and validation sets. and you can see the initial performance results (AUC score) we get from this model.

Part 3 is the analysis of any given dataset. It contains the necessary blocks code from Part 2 and then demonstrates how 5 models can be developed for different training and validation set choices as in k_fold (k = 5).From these 5 models, the probabilities for all types of toxicity for each comment are then estimated as a mean value.

Parameters affecting simulation time For running this noteboook quickly, to see how it works, in both part I and part II, you can reduce the training set to the limited number of rows. I took 200 rows in Part I and 2000 in Part II. The reason for having it very low in Part I is that the code opts for educational results rather than being efficient. Therefore, it reads in many different variables and causes the cuda memory to crash if we go for more than 200 rows. This gives us unimpressive results for Part I. (accuracy 86%) In Part 3, the code is more concise compared to Part 2, and it's possible to raise the number of rows to include the whole training set. However, It's limited to 2000, so you manage to get a fairly good result (94% accuracy and a 0.988 auc score) in 22 minutes of simulation. You can have (epochs = 5, k = 5) and see how the accuracy and losses change in different epochs. The accuracy and loss are in an acceptable range, as this notebook is not concerned with reaching state-of-the-art results.
