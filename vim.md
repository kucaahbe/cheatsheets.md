---
tags:
  - tools
---
### Search/replace

substitute list: [`:h \s/\&`](https://vimhelp.org/change.txt.html#s%2F%5CL)

example | description
---     | ---
`:%s/\(SMTH\)/\L\1/g` | search and replace `SMTH` with `smth`

### Buffers

command | description
---     | ---
`:ls`     | list buffers
`:bu 5`<br>`:buffer 1` | open buffer by number
`:bd 4`<br>`:bdelete f1.txt` | remove buffer  (by name or number)

### Netrw (built-in file explorer)

hotkeys: [`:h netrw-quickmap`](https://vimhelp.org/pi_netrw.txt.html#netrw-quickmap)

hotkey | action
---    | ---
`-` | go up one directory
`gn` | make current directory top of the tree
`cd` | make opened directory (under cursor) current directory
`ctrl+l` | refresh netrw
`gh` | hide/show hidden .files

### Regexp
https://vimregex.com/#alternations
. any character except new line
\s whitespace character
\S non-whitespace character
\d digit
\D non-digit
\x hex digit
\X non-hex digit
\o octal digit
\O non-octal digit
\h head of word character (a,b,c...z,A,B,C...Z and _)
\H non-head of word character
\p printable character
\P like \p, but excluding digits
\w word character
\W non-word character
\a alphabetic character
\A non-alphabetic character
\l lowercase character
\L non-lowercase character
\u uppercase character
\U non-uppercase character
