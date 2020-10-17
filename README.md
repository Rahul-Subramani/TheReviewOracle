## 1.1 INTRODUCTION

When people plan to purchase a product (eg. Smartphone), they conduct extensive research of the product category for features, prices, customer-reviews, video-reviews on YouTube and ask their friends who know the product category very well.

In these scenarios, consumers spend hours of time researching the product that matches their needs and budget. A lot of times, research conducted online is very time-consuming as it needs a good read through and many view hours of the content.


## Requirements
* Beautiful Soup
* Selenium WebDriver

## Usage
* Install the requirements by running `pip install bs4 selenium`.
* Add geckodriver to the PATH. Follow these [instructions](http://stackoverflow.com/questions/40208051/selenium-using-python-geckodriver-executable-needs-to-be-in-path).
* Put the link of the product in `site` variable inside the script.
* Run the script by running `python scrape.py`.
* Reviews will be saved in the file `review.txt`.


## 1.2 OBJECTIVES OF THE PRODUCT

Our aim is to build a web application that assists users in making decisions to buy products. It will gather reviews along with the details, from multiple websites, which sell the product and produces it to the user. Other than that, the system is trained using Machine Learning to analyse the polarity of the product.

## 1.3 PROBLEM STATEMENT

To create a web application that gathers reviews along with the details from multiple websites and present it to the user.

Other than that, the system is trained using Machine Learning to analyse the polarity of the product.

Our project mainly relays on three modules - information crawler, sentiment analysis, review overview.

## 2.1 Information crawler

A Web crawler, sometimes called a spider or spiderbot, often shortened to crawler, is an Internet bot that systematically browses the World Wide Web, typically for the purpose of Web indexing (web spidering).

Web search engines and some other sites use Web crawling or spidering software to update their web content or indices of others sites' web content. Web crawlers copy pages for processing by a search engine which indexes the downloaded pages so users can search more efficiently.

In our system we use R script to crawl amazon website to scrape information about our project. The main library use is rvest. Rvest is new package that makes it easy to scrape (or harvest) data from html web pages, inspired by libraries like beautiful soup. It is designed to work with magrittr so that you can express complex operations as elegant pipelines composed of simple, easily understood pieces.  

## 2.2 Sentiment Analysis

Sentiment Analysis is the most common text classification tool that analyses an incoming message and tells whether the underlying sentiment is either positive, negative or neutral. There are many methods and algorithms to implement sentiment analysis systems, which can be classified as:

• Rule-based systems that perform sentiment analysis based on a set of manually crafted rules.

-   Automatic systems that rely on machine learning techniques to learn from data.
    
-   Hybrid systems that combine both rules based and automatic approaches.

We use automatic system (RNN) to build our Sentiment analyzer. Recurrent Neural Network (RNN) are a type of Neural Network where the output from previous step are fed as input to the current step. In traditional neural networks, all the inputs and outputs are independent of each other, but in cases like when it is required to predict the next word of a sentence, the previous words are required and hence there is a need to remember the previous words. Thus, RNN came into existence, which solved this issue with the help of a Hidden Layer. The main and most important feature of RNN is Hidden state, which remembers some information about a sequence.

RNN have a “memory” which remembers all information about what has been calculated. It uses the same parameters for each input as it performs the same task on all the inputs or hidden layers to produce the output. This reduces the complexity of parameters, unlike other neural networks

## 2.3 Review Overview

An Overview is a text output that is generated from one or more texts that conveys relevant information from the original text in a shorter form. The goal of automatic review overview is to transform the source text into a shorter version using semantics.

We develop a basic character-level sequence-to-sequence (seq2seq) model by defining the encoder-decoder recurrent neural network (RNN) architecture.

The encoder-decoder architecture is used as a way of building RNNs for sequence predictions. It involves two major components: an encoder and a decoder. The encoder reads the complete input sequence and encodes it into an internal representation, usually a fixed-length vector, described as the context vector. The decoder, on the other hand, reads the encoded input sequence from the encoder and generates the output sequence. Various types of encoders can be used — more commonly, bidirectional RNNs, such as LSTMs, are used.

# SYSTEM IMPLEMENTATION

Dividing the modules before developing is very important for every product that is being developed. Because, it paves the way for parallel development and then finally combining It by integration. Some of the major modules of this project include.

1.Input Query
2.Information Crawler 
3.Sentiment Analysis 
4.Review Overview 
5.Data Visualizer

3.1.1 INPUT QUERY

The input to the system will be given by the user. Usually the input will be the products that the user wishes to buy.


3.1.2 INFORMATION CRAWLER

A Web crawler, sometimes called a spider or spiderbot and often shortened to crawler, is an Internet bot that systematically browses the World Wide Web, typically for the purpose of Web indexing (web spidering).

Web search engines and some other sites use Web crawling or spidering software to update their web content or indices of others sites' web content. Web crawlers copy pages for processing by a search engine which indexes the downloaded pages so users can search more efficiently.

In our system we use R script to crawl amazon website to scrape information about our project. The main library use is rvest. Rvest is new package that makes it easy to scrape (or harvest) data from html web pages, inspired by libraries like beautiful soup. It is designed to work with magrittr so that you can express complex operations as elegant pipelines composed of simple, easily understood pieces.

3.1.3 SENTIMENT ANALYSER

Sentiment Analysis also known as Opinion Mining. It is a field within Natural Language Processing (NLP) that builds systems which try to identify and extract opinions within text. In order to load the data, we will use the SQLITE dataset where we will only fetch the Score and the recommendation summary. The purpose of this model is to make up a prediction where we will be able to predict whether a recommendation is positive or negative.

We use RNN for Sentiment Analyser. RNN input requires array data type, therefore, we convert the “Reviews” into the X array and “Sentiment” into the Y array accordingly. Text data has to be integer encoded before feeding it into the RNN model. This can be easily achieved by using basic tools from the Keras library. The text should be tokenized by fitting Tokenizer class on the data set.

The original reviews turn into a sequence of integers after applying prepocessing. we use pad_sequences class on the list of integers to ensure that all reviews have the same length, which is a very important step for preparing data for RNN model. Applying this class would either shorten the reviews to 100 integers, or pad them with 0’s in case they are shorter. As embedding requires the size of the vocabulary and the length of input sequences, we set vocabulary size at the number of words in Tokenizer dictionary + 1 and input_length at 100 (max_words).

We add 1 hidden LSTM layer with 200 memory cells. Potentially, adding more layers and cells can lead to better results. We have successfully trained and validated the performance of RNN for sentiment prediction.

## CONCLUSION

Thus, the product being developed is useful for those who want to analyse about a particular product and they will find answer for whether to buy a product or not. Instead of manually searching for many websites, they can find all these information using our product.

### References: 
1.  Joseph O'Connor, NLP Workbook: A Practical Guide to Achieving the Results You Want.
    
2.  Natural language processing (almost) from scratch (2011), R. Collobert et al.
    
3.  Auli M, Galley M, Zweig, Joint Language and Translation Modeling with recurrent neural network.
    
4.  François Chollet, Deep Learning with Python.
    
5.  Jerome H. Friedman, Robert Tibshirani, and Trevor Hastie, The Elements of Statistical Learning.
    
6.  AntonioGulli,DeepLearningwithKeras.
