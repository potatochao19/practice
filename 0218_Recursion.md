## Intro to Recursion 

- Replace while loops
- Build using base case, recursive case

#### Factorials

While loop:
```
def factorial_loop(n):
    num = 1
    while n >= 1:
        num = num * n
        n -= 1
    return num
 ```
 
Recursion:
 ```
 def factorial_rec(n):
    if n == 1:
        return 1
    else:
        n *= factorial_rec(n-1)
        return n
 ```
 #### Collatz Conjecture
 - if n is even, n /= 2
 - if n is odd,  n = n * 3 + 1
 - return number of steps it takes to reduce n to 1
 
 While loop:
 ```
 def collatz(n):
    steps = 0
    while n > 1:
        if n % 2 == 0:
            n /= 2
            steps += 1
        else:
            n = n * 3 + 1
            steps += 1
    return steps
   ```
   
   Recursion:
   ```
   def collatz(n):
 
    if n == 1:
        # base case, where recursion stops
        return 0
    elif n % 2 == 0:
        # recursive case for even num
        return 1 + collatz(n/2)
    else:
        # recursive case for odd num
        return 1 + collatz(3*n+1)
   ```
 
