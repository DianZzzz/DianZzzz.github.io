---
layout: blog
topic: HTML
title: CSS
tags: 
comments: true
date: 2023-01-11
---

#  CSS

Link a css file to HTML

```html
<head>
    <link rel="stylesheet" href="master.css">
</head>
```

## Boostrap
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js" integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN" crossorigin="anonymous"></script>
```
Source: [https://getbootstrap.com/docs/5.3/getting-started/download/](https://getbootstrap.com/docs/5.3/getting-started/download/)
## Bascis

```css

body{
    font-family: Tahoma
    font-size: 100%;
}
h1{
    text-align: center;
}

p{
    background-color: green;
}

div{
    border-width: 20px;
    border-style: dashed;
}

span{
    color: red;
}
```

## Selectors

```html
<p id="one"> this is red</p>

<div class="myclass">
    <p>this is pink</p>
</div>
```

```css
# class uses dot
.myclass{
    color:pink;
}

# id uses hashtag
#one{
    color:red;
}
```
## CSS Box Model

![](/assets/2023-01-11-16-40-56.png)
```css
#one{
    padding:10px;
    margin-left:10px;
}
```


## Use Googel Fonts
```html
<link rel="stylesheet"
          href="https://fonts.googleapis.com/css2?family=Crimson+Pro">
<style>
    body {
    font-family: 'Crimson Pro', serif;
    font-size: 48px;
    }
</style>
```