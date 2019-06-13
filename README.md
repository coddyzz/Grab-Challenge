# Grab Challenge AI for SEA 2019

## Topic: Traffic 
To tackle this problem, I used a general 4 layer neural network. <br>
Please read through the notebooks below for the detail solution and how to test the model in the testing notebook

#### Notebooks
Here I explained my methodology and limitations. [Training Notebook with detailed comments](../Model_Preparation_and_Training.ipython)
<br>
Refer upload your dataset into this notebook to obtain the mean square error as required. [Testing Notebook for your test dataset ](../Model_Testing.ipython)

#### Other files
**devX.csv , devY.csv** 1% development set, takes about 7min to process from sratch, so I will load it for faster processing<br>
**training_1st_half.csv,training_1st_half.csv** Combine to form original dataset (divided for uploading purpose only)<br>
**1%test_sample.csv** A random test set from the original data || placeholder for your test set<br>
**training_parameters.pkl** A pickle file containing [model parameters (weights), train accuracy,development accuracy , remaining training set]

#### Results from 1% development test
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")