---
layout: post
title: "Using Ajax, Xhttp, Fetch, and Axios to get page content"
categories: javascript
comments: false
author: "Son Pham"
---



## Axios

Axios is a popular JavaScript library used for making HTTP requests from a browser or Node.js. It provides a simple and elegant way to make asynchronous HTTP requests to a server, and handle responses in a clean and efficient manner.

One common use case for Axios is to retrieve the content of a web page from a server. This can be achieved by sending a GET request to the server using Axios, and handling the response in the form of a promise.

In this way, you can fetch data from a web page and use it in your application. Whether you need to retrieve data for a single page or multiple pages, Axios can simplify the process and help you manage your data more efficiently.

```javascript
axios.get({
  method: 'get',
  url: url,
  responseType: 'stream'
})
  .then(function (response) {
    // handle success
    document.getElementById("result").innerText = JSON.stringify(response.data);
    document.getElementById("error_001").innerText = response.data;
    console.dir(response.data);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .then(function () {
    // always executed
  });

    event.preventDefault();

}, false);
```



## Fetch

Fetch is a built-in web API in modern browsers that allows you to make HTTP requests to a server and retrieve data in a simple and straightforward way. It provides an alternative to the traditional XMLHttpRequest (XHR) API, and is designed to be easy to use and flexible.

Fetch can retrieve the content of a web page from a server by sending a GET request to the server using the fetch() function, and handling the response in the form of a promise.

It's important to note that Fetch only works in modern browsers, and may not be supported in older versions. However, it offers several advantages over the XHR API, including a simpler API, support for Promises and async/await, and better handling of errors and response types.


HTML
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<div id="result">If you don't have one, try this: https://jsonplaceholder.typicode.com/users/1</div>
<input type="text" name="url" id="link_box" placeholder="Please input the link" value="https://jsonplaceholder.typicode.com/users/1">
<div class="spacer"></div>
<button id="link_box_submit_btn">Okay, here you go</button>
<div id="error_001">This is the error</div>
```
CSS
```css
#result{
  padding: 10px;
}
#link_box, #link_box_submit_btn, #result, #error_001{
  display: block;
  margin: auto;
  padding: 5px;
  text-align: center;
}
#result{
  width: 500px;
}
.spacer {
  padding:5px;
}
```
JS
```javascript
document.querySelector("#link_box_submit_btn").addEventListener("click",
  function (event) {
    const url = document.getElementById("link_box").value;
    console.log(url);
    document.getElementById("error_001").innerText = url;
    fetch(url, {
      method: "GET",
      mode: "cors",
      headers: {
        "Content-Type": "application/json"
      }
    })
      .then((response) => response.json())
      .then((data) => $("#result").text(JSON.stringify(data)))
      .catch((error) => console.log("Error:",error));
    event.preventDefault();
  },
  false
);
```