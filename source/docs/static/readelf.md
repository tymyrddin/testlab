# readelf (Linux)

To display file headers of a elf file:

    $ readelf -h elf_file

For information about the different sections of the process’ address space:

    $ readelf -S elf_file

To display symbols table:

    $ readelf -s elf_file

Core notes:

    $ readelf -n elf_file

Relocation section:

    $ readelf -r elf_file

Dynamic section:

    $ readelf -d elf_file