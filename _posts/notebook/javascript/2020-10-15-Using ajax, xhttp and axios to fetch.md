---
layout: post
title: "Using Ajax, Xhttp, Fetch, and Axios to get page content"
categories: en notebook git
author: "Son Pham"
---



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

