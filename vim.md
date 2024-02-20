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

