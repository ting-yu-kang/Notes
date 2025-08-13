# Python Notes

### Strings are immutable:
Use `list(s)` to manipulate and then use `"".join(l)`. Better performance.

### Trim a string
s = s.strip()

### Split a string
`l = s.split()` : treat any amount of white spaces as separator
`l = s.split(" ")`: treat only one space

### Max Number
* Float: `math.inf` (`float('inf')`), `-math.inf`, (`float('-inf')`)
* Integer: `sys.maxsize`, `-sys.maxsize`

### Check character
* isalnum() → True for letters or digits
* isalpha() → True for letters only
* isdigit() → True for digits only

### is not vs !=
* Use != when you want to compare contents (E.g. numbers, strings, lists)
* Use is not when you want to check identity (E.g. is not None, singleton objects)

### characters
* s.isalnum() # alphanumeric
* s.isalpha() # alphabet
* s.islower()
* s.isupper()
* s.isdigit()
* s.lower() # to lowercase
* s.upper() # to uppercase