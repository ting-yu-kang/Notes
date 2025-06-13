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