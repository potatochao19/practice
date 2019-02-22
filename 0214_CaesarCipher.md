## Caesar Cipher
https://en.wikipedia.org/wiki/Caesar_cipher

Ask user for text and number of places to shift by, and return encrypted message.

- Dictionary methods

### Steps
- Create alphabet dictionary
- For letter in text, find key-value, and return new letter
- If value > 26, loop back around 

```
import string

d = list(string.ascii_lowercase)

t = input("What text message to encode? ")
text = t.lower()
newstr = ""
s = ""

while not s.isdigit():
    s = input("How many letters to shift by? Enter number: ")

shift = int(s)

for x in list(text):
    if x in (" ","?",",",":", ";","&","!"):
        newstr += x
    else:
        i = d.index(x) + shift
        if i < 26:
            newstr += d[i]
        else:
            i %= 26
            newstr += d[i]

print(newstr)

```

Used silly dictionary and reverse dictionary in v1. 
```
d1 = dict(zip(string.ascii_lowercase, range(1,27)))
d2 = dict([[v,k] for k,v in d1.items()])
```


