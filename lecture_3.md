# Network Reconnaissance - port scanning

Different scanning positions
- Mapping from outside the network
- Mapping from compromised DMZ
- Mapping from inside the network


### Circuit switched vs Packet switched network

Nowadays we use packet switched networks

### Network mapping - answer options

- Positive answer
    in case of icmp we cet a echo reply for our echo request

- Negative answer
    In case of icmp we get destination unreachable / host unreachable message

- No answer
    In case of icmp, we have no response from the host that was addressed by the echo request (filtered maybe)

TTL for linux is usually 64


### ICMP - traceroute

Sends a message with TTL 1, TTL 2 etc...
Lists nodes in the network between you and a host

*Visual traceroute*

### Nmap

**ping**

```bash
nmap -sP rema.no
```

**list scan**
Asks the DNS server of the name (no connection to the hosts directly)
```bash
nmap -sL 192.0.0.0/24
```

**TCP scan**
Remember Nmap does not very that the service type is correct
```bash
nmap -sT <target>
```
Scan specific ports (port 800 to 850)

```bash
nmap -sT -p800-850 <target>
```

### TCP scan

Three options
- Port is open
- Port is closed
- Port is filtered


### SYN scan (half open scan)
A TCP scan where RST is sent instead of the final ACK

```bash
nmap -sS <target>
```

### Reverse scans

- Null scan
- Fin scan
- Christmas scan

### ACK scan

To determine if the target is behind a stateful or stateless firewall.
*Stateful firewalls will drop ACK packets without previous SYN-ACK packages registered.

### Decoy scan

If a TCP connection is established it will be loged by the firewalls. Decoy scan uses needle in the haystack theory. It sends out packets with different source IPs to hide the true origin.


### Idle scan, ftp bounce - hide ourselves

### Operating system detection

Nmap uses TCP/IP stack fingerprinting

### Service detection

Uses banner grabbing




