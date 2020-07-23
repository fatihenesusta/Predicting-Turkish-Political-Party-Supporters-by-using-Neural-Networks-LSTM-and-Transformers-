# Predicting-Turkish-Political-Party-Supporters-by-using-Neural-Networks-LSTM-and-Transformers-
## Aim of this project

The aim of this project is to be able to analyze if a given text is supporter of the current ruling party or against the current ruling party in Turkey. (2020)

### Data Preparation Part
##### Collecting Part

Since there is no such a labeled data set available for this kind of task, data had to be collected. I used BeautifulSoup from python to create a database in the first step.
I accessed different news sources and started to store their column writes. I specifically selected political ones because they will focus on political issues. After i started labeling them by looking at each column writer. You can learn a lot about which political party a column writer support by reading their few of their writes. Since i already have a political and international relations background it was not a hard task for me. I labeled them by [0 or 1], 0 if they are supporting current ruling party and 1 if they are against it. In the end, i was able to create my database with 5000f instances of column writes. 

##### Cleaning Part

1) Cleared data from html tags 
2) Lowered all data

### Modeling Part

I used BERT to stem and tokenize my data.

#### Long Short Term Memory Part

In this data base i had about 55000 unique tokens. So i set the maximum word number to be that number.

1) Tokenizer.text_to_sequences
 Every word in the database become a number and represented by a number and this transformed all my database to numbers to begin with. (Encoded words into numbers)

2) Pad sequences
  Remember, every sentence does not have equal length so what we need to is pad sequences in this part.
So we get the maximum length in our data base for an column write and based on this length we basically but 0's to beginning and end of the      other instances which is shorter. 
 

3) - I have set a [5] layer LSTM model after trying out different layers with the dropout rate being [0.2]
   - I used a softmax activation function
   - Used categorical_crossentropy
   - Set epoch to be [3]
   - Batch_size to be [100]
   
Some notes: After 3 epoch my model started to overfit so i decided to stick with 3. Best optimizer for my model was ["Nadam"]

#### Training

For training part accuracy hit 0.91 and validation accuracy hit about 0.7422 this number was the best i got after observering different types of parameters.

#### Test

Accuracy score of testing is: 0.75
F1 score is: 0.68


#### Transformers model will be added in near time
