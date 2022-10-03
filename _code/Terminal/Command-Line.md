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

### Git workflow

1. Clone the repo

```git clone https://github.com/someorg/reponame.git```

2. a. Go into the repository directory
```cd reponame```

2. b. Pull from master
```git checkout master```
```git pull```

3. Create a branch

```git checkout –b username/feature_description```

4. ```git push origin username/feature_description```

5. Add files
```git add file1.py```

6. Commit 

```git commit –m “some message"```

7. git push

8. git pull

9. See the changes made

```git diff```

8. 



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

Terminate notebook: control + c

