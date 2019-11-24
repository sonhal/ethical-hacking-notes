# Ethical Hacking - first day

Lecture and exercises will be recorded

## Introduction

### What is ethical hacking?
In general hacking is illegal.

Limitations

Different goals than black hat hacking

### Why is ethical hacking necessary?
human factor, old system, faulty software

Reasons for security issues:

- Lack of money
- Lack of time
- Lack of expertise
- Negligence
- Convenience
- Old systems
- Too complex systems
- 3rd party components
- ...


Checking the system from the attackers perspective can reveal serious security deficiencies.

### The motivation behind blackhat hacking

- Coolness
- Because I can <- most common reason
- Money
- Revenge
- Annoyance
- Protest
- Organized professional groups

### The motivation behind ethical hacking

Promote the security of the system

### Goal of hacking
Break the information security trinity (confidentiality, integrity, availability)

- Steal confidential information
- Modify data
- Make services unavailable (DoS)


### Types of hackers

- black hat
- white hat
- script kiddies
- ...

### Differences of white and black hat

**blackhat**
- Does what is easiest
- Illegal
- Steal information, modify data, make service unavailable for own purpose
- Does not care about destruction
- Does not document, deletes all clues

**whitehat**
- Have to try to find all vulnerabilities
- Legal (Contract)
- Promote security by showing the vulnerabilities
- Document all activities
- Presentation and report

### Main steps of hacking

- Information gathering
- Identifying the target domain
- Finding vulnerabilities
- Exploiting the vulnerabilities
- Lateral movements
- Carry out the goal


### Hacking arena
hackingarena.no
sidious.hackinarena.no <- competisions


### Detailed steps of hacking

- General imformation gahtering
- Techincal infomation gathering: Collection network and system specific information like target ip ranges
- Identifying availible hosts in the target network
- Identifying availible services in the target network
- Manual mapping of the services
- Automatic vuneralibility scanning
- ...

### Type of ethical hacking projects

From the attackes location PoW
- External penetration testing
- Web hacking
- Internal penetration testing
- Wireless penetration testing
- Social engineering

From the attackes access PoW:
- Black box testing
- Grey box testing <- some internal knowledge of/access to the system
- White box testing

### Contract

The person that gives the contract has to have the power to issue such a contract.

example: Hosted websites. Owner of website cannot issue contract to hack the site as it is another company that owns the servers/infrastructure.


### Methods for information gathering

Google is our best friend


Start with homepage and wikipedia

Identify the key persons, pages and services in the company/target. 

Key persons
- Admins

For older information/websites: archive.org
For deleted pages etc: Google cached

### Collecting actual target related information

**Social media**
 - Most people have it

**Social media search services:**
 - Pipl.com <- paid

 - social-searcher.com <- free

### Collecting information from webpages
- All static information can ble downloaded at once (noisy, bur useful)
- Several tools exist like wget and Httrack

### Specific information search

- We can look for specific information on a webpage such as email addresses, phone numbers etc
    - Web data extractor
    - FOCA <- webpage document enumerator

### Google searching

site: <- filter to specific site
filetype: <- search for filetype
intitle: "index of" <- in title of page

finding files example: 
```
site: uio.no filetype:xls
```

**For more:**

ghdb.exploit-db

exploit-db.com/google-hacking-database
