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

### Time
```python
from datetime import datetime

date_str = "2025-09-07 14:30:00"

# 1. Parse string to datetime (specify format)
dt = datetime.strptime(date_str, "%Y-%m-%d %H:%M:%S")

# 2. Convert to timestamp (float, seconds since epoch)
ts = dt.timestamp()

print(ts)
```

### Random
* random.random(): Returns a random floating-point number in the range [0.0, 1.0).
* random.randint(a, b): Returns a random integer N such that a <= N <= b.
* random.randrange(start, stop, step): Returns a randomly selected element from range(start, stop, step). The stop value is not included.
* random.choice(sequence): Returns a random element from a non-empty sequence (e.g., a list or tuple).
* random.shuffle(x): Shuffles the elements of a sequence x in place.
* random.seed(a=None): Initializes the random number generator. If a is omitted or None, the current system time is used. Setting a specific seed allows for reproducible sequences of "random" numbers.

### File
```python
base_dir = os.path.dirname(__file__)  # current dirname
filepath = os.path.join(base_dir, "myfile.txt")

with open("data.txt", "r") as f:
    for line in f:
        line = line.strip()   # remove newline + spaces
        if not line:          # skip empty lines
            continue
        # process the line
        print(line)


with open("output.txt", "w") as f:
    for line in lines:
        f.write(line + "\n")
```

### Dict and Set
#### OrderedDict
```python
from collections import OrderedDict

# Create an OrderedDict
od = OrderedDict()

# Move 'banana' to the end
od.move_to_end('banana')

# Move 'orange' to the beginning
od.move_to_end('orange', last=False)

# Pop the first inserted item
first_key, first_val = od.popitem(last=False)
print(first_key, first_val)  # Output: orange 2

# Pop the last inserted item
last_key, last_val = od.popitem()
print(last_key, last_val)    # Output: banana 3
```

#### SortedDict
```python
from sortedcontainers import SortedDict

# Create a SortedDict
sd = SortedDict()

# Get first and last keys
print(sd.peekitem(0))   # ('apple', 5)
print(sd.peekitem(-1))  # ('cherry', 1)

# Get all keys between 'apple' and 'cherry' (inclusive)
for key in sd.irange('apple', 'cherry'):
    print(key)
```

#### SortedSet
```python
from sortedcontainers import SortedSet

# Create a SortedSet
s = SortedSet()


# Index-based access (like a sorted list)
print(s[0])  # Output: 5
print(s[-1]) # Output: 10

# Get all elements >= 6 and < 11
subset = s.irange(6, 11, inclusive=(True, False))  # inclusive lower, exclusive upper
```