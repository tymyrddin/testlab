# Cowrie

The Cowrie honeypot can work both as an SSH proxy or as a simulated shell. The emulated shell is pretty convincing and could catch an unprepared adversary off guard. Most of the commands work like how you'd expect, and the contents of the file system match what would be present on an empty Ubuntu 18.04 installation. 

## Attacks against SSH

By default, Cowrie will only expose SSH. This means adversaries will only be able to compromise the honeypot by attacking the SSH service. The attack surface presented by a typical SSH installation is limited so most attacks against the service will take the form of brute-force attacks. Defending against these attacks is relatively simple in most cases as they can be defeated by only allowing public-key authentication or by using strong passwords. These attacks should not be completely ignored, as there are simply so many of them that you are pretty much guaranteed to be attacked at some point.

Arguably the most common tool for brute-forcing SSH is Hydra, and commonly fail2ban is used to mitigate SSH brute-force attacks.

## Bot intrusions

The majority of attacks against typical SSH deployments are automated in some way. As a result, most of the post-exploitation activity that takes place after a bot gains initial access to the honeypot will follow a broad pattern. Most bots will perform a combination of the following:

* Perform some reconnaissance using the `uname` or `nproc` commands or by reading the contents of files like 
`/etc/issue` and `/proc/cpuinfo`. It is possible to change the contents of all these files so the honeypot can pretend 
to be a server or even an IoT toaster.
* Install malicious software by piping a remote shell script into bash. Often this is done using `wget` or `curl`. 
On occasion `FTP` is used. Cowrie will download each unique occurrence of a file but prevent the scripts from 
being executed. Most of the scripts tend to reference cryptocurrency mining in some way.
* A more limited number of bots will do some anti-forensics tasks by deleting various logs and disabling bash history. 
This does not affect Cowrie since all the actions are logged externally.

Bots are not limited to these actions in any way and there is still some variation in the methods and goals of bots.

It is possible to use the data recorded by Cowrie to identify individual bots. The factors that can identify traffic from individual botnets are not always the same. However, some artifacts tend to be consistent across bots including the IP addresses requested by bots and the specific order of commands. Identifiable messages may also be present in scripts or commands though this is uncommon. Some bots may also use highly identifiable public SSH keys to maintain persistence.

It is also possible to identify bots from the scripts that are downloaded by the honeypot, using the same methods that would be used to identify other malware samples.

## SSH tunnelling

Some bots will not perform any actions directly against honeypot and instead will leverage a compromised SSH deployment itself. This is done with the use of SSH tunnels. SSH tunnels forward network traffic between nodes via an encrypted tunnel. SSH tunnels can add a layer of secrecy when attacking other targets as third parties are unable to see the contents of packets that are forwarded through the tunnel. Forwarding via SSH tunnels also allows an adversary to hide their true public IP in much the same way a VPN would.

The IP obfuscation can then be used to facilitate schemes that require the use of multiple different public IP addresses like SEO boosting and spamming. SSH tunnelling may also be used to by-parse IP-based rate limiting tools like Fail2Ban as an adversary is able to transfer to a different IP once they have been blocked.

By default, Cowrie will record all SSH tunnelling requests received by the honeypot, but will not forward them on to their destination. This data is of particular importance as it allows for the monitoring and discovery of web attacks that may not have been found by another honeypot. 

## Detection

There are ways to identify this type of Cowrie deployment. For example, it's not possible to execute bash scripts as 
this is a limitation of low and medium interaction honeypots. And when creating a file and then logging back in it
does not exist. It is also possible to identify the default installation as it will mirror a Debian 5 Installation 
and features a user account named Phil. The default file system also references an outdated CPU.

    Intel(R) Core(TM) i9-11900KB CPU @ 3.30GHz

## Cowrie Event Logging

Cowrie uses an extensive logging system that tracks every connection and command handled by the system. It can log 
to a variety of different local formats and log parsing suites. When logging in to the real `ssh` port the logs can
be found in, for example:

    /home/cowrie/honeypot/var/log/cowrie

## Log Aggregation

The amount of data collected by honeypots, especially external deployments can quickly exceed the point where it is 
no longer practical to parse manually. It is often worth deploying Honeypots alongside a logging platform like the [ELK stack](../siem/elk-stack). 

Other SIEM platforms like [Splunk](../siem/splunk) can provide live monitoring capabilities and alerts. This can be particularly beneficial when deploying honeypots with the intent to respond to attacks rather than to collect data.

## Resources

* [cowrie/cowrie](https://github.com/cowrie/cowrie)
* [How to send Cowrie output to an ELK stack](https://cowrie.readthedocs.io/en/latest/elk/README.html)
