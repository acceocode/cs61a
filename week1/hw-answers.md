### Week 1 Homework

1. Since the new-if is a normal procedure, it will first try to evalutate all its formal paramters. This means that it will evalute (sqrt-iter (improve guess x) x) which results in infinite recursion of calling the sqrt-iter function. 

<br>

2.
```scheme
(define (squares numbers)
    (if (null? numbers) 
        numbers
        (cons (square (car numbers)) (squares (cdr numbers)))))
    
(define (square x)
    (* x x))

(display (squares '(2 3 4 5))) 
```

<br>

3.
```scheme
(define (switch sentence)
    (define (recurse sentence first?)
        (if (null? sentence) 
            sentence
            (cons (convert (car sentence) first?) (recurse (cdr sentence) #f))))
    (define (convert word first?)
        (let ((word-str (symbol->string word)))
             (cond ((string-ci=? word-str "me") 'you)
                  ((string-ci=? word-str "i") 'you)
                ((and (string-ci=? word-str "you") first?) 'i)
                ((string-ci=? word-str "you") 'me)
                (else word-str))))
    (recurse sentence #t))

(display (switch '(You told me that I should wake you up))) 
(newline)
(display '(i told you that you should wake me up))
```

<br>

4. Write a predicate ordered? that takes a sentence of numbers as its argument and 
   returns a true value if the numbers are in ascending order, or a false value otherwise.
```scheme
(define (ordered? numbers)
    (cond ((null? numbers) #t)
          ((null? (cdr numbers)) #t)
          ((<= (car numbers) (car (cdr numbers))) (ordered? (cdr numbers)))
          (else #f)))
      

(display (ordered? '(1 2 3)))
(newline)
(display (ordered? '(1 2 2 3 4 5)))
(newline)
(display (ordered? '(1)))
(newline)
(display (ordered? '(1 1)))
(newline)
(display (ordered? '()))
(newline)
(display (ordered? '(1 3)))
(newline)
(display (ordered? '(1 3 2)))
(newline)
(display (ordered? '(1 2 3 4 1)))
```