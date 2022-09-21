---
layout: post
title: "Using Ajax, Xhttp, Fetch, and Axios to get page content"
categories: javascript
comments: false
author: "Son Pham"
---



## Axios

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