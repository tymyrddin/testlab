# Listing subdomains

The quickest ways to gather a lot of subdomains is search in external sources.

## Amass

    amass enum [-active] [-ip] -d <target domain>
    amass enum -d <target domain> | grep <target domain> # To just list subdomains

## Subfinder

Use `-silent` to only have subdomains in the output:

    ./subfinder-linux-amd64 -d <target domain> [-silent]

## Findomain

Use `--quiet` to only have subdomains in the output:

    ./findomain-linux -t <target domain> [--quiet]

## OneForAll

    python3 oneforall.py --target <target domain> [--dns False] [--req False] [--brute False] run

## assetfinder

    assetfinder --subs-only <target domain>

## Sudomy

Create a sudomy.api file with API keys first:

    sudomy -d <target domain>

## vita

    vita -d <target domain>

## theHarvester

    theHarvester -d <target domain> -b "anubis, baidu, bing, binaryedge, bingapi, bufferoverun, censys, certspotter, crtsh, dnsdumpster, duckduckgo, fullhunt, github-code, google, hackertarget, hunter, intelx, linkedin, linkedin_links, n45ht, omnisint, otx, pentesttools, projectdiscovery, qwant, rapiddns, rocketreach, securityTrails, spyse, sublist3r, threatcrowd, threatminer, trello, twitter, urlscan, virustotal, yahoo, zoomeye"

There are other interesting tools/APIs that even if not directly specialised in finding subdomains could be useful 
to find subdomains, like:

## Crobat

Get list of subdomains in output from the API. This is the API the crobat tool will use.

Sonar omnisint:

    curl https://sonar.omnisint.io/subdomains/<target domain> | jq -r ".[]"

JLDC free API:

    curl https://jldc.me/anubis/subdomains/<target domain> | jq -r ".[]"

RapidDNS free API:

    # Get Domains from rapiddns free API
    
    rapiddns(){
     curl -s "https://rapiddns.io/subdomain/$1?full=1" \
      | grep -oE "[\.a-zA-Z0-9-]+\.$1" \
      | sort -u
    }
    rapiddns <target domain>

From https://crt.sh/:

    # Get Domains from crt free API
    
    crt(){
     curl -s "https://crt.sh/?q=%25.$1" \
      | grep -oE "[\.a-zA-Z0-9-]+\.$1" \
      | sort -u
    }
    crt <target domain>

## gau

gau fetches known URLs from AlienVault's Open Threat Exchange, the Wayback Machine, and Common Crawl for any given domain.

    # Get subdomains from GAUs found URLs
    gau --subs <target domain> | cut -d "/" -f 3 | sort -u

## SubDomainizer

SubDomainizer & subscraper scrape the web looking for JS files and extract subdomains from there.

Get only subdomains from SubDomainizer:

    python3 SubDomainizer.py -u https://<target domain> | grep <target domain>

Get only subdomains from subscraper, this already perform recursion over the found results

    python subscraper.py -u <target domain> | grep <target domain> | cut -d " " -f

## Shodan

Get info about the domain

    shodan domain <domain>

Get other pages with links to subdomains

    shodan search "http.html:help.domain.com"

## Censys subdomain finder

    export CENSYS_API_ID=...
    export CENSYS_API_SECRET=...
    python3 censys-subdomain-finder.py <target domain>

## securitytrails.com

securitytrails.com has a free API to search for subdomains and IP history

## chaos.projectdiscovery.io

chaos.projectdiscovery.io offers all the subdomains related to bug-bounty programs. You can access this 
data using chaospy or even access the scope used by 
[chaos-public-program-list](https://github.com/projectdiscovery/chaos-public-program-list)

## Resources

* [amass — Automated Attack Surface Mapping](https://danielmiessler.com/study/amass/)
* [Subdomains cheatsheet](https://pentester.land/cheatsheets/2018/11/14/subdomains-enumeration-cheatsheet.html)
* [Knockpy subdomains](https://github.com/guelfoweb/knock), already installed on Kali
* [Subdomains enumeration via favicon.ico hashing](https://github.com/m4ll0k/BBTz/blob/master/favihash.py)

