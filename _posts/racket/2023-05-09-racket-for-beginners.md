---
layout: post
title: "Racket for Beginners"
published: yes
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

        ```scheme  
        > pi  
        3.141592653589793  
        ```  

### List

### Define, assign, variables

There is the difference between `define` and `set!` in racket. We will go over the below code first, and then examine the difference.
```scheme
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
```scheme
> (define x 122)
> x
122
> (set! x 124455)
> x
124455
> (set! y 123)
set!: assignment disallowed;
 cannot set variable before its definition
  variable: y
  in module: top-level
 [,bt for context]
> 
```
However, you will see error because variable y is not defined before. Its memory is not located.

```scheme
> (< 1 3) ; one less than three?
#t
> (> 1 3) ; one greater than three?
#f
```




### Function
#### Lambda function
hello, i'm lamda function, i don't need a name for each func to keep it simple.

```scheme
> (lambda (x) (+ 2 x) 5)
#<procedure>
> ((lambda (x) (+ 2 x)) 5)
7
> [(lambda (x) (+ 2 x)) 5]
7
```

#### Higher-Order functions
1. `map` function: basically, use a list as an input for a lambda function
    ```scheme
    > (map (lambda (x) (+ 2 x)) '(1 5 4 8))
    '(3 7 6 10)
    ```
    This is an example in python
    ```python
    >>> list(map(lambda x: x + 2, [1,5,4,8]))
    [3, 7, 6, 10]
    ```
2. `apply` function: apply a <operation, or something else> to a list '(1 2 2 3)
    ```scheme
    > (apply + '(5 5 5 5))
    20
    ```


### 


## References
1. [Racket in CS60 (youtube)](https://www.youtube.com/playlist?list=PLHqz-wcqDQIEThNEXViEb1iFh9vbOtUD_)
2. 