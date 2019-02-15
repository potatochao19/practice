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
d1 = dict(zip(string.ascii_lowercase, range(1,27)))
d2 = dict([[v,k] for k,v in d1.items()])

t = input("What text message to encode? ")
shift = int(input("How many letters to shift by? Enter number: "))

text = t.lower()
newstr = ""

for x in list(text):
    if x in (" ","?",",",":", ";","&","!"):
        newstr += x
    else:
        i = d1[x] + shift
        if i < 27:
            newstr += d2[i]
        else:
            while i > 26:
                i -= 26
            newstr += d2[i]
print(newstr)
```


