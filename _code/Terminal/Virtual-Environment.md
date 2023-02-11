---
layout: blog
topic: Terminal
title: Virtual Environment
tags: 
comments: true
date: 2022-09-24
---

# Virtual Environment


## Create a Local Virtual Environment

```shell
# On MacOS
python3 -m venv ~/.virtualenvs/bane

source ~/.virtualenvs/bane/bin/activate

pip3 install -r requirements.txt

# On Windows
python -m venv venv/bane
venv/bane/scripts/activate

## On Windows, may need to reset execution policy. Run Powershell as administrator and run the following code
Set-ExecutionPolicy Unrestricted -Force
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



