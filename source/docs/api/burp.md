# Burp intruder

Using [BurpSuite Intruder](https://portswigger.net/burp/documentation/desktop/tools/intruder/using) for fuzzing:

The payload sets determine which list will be used to a determined parameter. Choose **simple list**. For payload **Options** for example, select the lists **Fuzzing — Full** and **Fuzzing — SQL Injection**.

Additional options are selecting **Grep** to match with info in response, for example `SQL`. And the timeout option can be useful to bypass rate limit or some WAF’s. If there is a redirect parameter in the request, activate the option **Follow redirections**. Note that sometimes an error can trigger before the redirect, so test both.

Analyse the response code of any anomalies, status code is important and look at the **Length** column: A bigger length could be an error in the response page.