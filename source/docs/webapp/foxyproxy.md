# Using firefox as proxy for Burp and Zap

## FoxyProxy

Foxy Proxy allows us to port switch between [Burp](burp.md) and [ZAP](zap.md), or completely turn off the proxy 
feature altogether.

| ![Get FoxyProxy](../../_static/images/fox1.png) |
|:--:|
| There are two versions. We only need the [basic version](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/) |

| ![Burp](../../_static/images/fox2.png) |
|:--:|
| I set port `8080` for Burp |

| ![Zap](../../_static/images/fox3.png) |
|:--:|
| And port `8081` for Zap |

| ![Result](../../_static/images/fox4.png) |
|:--:|
| Results look like this |

## Burp certificate

Install the certificates for both Burp and Zap to allow us to navigate HTTPS traffic without having encryption warnings.

Start up BurpSuite and go to Proxy tab -> Options. 

| ![In Burp](../../_static/images/fox5.png) |
|:--:|
| You should see an entry for your localhost, `127.0.0.1`, and port `8080`.<br> These are the default settings for BurpSuite. If not, add.|

Select BurpSuite on FoxyProxy, and navigate to `http://burpsuite`:

| ![Get cert](../../_static/images/fox6.png) |
|:--:|
| Download that cert |

Go to the options menu in Firefox and select Settings -> Privacy & Security. Nearly all the way down, in the Security section click on the `View Certificates` button. And from the `Authorities` tab, choose `Import`.

| ![Import cert](../../_static/images/fox7.png) |
|:--:|
| Import the cert. |

| ![Import cert](../../_static/images/fox8.png) |
|:--:|
| Select "Trust this CA to identify websites", and OK. |

Test that the certificate is imported correctly by visiting an HTTPS website with BurpSuite running and Burp being selected in FoxyProxy. It should load without errors.

## Zap certificate

| ![Import cert](../../_static/images/fox9.png) |
|:--:|
| Zap, smart as it is when opening it up with Burp still running. |

| ![Import cert](../../_static/images/fox10.png) |
|:--:|
| If not, set it in `Tools` -> `Options` -> `Local Servers/Proxies` |

To install the HTTPS certificates for Zap, within the Options menu, `Network` -> `Server Certificates`.

| ![Import cert](../../_static/images/fox11.png) |
|:--:|
| Click `Save` |

Open Firefox `Settings` -> `Privacy & Security` menu -> `View Certificates` button -> `Authorities` tab, select `Import`. Trust this CA to identify websites.

To test it, have Zap running and FoxyProxy set to Zap. Go to any HTTPS website, and it should load without error.

