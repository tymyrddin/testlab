# Tools for DNS zone transfers

👉 If zone transfers are not refused, make sure to document that immediately in the report.

DNS zone transfer is a method of copying DNS-related databases across different DNS servers, a type of DNS transaction. 
A vulnerability in DNS configuration led to the release of sensitive data by responding to global Asynchronous 
Transfer Full Range (AXFR) requests. 

This could reveal new subdomains which increase the attack surface of the target. Because a zone transfer lists all 
hostnames in the domain, giving a list of potential targets. If a particular network address in a subnet does not 
exist in a domain transfer, then there is no need to scan or attempt to compromise the missing host.

## dig

`dig` stands for domain information groper and is a DNS lookup utility, commonly used for troubleshooting DNS problems. 
It can also be used to test zone transfer:

    # dig +short ns <domain>
    # dig axfr <domain> @<ns.domain>

## fierce

`fierce` is a Perl script, commonly used for recon. It comes pre-installed on Kali Linux and can be used to test 
zone transfer:

    # fierce -dns <domain>

## host

The `host` command is a DNS lookup tool which converts names to IP addresses and vice versa. It has a 
one-liner to test zone transfer:

    # host -t axfr <domain> <ns.domain>

To try a zone transfer for a domain from the primary name server ns.domain:

    # host -l <domain> <ns.domain>

## nslookup

The `nslookup` command can be used in two modes: interactive and non-interactive. To initiate the `nslookup` 
interactive mode, type the command name only:

    nslookup

The prompt that appears lets one issue multiple server queries. For a zone transfer:

    > server <ns-domain>
    > set type=any
    > ls -d <domain>

## dnsrecon

The `dnsrecon` script comes preinstalled on Kali Linux, and can check ns records for a zone transfer:

    # dnsrecon -d <domain> -t axfr

## Mitigations

The most direct method to mitigate risks from zone transfers is to disable this functionality. Although many companies 
disable zone transfers, a surprisingly large number of DNS servers provide this functionality. If zone transfers are 
required for populating secondary or caching servers, then it should be configured as a push from the primary DNS 
server rather than a pull request initiated by a secondary.

Other technologies, such as DNSSEC, per RFC4033, 4034, and 4035, define methods for cryptographically authenticating 
zone information. DNSSEC can also authenticate secondary and caching servers that are permitted to conduct zone 
transfers.