## Use Luhn's Algorithm to check multiple results
- CSV Module
- Import
- Lists

2/12
#### From yesterday:
- Read in a CSV of valid and invalid test credit card numbers and evaluate numbers
- Produce number of cases where expected results are achieved
- If success rate < 100%, print out numbers that are unsuccessful and debug

My csv has 30 lines (not including headers) and looks like:  

| cc_type  | cc_number | is_valid |
| ---- | --- | ----|
| American Express  | 378282246310005  | TRUE  |
| MasterCard  | 5555555555554444  | TRUE  |
| Fake card  | 18297058137286780  | FALSE  |

Evaluate credit card numbers:
```
from creditcard import func1,func2,luhn

import csv
with open("creditcardnum.csv", "r") as csv_file:
    csv_reader = csv.DictReader(csv_file)
    for line in csv_reader:
        ccn = int(line['cc_number'])
        luhn(ccn)
```
From a quick glance, I received several unexpected results. I want to return how many there were and the results causing the problem.
First step is to compare my results with csv is_valid.

2/13
#### Steps
1. Store results in list
2. Compare expected and given results
3. Return count of good results
4. If test is successful, +1 to counter. Else return cc_number

Note: Changed previous function to return True/False instead of printing Valid/ Invalid:
```def luhn(n):
    finalsum = func1(n) + func2(n)
    if finalsum % 10 == 0:
        return True
    else:
        return False
```

Final code prints out cc_numbers and number of items checked:

```
import csv

def str_to_bool(s):
    if s == 'TRUE':
        return True
    elif s == 'FALSE':
        return False
    else:
        raise ValueError

num_good = 0
total = 0
from creditcard import func1,func2, luhn
with open("creditcardnum.csv", "r") as csv_file:
    csv_reader = csv.DictReader(csv_file)
    for line in csv_reader:
        list = []
        ccn = int(line['cc_number'])
        exp = str_to_bool(line['is_valid'])
        list.append(ccn)
        list.append(exp)
        list.append(luhn(ccn))
        if list[1] == list[2]:
            num_good += 1
            total +=1
        else:
            total +=1
            print(list[0])
print("{0} out of {1} passed.".format(num_good,total))
```
        
