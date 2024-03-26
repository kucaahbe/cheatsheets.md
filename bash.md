---
tags:
  - shells
  - languages
---
# Bash

## Language

### Variables

https://tldp.org/LDP/abs/html/parameter-substitution.html
```bash
a=1 # not a = 1
b=one
```

#### environment variables
```bash
export VAR_1=val_1
unset VAR_1
# to list
env
env VAR_1=123 command # run a "command" with VAR_1 set to 123
env -u VAR_1 command # run a "command" with VAR_1 unset
```
### if/else/case

```bash
# man test
if [[ "a" = "a" ]]; then
  echo "a=a"
fi

if ! grep -q 'smth' file.txt; then
  echo -e "smth" >> file.txt
fi

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
https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html

```bash
s1="my_"
s1+="\nstring"
# -e honors newlines
echo -e $s1

file=sraka.scss
echo ${file/.scss/.css.scss}

for file in $(git ls-files  -- *.scss G -v css.scss); do; git mv $file ${file/.scss/.css.scss}; done
```

### arrays/dictionaries
https://www.cyberciti.biz/faq/bash-for-loop-array/
```bash
array=( one two three )
from_cmd=( $(ls -1 *.lst) )
# or
declare -a ARRAY_NAME_HERE=(value1 value2 valueN)
echo "length: ${#ARRAY_NAME_HERE[@]}"

declare -A ARRAY_NAME_HERE
declare -A fruits
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"

printf "%s\n" "${array[@]}"
printf "%s\n" "${files[@]}"
printf "%s\n" "${limits[@]}"
printf "%s\n" "${fruits[@]}"

for key in "${!fruits[@]}"; do
  echo "Key for fruits array is: $key"
done

for value in "${fruits[@]}"; do
  echo "Value for fruits array is: $value"
done
```

### docstrings
```bash
a=ZZZ
cat << XML > test.file
  HERE-DOCUMENT $a
XML

cat << 'XML' > test.file
  HERE-DOCUMENT $a - no interpolation!
XML

program loadScriptFromString "$(cat << JS
console.log("hello")
JS
)"

if true; then
	cat <<- EOF
	++Line with a leading TAB --> TAB TAB TAB.
	EOF
fi
```

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

## CLI

CLI shortcuts

https://cheatography.com/clyde-stiller/cheat-sheets/bash-command-line-shortcuts/

## Interpreter settings

| option | description |
| --- | --- |
| `set -e` | abort if something went wrong |
| `set -x` (`set -o xtrace`) | print execution statements using PS4 |
| `set -u` | raise an error about undefined variable |

## Misc

split line by delimiter: **cut**
merge lines: **paste**
calculator: **bc**

### Examples

calculate the sum of numbers from file (line with needed numbers looks like this: `# Offense count: 13”):`

```bash
grep 'Offense count' .rubocop_todo.yml | cut -d' ' -f 4 | paste -s -d+ - | bc
# or
grep 'Offense count' .rubocop_todo.yml | awk -F' ' '{s+=$4} END {print s}'
```