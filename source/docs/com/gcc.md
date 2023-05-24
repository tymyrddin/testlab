# GNU compiler (gcc) on Linux

GNU Compiler Collection (GCC) is a GNU project optimizing compiler that supports a wide range of programming languages, hardware architectures, and operating systems. GCC is an important part of the GNU toolchain and the standard compiler for most GNU and Linux kernel projects.

It comes pre-installed in nearly all Linux distributions, and is also available in their repositories. To install it on Debian-based distributions, including Ubuntu and Linux Mint:

    apt install build-essentials

Check with:

    gcc --version

CentOS, Fedora, and Red Hat:

    sudo dnf group install "Development Tools"

To compile and execute 32-bit programs on 64-bit Kali Linux, install `gcc-multilib` (cross-compilING 32-bit binaries):

    sudo apt update && sudo apt install gcc-multilib
