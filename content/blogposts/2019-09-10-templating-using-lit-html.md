---
title: Templating using lit-html 🔥
date: '2019-09-10'
author: Shreerang Patwardhan
tags:
- templates
- lit-html
- polymer
- google
- performace
- web performace
photo_url: /blog/The_UI_Dev_Default.png
---


I joined [Williams Sonoma](https://www.williams-sonoma.com) as a Software Engineering Manger over 6 months back and that is when I was exposed to the world of `lit-html` 🔥. lit-html is an extremely small, simple and fast Javascript templating library. It provides for fast, efficient rendering and updating of HTML. lit-html is part of the [Google Polymer project](https://www.polymer-project.org/) and is built and maintained by the amazing team of engineers at Google led by [Justin Fagnani](https://twitter.com/justinfagnani).

lit-html utilizes some unique properties of JavaScript template literals and HTML `<template>` elements to function and achieve efficiency and fast performance. lit-html is not a framework and does not include any component model and so can be used with any existing framework like Vue or React or a component model like Web Components. lit-html focuses on one and only thing - **efficiently creating and updating the DOM.**

Let's look at some key factors you would want to consider before you start using lit-html as your templating library.

## Efficiency ⚡
I have been mentioning that lit-html is fast and efficient. The reason why it is fast is because it efficiently parses and renders the HTML. lit-html doesn’t use Virtual DOM like the latest trends in many UI libraries like React or Preact for instance, but instead is using web standards to generate and update a UI component. With this approach, lit-html is capable of analyzing the template literals and updating only the changed data, leaving the actual HTML node as is, increasing the render performance compared to the virtual DOM approach. Let's look at a simple template.

```javascript
<p>Welcome to the world of lit-html ${data.name}!</p>
```

Every time the value of `data.name` changes, libraries using virtual DOM will parse this template and re-render the entire node. lit-html on the other hand only renders the changed data value, which makes it extremely fast.

## Learning Curve 📉
lit-html relies on and leverages standard ES6 features, which means you need not learn anything new special syntax. If you are writing Javascript today you can start using lit-html now.

## Browser Compatibility 🌏
lit-html works across all major browsers including Google Chrome, Firefox, Safari, IE11 and Edge.

Hope this gave you a brief overview of `lt-html`. We are going to look into the detailed usage of it. In the blog posts to follow, I will look into the different aspects of creating and styling templates using lit-html and share some examples that you can follow along.