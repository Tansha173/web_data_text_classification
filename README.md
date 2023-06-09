# Web Data Text Classification

## About the project

Given a dataset of natural language text scraped from websites. The goal is to build a classifier to take text and
associate it with a brand.

## Methodology
* EDA: 
    * Checking for label distribution
    * Checking for length of raw text for unknown vs not-unknown classes
    * Checking for log_scaled length distribution of raw text across brands categorized with frequency
    * Visible difference between the median count of numbers across different categories
    
* Preprocessing:
    * Removing stopwords
    * removing punctuation and non ASCII characters
    * Removing less frequenct words and creating a word to index mapping dict(non-frequent words are mapped to token-UNK)

* Baseline: LSTM
    * Does not perform well with sequential data as it takes one input at a time
    * Takes longer to train
    
* xlm-roberta-base
    * XLM-RoBERTa is a multilingual version of RoBERTa. It is pre-trained on 2.5TB of filtered CommonCrawl data containing 100 languages.RoBERTa is a transformers model pretrained on a large corpus in a self-supervised fashion with the Masked language modeling (MLM) objective. Taking a sentence, the model randomly masks 15% of the words in the input then run the entire masked sentence through the model and has to predict the masked words.
    
## Usage

import requests

url = 'http://127.0.0.1:5000/'
response = requests.post(url, json=text_to_predict)
print(response.json())

Output
{'roblox': 2.0151207447052, 'unknown': 2.862473964691162, 'wayfair': 2.7404298782348633}
