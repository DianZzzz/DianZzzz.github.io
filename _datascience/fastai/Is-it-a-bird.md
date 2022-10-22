---
layout: blog
topic: fastai
title: Is it a bird
tags: learning datascience fastai ai
comments: true
date: 2022-10-19
---

# Is it a bird

Works better on Google Colab with GPU
## Download images from DuckDuckGo
```python
!pip install -Uqq duckduckgo_search
!pip install fastcore
!pip install fastai
!pip install fastdownload

from duckduckgo_search import ddg_images
from fastcore.all import *
from fastdownload import download_url
from fastai.vision.all import *

def search_images(term, max_images=200): 
    return L(ddg_images(term, max_results=max_images)).itemgot('image')

# test
download_url(search_images('bird photos', max_images = 1))[0],'bird.jpg', show_progress = False)
Image.open('bird.jpg').to_thumb(256,256)

# download a bunch of bird and non-bird photos and save to separate folders

from time import sleep

searches = 'forest','bird'
path = Path('bird_or_not')

for o in searches:
    dest = (path/o)
    dest.mkdir(exist_ok=True, parents=True)
    download_images(dest, urls=search_images(f'{o} photo'))
    sleep(10)  # Pause between searches to avoid over-loading server
    download_images(dest, urls=search_images(f'{o} sun photo'))
    sleep(10)
    resize_images(path/o, max_size=400, dest=path/o)

# check for failed downloads
failed = verify_images(get_image_files(path))
failed.map(Path.unlink)
len(failed)

# train the model 
dls = DataBlock(
    blocks=(ImageBlock, CategoryBlock), 
    get_items=get_image_files, 
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    get_y=parent_label,
    item_tfms=[Resize(192, method='squish')]
).dataloaders(path)

dls.show_batch(max_n=6)

# resnet18 currently the fastest computer vision model
learn = vision_learner(dls, resnet18, metrics=error_rate)
learn.fine_tune(3)

# apply the model
is_bird,_,probs = learn.predict(PILImage.create('bird.jpg'))
print(f"This is a: {is_bird}.")
print(f"Probability it's a bird: {probs[0]:.4f}")

```
