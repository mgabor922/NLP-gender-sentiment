## Deep Learning Homework

- Team name: DieWelle
- Team members:
    - Molnár Gábor
    - Papp Viktor
    - Foltányi Bence

### Project Specification

We chose our homework subject from the field of Natural Language Processing (NLP). We would like to determinate the age and gender of bloggers based on their blog posts.

### Data sets

We have found a data set on kaggle, with more than 170,000 blog posts, each labeled with the authors age and gender. We made the data processing on this set.

- [Link to our data set.](https://www.kaggle.com/tomlisankie/blog-posts-labeled-with-age-and-gender/)

We have also found an other [data sets which contains twitter posts.](https://www.kaggle.com/s1m0n38/twitter-text-and-gender/version/1)

### Our solution
The database we used is actually the test database from the dataset, since it already had plenty of samples. We have uploaded it to a [google drive](https://drive.google.com/drive/folders/1W9bwUnqgRu7ZzjSONEh-AsJmdULVaeln) as 'data.json'. This is what our script loads before preprocessing.

Our scrip right now loads the original data then creates a word dictionary out of all the loaded documents. This is used to gather information of the vocabulary of the dataset. After this is done we go through the documents and make sure none of them are longer than a set amount of words. This is done by saturating them to that specific size if they happen to be longer.
When this is done we save these documents with the original labels as a new database, as this task can take quite long given the size of the data.

Finally we use the now processed documents to create one-hot encoded vectors that we pad to a length set at the beginning of the script (this is the same size we set as the maximum word count for our documents).
These vectors can then be used to create our train, validation and test inputs.

### Related work

We have found [this paper](https://cs224d.stanford.edu/reports/BartleAric.pdf) in the subject that gave us some ideas to try out later at the modelling phase, for example using a convolutional neural network.
We also found [this paper](https://pdfs.semanticscholar.org/ab57/f45889b7099b98eea56399782dc7a4d5893a.pdf), which uses CNN-s to predict gender and age of blog posts, and [this paper](https://web.stanford.edu/class/cs224n/reports/6846198.pdf) where they predict genders of poems, with using CNN-s for extracting high level features from the text, and RNN-s to capture long term dependencies.

### Plans

We would like to try different kinds of networks (fully connected, convolutional, LSTM) and compare the results. We also planning to try other data preprocessing algorithms like stemming, for reducing vocabulary size, if necessary.


## Milestone II.

We refactored the data processing script, so it is now a cleaner code. We added world stemming to remove stopwords and also words that appear infrequently.

We built our neural network using the keras word embedding layer, which provide a dense representation of words and their relative meanings. It requires that the input data be integer encoded.

After the embedding layer we used dense layers to capture our feature, but the network is not learning well.


## Milestone III.

### Sentiment
We tried sentiment analysis to build a base model for the more complex gender classification. The related Python notebook is sentiment.ipynb and the database that was used is called Tweets.csv. This model was trained using a 7700k CPU.

### Gender determination
We preprocessed 50.000 blog posts with the methods presented in the first two milestones. After that we used our experience from the sentiment analysis, and we built a 1D convolutional network upon the keras word embedding layer. This model was trained on colab, with GPU-s.
The original database can be downloaded [from here](https://www.kaggle.com/tomlisankie/blog-posts-labeled-with-age-and-gender/) .It has to be renamed for test.json, for the dataPrepoc.ipynb, which we used to create a smaller database, already preformatted for training. The resulting file is the out2.json file, which can be downloaded from [google drive](https://drive.google.com/open?id=1eP3XWK-3QfMBlG6VepQmmD2Jccg-zsR6), which contains 50.000 blog posts. It is used for running the gender_conv.ipynb.

### Documentation
Our documentation is in Hungarian since we no longer aim to finish the course without an exam due to time constraints.

