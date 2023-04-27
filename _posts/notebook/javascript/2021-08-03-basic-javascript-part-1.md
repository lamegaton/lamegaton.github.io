---
layout: post
title: Basic JavaScript Part 1
categories: javascript
author: "Son Pham"
meta: Javascript tutorial
description: "Basic javascript for a simple dynamic or static website"
tags: [javascript]
comments: false
---



In this tutorial, I will introduce a few steps to access and edit elements in JavaScript. Mastering and understanding these steps can help you make a simple form, handling submission, and change the outlook of your website.

Table of Contents:

* Placeholder for Table of Content (Must not be removed)
{:toc}

### Edit a text or HTML via jQuery  

This example implement jQuery. 

jQuery is a popular JavaScript library that simplifies DOM manipulation and event handling in web development. One of its key strengths is its ability to quickly and easily edit the content of text or HTML elements on a web page.

So we have an HTML file with div id="text." 

<div id="test" style="background-color:#CCFFCC">Hello, this is wrapped with a div, you can open your console and test it.</div>


```html
<html>
<div id="test">Hello</div>
</html>
```

To change "Hello" to "Hello, dolly" using jQuery, you can use the `text()` method as follows:


|JavaScript|jQuery|
|--|--|
| `document.getElementById("text").innerText = "Hello, dolly";` |`$(#text).text("Hello, dolly");`|


```javascript
$("<selector><put your class, id or type here>").text("<what do you want to change>");
<selector>:
"." : for class
empty: for type
"#": for id
```

### Target other elements:  

```html
<div id="mom-dad">
    <div id="son">Bob</div>
    <div id="daughter">Allice</div>
</div>
```

#### Parent

The code will change the background color of the `div` element with `id="mom-dad"` to blue.

```javascript
$("#son").parent().css("background-color", "blue")
```

#### Child 

```javascript
$("#mom-dad").children().css("color", "blue")
```
#### Next sibling

```javascript
$("#son").nextSibling;
```


### Submit to another page  

```javascript
$("#myform").attr('action', 'page1.php');
```

ref:
1 https://stackoverflow.com/questions/5451600/jquery-to-change-form-action  
2 https://stackoverflow.com/questions/15308017/save-data-through-ajax-jquery-post-with-form-submit  

### Add new item $().append

   

### If else in jQuery

```javascript
$(function() {
    $("#reg").click(function () {
        if ($("#frm01").is(":visible"))
            $("#frm01").slideUp(1000);
        else
            $("#frm01").slideDown(1000);
    });
});
```

https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/create-a-basic-javascript-object

### change display of an element
```javascript
document.getElementbyId(<ID>).style.display='none'; // or inherit
```

```
<option selected disable value="">  </option>
```

### Async 
Asynchronous requests are commonly used when a user wants to fetch data from a server without having to refresh the page. This allows for a smoother user experience and faster loading times. 

It's important to note that different web browsers may have different object names for handling asynchronous requests. For example, IE5 and IE6 use the `ActiveXObject` object, while modern browsers use the `XMLHttpRequest` object. Therefore, it's important to use feature detection and check for the availability of these objects before making an asynchronous request to ensure compatibility across different browsers.

```javascript
function asynRequest(){
	try {
		var xhtml = new XMLHttpRequest()
	} catch {
		try {
			something
			} catch {
				something different
			}
		}
	}
}
```

According to Mozilla, the `XMLHttpRequest` object does not require any parameters and will return after the `open()` and `send()` methods have been executed.

Here's a simple example of how to make an `XMLHttpRequest`:

```javascript
const request = new XMLHttpRequest();
var url = 'https://jsonplaceholder.typicode.com/users/2';
//XMLHttpRequest.open(method, url[, async[, user[, password]]])
request.open('GET',url,true);
// every time the readyState property change, this (callback) funtion will be executed
request.onreadystatechange = function() {
    let status = request.status;
    if (status === 0 || (status >= 200 && status < 400)) {
      // The request has been completed successfully
		console.log(xhr.responseText);
    } else {
    	console.log("Error!");
}
```

