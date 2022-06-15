---
layout: blog
topic: Python
title: Instagram and Twitter Scrapping
tags: python ins instagram twitter scrapping
comments: true
date: 2022-06-15
---

# Instagram and Twitter Scrapping

## Instagram
```Python
import instaloader
import pandas as pd

L = instaloader.Instaloader()
L.login('username', 'password')
df = pd.DataFrame()

i=0
for post in instaloader.Profile.from_username(L.context, 'zara').get_posts():
    df = df.append({'Caption':post.caption, 'Likes':post.likes, 'Comments':post.comments, 'URL': post.url}, ignore_index = True)
    df.to_excel('zara_v3.xlsx', index = False)
    i = i + 1
    if i > 500:
        break
print('finished')
```

## Twitter
```Python
import os
import tweepy as tw
import pandas as pd

consumer_key= 'dGBHv4TVsWNvs9mu8qV0nechi'
consumer_secret= 'lqEggrb8Smsr6unaoc6pGLRrGHuHiaCOVHN4mLaKPCuvN2ztIZ'
access_token= '1067934304683139072-478JrFNGdIz8VuIScRpwcQxPUvrlQ7'
access_token_secret= 'W6MkqRH5ssdQR4qiR6t0P79bXOIeyJGm0TKTnr6tvyHv5'

auth = tw.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)
api = tw.API(auth, wait_on_rate_limit=True)

#set the search words
search_words = "debate"
tweets = tw.Cursor(api.search,
              q=search_words,
              lang="en").items(5000)
outtweets = [[tweet.id_str, tweet.created_at, tweet.text.encode("utf-8"), tweet.user.location] for tweet in tweets]
df = pd.DataFrame(outtweets, columns=["id", "created_at", "text", "location"])
df.to_csv(f"query_{search_words}.csv", index=False)

# scrap the tweets of a specific account
trump_tweets = api.user_timeline('realdonaldtrump')
for tweet in trump_tweets:
    print(tweet.text)
    
# scrap tweets containing the search word
search_words = "debate"
tweets = tw.Cursor(api.search,
              q=search_words,
              lang="en").items(5000)
outtweets = [[tweet.id_str, tweet.created_at, tweet.text.encode("utf-8"), tweet.user.location] for tweet in tweets]
df = pd.DataFrame(outtweets, columns=["id", "created_at", "text", "location"])
df.to_csv(f"query_{search_words}3.csv", index=False)
```
