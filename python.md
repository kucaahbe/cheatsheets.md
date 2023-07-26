# Python

## Language

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

lalala

### branching

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

### docstrings

### comments

### regexp

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
python -m pip uninstall <package>
```

### manage dependencies

```bash
python -m pip install -r requirements.txt
```

```bash
python -m pip freeze > requirements.txt
```

## Version management

https://docs.python.org/3/library/venv.html

### venv

```bash
python3 -m venv path/to/dir
```
