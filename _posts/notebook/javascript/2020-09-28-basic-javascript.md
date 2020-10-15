---
layout: post
title: "Basic Javascript"
categories: en notebook javascript
author: "Son Pham"
---


### Edit a text   

```javascript
$("<selector><put your class, id or type here>").html("<what do you want to change>");
<selector>:
"." : for class
empty: for type
"#": for id
```

### Target parent elements:  

```javascript
div id="mom-dad"
    div id="son"
$("#son").parent().css("background-color", "blue")
```

### Target children elements:  

```javascript
$("#left-well").children().css("color", "blue")
```

### submit to another page  

```javascript
$("#myform").attr('action', 'page1.php');
```

ref:
1 https://stackoverflow.com/questions/5451600/jquery-to-change-form-action
2 https://stackoverflow.com/questions/15308017/save-data-through-ajax-jquery-post-with-form-submit
### add new item $().append

### if else in jquery

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

### next sibling

### change display of an element
```javascript
document.getElementbyId(<ID>).style.display='none'; // or inherit
```

```
<option selected disable value="">  </option>
```


