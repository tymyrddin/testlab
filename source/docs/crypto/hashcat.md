# Hashcat

[Hashcat](https://hashcat.net/hashcat/) is a GPU-based cracking engine designed for brute-force and dictionary attacks using rules and filters. It is designed to target password hashes and is considered to be the fastest method for password cracking. Useful with a hash that does not pass, or when auditing password strength based on a collection of hashes. It comes pre-installed in Kali and Parrot OS. 

In addition to Hashcat, also download a wordlist like the [10-million-password-list-top-100.txt](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/10-million-password-list-top-100.txt) or [rockyou.txt](https://github.com/teamstealthsec/wordlists/blob/master/rockyou.txt.gz). It contains a list of commonly used passwords and is popular among pen testers. You can find the Rockyou wordlist under `/usr/share/wordlists` in Kali Linux.

And the [mode](https://hashcat.net/wiki/doku.php?id=hashcat#options) (`-m`) for the type of hash.

For example, the hash mode value for SHA1 is `100`, and for doing a dictionary attack (`-a 0`):

    $ hashcat -m 100 -a 0 sha1.txt /usr/share/wordlists/rockyou.txt