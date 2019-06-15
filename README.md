# Grab Challenge AI for SEA 2019

## Topic: Traffic 

### 1.Introduction
I would like to thank grab for giving me this opportunity to practice what I have learnt.<br>
I did a course on deeping learning just last week and I glad to be able to practice a few of the techniques here.<br>
To tackle this problem, I used a general 4 layer neural network. <br>
Please read through the notebooks below for the detail solution and how to test the model in the testing notebook
### 2.Important Files
#### 2.1.Notebooks
Here I explained my methodology and limitations.<br> [Training Notebook with detailed comments](Model_Preparation_and_Training.ipynb)
<br>
Refer upload your dataset into this notebook to obtain the mean square error as required. <br>[Testing Notebook for your test dataset ](Model_Testing.ipynb)

#### 2.2.Other files
**training_1st_half.csv,training_1st_half.csv** Combine to form original dataset (divided for uploading purpose only)<br>
**sample_test.csv** A random test set from the original data || placeholder for your test set<br>
**training_parameters.pkl** A pickle file containing [model parameters (weights), train accuracy,development accuracy , remaining training set]

### 3.Methodology
#### 3.1.Data
The goal is to use upto 14 days prior demand data to predict 5 timestamps worth of demand after time T.<br>
I used 13 days prior demand data as I do not wish to exceed the limit accidentally.<br>

The original data looks like:![alt text](./images/Data_head.PNG)
The time stamp and day column is transformed into a running index to better keep track of the prior and after set at any time T.<br>
![alt text](./images/Running_time_stamp.PNG)
To train the dataset, I have to change it into the desire features of [demand on T-1248, demand on T-1247 ... demand on T, latitude, longitude] **1251** columns:
Example features: ![alt text](./images/X_head.PNG)
Example targets: ![alt text](./images/Y_head.PNG)
**However this is caused memory issues (~160 GB required for such dataframe of roughly 4million by 1251)**<br>
Thus I used random sampling to seperate the training set into smaller subsets. And also adopted a minibatch approach in training.
![alt text](./images/Data_sampling.jpg)
#### 3.2.Model
I used a 3 layers neurual network as of following:
![alt text](./images/NN.PNG)
_picture taken from [http://neuralnetworksanddeeplearning.com/chap1.html] and edited on 15 June 2019_<br>
**Each layer is activated by a rectilinear function, and its value calculated as a linear function of X @ W + b.**<br>
**The model is regulated via L2 regulation for less overfitting due to having 1251 inputs** <br>
where x is the output of last layer, W is the weights, and b is a constant
### 4.Results
The training and development(1%) error in terms of mean square error is measured as of following with respect to iterations of sub training set<br>
**The average mean standard error for training is 0.0034550717, while mean standard error for development is 0.006478587**<br>
<br>
The entire training set contains 66 sub training set (thus the pattern observed below)
![alt text](./images/Results.PNG)
The below graph shows the mean square error of development set for each loop of 66 sub trainin sets (entire training set):<br>
It shows a smaller but limited improvement as we continue the training.<br>
This could be due to the stochasticity of the small random sub set
![alt text](./images/Improvement.PNG)
### 5.Conclusion
I would consider the model a rather accurate predicition of the case. <br>
However it would perform much better if I am able to training on the entire dataset instead of resampling.<br>
I received the email about Amazon Web service just this week, however I had a lot difficulties setting up an Amazon account due to payment issues. I ended up training on my local host where the computing power and memory is limited.<br>
<br>
I would like to thank Grab once again for providing such an opportunity.<br>
And I wish you a pleasant read of my reading.<br>

Best Wishes,<br>
Zhou Zhi