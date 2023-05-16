# John the Ripper

[John the Ripper (JtR)](https://www.openwall.com/john/) is an offline password cracking tool. For CPU-based cracking, John is one of the fastest tools for password recovery and implements different rule sets than other cracking tools. These rule sets may recover passwords where other cracking tools fail.

While you can use popular wordlists like RockYou, John also has its own set of wordlists with thousands of common passwords. This makes John very effective when cracking systems with weak passwords.

No mode needs to be entered. John recognises the hash type, generates hashes on the fly for all the passwords in the dictionary, and stops when a generated hash matches the current hash.

If you are using Kali Linux, John is pre-installed.

```text
$ john --single --format=raw-sha1 crackthishash.txt
```

`crackthishash.txt` contains username and hash value of the password (separated by a colon).

Dictionary attack:

```text
$ john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-sha1 crackthishash.txt
```
