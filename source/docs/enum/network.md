# Network scanning

## nmap

[nmap](https://nmap.org/) is not only the best port-scanning tool out there, but also a very good service-level enumeration tool with support for customized scripts and hundreds of publicly available scripts ready to use out of the box. This is possible through the Nmap Scripting Engine (NSE), Nmap’s most powerful feature that gives its users the ability to write their own scripts and use Nmap for more than just port scanning.

Nmap’s pre-installed scripts can be found at `/usr/share/nmap/scripts`. Script names are assigned prefixes according to which service they are meant for - making it easier to search for service-specific scripts.

Examples:

Try to enumerate users, or list the users:

    nmap --script smb-enum-users.nse [ip_or_hostname]

Try to enumerate the groups on a system:

    nmap --script smb-enum-groups.nse [ip_or_hostname]

Network shares (download script first):

    nmap --script smb-enum-shares.nse [ip_or_hostname]

URLs/Web pages:

    nmap --script http-enum.nse [ip_or_hostname]

Services:

    nmap --script smb-enum-services.nse [ip_or_hostname]

## zenmap

Zenmap is the official Nmap Security Scanner GUI. It is a multi-platform (Linux, Windows, Mac OS X, BSD, etc.) free and open source application which aims to make Nmap easy for beginners to use while providing advanced features for experienced Nmap users. Frequently used scans can be saved as profiles to make them easy to run repeatedly. A command creator allows interactive creation of Nmap command lines. Scan results can be saved and viewed later. Saved scan results can be compared with one another to see how they differ. The results of recent scans are stored in a searchable database.

You can download Zenmap (often packaged with Nmap itself) from the [Nmap download page](https://nmap.org/download). Zenmap is quite intuitive, but you can learn more about using it from the [Zenmap User's Guide](https://nmap.org/book/zenmap.html) or check out the [Zenmap man page](https://nmap.org/zenmap/man.html) for some quick reference information. 