## Luhn's check for credit card validity
- Operators
- Enumerate
- Looping through list

#### Steps:
  - From second to last digit, multiply every other digit by 2
  - Store sum of digits from prior result to sum
  - If digit > 9 then digit = digit - 9 and store to sum
  - Store sum of unused digits to sum (invert previous method used)
  - If sum % 10 = 0 then valid card
  - Finally, create as function and prompt for input

#### Step 1 Brainstorm and Basics
Sum every other number from right to left
(num = _some number_)
```
num_list = [int(d) for d in str(num)]
(sum(num_list[::-2]))
```
Same as above, but starting from second to last number
```
start_index = len(num_list) - 2
(sum(num_list[start_index::-2]))
```
Multiplying items in list and addiing digits of results
```
num_new = []
for i in num_list:
    num_new.append(i * 2)

for n, i in enumerate(num_new):
    if i > 9:
        num_new[n] = i - 9
(sum(num_new))
```
Alternative solution - defining function to sum every other digit right to left:
```
def customSum(n):
    s = 0
    while n:#ask about this while n
        s += n % 10
        n //= 100
    return s
```

## Final code:
```
def func1(n):
    """This function sums every other number from right to left"""
    
    s = 0
    while n:
        s += n % 10
        n //= 100
    return s

def func2(n):
    """This function multiplies every other number from right to left by 2, starting with the second to last digit, then adds together all digits from the result. ie the final "sum" of [10,4,7] is 1+0+4+7"""
    
    num_list = [int(d) for d in str(n)]
    s = 0
    for i in range(len(num_list)-1,0,-2):
        x = num_list[i-1]
        x *= 2
        if x > 9:
            x -= 9
        s += x
    return s

def luhn(n):
    finalsum = func1(n) + func2(n)
    if finalsum % 10 == 0:
        print("Valid Card")
    else:
        print("Invalid")

ccn = int(input("Input credit card number"))
luhn(ccn)
```

## Tomorrow's tasks:
- Read in a CSV of valid and invalid test credit card numbers and evaluate numbers
- Produce number of cases where expected results are achieved
- If success rate < 100%, print out numbers that are unsuccessful and debug
