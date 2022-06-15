---
layout: blog
topic: Python
title: Text & Image Analytics
tags: python analytics 
comments: true
date: 2022-06-15
---

# Text & Image Analytics

## Word Frequency

```Python

import matplotlib.pyplot as plt
%pylab inline
import numpy as np
import pandas as pd
import warnings
warnings.filterwarnings('ignore')

#remove punctuation and lowerize

from string import punctuation

def removepunc(item):
    for p in punctuation:
        item = item.strip().replace(p,'')
    return item

def lowerize(x):
    return x.lower()

text['comments2'] = text['comments'].apply(removepunc).apply(lowerize)

#tokenize

import nltk
from nltk.tokenize import sent_tokenize, word_tokenize
nltk.download('punkt')

text['comments3'] = text['comments2'].apply(word_tokenize).apply(set).apply(list)

#remove stopwords

nltk.download('stopwords')
stop_words = stopwords.words('english')
def remove_stopwords(s):
    return [w for w in s if w not in stop_words]
text['comments4'] = text['comments3'].apply(remove_stopwords)

#lemmatize
wordnet_lemmatizer = WordNetLemmatizer()

def lemma(n):
    return wordnet_lemmatizer.lemmatize(n)
    
text['comments5'] = text['comments4'].apply(lemma) 

#get word frequency list

total_tag = text['comments5'].sum() # add up all the words

from nltk import FreqDist
word_freq = nltk.FreqDist(total_tag)

#return a list of top 500 most frequent words in a tuple of (word, freq)
top_words = word_freq.most_common(500)

#convert to dictionary
top_words_dict = {}
for (key, items) in top_words:
    top_words_dict = items
```

## Sentiment Analysis

```Python
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyser = SentimentIntensityAnalyzer()

def vader(item):
    return analyser.polarity_scores(item)['compound']

raw['sentiment'] = raw['text'].apply(vader)
```

## GCP Image Analytics

```Python
import xlrd
from google.cloud import vision
import os

application_credentials = 'xxxx.json'
os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = application_credentials
client = vision.ImageAnnotatorClient()
image = vision.Image()

loc = ('zara_v4.xlsx')
wb = xlrd.open_workbook(loc)
sheet = wb.sheet_by_index(0)
sheet.cell_value(0,0)
df_gogl = pd.DataFrame()

for i in range(sheet.nrows):
    image_src_temp = sheet.cell_value(i, 3) #point to the cell with image address
    image.source.image_uri = image_src_temp
    response = client.label_detection(image=image)
    labels = response.label_annotations
    l = []
    for label in labels:
        l.append(label.description)
    s = ' '.join(l)
    print(s)
    df_gogl = df_gogl.append({'URL':image_src_temp, 'Labels': s}, ignore_index = True)
df_gogl.to_excel('labels.xlsx', index = False)
```

## Topics Analytics
```Python
import lda
import nltk
from nltk.tokenize import PunktSentenceTokenizer, RegexpTokenizer
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer
from scipy import sparse
from sklearn.feature_extraction.text import CountVectorizer

nltk.download('stopwords')
nltk.download('punkt')
nltk.download('wordnet')

word_tokenizer = RegexpTokenizer(r'\w+')
wordnet_lemmatizer = WordNetLemmatizer()
stopwords_nltk = set(stopwords.words('english'))

def tokenize_text(s):
    lowercase = s.lower()
    text = wordnet_lemmatizer.lemmatize(lowercase)
    tokens = word_tokenizer.tokenize(text)
    return tokens

vec_words = CountVectorizer(tokenizer=tokenize_text, stop_words = stopwords_nltk, decode_error = 'ignore')
total_features_words = vec_words.fit_transform(zara_label['Labels'])

# set the number of topics to be selected
ntopics = 3
model = lda.LDA(n_topics = ntopics, n_iter=500, random_state = 1)
model.fit(total_features_words)

topic_word = model.topic_word_
doc_topic = model.doc_topic_
doc_topic = pd.DataFrame(doc_topic)
zara_label = zara_label.join(doc_topic)

zara = pd.DataFrame()
for i in range(ntopics):
    topic = 'topic_' + str(i)
    zara[topic] = zara_label.groupby('URL')[i].mean()
    
zara.to_excel('document_topic_dist.xlsx')

topics = pd.DataFrame(topic_word)
topics.columns = vec_words.get_feature_names()
topics1 = topics.transpose()

topics1.to_excel('topic_word_dist.xlsx')
```
