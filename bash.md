# Bash

### variables
https://tldp.org/LDP/abs/html/parameter-substitution.html
a=1 # not a = 1
b=one

### branching

```bash
var=123
case $var in
  123)
    echo 123
    ;;

  PATTERN_N)
    STATEMENTS
    ;;

  *)
    echo whatever
    ;;
esac
```

### functions

```bash
func_name () {
  echo params: $*
  echo param1: $1
  echo from function
}
```

### loops

```bash
for OUTPUT in $(Linux-Or-Unix-Command-Here)
do
    command1 on $OUTPUT
    command2 on $OUTPUT
    commandN
done

for VARIABLE in file1 file2 file3
do
    command1 on $VARIABLE
    command2
    commandN
done
```

### IO

### strings

```bash
file=sraka.scss
echo ${file/.scss/.css.scss}

for file in $(git ls-files  -- *.scss G -v css.scss); do; git mv $file ${file/.scss/.css.scss}; done
```

### arrays
https://www.cyberciti.biz/faq/bash-for-loop-array/

### dictionaries

### docstrings

### comments

### regexp

### redirects

redirect stderr to stdout
```bash
command 2>&1
```
redirect stderr to file
```bash
command 2>file.txt
```
