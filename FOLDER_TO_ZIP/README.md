# Group Challenge for class CSC_51054_EP - Machine & Deep Learning at École Polytechnique

Here is the submissions of the Group Weight Watchers on the Data Challenge on sub-event detection.

The `code` folder contains two notebooks:
 - `Challenge_weight_watchers_main.ipynb` contains the main code for data preprocessing and building of our final model.
 - `Challenge_weight_watchers_additional.ipynb` contains additional code for observation and model testing.

The file `our_predictions.csv` is the submission we used for our final score on Kaggle. Every details about its creation can be found on `Challenge_weight_watchers_report.pdf`.

There are also a few subfolders:
 - `\processed_data` contains two files containing preprocessed data saved for use in the model. ***Those files can only be used for the additional code as the dataframe format is slightly different from the main code.***
 - `\test_submissions` is the destination folder for the test submissions and contains a few of them that has been used on Kaggle.

The notebooks make use of scikit_learn, Pandas, NumPy, PyTorch, NLTK and Gensim. They also downloads the *stopwords* and *wordnet* list from NLTK, and the *glove-twitter-200* model from GenSim.

### Challenge_weight_watchers_main

This notebook is made to be run in order.
The section <ins>Data preprocessing and feature extractions</ins> loads the training files, preprocesses them and creates the tweet embeddings to make a data frame usable by the models. The data frame is then parsed between a training and a testing set, which will be used in the next section to find the best hyperparameters.
Then, the section <ins>For Kaggle Submission</ins> loads and preprocesses the evaluation files the same way as for the training files, trains the final model on the whole training data frame (train set + test set), predict the events of the evaluating set, and output the result in the file `our_predictions.csv`. This file is supposed to be the final submission of our model and should **not** be moved to the `\test_submissions` folder with the others.

### Challenge_weight_watchers_additional

The section <ins>Data preprocessing and feature extractions</ins> is the same as in the maincode, except for a few lines of code, as it preprocess the evaluation dataset at the same time, and the used dataframe is a little different. ***It can be skipped as it saves the preprocessed data in files that are loaded in the next sections.*** This is done to avoid preprocessing when working on the models.
The section <ins>Model Training</ins> contains a PCA representation of the data, along with optimization of the hyperparameters of a few models:
 - KNN
 - KNN on the PCA representation
 - Decision Tree
 - Bagging
 - Random Forest
 - XGB
 - LGBM
The most promising models are then used in the section <ins>Application of the models</ins>, where they are trained on the whole training dataset and submit a .csv file in the `\test_submissions`, to be sent to Kaggle.

**Weight Watchers**
Jonas BERGER
Kenneth BROWDER
Victor MICHA