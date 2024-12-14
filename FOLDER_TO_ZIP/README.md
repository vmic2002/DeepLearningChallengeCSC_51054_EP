# Group Challenge for class CSC_51054_EP - Machine & Deep Learning at École Polytechnique

Here is the submissions of the Group Weight Watchers on the Data Challenge on sub-event detection.

*Note: before running any code, make sure to add the `\eval_tweets` and `\train_tweets` folders with their respective contents in the `\code` folder.

The `code` folder contains three notebooks:
 - `Challenge_weight_watchers_main.ipynb` contains the main code for data preprocessing and building of our final model.
 - `Challenge_weight_watchers_additional_models.ipynb` contains additional code for observation and model testing.
 - `Challenge_weight_watchers_alternative_features.ipynb` contains test for alternative features representations.

The file `our_predictions.csv` is the submission we used for our final score on Kaggle. Every details about its creation can be found on `Challenge_weight_watchers_report.pdf`.

There are also a few subfolders:
 - `\processed_data` contains two files containing preprocessed data saved for use in the model. ***Those files can only be used for the `additional_model` code as the dataframe format is slightly different from the rest of the code.***
 - `\test_submissions` is the destination folder for the test submissions, i.e. everything that is not on the main notebook.

The notebooks make use of scikit_learn, Pandas, NumPy, PyTorch, NLTK and Gensim. They also downloads the *stopwords* and *wordnet* list from NLTK, and the *glove-twitter-200* model from GenSim.

### Challenge_weight_watchers_main - LSTM

This notebook is made to be run in order.
The section <ins>Data preprocessing and feature extractions</ins> loads the training files, preprocesses them and creates the tweet embeddings to make a data frame usable by the models. The data frame is then parsed between a training and a testing set, which will be used in the next section to find the best hyperparameters.
Then, the section <ins>For Kaggle Submission</ins> loads and preprocesses the evaluation files the same way as for the training files, trains the final model on the whole training data frame (train set + test set), predict the events of the evaluating set, and output the result in the file `our_predictions.csv`. This file is supposed to be the final submission of our model and should **not** be moved to the `\test_submissions` folder with the others.

### Challenge_weight_watchers_additional_models

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


### Challenge_weight_watchers_alternative_features

Each main section ("Alternative Features X", where X$\in \{1,2,3,4\}$), is originally a separate notebook and is intended to be run separately from the other sections.

The four sections use an additional library not required for the main and additional notebook, `swifter`, which is just used to speed up some processing of dataframes through parallelization. It can be installed using ```pip install swifter```.

The notebook is also optimized to run on a GPU, but will run on the CPU as currently written. To change this, change the line in each that says: `gpu = torch.device('cpu')` to whichever device you would like to run on.

Note that this notebook was created primarily to run experiments, and thus is not thoroughly edited for readability.

**Weight Watchers**
Jonas BERGER
Kenneth BROWDER
Victor MICHA
