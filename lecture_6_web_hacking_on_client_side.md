# Lecture 6: Web hacking 2
Cross Site Scripting (XSS), Cross Site Request Forgery (CSRF) Session related attacks

## Burp suite
Burp is a graphical tool for testing websites. It has several modules for manipulating the web traffic

- Spider: Automatic crawl of web applications
- Intruder: Automatic attack on web applications
- Sequencer: Quality analysis of the randomness in a sample of data items
- Decoder: Transforms encoded data
- Comparer: Perform comparison of packets
- Scanner: Automatic security test (not free)

### Parameter tampering

Manual
 - Burp repeater

Automatic
 - Burp Intruder


## Cross Site Scripting (XXS)
Reason: Insufficient user input validation

Without validation the attacker can provide:
 - HTML elements
 - Javascript


What can you do with XXS:
*What can you do with javascript*

- Redirect the page
- overwrite content
- Get cookie variables (if they are not protected with HTTPOnly). e.g the session variables for session hijacking, authentication cookies
- Keylogging, the attacker can register a keyboard event listener using addEventListener and then send all of the users keystrokes to his own server
- Phishing: tha attacker can insert a fake logging form into the page to obtain the users credentials
- Launch browser exploits ( ex: escaping sandboxing)

BUT
- Local files of the clients are NOT accessible (browser sandboxing)

## XSS redirection
Redirection is possible with e.g javascript document.location syntax
Encode the script to avoid filters

## XSS page rewrite

Rewriting the page is possible with e.g the javascript document.body..innerHTML syntax

## XSS cookie stealing

The cookies contain the session variables (see later). If the attacker
manages to steal the cookie with the session variable then he can carry
out session fixation to obtain the victim’s data.

## XSS filter evasion

Just filtering on the `<script>` tag is not sufficient. There are many was to evade filters

- encoding
- Adding javascript in image tags or other HTML constructs
- combination of the above

## XSS types

- DOM based XSS
- Stored XSS
- Reflected XSS

- Client Side XSS
- Server Side XSS

## Preventions against XSS

- Escaping user input

- Filtering

- Input validation (best)
    Comparing the input against a whitelist or regxp(regex might open you up to regex DoS)

- Sanitizing input


## Session related attacks - What is the session variable
Session variables are used to persist sessions over the stateless HTTP protocol. The session variable (cookie) identifies the user across multiple HTTP calls.

If the session variable is not random it can be predicted and open up the page/service to session attacks.

**If you can steal the session, you can steal the users identity.**
Session variables can have a expiry time which limits the usability.

## Session related attacks

- Predictable session tokes
    THe attacker finds out what is the next session id and sets his own session according to this.
- Session sniffing
    The attacker uses a sniffer to capture a valid session id (mitigated by HTTPS). 
- Client-side attacks (e.g XSS)
    The attacker redirects the client browser to his own website and steals the cookie (Javascript: document.cookie) containing the session id.
. Man-in-the-middle attacks
    The attacker intercepts the communication between two computers.
- Man-in-the-browser-attacks

## Session related attacks - protections
THe session variable should be stored in the cookies. Since only the session id identifies the user, additional protections such as geoip significantly decreases the chance for the session id to be stolen. FOr protecting the session id there are several options:

- Using SSL/TLS
    If the packet is encrypted then the attacker cannot obtain the session id.
- Using HTTPOnly flag
    Additional flag in the response header that protects the cookie to be accessed from client side scripts.
- Using Geo location
    Bonding the session id to ip address is a bad idea because the ip of a user can be changed during the browsing (dynamic ip addresses especially for mobile clients). But checking geo locations is a good mitigation.

## Session variables in URL
Session id should be stored in cookies.

Why is it a bad idea to pass the session id as a GET parameter or store it in the URL?
- The attacker can read it through the screen (shoulder surfing social engineering)
- The user can send the session variable accidentally by copying the url

## Session variable expiry

THe session should be expired after there is no user interaction. If the session expires after a long time or never then the attack has time to bruteforce the session variables.


## Cross Site Request Forgery (CSRF)
Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application in which they're currently authenticated.

**Example**
The attacker sends a tricky link to the user that executes a malicious action (transferer money to Maria) without realizing it.

```html
<a href="http://bank.com/transfer.do?acct=MARIA&amount=100000">View my
Pictures!</a>
```

```html
<img src="http://bank.com/transfer.do?acct=MARIA&amount=100000" width="0"
height="0" border="0">
```

If the user is previously logged into the bank he has a valid session and the malicious action will be executed. Without the session the action will not be carried out.

https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)

