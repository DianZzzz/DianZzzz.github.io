---
layout: blog
topic: Terminal
title: Terminal Cheatsheet
tags: 
comments: true
date: 2023-01-23
---

# Terminal Cheatsheet

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