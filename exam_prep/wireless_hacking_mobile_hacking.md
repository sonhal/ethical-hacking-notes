# Wireless hacking / Mobile hacking

## Wi-Fi protection methods and attacks

### Protection methods
- No protection
    Open Wi-Fi (Public Wi-FI), everyone can connect without authentication.
- No beacon frames
    The hotspot does not advertise itself. It wont appear on our Wi-Fi list. Hidden but not secured
- MAC filtering
    The hotspot maintains a list of the acceptable MAC addresses, only those client can connect. The MAC addresses are sent in clear text in the wireless packet. This protection can be bypassed with MAC spoofing.
- WEP (Wireless Equivalent Privacy)
    An old security algorithm for IEEE 802.11, not used anymore
- WPA (Wi-Fi Protected Access)
    All WP vulnerabilities are corrected(increased key size, etc)
- WPA2
    Improvement of WPA (Mandatory use of AES)

### Attacks

#### WEB
Hotspot using WEP can be attacked by collecting messages in a monitored network

The weakness of WEP is the IV collision. IF the attacker can obtain packages with the same IV then that can be used for the analysis for finding the key.

The attacker needs to collect 60 000 - 100 000 IVs to find the password.

#### WPA&WPA2

WPA/WPA2 uses a **4-way handshake** to authenticate devices to the
network. These handshakes occur whenever a device connects to
the network. The handshake has to be obtained to crack the
password.

and WPA-PSK keys. There are different attacks which can cause
deauthentications for the purpose of capturing WPA handshake data,
fake authentications, etc.
- Attack 0: Deauthentication
- Attack 1: Fake authentication
- Attack 2: Interactive packet replay
- Attack 3: ARP request replay attack
- Attack 4: KoreK chopchop attack
- Attack 5: Fragmentation attack
- Attack 6: Cafe-latte attack
- Attack 7: Client-oriented fragmentation attack
- Attack 8: WPA Migration Mode https://www.aircrack-ng.org/doku.php?id=aireplay-ng


## WPA handshake

When does the WPA handshake occur? How can the handshake be forced by the attacker?

Answer:

WPA handshake occurs when a device tries to connect to a WPA enabled hotspot. A handshake can be forced by the attacker by fooling the hotspot to think the device has disconnected

## Mobile device attack types (attack surface)

## OWASP mobile top 10