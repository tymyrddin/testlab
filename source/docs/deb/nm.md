# GNU nm

The basic usage of this command is very straightforward - all you have to do is to run the `nm` command and pass the name of the object file as input to it. For example, to use the `nm` command with the binary file named `binary`:

    nm binary

The three columns produced in output represent the symbol value (virtual address), symbol type, and symbol name, respectively. There are several types of symbols - to know the complete details, see the [nm man page](https://www.commandlinux.com/man-page/man1/nm.1.html).

Of interest are:

```text
nm ./binary_debug | grep ' B '
nm -a ./binary_debug | grep ' D '
nm -A ./binary_debug | grep function_name
nm -n ./binary_debug (sorted order by symbol value)
nm -g ./binary_debug (external)
nm -S ./binary_debug (display size in second column)
```
