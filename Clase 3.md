


CLASE 3 


IoT: Internet of things, conectividad de los objetos a nuestro alrededor a internet




# Class 03.1: Switching concepts (ARP)

```
      ┌─────────┐
  ┌───┤Switch-01├───┐
  │   └─┬─────┬─┘   │
  │     │     │     │
┌─┴─┐ ┌─┴─┐ ┌─┴─┐ ┌─┴─┐
│PC1│ │PC2│ │PC3│ │PC4│
└───┘ └───┘ └───┘ └───┘
```

1. **Flooding**
- When the swith doesnt know the destination MAC-address, it floods all the interfaces !!with exeption of the incomming interface

2. **MAC-address learning**
- switch learns by ingress mac-address

3. **mac-address-table**
- Switch saves the information on the "mac-address-table" 

4. **how to check basic network information on your PC:** 
- ipconfig /all (windows cmd)
- arp -a (shows ARP table in the windows PC)




### Activity class 03: PT activity
*check file : "PT activity"*
* packet tracers:
* 153 LAB basic configs SW
* 033 verduras
* 148 physical-mode INT-2.9.2 (research if needed)



### QUESTIONS
*check file : 039 questions.md*


# Class 04.1: Typical Home Network HomeRouter

A typical home network router acts as the central point connecting your home devices to the internet. It has one Internet (WAN) port  and multiple Ethernet (LAN) ports. Differentiating these ports is important because plugging a cable into the wrong one can break internet access, cause network issues, or stop devices from communicating properly.

![Alt text](181image.png)

### Ethernet Ports (LAN):
These ports connect to the internal switch portion of the router. These ports are usually labeled “Ethernet” or “LAN”, as shown in the figure. All devices connected to the switch ports are on the same local network.
### Internet Ports (WAN):
This port is used to connect the device to another network. The internet port connects the router to a different network than the Ethernet ports. This port is often used to connect to the cable or DSL modem in order to access the internet.



## WPA, WPA2, WPA3 (security)       

__WPA__ replaced the insecure WEP (Wired Equivalent Privacy) standard, WPA is now deprecated due to weak security and known vulnerabilities

__WPA2__ became the long‑time default with stronger AES encryption, and 

__WPA3__ is the modern standard, designed to provide better protection against password‑guessing attacks and improve security on both personal and public Wi‑Fi networks.

*Alert: The Wi‑Fi WPA security setting must be WPA2 for Sonos to work properly.*
<!--! Alert: The Wi‑Fi WPA security setting must be WPA2 for Sonos to work properly. -->



## Choosing between Personal and Enterprise; 


* __Personal__ = LOCAL wifi_name and password
WPA Personal authentication is a Wi‑Fi security method that uses a pre‑shared password (PSK) to control access to the wireless network. All devices use the same password to connect, making it simple and suitable for home or small networks



* __Enterprise__= REMOTE DATABASE user_name AND password
WPA Enterprise authentication secures a Wi‑Fi network using individual user credentials and a central authentication server (RADIUS). Each user is authenticated separately, making it more secure and easier to manage for businesses and organizations.

WIFI = 802.11 (IEEE)

*Alert: Sonos devices do not support WPA Enterprise authentication.*
<!--! Alert: Sonos devices do not support WPA Enterprise authentication. -->


## Wireless security concepts
- __SSID__ Broadcast (SSID = Service Set Identifier = Wifi name): Determines if the SSID will be broadcast to all devices within range. By default, set to Enabled.

- __MAC address filtering__
- use MAC address to limit access to a wifi network -->


### Activity class 04: PT activity
*check file : "PT activity"*
* packet tracers:
* 044 home routerv2
* 045 Configure a Wireless Router and Client (research if needed)



### Activity class 04: PT activity
*check file : "PT activity"*
* packet tracers:
* 044 home routerv2
* 045 Configure a Wireless Router and Client (research if needed)
