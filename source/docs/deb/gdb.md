# GNU debugger (Linux)

[The GNU Debugger](https://www.gnu.org/software/gdb/) is a free debugger. Useful for vulnerability research, reverse engineering, and exploit development. For example, it can be used to change a value sent from an authentication function to the rest of the application, which could bypass authentication.

It was originally developed for Linux and a couple of other operating systems. It is capable of debugging not only low-level languages but also used for debugging high-level languages such as C, C++, and Java. GDB can also be used in Windows. GDB uses a commandline interface, but there are existing GUI programs that use GDB for a more informative look.

## Usage examples

Compile with `gdb` symbola:

    $ gcc file.c -ggdb -o binary_debug

Load:

    (gdb) ./binary_debug

List source file (around main):

    (gdb) list

List source file from the top:

    (gdb) list 1

Information gathering:

```text
(gdb) info sources
(gdb) info functions
(gdb) info variables
(gdb) info scope [function_name]
(gdb) info files
```

Getting the symbols:

    $ objcopy --only-keep-debug binary_debug debug_symbols

Stripping for production:

    $ strip --strip-debug --strip-unneeded binary_debug

Adding the symbols in the binary itself:

    $ objcopy --add-gnu-debuglink=debug_symbols binary

Load the `symbol_file_name` within gdb:

    (gdb) symbol-file debug_symbols

