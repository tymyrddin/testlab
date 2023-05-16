# Netwide Assembler (NASM) on Linux

The [Netwide Assembler (NASM)](https://www.nasm.us/) is a portable and modular assembler for x86-64 architectures. It makes use of syntax that is easy to read and understand. It also enables support for macros and a wide range of x86 architecture extensions. NASM supports [a wide range of formats](https://www.nasm.us/xdoc/2.09.10/html/nasmdoc7.html). 

It is available for almost every x86-based operating system (including macOS), and also accessible as a **cross-platform assembler** on other platforms. It employs Intel syntax, but differs from others in that it emphasises its own macro language, which allows for constructing more complicated expressions from simpler definitions, allowing new instructions to be created.

## Install nasm

On Kali, [nasm is installed by default](https://www.kali.org/tools/nasm/). To install `nasm` on most other distros (if it is not available):

* Get the latest version of nasm from the [netwide assembler (NASM) website](http://www.nasm.us/).
* Download the Linux source archive `nasm-xxxxxx.tar.gz`, where `xxxxxx` is the nasm version number in the archive. At time of writing, that was `nasm-2.16.01.tar.gz`.
* Unpack the archive.
* `cd` to `nasm-xxxxxx` and type `./configure`. This shell script will find the best C compiler to use and set up Makefiles accordingly.
* Type `make` to build the `nasm` and `ndisasm` binaries.
* Type `make install` to install `nasm` and `ndisasm` in `/usr/local/bin` and to install the man pages.

On CentOS, Fedora, and Red Hat, you can use an RPM distribution and double-click the RPM file.

## Editing, assembling, and running a NASM source file

Set the path of `nasm` and `ld` binaries in your `PATH` environment variable. 

Using any editor or IDE, create a simple `hello.asm`:

```text
section	.text
   global _start     ;must be declared for linker (ld)
	
_start:	            ;tells linker entry point
   mov	edx,len     ;message length
   mov	ecx,msg     ;message to write
   mov	ebx,1       ;file descriptor (stdout)
   mov	eax,4       ;system call number (sys_write)
   int	0x80        ;call kernel
	
   mov	eax,1       ;system call number (sys_exit)
   int	0x80        ;call kernel

section	.data
msg db 'Hello, world!', 0xa  ;string to be printed
len equ $ - msg     ;length of the string
```

To assemble the program:

```text
┌──(kali㉿kali)-[~/Development]
└─$ nasm -f elf hello.asm
                                                            
┌──(kali㉿kali)-[~/Development]
└─$ ls
hello.asm  hello.o
```

If there is any error, you will be prompted about it. Otherwise, an object file of the program named `hello.o` will be created.

To link the object file and create an executable file:

```text
┌──(kali㉿kali)-[~/Development]
└─$ ld -m elf_i386 -s -o hello hello.o

┌──(kali㉿kali)-[~/Development]
└─$ ls                                
hello  hello.asm  hello.o
```

Execute the program:

```text
┌──(kali㉿kali)-[~/Development]
└─$ ./hello                                                   
Hello, world!
```
