---
layout: blog
topic: Terminal
title: Command Line
tags: 
comments: true
date: 2022-09-24
---

# Command Line

## General

```shell
pwd # current working directory
cd downloads # go to downloads folder
cd .. # go to parent folder
ls # list directory contents
```

## Git

![](/assets/2022-09-28-01-45-43.png)


### Conda Environment

1. Create a conda environment file .yml

```
name: NAME
channels:
  - defaults
  - conda-forge
dependencies:
  - jupyter
  - nb_conda_kernels
  - python=3.10
  - pip:
    - numpy
    - pandas
    - scikit-learn
    - matplotlib
    - seaborn
```
2. In the terminal, run ```conda env create -f NAME.yml```

3. In the terminal, run ```conda activate NAME```

4. To open jupyter notebook in that environment, in the terminal, run ```jupyter notebook```

5. To remove an environment, in the terminal, run ```conda env remove -n NAME```

6. To save environment configuration, in the terminal, run ```conda env export > NAME.yml```

## Jupyter Notebook

Terminate notebook: control + x c

