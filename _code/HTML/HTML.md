---
layout: blog
topic: HTML
title: HTML
tags: 
comments: true
date: 2023-01-10
---

#  HTML

## Shortcuts

### doc
Start writing an HTML file with ```doc``` which will autopopulate the following script

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

### lo
Generate text filler with ```lo```
```html
Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quo numquam officiis sapiente officia minus saepe accusamus eaque, distinctio quis pariatur quae omnis incidunt ut temporibus nulla sunt laudantium. Eligendi, neque?
```

## Tags

```html
<h1>Header 1</h1>
<h2>Header 2</h2>
<h6>Header 6</h6>

<div style="color:red">
    <p> paragraph 1</p>
    <p> the word <span style="color:pink">pink</span> is pink</p>
</div>

<! Comment>

# Images
<img src="path-to-image" alt="Image not found">

# Hyperlinks
<a href="https://www.google.com">CLICK HERE</a>

# Lists
<ol> 
    <li> item 1</li>
    <li> item 2</li>
</ol>

<ul>
    <li> item 1</li>
    <li> item 2</li>    
</ul>

# Nested list
<ol> 
    <li> item 1</li>
    <ul>
        <li> sub item</li>
        <li> sub item</li>    
    </ul>
    <li> item 2</li>
</ol>

# Table

<table border="2">
    <thead>
        <th> Col 1</th>
        <th> Col 2</th>
        <th> Col 3</th>
    </thead>
    <tr>
        <td> data 1</td>
        <td> data 2</td>
        <td> data 3</td>
    </tr>
</table>

```

## HTML Forms
```html
<form action = "example.html">

    <label for="lname">Last Name:</label>
    <input type="text" id="lname" name="lname" placeholder="Last Name">
    <br>
    <textarea name="feedback" id="feedback" cols="30" rows="10"> 
    </textarea>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
    <br>
    <label for="pw">Password:</label>
    <input type="password" id="pw" name="pw">
    <br>
    <label for="search">Search:</label>
    <input type="search" id="search" name="search" />
    <br>
    <input type="submit">
</form>

<form action = "example.html">
    <p> A multiple choice question</p>
    <br>
    <label for="a">Option A</label>
    <input type="radio" id="a" name="a">
    <label for="b">Option B</label>
    <input type="radio" id="b" name="b">
    <br>

    # To force single choice, assign the same name to both options
    <label for="a">Option A</label>
    <input type="radio" id="a" name="option" value="a">
    <label for="b">Option B</label>
    <input type="radio" id="b" name="option" value="b">
    </form>

<form action = "example.html">
    <p>Drop down box</p>
    <select name="box" id="box">
        <option value="good">Good</option>
        <option value="bad">Bad</option>
    </select>

</form>
```