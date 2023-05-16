# Tracing routes

Traceroute is a great tool for seeing where a `ping` goes before it hits the target system, allowing for greater 
situational awareness on the target.

`traceroute` (Windows `tracert`) traces the route taken by the packets from the attack host to the target host. 
The console output shows the path between the two and reveals firewalls and routers that it hits on the way,

Basic traceroute:

    # traceroute [domain]

Disable IP address and host name mapping:

    # traceroute [domain] -n

Configure response wait time. The -w option expects a value which will be taken as the response time to wait for 
(for example 0,1 seconds) If traceroute is unable to wait for any response it will print *’s.

    # traceroute [domain] -w 0.1

Configure number of queries per hop. Traceroute uses a default value of 3 packets per hop to provide 3 round trip times. With the option ‘-q’ (integer) you can set a new value for the number of probes per hop.

    # traceroute [domain] -q 5

Configure the TTL value. By default, the TTL value is 1 which means the output starts off with the first router in the path but using the ‘-f’ option a new value of the TTL field can be set.

    # traceroute [domain] -f 8 

Some routers do not respond to packets sent by traceroute, and a `*` is used to indicate such a case.

    traceroute clinic.thmredteam.com

```text
traceroute to clinic.thmredteam.com (104.21.93.169), 64 hops max
  1   *  *  * 
  2   45.83.90.145  64,469ms  73,575ms  70,986ms 
  3   *  *  * 
  4   217.138.223.188  53,067ms  52,242ms  55,242ms 
  5   89.44.212.140  52,708ms  55,677ms  53,332ms 
  6   172.71.132.4  57,544ms  52,764ms  53,005ms 
  7   104.21.93.169  52,763ms  64,055ms  53,459ms 
```
