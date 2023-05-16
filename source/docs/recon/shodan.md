# Passive DNS recon with Shodan

Use [Shodan](https://www.shodan.io/) to get a list of the target's publicly available servers and devices with their 
IP addresses, the services running on them, and the ports that are open.

Shodan gathers information about all devices directly connected to the Internet. If a device is directly hooked up to 
the Internet then Shodan queries it for various publicly-available information. That information can be queried, so 
there is no scanning of the target directly.

* Go to `www.shodan.io`, register if you have not already.
* Use the Search box to search for the target.
* Scroll through the results.
* Choose the Maps tab to see the physical locations of those systems.
* Choose one of the red dots representing one of the systems to see the IP address and ports open on that system.
* Click the View Details button to view more information about that system.
* Investigate all systems on the map belonging to the target.

## Shodan online

The basic search filters:

    city: find devices in a particular city
    country: find devices in a particular country
    geo: you can pass it coordinates
    hostname: find values that match the hostname
    net: search based on an IP or /x CIDR
    os: search based on operating system
    port: find particular ports that are open

Apache servers in Paris:

    apache city:"Paris"

Nginx servers in France:

    nginx country:"FR"

Cisco devices on a particular subnet:

    cisco net:"xxx.xxx.xxx.0/24"

Cleartext Wi-Fi passwords:

    html:"def_wirelesspassword"

Surveillance cameras with username: admin and password: password

    NETSurveillance uc-httpd

Citrix Gateways:

    title:"citrix gateway"

Info about mongo DB servers:

    "MongoDB Server Information" port:27017 -authentication

FTP servers allowing fully anonymous access:

    "220" "230 Login successful." port:21

Android root bridges with port 5555.

    "Android Debug Bridge" "Device" port:5555

## Shodan CLI

The shodan command-line interface (CLI) is a command-line library for Shodan search engine. 

Install with pip:

    pip install shodan

Get the private API key from your shodan account settings:

    shodan init PRIVATE_API_KEY

List with help

    shodan

```text
Usage: shodan [OPTIONS] COMMAND [ARGS]...

Options:
  -h, --help  Show this message and exit.

Commands:
  alert       Manage the network alerts for your account
  convert     Convert the given input data file into a different format.
  count       Returns the number of results for a search
  data        Bulk data access to Shodan
  domain      View all available information for a domain
  download    Download search results and save them in a compressed JSON...
  honeyscore  Check whether the IP is a honeypot or not.
  host        View all available information for an IP address
  info        Shows general information about your account
  init        Initialize the Shodan command-line
  myip        Print your external IP address
  org         Manage your organization's access to Shodan
  parse       Extract information out of compressed JSON files.
  radar       Real-Time Map of some results as Shodan finds them.
  scan        Scan an IP/ netblock using Shodan.
  search      Search the Shodan database
  stats       Provide summary information about a search query
  stream      Stream data in real-time.
  version     Print version of this tool.
```

Public internet-facing ip address:

    shodan myip

Get information on location, ports, owner of an IP.

    shodan host xxx.xxx.xxx.xxx
