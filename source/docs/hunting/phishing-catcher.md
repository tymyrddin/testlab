# Phishing Catcher

This tool enables discovering potential phishing domains by checking for suspicious TLS certificate issuances submitted to the Certificate Transparency Log (CTL). Its most important benefit is that it works in almost real-time. Since it`s written in Python and uses YAML for configuration it is also easy to employ.

According to GitHub, Phishing Catcher uses a YAML configuration file to assign a numeric score for strings that can be found in a TLS certificate’s common name or SAN field. Adjust the default configuration to your needs. For macOS or another operating system, installation may be difficult. Consider dockerizing it.

## Resources

* [Phishing Catcher](https://github.com/x0rz/phishing_catcher)
