# Web

## Web1

### The obligatory header fields of HTTP

Request:
The protocol version
The requested file
The Web method
The host name

Response:
The web answer (in the response)
The data
The content type

### Information disclosures on a website

Write examples of three different information disclosures on a website.

Robots.txt
Directory listing with service version
Comments in the source code

### Brute-force on a website

Different webserver use different default folder and default files. Dirb has collections of typical webserver related folder names

Hydra can be used to bruteforce login forms or other login methods.

### Web-methods, inappropriate configuration related to web methods

The web methods are
GET <- Get content
POST <- send data
HEAD <- Get the HTTP header
PUT <- Plcae content on the server
DELETE <- Delete a server resource
OPTIONS <- Get the supported web methods for the host

Inappropriate configuration of PUT method permissions can result in that attackers can upload files to the host

## Web2

### Burp method attack types

#### Sniper
This uses a single set of payloads. It targets each payload position in turn and places each payload into that position in turn.

#### Battering ram
This uses a single set of payloads. It iterates through the payloads and places the same payload in to all the defined payload positions at once.

#### Pitchfork
This uses multiple payload sets. This attack type is useful where an attack requires different but related input to be inserted in multiple places within the request.

#### Cluster bomb
This uses multiple payload sets. There is a different payload set for each defined position (up to a maximum of 20). This attack type is useful where an attack requires different and unrelated or unknown input to be inserted in multiple places within the request(e.g. when guessing credentials, a username in one parameter, and a password in another parameter).

### Cross Site Scripting

Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites.

There are different XXS types

#### Domain XSS
Reflected XSS
The malicious script is reflected to the target through a link or another delivery method. Usually the target is sent a link crafted by the attacker that contains javascript embedded in some query parameter which results in the javascript being reflected to the user.

#### Stored XSS
Stored XSS generally occurs when the user input is stored on the target server, such as a database, log, message, etc. When a users retrieves the data the payload is executed in the target browser.

#### DOM based XSS
 DOM Based XSS is a form of XSS where the entire tainted data flow from source to sink takes place in the browser, i.e., the source of the data is in the DOM, the sink is also in the DOM, and the data flow never leaves the browser. 

### Ways to compromise a website with XSS

When a attacker discover a website that is vulnerable to XSS the attacker can depending on the vulnerability send crafted links to targets that executes a exlplot.

If the vulnerability is a server side vulnerability the attacker can store a exploit on the target sever which will execute on many victim browsers (example: forum, blog message board, etc).



### XSS filter evasions

List and explain 3 different ways for XSS filter evasion.

hex encode script tags
use img tag onerror to execute the javascript
hide the payload in the iframe

### Ways of stealing the session variable

stored or server side XXS can be used to steal a session variable
If the traffic is HTTP and not HTTPS the session variable can be stolen using a *man-in-the-middle attack*

The attacker can obtain a session variable for him/herself and analyze it for patterns that can be exploited to get other session variables.



## Web3

### Sql injection exploitation types

#### Boolean based bind
The attacker provides a input and observes the website answer. The answer is either page 1 or page 2 (only two options). There is no direct response to the attackers query but it is possible to play a true and false game using the two different responses. THe difference between the two responses can be only one byte or totally different pages.

#### Error based
The attacker forces syntactically wrong queries and tries to map the
database using the data provided by the error messages.

#### Union query

The attacker takes advantage of the SQL UNION SELECT statement. If the attack er can intervene to the sql query then he can append it to a union select and form the second query almost freely.

#### Stacked query

If the SQL engine supports stacked queries (first query; second query; etc) then in case of a vulnerable parameters the attacker closes the original query with a semicolon and writes additional queries to obtain the data.

#### Time based bind

It is the same as the boolean based, but instead of having two different web responses the difference is the response time (less trustworthy)

### Other options
SQL vulnerabilities can be be used for other attacks than directly against the database.

#### Reading local files

#### Writing local files
With the SELECT INTO OUTFILE command the attacker can write local files.

#### Executing OS commands
In some cases the db engine has the right to execute OS level commands.

### File uploading with sql injection

In case of a Boolean based bind the attacker could use the *SELECT INTO OUTFILE* SQL synta<> to write to a local file on the server.

This is only possible if:
- UION SELECT or stack stacked queries are enabled
- With union select the attacker has to know or guess the row number
and the types of the chained query (see example)
- The writable folder needed in the webroot is accessible by the attacker.
- The attacer has to know or guess the webroot folder on the server

#### Example
http://193.225.218.118/sql3.php?email=laszlo’ union select ‘Imagine
here’s the attacking script’ ‘0’,’0’,’0’ into outfile ‘/var/www/temp/lennon.php

### SQL injection filer evasion

White space
NULL bytes
SQL comments
URL encoding
Character encoding
String concatenation
Hex encoding

### Xpath injection and its exploitation

Xpath injection is possible if the target website uses XML and xpath to interact with the website data, and that interaction does not have sufficient input validation.

The attacker can then enumerate the XML data store using provided Xpath commands.

### Exploitation of local file inclusion

List and explain 3 different ways of exploiting local file inclusion.

Accessing local files on the sevices like /etc/passwd
Reveal the service scripts source code with base64 encoding filter
Inject a script trough logs or HTTP headers and read it back through LFI

