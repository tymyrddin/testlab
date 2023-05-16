# Using whois

WHOIS is a request and response protocol that follows the [RFC 3912](https://www.ietf.org/rfc/rfc3912.txt) 
specification. A WHOIS server listens on TCP port 43 for incoming requests. 

    PORT   STATE  SERVICE
    43/tcp open   whois?

A domain registrar is responsible for maintaining the WHOIS records for the domain names it is leasing. 

* Go to `www.arin.net/whois` and search for `target name` in the ARIN Whois/RDAP Search bar.
* Find a handle which displays more information about this registration including the range of IP addresses.
* Find an entry with a net range (public IPs).
* Determine all the public IP blocks the target may have.

If you cannot find any results try some other Whois database search sites.

## Whois CLI

The cli `whois` command helps in identifying the owner of a target, hosted company, and location of servers, 
IP address, Server type, etc. Give it a target domain name and the WHOIS server provides saved records:

```text
whois <domainname>
```

* Registrar WHOIS server
* Registrar URL
* Record creation date
* Record update date
* Registrant contact info and address (unless withheld for privacy)
* Admin contact info and address (unless withheld for privacy)
* Tech contact info and address (unless withheld for privacy)
* On occasion the database being used also appears in the response

```text
whois thmredteam.com
```

Example:

```text
   Domain Name: THMREDTEAM.COM
   Registry Domain ID: 2643258257_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.namecheap.com
   Registrar URL: http://www.namecheap.com
   Updated Date: 2022-09-26T15:22:32Z
   Creation Date: 2021-09-24T14:04:16Z
   Registry Expiry Date: 2023-09-24T14:04:16Z
   Registrar: NameCheap, Inc.
   Registrar IANA ID: 1068
   Registrar Abuse Contact Email: abuse@namecheap.com
   Registrar Abuse Contact Phone: +1.6613102107
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Name Server: KIP.NS.CLOUDFLARE.COM
   Name Server: UMA.NS.CLOUDFLARE.COM
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of whois database: 2022-10-06T09:13:18Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

NOTICE: [...]

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
Domain name: thmredteam.com
Registry Domain ID: 2643258257_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.namecheap.com
Registrar URL: http://www.namecheap.com
Updated Date: 2022-09-26T15:22:32.57Z
Creation Date: 2021-09-24T14:04:16.00Z
Registrar Registration Expiration Date: 2023-09-24T14:04:16.00Z
Registrar: NAMECHEAP INC
Registrar IANA ID: 1068
Registrar Abuse Contact Email: abuse@namecheap.com
Registrar Abuse Contact Phone: +1.9854014545
Reseller: NAMECHEAP INC
Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
Registry Registrant ID: 
Registrant Name: Redacted for Privacy
Registrant Organization: Privacy service provided by Withheld for Privacy ehf
Registrant Street: Kalkofnsvegur 2 
Registrant City: Reykjavik
Registrant State/Province: Capital Region
Registrant Postal Code: 101
Registrant Country: IS
Registrant Phone: +354.4212434
Registrant Phone Ext: 
Registrant Fax: 
Registrant Fax Ext: 
Registrant Email: e17b7976233e4e72a76b3dadb1d574bd.protect@withheldforprivacy.com
Registry Admin ID: 
Admin Name: Redacted for Privacy
Admin Organization: Privacy service provided by Withheld for Privacy ehf
Admin Street: Kalkofnsvegur 2 
Admin City: Reykjavik
Admin State/Province: Capital Region
Admin Postal Code: 101
Admin Country: IS
Admin Phone: +354.4212434
Admin Phone Ext: 
Admin Fax: 
Admin Fax Ext: 
Admin Email: e17b7976233e4e72a76b3dadb1d574bd.protect@withheldforprivacy.com
Registry Tech ID: 
Tech Name: Redacted for Privacy
Tech Organization: Privacy service provided by Withheld for Privacy ehf
Tech Street: Kalkofnsvegur 2 
Tech City: Reykjavik
Tech State/Province: Capital Region
Tech Postal Code: 101
Tech Country: IS
Tech Phone: +354.4212434
Tech Phone Ext: 
Tech Fax: 
Tech Fax Ext: 
Tech Email: e17b7976233e4e72a76b3dadb1d574bd.protect@withheldforprivacy.com
Name Server: kip.ns.cloudflare.com
Name Server: uma.ns.cloudflare.com
DNSSEC: unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2022-10-05T20:08:51.20Z <<<
For more information on Whois status codes, please visit https://icann.org/epp
```

## Hacking WHOIS for more info

The WHOIS service always needs to use a database to store and extract the information, and a possible SQLInjection 
could be present when querying the database from some information provided by the user. For example, it could be 
possible to extract all the information saved in the database with: 

    whois -h <IP address> -p 43 "a') or 1=1#" 

## Whois history

WHOIS history provides a history of WHOIS data and can come in handy if the domain registrant did not use WHOIS 
privacy when they registered the domain. It takes years and huge databases to collect and maintain that data, so most 
sites offering this service charge a fee. [Whoismind](https://whoismind.com) offers some history and is free, but not working atm.

## Reverse lookup

ViewDNS.info offers Reverse IP Lookup. It is common to come across shared hosting servers. With shared hosting, 
one IP address is shared among different web servers with different domain names. With reverse IP lookup, 
starting from a domain name or an IP address, you can find the other domain names using a specific IP address(es). 
And maybe one of those sites is easy to compromise and gain access to the webserver as a whole.

Using amass:

    amass intel -d <target.com> -whois

## Resources

* [WhoIs LookUp DomainTools](https://whois.domaintools.com/)
* [Robtex](https://www.robtex.com/)
* [DNSDumpster](https://dnsdumpster.com/)
* [ViewDNSInfo](https://viewdns.info/reversewhois/)
* [DomainEye](https://domaineye.com/reverse-whois)
* [Reverse Whois Lookup](https://www.reversewhois.io/)