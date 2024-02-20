---
tags:
  - languages
---
# D
## Language
### CLI handling
```d
#!/usr/bin/env rdmd
import std.stdio;

int main(string[] args)
{
	writeln(":");

	return 0;
}

```

string concatenation
```d
"asdasd" ~ "ASdasd"
```

## Dub (package manager & build tool)
run package command: `dub run ddox`

### generate documentation
`dub build -b docs` or `dub build -b ddox`
### examples (how to use libraries, c sources etc.)
https://github.com/dlang/dub/tree/master/examples
https://timurgafarov.medium.com/dub-tricks-d16f02c6ea81

## Projects (worth browsing sources)
Check these code for examples and best practices:

| Link | Description |
| ---- | ---- |
| [HipremeEngine](https://github.com/MrcSnm/HipremeEngine) | game engine |
| [phobos](https://github.com/dlang/phobos) | D lang standard library |
| [libmir](https://github.com/libmir) | some library |
