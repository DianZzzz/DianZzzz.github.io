---
layout: blog
topic: Terminal
title: Terminal Cheatsheet
tags: 
comments: true
date: 2023-01-23
---

# Terminal Cheatsheet
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
## Python

```shell
python --version # check python version
exit() ## exit python environment

```

## Jupyter Notebook
Terminate notebook: `control` + `c`

## Airflow

Run DAG: `python run.py dag <dag-label>`

### Second Screen

```shell
## Start a second screen
screen

python run.py dag <dag-label>

## Exit
control a + d

## Return to the second screen
screen -r <screen-id>