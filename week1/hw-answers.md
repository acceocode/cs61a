### Week 1 Homework

1. Since the new-if is a normal procedure, it will first try to evalutate all its formal paramters. This means that it will evalute (sqrt-iter (improve guess x) x) which results in infinite recursion of calling the sqrt-iter function. 

<br>

2.
```scheme
(define squares '(2 3 4 5)
  )
```