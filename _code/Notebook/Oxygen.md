---
layout: blog
topic: Notebook
title: Connect to Oxygen
tags: 
comments: true
date: 2023-01-23
---

# Connect to Oxygen

```python
# To load packages and functions from oxygen:

import os
os.environ.setdefault("SETTINGS_MODULE", "configs.settings")
from oxygen.conf.context import context
```