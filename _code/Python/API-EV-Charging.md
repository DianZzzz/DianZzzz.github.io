---
layout: blog
topic: Python
title: API EV Charging
tags: python api
comments: true
date: 2022-06-14
---

# API EV Charging

```Python
!pip install requests
import requests
import json
import pandas as pd

response = requests.get("https://developer.nrel.gov/api/alt-fuel-stations/v1.json?&api_key=[API KEY]")
data = json.loads(response.text)

data.keys()

df = pd.DataFrame(data['fuel_stations'])
df.to_csv('evcharging.csv')
```

  
