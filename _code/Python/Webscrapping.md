---
layout: blog
topic: Python
title: Webscrapping
tags: python
comments: true
date: 2022-06-15
---

# Webscrapping

```Python
import requests
from bs4 import BeautifulSoup
from lxml import html
import pandas as pd

df = pd.DataFrame(columns=['product_name', 'product_review', 'user_rating'])
    
base_url = 'https://www.beeradvocate.com'
    
page = requests.get(base_url+'/beer/top-rated/')
soup = BeautifulSoup(page.text,'html.parser')

cells = soup.find_all('td')

for cell in cells:
    if len(cell) == 2:            
        product = cell.find('b').text
        ex_url = cell.find('a')['href']
        test1 = cell.find('a').text
        product_page = requests.get(base_url+ex_url)
        tree = html.fromstring(product_page.content)
        for i in range(1,26):
            try:
                reviews = tree.xpath('/html/body/div[2]/div/div[2]/div[2]/div[2]/div/div/div[3]/div/div/div[2]/div[8]/div/div[{}]/div[2]/text()'.format(i))[1:]
                review = ''
                rating = tree.xpath('/html/body/div[2]/div/div[2]/div[2]/div[2]/div/div/div[3]/div/div/div[2]/div[8]/div/div[{}]/div[2]/span[2]/text()'.format(i))[0]
                for line in reviews:
                    review += line.strip('\n') + ' '
                df = df.append({'product_name': product,
                                'product_review': review, 
                                'user_rating': rating}, 
                                ignore_index=True)
            except:
                pass
```
