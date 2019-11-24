

# Technical information Gathering

### Technical information

- Domain names of the target
- Domain owner(s) of the target
- Domain registrants
- Ip addresses associated with the target websites
- Ip ranges of the target
- Ip range of the owner(s)
- List of hosted websites
- Hosting companies
- Etc

### Domain names
A domain is a identification string that defines a realm of administrative e autonomy, authority or control within the internet.

Example: aftenposten.no
          second level domain.topleveldomain


Domain names are formed by the rules and procedures of the Domain Name System (DNS). Any name registered in the DNS is a domain name.

Top level domain can be (com, net, info, edu, org and country code). Second and third level domains can be any string. The full length of the domain cannot be longer than 255 characters.


www.mn.uio.no
hostname,thirdlevel.secondlevel.TLD

- A hostname is a domain name that has at least one associated IP address
- The first domain was registered in 1985 (symbolics.com)
- Domains are registered by the domain registrars that are accredited by the Internet Corporation for Assigned Names and Numbers(ICANN).
- Each TLD is maintained and serviced technically by an administrative organization operating a registry (UNINETT Norid AS for .no) 
- All data has to be published and accessible with the whois protocol


### Domain name registration data - whois (e.g. http://who.is)

THe whois database must contain the following information:
- Administrative contact
- Billing contact
- Name servers

Nameservers are computers that provide subdomain information for the particular domain using the dns protocol.

 - whois protocol
 - TLD registrars search for more info
 - viewdns.info


### Domain name search
remove www from google search to find other subdomains
``site:uio.no -www.uio.no``
tools:
- netcraft <- not to good
- pentest tools.com

### Domain to ip conversions (DNS service)
- Address mapping records (A)
- IP Version 6 Address records (AAAA)
- Canonical Name records (CNAME)
- Host Information records (HINFO)
- Mail exchanger records (MX)
- Name Server records (NS)
- Reverse-lookup Pointer records (PTR)

### Reverse ip lookup

viewdns.info

### IP addresses

 - whos.is lookup for ip address space

### Hosted websites /Cloud services

Make sure the target owns the network range

### Finding network ranges

- Search for all domains including second and third level
- Look for corresponding IPs
- Check which database contains the IP owner (whois)
- Check the IP ranges (ripe, arin, etc...)

reverse whois
robtex.com

## Internal network IP address ranges

DMZ
