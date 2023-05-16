# Google dorking

Use Google dorking to look for events or articles that give indications of the company's reputation and security posture, to locate login pages, web pages that contain the word "intranet", etc.

Combining advanced Google searches with specific terms, documents containing sensitive information or vulnerable web servers can be found. Websites such as [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database) collect such search terms and are publicly available. Let's take a look at some GHDB queries to see if our client has any confidential information exposed via search engines. GHDB contains queries under the following categories:

Footholds, for example [GHDB-ID: 6364](https://www.exploit-db.com/ghdb/6364) to discover Nginx logs, which might reveal server misconfigurations that can be exploited:

    intitle:"index of" "nginx.log"

Files Containing Usernames, for example [GHDB-ID: 7047](https://www.exploit-db.com/ghdb/7047) to discover files that leak juicy information.

    intitle:"index of" "contacts.txt"

Sensitive Directories, such as [GHDB-ID: 6768](https://www.exploit-db.com/ghdb/6768) to find out if a private RSA key is exposed.

    inurl:/certs/server.key

Web Server Detection, like [GHDB-ID: 6876](https://www.exploit-db.com/ghdb/6876) for detects GlassFish Server information with:

    intitle:"GlassFish Server - Server Running"

Vulnerable Files, as provided by [GHDB-ID: 7786](https://www.exploit-db.com/ghdb/7786) to locate PHP files:

    intitle:"index of" "*.php"
    
Vulnerable Servers, for example [GHDB-ID: 6728](https://www.exploit-db.com/ghdb/6728) to discover SolarWinds Orion web consoles:

    intext:"user name" intext:"orion core" -solarwinds.com.

Error Messages, such as [GHDB-ID: 5963](https://www.exploit-db.com/ghdb/5963), to find log files related to errors:

    intitle:"index of" errors.log

Adapt these Google queries to fit your needs as the queries will return results from all web servers that fit the criteria and were indexed. To avoid legal issues, refrain from accessing any files outside the scope of the legal agreement.




