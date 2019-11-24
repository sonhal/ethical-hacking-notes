# Lecture 11: Internal network hacking

## Overview
- Internal network hacking steps
- Packet sniffing
- ARP protocol, ARP/DNS poisoning
- Internal network Windows protocols

## Get access to the internal network

How to get inside the internal network?
- Physically?
- Logically?

Physical Access

- Simple walk inside the building and find endpoints
- How to get inside if there is access restrictions?
    - Social engineering
    - Taking a real job (insider attack)


## Type of ethical hacking projects
*Form the attackers point of view*

- External peneratration testing
- Web hacking
- **Internal penetration hacking**
- Wireless penetration testing
- Social Engineering

Form the access right point of view

- Black box testing
- Grey box testing
- White box testing


## Steps of hacking (internal network)

1. General Information gathering
    Collecting all available information from the target and systemize the information from the outside?
2. Technical Information gathering
    Collecting network and system specific information from the outside?
**We need physical or logical access to the network to proceed**

3. Identifying available hosts in the target network (which computers can be attacked) 
4. Identifying available services in the target network (which services can be attacked)
5. Manual mapping of the services (to check how it looks like, the impressions, system reactions, mitigations, etc)

## Get access

What is needed for the tcp/ip communication?
- Valid IP
- Netmask
- Gateway
- DNS(es)

Can we do something without a valid IP? Yes we can listen to the traffic. The network topology can be different for the network (ring, star, line). Packets addressed to a different device can pass through our computer and also the broadcast messages. The network card works in layer 2 level and the addressing is done by the MAC. Normally all network cards process only the packet that has its own MAC in the destination filed.

**But network cards can work in promiscuous mode as well!**

## Promiscuous mode / Monitor mode

In **promiscuous mode** the network card (NIC) passes all the traffic it receives to the CPU rather than passing only the frames that the controller is specifically programed to receive (MAC). This mode is normally used for packet sniffing

**Monitor mode** is for wireless adapters (WNIC). It allows to monitor all the traffic received from the wireless network. Unlike promiscuous mode, which is also used for packet sniffing, monitor mode allows packets to be captured without having to associate with an access point or ad hoc network first.


## Wireshark
Wireshark is a packet sniffer. It sets the NIC to promiscuous mode and displays all the traffic crossing the NIC.

Each frame that crosses the NI can be analyzed in more detail, all the data with labels appears when opening the frame data.

In case there is no access to the network (no ip) relevant information can be revealed by only sniffing the traffic of other 
devices. 

What can we see form the Wireshark traffic?
- MAC addresses in use
- IPs in use
- Traffic directions
- Possible subnets
- Proxy servers
- Server zone
- Clear text data

## Get access

How to get access logically? I have found an endpoint and plugged in my computer. What are the options?

- Do we have a link? (is the endpoint patched?)
- Do we get an IP with DHCP? THe Dynamic Host Configuration Protocol (DHCP) is a network management protocol used on UDP/IP networks whereby DHCP server dynamically assigns an IP address and other network configuration parameters to each device on the network so they can communicate with other IP networks.
- **Port security** is a layer two traffic control feature on Cisco Catalyst switches. It enables an administration to configure individual switch port to allow only a specified number of source MAC addresses to connected to the port

## Get access - bypassing port security

How to bypass port security? We need a valid MAC address for the port.

- Sniffing the traffic to obtain a valid MAC
- Plug out a device from the network(e.g printer and fake our MAC)

## Get access to the internal network

What happens if
- There is no available endpoints?
- There are endpoints but we do not get a IP (no DCHP, faking MAC does not help)
- Cannot get access with social engineering?

How to move on? Ask the contractor to proved access to the network as an employee.
- First test is passed (unknown attacker sneaking inside cannot get access)
- But we need to see what the employees can do from the inside

## Internal hacking steps

After we have the IP and can communicate through the network the steps are very similar to external hacking.

- Identifying available host in the target network
- Identifying available services in the target network
- Manual mapping of the services
- Automatic vulnerability scanning
- Manual verification of the findings
- Exploitation
- Lateral movements
- Ensure access
- Collect info - achieve primary and secondary goals
- Remove clues and traces 


## Internal hacking - port scanning

For host and service identification port scanning can be used here as well. There is one significatnt difference. The internal network range is much larger. How to scan a 10.0.0.0/8?

- Only ping-ing all (256^3 = 16777216 hosts) takes days and we have no info from the services

Some options how to proceed:

- Identifying network sub-ranges in use. It can be done using the packet sniffing data (if there is a specific IP un use can the whole /24 subnet there)
- Identifying special network sub-range domains (e.g server domains, printer domains) using the captured data
- Carrying out limited port scans e.g 10.0-255,0-255.1 (checking only IPs ending with 1)
- Finding out the logic in the addressing e.g 10.3.1.104 (pc on the 3rd floor and the 1st corridor)
- Obtain network topology documentations/drawing in the admin documents (best option)

The service identification can be done in the same way as in the case of external network hacking (tcp can, udp scan, syn scan, etc)

Making an inventory for the discovered hosts and services is even more important than in the case of external hacking.

Which tests find more services the external network discovery or the internal network discovery
- internal


# Layer 2 and layer 3 communication

The basis of layer 3 communicator is the IP address. But devices in the same internal subnet (behind the same gateway) are using layer 2 level communication despite the device has IP address too.

When a device in the subnet address another device in the subnet it use both the MAC and the IP (but only the MAC is used). To go outside the subnet the gateway addresses are needed (IP and MAC).

## ARP protocol

Since both the MAC address and the IP address are needed for  communication a special protocol is used to discover and maintain the IP MAC pairs.

**ARP (Address Resolution Protocol** is a network protocol used to find ot the hardware (MAC) address of a device from an IP address. It is used when a device wants to communicate with some other device on a local network (For example on an Ethernet network that requires physical address to be know before sending packets). The sending device uses ARP to translate IP addresses to MAC addresses. The device sends an ARP request message containing the IP address of the receiving device. ALl devices on the local network segment sees the message, but only the devices that has that IP address response with the ARP reply message containing its MAC address. THe sending device now has enough information to send the packet to the receiving device.

https://study-ccna.com/arp/

## ARP protocol

Each device maintains an ARP table. It can easily be printed with all OSes.

The ARP table is built continuously throughout the communication. ARP request broadcasts + ARP response.

## ARP poisoning

**ARP poison routing**, is a technique by which an attacker sends (spoofed) Address Resolution Protocol (ARP) messages onto an Local Area Network to associate the attackers MAC address with the IP address of another host, such as the default gateway, causing any traffic meant for that IP address to be sent to the attackers instead.

## ARP poisoning mitigations
Dynamic ARP Inspection (DAI) is a security feature that helps prevent ARP poisoning and other ARP-based attacks by intercepting all ARP requests and responses, and by verifying their authenticity before updating the switch's local ARP cache or forwarding the packets to the intended destinations.

The DAI verification consists primarily of intercepting each ARP packet and comparing its MAC address and IP address information against the MAC-IP bindings contained in a trusted binding table. The trusted binding table is dynamically populated by DHCP snooping. DAI allows the configuration of static ARP ACLs to support systems that use statically configured addresses.

## DNS poisoning

DNS poisoning is a general expression for different attacks to manipulate the dns database to divert Internet traffic away from legitimate servers and towards fake ones. In case of the internal networks one option is to do a *man-in-the-middle attack* with ARP poisoning.

The attacker mislead the victim and provides his MAC as the DNS MAC (in case of internal DNS the gateway MAC is faked). For a DNS resolve request the attacker sends his own IP address to redirect the victim to another site..


## Netbios
Commonly used by Windows devices

**Network Basic Input/Output System (Netbios)** provides services related to the session layer of the OSI model allowing applicators on separate computers to communicate over a LAN

- NetBIOS Name Service is a service providing name lookup, registration, etc (tcp 137)
- NetBIOS Datagram Service is a connectionless service to send data (udp 138)
- NetBIOS Session Service lets two computer establish a connection for a "conversation" allows larger messages to be handled, and provides error detection adn recovery (tcp 139).
For NetBIOS troubleshooting the nbstat is used.

NetBIOS has several recorded vulnerabilities


## Server Message Block (SMB)

SMB is mainly used for providing shared access to files, printers and serial ports and miscellaneous commutation between nodes on a network. It can run:

- Directly over TCP (tcp/445)
- On NetBIOS (TCP 137/139, udp 138)

SMB has different versions: 2.1 is introduced with Windows 7, 3.1 was introduced with Windows 10.

### SMB vulnerabilities
SMB has several recorded vulnerabilities

## Active Directory (AD)
Active Directory provides the methods for storing directory data and making this data available to network users and administrators.

It stores information about objects on the network and makes this information easy for administrators and users to find and use. Active Directory uses a structured data store as the basis for a logical, hierarchical organization if directory information.

Vulnerabilities:
- CVE-2013-1282 Denial of Service
- CVE-2018-0890 Microsoft Active Directory Security Bypass
Vulnerability