---
layout: post
title: "Racket for Beginners"
published: no
categories: racket
comments: false
author: "Son Pham"
meta: easy to understand racket tutorial for beginner
description: "easy to understand racket tutorial for beginner"
tags: [racket]
---

* Placeholder for Table of Content (Must not be removed)
{:toc}

## Placeholder for mindmap

## Basic Stuff
### Atomic data
- number
    - ex: 123  
- string
    - ex: "hello world"  
- identifiers
    - ex: pi  

        ```racket  
        > pi  
        3.141592653589793  
        ```  

### List

### Define, assign, variables

There is the difference between `define` and `set!` in racket. We will go over the below code first, and then examine the difference.
```racket
;; similar to int a = 123;
(define a 123)

;; bind variable to value
(define-values (x y z) (values 1 2 3))
> (define-values (x y z) (values 1 2 3))
> x
1
> y
2
> z
3

;; Now, we can change value of x by using define again
(define x 123)
> x
123
```

Another way to assign value to a variable is to use `set!` 
```racket
(set! )
```

```racket
> (< 1 3) ; one less than three?
#t
> (> 1 3) ; one greater than three?
#f
```

do

let




###

### 


## References
1. [Racket in CS60 (youtube)](https://www.youtube.com/playlist?list=PLHqz-wcqDQIEThNEXViEb1iFh9vbOtUD_)