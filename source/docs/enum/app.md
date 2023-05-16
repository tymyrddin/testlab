# Web application scanners

## Burp Suite scanner

[Burp Suite](../webapp/burp.md)'s scanner can passively or actively crawl sites and highlight potential security issues as it goes, using a built-in vulnerability scanner. It is only available in the professional and enterprise version. The cost is steep (around 500 Euro a year).

## Wapiti

[Wapiti](https://wapiti-scanner.github.io/) audits the security of websites or web applications. It performs "black-box" scans (it does not study the source code) of the web application by crawling the webpages of the deployed webapp, looking for scripts and forms where it can inject data.

Once it gets the list of URLs, forms and their inputs, Wapiti acts like a fuzzer, injecting payloads to see if a script is vulnerable.

## ZAP

* [OWASP Zed Attack Proxy (ZAP)](https://www.zaproxy.org/docs/) is a free web application scanner, and functionally similar to Burp Suite, but offers a different array of features.

## w3af

[w3af](http://w3af.org)  is a Web Application Attack and Audit Framework. The project's goal is to create a framework to help secure web applications by finding and exploiting all web application vulnerabilities. Developed using Python easy to use and extend (licensed under GPLv2.0).

## WPScan

[WPScan](https://github.com/wpscanteam/wpscan) is a web application security scanner that focuses on WordPress installations. It attempts to identify insecure WordPress configurations and plugins based on versioning data, username enumeration, known default passwords, exposed files, and a database of known vulnerabilities. It requires a license.

