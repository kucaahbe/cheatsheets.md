varargs:

```c
#include <stdarg.h>

void log_error (const char * msg, ...) {
        va_list valist;

        va_start(valist, msg);

        fprintf(stderr, "ERROR: ");
        vfprintf(stderr, msg, valist);
        fprintf(stderr, "\n");

        va_end(valist);
}
```

lookup library symbol list:

```sh-session
nm /usr/local/lib/liblua.5.3.dylib
```


## Linker

`otool -L executable` - macOS
`ldd executable` - Linux

```sh-session
LD_LIBRARY_PATH # linux
DYLD_LIBRARY_PATH # macos
```

## debugger

[GDB to LLDB command map](https://lldb.llvm.org/use/map.html)