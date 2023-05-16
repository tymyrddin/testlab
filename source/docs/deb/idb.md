# Immunity Debugger (Windows)

[Immunity Debugger](https://www.immunityinc.com/products/debugger/) is useful for exploit development, malware analysis, and reverse engineering. It can graphically render functions and program flows, facilitates heap analysis, and implements a Python API for scriptability. The Mona Python plugin, for example, supports figuring out offsets for buffer overflows, identifying ROP chains, and exploring more.

## Installation

Installing [Immunity Debugger](https://www.immunityinc.com/products/debugger/) requires the 32bit MSI installer for Python 2.7.18.

To make Immunity Debugger work on Windows 10 modify (and ADD if necessary) the following environment variables(assuming Python is installed at C:\Python27):

    PATH="C:\python27;%PATH%"
    PYTHONHOME="C:\python27"
    PYTHONPATH="C:\Python27\DLLs;C:\Python27\Lib;C:\Python27\Lib\site-packages"

## Mona

For using `mona`, copy the [mona.py file](https://github.com/Jtw0/Immunity-Debugger-Scripts) into the PyCommands folder in the Immunity install.

## Configuration

To configure mona (bottom of mona):

    !mona config -set workingfolder c:\mona\%p

In Immunity, go to `Options -> Preferences -> Events`, and un-tick everything under `Break on`. Now a program will only break when crashing on an overflow.
