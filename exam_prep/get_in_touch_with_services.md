# Get in touch with services

## Factory defaults
Most commonly used services have default passwords and configurations that are available on the internet. If an attacker can fingerprint the target service the attacker can attempt to exploit the service by attempting default passwords or actions that are enabled with default or permissive configurations.

## Configuration errors

A common way to compromise a public facing service is configurations releated errors. Typical errors are:

- Default credentials
- Easy to guess credentials
- No or bad protection against bruteforce attacks
- Unnecessary functions that are enabled
- Privilege misconfigurations

## Service specific attacks: Open-relay smtp, DNS zone transfer

What is Open-relay smtp and how to send a email with it?

Accept all emails without authentication. You can connect with telnet and send emails

#### DNS zone transferer
Since DNS data is stored redundant the slave DNS can ask the master DNS to send a copy of a part of its database (zone) to the slave.

Zone transfer operation should be limited for the slave ip address. If this is not the case, anyone can obtain the whole zone data (and network topological information too).

## Brute-forcing, services that can be attacked by Hydra!

### Domain brute forcing

The act of brute force resolve A, AAA and CNAME records against a domain. 