# Lecture 4: Get in touch with services

## Where are we in the process of ethical
hacking?
- We have several general information about the target
- We have the technical details (domains, ip ranges)
- We mapped the target network and have an inventory
(live hosts, responding services)
- What’s next?
- We try to compromise services
    - Find a vulnerability
    - Exploit the vulnerability


## How to start compromising a service?
What kind of services do we face form the outside?
Wb, FTP, SSH, DNS, mail (SMTP, POP3, IMAP, Exchange), VPN

Typical services inside
NetBIOS, SMB, Printer, RDP, DB services, LDAP, Kerberos etc


What kinds of errors (vulnerabilities) can we expect?

**Configuration related errors**
- Default credentials
- Easy to guess credentials
- No or inappropriate protection against guessing (brute-force)
- Unnecessary function
- Privilege misconfiguration
- Other configuration errors

**Software vulnerability related error**
- No input validation
- Memory handling errors
- Several other issues (see later)

## How to start compromising a service?
- First use in the normal way
    - Is there any information disclosures?
    - Error messages, etc
    - Restrictions

- Force it to error and obtain information
    - Provide invalid data
    - Use it in an invalid way

- Try factory defaults
- Brute-forcing
- Search for known exploits
- Service specific exploitations
- Unique ways


#### Find listed vulnerabilities
cvedetails.com

#### Default credentials
cirt.net

## Brute-forcing
- Trying out multiple combinations
- How to generate the options
    - Random
    - Trying out all combinations
    - Using a list or dictionary

#### Brute-forcing tools
- THC Hydra(ssh, ftp, http)
- Ncrack
- Medusa

## Service specific attacks
FTP
SSH
SMTP
DNS
WEB
etc...

## What is an exploit
An exploit (from the English verb to exploit, meaning "to
use something to one’s own advantage") is a piece
of software, a chunk of data, or a sequence of commands
that takes advantage of a bug or vulnerability to cause
unintended or unanticipated behavior to occur on computer
software, hardware, or something electronic (usually
computerized). Such behavior frequently includes things
like gaining control of a computer system, allowing privilege
escalation, or a denial-of-service (DoS or related DDoS)
attack.

## Attacking ftp service
The ftp server configuration file declares what is enabled

``vsftpd.conf``


## Attacking SSH

## Attacking SMTP
