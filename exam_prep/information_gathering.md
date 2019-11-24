# Information gathering

## The technical information of a company
What are the technical information of a company?

Network range
Doman owners of the target
Domains
Subdomains
DNS data
DNS servers 
Specific IPs
Hosting companies


## How to collect technical information

Complete a DNS lookup for the domain names connected to the target.
Do a lookup for additional domain names connected to the target
Do a subdomain/hostname lookup for the domain names of the target. E.g 
*vulnerable-service.vg.no*
using pentest tools, robtex or other enumeration services, google search.

Lookup the Network range using the for the target(IP connected to the target domain) using the whois protocol or through RIPE or equivalent.

Check if the Network range/IP of the behind the target domain is owned by the target or is owned by a hosting service. This has implications for the attack using RIPE or equivalent.

Lookup the owners of the domains connected to the target using the NORID or equivalent.

## CIDR and usage

## Whois information

Whois is a DNS lookup protocol.

Typical information to be found trough a whois lookup is:

Registrar info: Information about what entity owns the domain name

Dates regarding the registration date and expirary

DNS name servers for the domain name

Registrar data:
    Location
    Organization 
    Contact informaation
    Email
    Site status
    DNS records

## DNS and its records

DNS is organized in a hierarchal tree structure. Like the following

subdomain2.subdomain1.topleveldomain

Examples of toplevel domains: com, net, no, io

DNS records

Adress Mapping records (A) contains the IP data
IP version 6 Address records (AAAA) contains IP 6 data
Canonical name (CNAME) maps one domain name (alias) to another (the canonical name)
Host Information record (HINFO) Redord intedend to provide information about the host CPU type and operating system
Name Server records (NS) The DNS server of the domain name. The name server is responsible for providing information about the domains sub domains