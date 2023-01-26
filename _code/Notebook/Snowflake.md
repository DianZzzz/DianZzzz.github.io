---
layout: blog
topic: Notebook
title: Connect to Snowflake
tags: 
comments: true
date: 2023-01-23
---

# Connect to Snowflake

## Download requirement file

[https://github.com/snowflakedb/snowflake-connector-python/tree/main/tested_requirements](https://github.com/snowflakedb/snowflake-connector-python/tree/main/tested_requirements)

```shell 
pip install -r https://raw.githubusercontent.com/snowflakedb/snowflake-connector-python/v2.5.0/tested_requirements/requirements_36.reqs
```

## Download connector
```shell 
pip install snowflake-connector-python
```

## Import liraries

```python
import os
import snowflake.connector
import numpy as np
import os
import pandas as pd
import warnings
warnings.filterwarnings('ignore')
from datetime import datetime
pd.set_option('display.max_columns', 500)
pd.set_option('display.max_rows', None)
```