---
layout: blog
topic: Django
title: Setup
tags: devop django
comments: true
date: 2023-01-12
---

# Setup Django Project

## Create a virtual environment

```shell
mkdir .virtualenvs
python3 -m venv ~/.virtualenvs/djangodev
source ~/.virtualenvs/djangodev/bin/activate
```

## Install Django

Once the virtual environment is activated, pip install django

```shell
python3 -m pip install Django
```

## Initiate a Project


```shell
#navigate to the project folder
#create a project named foodie
django-admin startproject foodie
```

## Create an app

Open a vscode terminal
```shell
#activate the virtual environment
source ~/.virtualenvs/djangodev/bin/activate

#navigate to the project folder 
cd foodie

#create an app named dian_list
python manage.py startapp dian_list  
```
It will create a folder `dian_list`. Under this folder, create a folder named `templates` and a subfolder `dian_list` under `templates`

![](/assets/2023-01-17-14-51-58.png)

## Create a view

