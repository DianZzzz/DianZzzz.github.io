---
layout: blog
topic: Python
title: Scrap App Store Reviews
tags: python scrap apple google android
comments: true
date: 2022-06-14
---

# Scrap App Store Reviews

## Google Play Store

```Python
!pip install -qq google-play-scraper

import json
import pandas as pd
from tqdm import tqdm
from pygments import highlight
from pygments.lexers import JsonLexer
from pygments.formatters import TerminalFormatter
from google_play_scraper import Sort, reviews, app

app_packages = [
  'com.dave',
]

app_infos = []

for ap in tqdm(app_packages):
  info = app(ap, lang='en', country='us')
  del info['comments']
  app_infos.append(info)
  
def print_json(json_object):
  json_str = json.dumps(
    json_object, 
    indent=2, 
    sort_keys=True, 
    default=str
  )
  print(highlight(json_str, JsonLexer(), TerminalFormatter()))
   
 app_reviews = []

for ap in tqdm(app_packages):
  for score in list(range(1, 6)):
    for sort_order in [Sort.MOST_RELEVANT, Sort.NEWEST]:
      rvs, _ = reviews(
        ap,
        lang='en',
        country='us',
        sort=sort_order,
        count= 200 if score == 3 else 100,
        filter_score_with=score
      )
      for r in rvs:
        r['sortOrder'] = 'most_relevant' if sort_order == Sort.MOST_RELEVANT else 'newest'
        r['appId'] = ap
      app_reviews.extend(rvs)
      
app_reviews_df = pd.DataFrame(app_reviews)
app_reviews_df.to_csv('google reviews.csv', index=None, header=True)
```

## Apple App Store

``` Python
!pip install app_store_scraper

from app_store_scraper import AppStore
import pandas as pd
import numpy as np
import json

chime = AppStore(country="us", app_name="chime mobile banking")

chime.review(how_many=10000)

df = pd.DataFrame(np.array(bakkt.reviews),columns=['review'])

df2 = df.join(pd.DataFrame(df.pop('review').tolist()))

df2.to_csv('apple_reviews.csv', index=None, header=True)
```
