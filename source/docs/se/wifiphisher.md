# Wifiphisher

Wifiphisher automates phishing attacks on Wi-Fi networks to get the WPA/WPA2 passwords of a target user base. The tool can choose any nearby Wi-Fi access point, jam it (de-authenticate all users) and create a clone access point that doesn’t require a password to join.

Any person who connects to the evil twin-like open network is presented with a seemingly legitimate phishing page asking for the Wi-Fi password to download a firmware update, which is cited as the reason the Wi-Fi isn’t working.

Once the targets enter a password, Wifiphisher sends an alert while stalling for time. After transmitting the captured password, it will display both a fake reboot timer and a fake update screen to buy time for testing the captured password. A handy tool for evaluating your security defenses against Wi-Fi-based social engineering.

On Kali:

    $ sudo python wifiphisher.py