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

### arrays

### dictionaries

### docstrings

### comments

### regexp

### logging

```python
import logging

logger = logging.getLogger(__name__)

logger.info('hello')
logger.error('fuck')
logger.debug('bla bla')
```

## Package manager (pip)

### upgrade package

```bash
sudo pip3 install <package_name> --upgrade
```

```bash
python -m pip uninstall <package>
```

### manage dependencies

```
python -m pip install -r requirements.txt
```

```
python -m pip freeze > requirements.txt
```

## Version management

https://docs.python.org/3/library/venv.html

### venv

```bash
python3 -m venv path/to/dir
```
