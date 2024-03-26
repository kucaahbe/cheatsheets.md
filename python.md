---
tags:
  - shells
  - languages
---
# Python

## Language

### CLI handling
```python
#!/usr/bin/env python3
import sys

COMMIT_SOURCE = sys.argv[2] if len(sys.argv) > 2 else ""

print 'Number of arguments:', len(sys.argv), 'arguments.'
print 'Argument List:', str(sys.argv)

print('Hello world', file=sys.stderr)

s = input('--> ')

if s != 'yes':
  sys.exit(-1)
```

### variables & basic data

```python
integer_number = 1_000 # 1000
binary_number = 0b_0011 # 0B001 == 1
hexadecimal_number = 0xCAFE_F00D # 0XCAFE_F00D
octal_number = 0o10 # 0O10 == 8

single_quoted_string = '1'
double_quoted_string = "1"

_list_or_array = [1,2,3]
_tuple = (1, '2', [3])
```

### operators (+= == etc.)

### branching (conditional)
```python
if True:
  print('do stuff')
elif a > b:
  # elif
else:
  # else

COMMIT_SOURCE = sys.argv[2] if len(sys.argv) > 2 else ""

```

### functions

#### main function

```python
import sys

def main(args):
  print("hello")

if __name__ == '__main__':
  main(sys.argv[1:])
```

### IO

```python
from pathlib import Path
path_to_file = Path('/some/path')
with open(path_to_file, encoding='utf8') as f:
  contents = f.readlines()
```

### strings

```python
len(s) # length
print(f'Hello {name}! This is {program}')
print("%s %s" %('Hello','World',))
print('Hello, {}'.format(name))
```
### lists (arrays)

```python
mylist = ["apple", "banana", "cherry"]
len(mylist)
thislist[1] = "blackcurrant"
thislist[1:2] = ["blackcurrant", "watermelon"]
thislist.insert(2, "watermelon")
thislist.append("orange")
thislist.remove("banana")
```

### dictionaries

### looping

```python
for key, value in {'k1': 'v1'}.items():
     # to exit loop:
     if key==6: break
     # to skip loop iteration:
     if key==5: continue
     print(key, "->", value)```
```


### docstrings

### comments

### regexp
```python
import re

x = re.search("^The.*Spain$", txt)
s.group(1)
```

### debug

```python
import pdb; pdb.set_trace()
# or (since 3.7)
breakpoint()
```

### logging

```python
import logging

logger = logging.getLogger(__name__)

logger.info('hello')
logger.error('fuck')
logger.debug('bla bla')
```
### file system access
### OOP
## Package manager (pip)

### show package

```bash
pip3 show <package_name>
```

### upgrade package

```bash
sudo pip3 install <package_name> --upgrade
```

```bash
python3 -m pip uninstall <package>
```

### manage dependencies

```bash
python3 -m pip install -r requirements.txt
```

```bash
python3 -m pip freeze > requirements.txt
```

### Remove all packages
```sh-session
python3 -m pip freeze | cut -d "@" -f1 | xargs python3 -m pip uninstall -y
```

## Version management

https://docs.python.org/3/library/venv.html

### venv

```bash
python3 -m venv [--system-site-packages] path/to/dir/.venv
```
