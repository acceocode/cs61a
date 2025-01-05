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