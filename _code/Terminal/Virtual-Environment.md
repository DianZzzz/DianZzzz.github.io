---
layout: blog
topic: Terminal
title: Virtual Environment
tags: 
comments: true
date: 2022-09-24
---

# Virtual Environment

## General

```shell
pwd # current working directory
cd downloads # go to downloads folder
cd .. # go to parent folder
ls # list directory contents
touch file.txt # create a new file
open -t file.txt #open a file 
ls -la #see hidden file and permission
ping ip_address #test connection
```
## Create a Local Virtual Environment

```shell

python3 -m venv bane

source bane/bin/activate

pip3 install -r requirements.txt
```
To create the same environment on jupyter notebook, activate the environment and run the following in the terminal

```shell
ipython kernel install --user --name=jarvis
```
## Create a Conda Environment

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



