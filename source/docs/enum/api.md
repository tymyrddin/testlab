# API scanners

## Burp API scanner

The [BURP Suite](../webapp/burp.md) API Scanner is only for Enterprise and Professional, and the price is very steep.

[API scanning](https://portswigger.net/burp/documentation/scanner/scanning-apis) works in a similar way to web page scanning with Burp Suite, but instead of crawling for web content Burp Scanner crawls for exposed API endpoints. Burp Scanner then audits these endpoints using the same configurations and techniques that it uses when scanning web pages.

Burp Scanner needs to be able to parse an API definition in order to scan it and can only parse definitions that meet the following requirements:

* The API definition must be a JSON-based OpenAPI version 3.x.x specification.
* The API definition must not contain any external references.

## ZAP API Scanner

[ZAP - API Scan](https://www.zaproxy.org/docs/docker/api-scan/) is a script that is available in the [ZAP Docker](https://www.zaproxy.org/docs/docker/about/) images.

It is tuned for performing scans against APIs defined by OpenAPI, SOAP, or GraphQL via either a local file or a URL. It imports the definition that you specify and then runs an Active Scan against the URLs found. The Active Scan is tuned to APIs, so it doesn’t bother looking for things like XSSs.

It also includes 2 scripts that raise alerts for any HTTP Server Error response codes and for any URLs that return content types that are not usually associated with APIs.
