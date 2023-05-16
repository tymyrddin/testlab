# LDAP enumeration

## Bloodhound

Bloodhound uses the collector which is called as SharpHound to collect various kinds of data by running a ton of LDAP queries to collect information within Active Directory. [BloodHoundAD/SharpHound] is designed targeting .Net 4.6.2. SharpHound must be run from the context of a domain user, either directly through a logon or through another method such as RUNAS.