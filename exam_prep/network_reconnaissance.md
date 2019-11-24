# Network reconnaissance

## The layers of the OSI model

Application layer
Presentation layer
Session layer
Transport layer
Network layer
Data link layer
Physical layer

## ICMP protocol and usage (tools)

ICMP protocol is used to check if a host is responding

## Main scan types and answers types in case of ping scan and tcp scan
What is a ping scan and what is a tcp scan? What kind of answers can occur in case of ping scan and tcp scan?

#### Ping scan (ICMP)

Positive answer
    Incase of icmp we get an echo reply for our echo request
Negative answer
    In case of icmp we get destination unreachable/ host unreachable message
No answer
    In case of icmp we have no response form the host that was addresses by the echo request

#### TCP scan

SYN SCAN

Response:

SYN+ACK
    Port is open
RST
    Port is closed
No response
    Port is filtered


Ping scan is layer 3
TCP scan is layer 4

## TCP header and flags, handshake

TCP flags are for maintaining the connection status
urg, ack, psh, rst, syn, fin

Important parts of the TCP header
source port, destionation port
Flag
sequence number

#### Handshake

sender->SYN
receiver->SYN+ACK
sender->ACK