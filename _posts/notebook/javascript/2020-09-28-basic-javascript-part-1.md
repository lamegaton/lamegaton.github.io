---
layout: post
title: Basic JavaScript Part 1
categories: en javascript
author: "Son Pham"
meta: 
description: "Basic javascript for a simple dynamic or static website"
---



In this tutorial, I will introduce a few steps to access and edit elements in JavaScript. Mastering and understanding these steps can help you make a simple form, handling submission, and change the outlook of your website.

* TOC {:toc}

### Edit a text or HTML via jQuery  

This example implement jQuery. So we have an HTML file with div id="text" and we want to change Hello to  Hello, dolly. 

<div id="test" style="background-color:#CCFFCC">Hello, this is wrapped with a div, you can open your console and test it.</div>


```html
<html>
<div id="test">Hello</div>
</html>
```

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
Asynchronous is used when user want to fetch data from server without refreshing the page.   
IE5 and IE6 have different object name for async 

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



According to Mozilla, XMHttpRequest doesn't need any parameters and return after open() and send() methods are executed. 

A simple request will be as the following snippet:

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

