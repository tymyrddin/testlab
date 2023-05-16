# Using Windows Subsystem for Linux with Visual Studio Code

But you might as well develop on a true Linux box.

1. [Enable Developer Mode](https://learn.microsoft.com/en-us/windows/apps/get-started/enable-your-device-for-development)
2. Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting "Run as administrator".
3. Get list of available distros:

```text
PS C:\Windows\system32> wsl --list --online
The following is a list of valid distributions that can be installed.
Install using 'wsl --install -d <Distro>'.

NAME                                   FRIENDLY NAME
Ubuntu                                 Ubuntu
Debian                                 Debian GNU/Linux
kali-linux                             Kali Linux Rolling
Ubuntu-18.04                           Ubuntu 18.04 LTS
Ubuntu-20.04                           Ubuntu 20.04 LTS
Ubuntu-22.04                           Ubuntu 22.04 LTS
OracleLinux_8_5                        Oracle Linux 8.5
OracleLinux_7_9                        Oracle Linux 7.9
SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
openSUSE-Leap-15.4                     openSUSE Leap 15.4
openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

4. Install distro of choice (I chose Debian):

```text
PS C:\Windows\system32> wsl --install -d Debian
```

5. Launching for the first time, Windows Bash will prompt for a username and password.
6. Do installs, for example:

```text
sudo apt-get install wget ca-certificates
```

and:

```text
sudo apt-get install build-essential gdb
```

7. [Get started using Visual Studio Code with Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode)
