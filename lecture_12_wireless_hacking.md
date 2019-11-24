# Lecture 12: Wireless hacking

Types of wireless protocols
WEP hacking
WPA&WPA2 hacking

## Wireless protocols

- LTE (Long Term Evolution): High speed wireless communication for mobile devices
- Wi-Fi: For Local Area Networks
- Bluetooth
    Bluetooth is an open wireless technology standard for transmitting data over short distances. Bluetooth equips its network and devices with high-level services like file pushing, voice transmission and serial line emulation.
- WirelessHD (UltraGig)
    A standard for wireless transmission if high definition video. The core technology allows theoretical data rates as high as 25 Gbit/s
- Z-Wave
    A wireless commutation protocol used primarily for home automation. It uses low-energy radio waves to communicate from appliance to appliance
- Zigbee
    High level communication protocol for low power devices

## Wi-Fi (IEEE 802.11)

Wi-Fi is a Local Area Network communication that implements layer 1 (physical) and layer 2 (MAC) for wireless connections. All different version are maintained by the IEEE 802.11 standard.

## Wi-Fi definitions

- SSID (Service Set Identifier)
    Is the primary name associated with an 802.11 wireless LAN (WLAN) including home networks and public hotsports. THis is the name of the network.
- BSSID (Basic Service Set Identifier)
    Each access point has a unique identifier. SSID identifies the WLAN, even when overlapping WLANs are present. Incase of multiple access points within a WLAN there has to be a way to identify all access point that have the same SSID.
- ESSID (Extended Service Set Identifier)
    Consist of all the BSSes in the network. For all practical purposes the ESSID identifies the same networks as the SSID does. The tem SSID is used most often.
- Beacon frame
    It is one of the management frame in IEEE 802.11 based WLANs. It contains all the information about the network. Beacon frames are transmitted periodically to announce the presences of a WLAN.

## Wi-Fi network protections

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

## Wireless Equivalent Privacy (WEP)

WEP is a security algorithm for Wi-Fi networks. There are 2 types:
- 64bit key (40 bits in the real)
- 128bit key (104 bits in real)

The basis of the data encryption is the XOR operation:


Since using XOR is not enough for WEP append the key with so called Initialization Vector (IV)

WEP64 = 24bit IV + 40bit key
WEP128 = 24bit IV + 104bit key

IV is keep changing during the communication and it travels as clear text in the network. The communication parties can observe the IV and append it to the key to use for the decryption.

The weakness of WEP is the IV collision. IF the attacker can obtain packages with the same IV then that can be used for the analysis for finding the key.

The attacker needs to collect 60 000 - 100 000 IVs to find the password.


## Wi-Fi hacking - Monitor mode

To collect the IVs first we need to change the wireless adapter to
monitor mode.
Monitor mode is for wireless adapters (WNIC). It allows to monitor all
traffic received from the wireless network. Unlike promiscuous mode,
which is also used for packet sniffing, monitor mode allows packets to
be captured without having to associate with an access point or ad hoc
network first.

The attacker collects several packets with different WEP IVs. *Airodump-ng* can filter the air traffic for specific conditions and save them to file.

*Aircrack-ng* is able to restore the key if appropriate number of
packets are provided. Multiple capture files can be provided. The
whole cracking process is automatic.

## WPA/WPA2 hacking

WPA aims to provide stronger wireless data encryption than WEP.
- 64 digit hexadecimal key or an 8 to 63 character passcode
- WPA protocol used the same cipher (RC4) as WEP but added
TKIP (Temporal Key Integrity Protocol) to make it harder to
decipher the key
- WPA2 - replaced RC4 with AES (Advanced Encryption Standard)
and replaced TKIP with CCMP (Counter mode with Cipher block
chaining Message authentication code Protocol)

WPA/WPA2 uses a **4-way handshake** to authenticate devices to the
network. These handshakes occur whenever a device connects to
the network. The handshake has to be obtained to crack the
password.


## WPA/WPA2 hacking - aireplay
Aireplay-ng is used to inject wireless frames. The primary function is to
generate traffic for the later use in aircrack-ng for cracking the WEP
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