# Store Item Demand Forecasting Challenge
# Few Questions
a.	[What is the overall purpose of this project?](#Overall-Purpose)\
b.	[What do each file in your repository do?](#File-Function)\
c.	[What methods did you use to clean the data or do feature engineering?](#Feature-Engineering)\
d.	[What methods did you use to generate predictions?](#Prediction-Method)

## Overall Purpose
This competition is provided to develop a machine learning program to identify when an article might be fake news. Run by the UTK Machine Learning Club.

The evaluation metric for this competition is accuracy, a very straightforward metric.

\[ accuracy = \frac{correct\ predictions}{correct\ predictions+incorrect\ predictions}\]

Accuracy measures false positives and false negeatives equally, and really should only be used in simple cases and when classes are of generally equal class size

Submission Format
For every article in the test dataset, submission files should contain two columns: `id` and `label`. The `id` column should refer to a row in the `test.csv` file, and the `label` column should refer it's class of reliable , or potentially fake .

The file should contain a header and have the following format:

id,label\
182041,1\
182042,0\
182043,1\
182044,0\
etc.


## File Function
There're 2 files in this Repo: fake-news.ipynb and README.md file which compelely describe how this file works.

## Feature Engineering
### Data Fields
* title: based on each day from 01/01/2013 - 12/31/2017
* author: Integer that represents different stores
* text: Integer represents different items
* label:    1 -- represent it potentially fake
            0 -- represent it's reliable

## Prediction Method

Sequential Model is the model I used for all three submission. A Sequential model is appropriate for a plain stack of layers where each layer has exactly one input tensor and one output tensor. To better optimize the model, the only difference between these three submission files are their text content. The basic step is: get all the text content, filter the stopwords and standardize the text bying lowering it and revoming the spaces. Then, using the tensorflow package one_hot/pad_sequences to convert the words into number and train the model using test data.

1 - Full content including title/author name/text - It takes a really long time to run the data cleaning process. But since it's pretty specific and detailed, the final public socre is 0.99, rank 1/12

2 - I only use text content for this model training, it reduces a fair amount of time, however, the accuracy decreased somehow. So I am wondering if the title and author name makes it a different or weigh a huge part. The submission score is 0.86, rank 9/12

3 - This time I only use title and author name to do the test, and this time it greatly reduced the processing time. And the final score is 0.99, rank 1/12
