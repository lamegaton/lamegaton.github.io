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

Racket, why racket? I don't know the main reason, but it is interesting and importantly my professor requires it for our Psychology course. I have never learned Racket before but I have a bit of experience in Erlang. In Erlang we cannot assign a value to a variable like Racket because `=` operator is a pattern matching that is similar to `car` and `cdr`. The game is totally changed in Racket. Now we can just `define whatever value` we want. 

* Placeholder for Table of Content (Must not be removed)
{:toc}

## Placeholder for mindmap

## Basic Stuff
### Atomic data
- number: 123  
- string: "hello world"  
- identifiers: pi  
    ```scheme  
    > pi  
    3.141592653589793  
    ```  

### Math operation
```scheme
> (sqrt 4/9)
2/3

```

I was listening to a TED talk on how to build muscle and this is the last line in that video "*meaningful growth requires challenge and stress*"

error: run-pdflatex: could not find a `pdflatex' executable



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

;; you can also bind multiple lists to variables
(define-values (point-a point-b)
  (values (list 122 3123) '(123 222)))
point-a 
point-b 

'(122 3123)
'(123 222)

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
#### Simple function
a function is a funnel that take arguments and map it to its parameters  
```scheme
#lang racket
;;function name: add  
;;arguments: 1 2  
;;parameter: x y 
(define (add x y)(+ x y))
(add 1 3)
> 4
```

#### Helper function 
Personally, I'm intrigued with philosophical idea. Helper function reduce DRY - don't repeat yourself. Oh and talking about philosophy, there is another one but not related. It is [no-hello](https://www.nohello.com/). I found it on my colleague's status and that reminds me that our time are important.

Alright, let's talk about helper function. We use it to first avoid repeating code. Second, to make a useful name. If you want to learn how to write code in calligraphy style you definitely can checkout this [Style Guide](https://docs.racket-lang.org/style/index.html)

```scheme
(define (distance x y)
  (let ((dx (- (car y) (car x)))
        (dy (- (car(cdr y)) (car(cdr x))))) ; (cdr y) will return list
    (sqrt (+ (* dx dx) (* dy dy)))))

; Example:
(distance '(1 2) '(4 6)) ; returns 5
```

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


## References
1. [Racket in CS60 (youtube)](https://www.youtube.com/playlist?list=PLHqz-wcqDQIEThNEXViEb1iFh9vbOtUD_)
2. Racket Programming the Fun Way - James W. Stelly
3. [Beautiful Racket](https://beautifulracket.com/)
4. 