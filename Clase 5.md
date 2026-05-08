
Clase 5


NAT (Network address translation): se usa para reutilizar ip dentro de redes privadas, las ips privadas no pueden salir al internet, el NAT las traduce a su version publica asignada para la red que pertenece


EJEMPLO


PC1 >> LAN 192.168.1.100
PC1 >> WAN 8.8.8.160

el ISP le asigna esta ippublica (8.8.8.160) a la red local para que se comunique con el Internet

Para eliminar un error donde hay dos routers donde ambos tiene un sistema de NAT, al segundo router se le debe cambiar su modo de operacion para que se comporte como un bridge (switch) y de esta forma comparten la misma informacion




# Class 07.1: Routing Consepts 

## Reasons to divide a network into multiple smaller networks.
    - To maintain smaller broadcast domains
    - Large networks are more difficult to troubleshoot.
    - Increase network security


## Host Forwarding Decision (ARP 2nd part)

A PC or host can send a packet to three different destinations: itself, a local host on the same network, or a remote host on another network. Let’s break down each one.

![Alt text](239image-1.png)

### Itself:
A host can send a packet to itself, commonly called __pinging the loopback interface__. This __tests__ the host’s own network settings and TCP/IP configuration.

### Local host:
This is a destination on the __same local network__ as the sender. The source and destination __share the same network.__

### Remote host:
This is a destination on a __different network__. The source and destination __do not share the same network__ and communication must go through a router.

# Routing Table:

### ROUTER 2 (R2) routing table:

``` 
                                     31.13.67.0/24
                                          ISP
                                           |
                                           |
                          10.0.0.0/24      |
                                ▼          |
                   .1┌──┐ .1           .2┌─┴┐.1
                ┌────┤R1├────────────────┤R2├────┐
                │f0/1└──┘f0/0        f0/0└──┘f0/1│
192.168.20.0/24 |                                │  172.16.20.0/24
                │                                │
               ┌┴──┐.254                      ┌──┴┐ .254
         ┌─────┤SW1├────┐                   ┌─┤SW2├──────┐
         │     └───┘    │                   │ └───┘      │
         │              │                   │            │
       ┌─┴──┐       ┌───┴┐               ┌──┴─┐       ┌──┴─┐
       │PC-A│       │PC-B│               │PC-C│       │PC-D│
       └────┘       └────┘               └────┘       └────┘
         .10          .11                  .10          .11

Gateway of last resort is 0.0.0.0 to network 0.0.0.0

C       10.0.0.0/24 is directly connected, FastEthernet0/0
C       31.13.67.0/24 is directly connected, FastEthernet1/1
C       172.16.10.0/24 is directly connected, FastEthernet0/1
S     31.13.67.0/24 is directly connected, FastEthernet0/0


```

*Alert: Multiple Wi‑Fi networks can share the same name (SSID) but use different IP addresses. If your Sonos devices aren’t on the same network, expect connectivity issues.*
<!--! **Alert:** Multiple Wi‑Fi networks can share the **same name (SSID)** but use **different IP addresses**. If your **Sonos devices aren’t on the same network**, expect connectivity issues. -->

### PT Activity
<!--! PT Activity -->
Demostration 


# Class 07.2 NAT (Network Address Translation) 

A Network Address Translation (NAT) is a technique used in computer networking to allow **multiple devices to share a single public IP address**, let’s quickly review **the two main types of IPv4 addresses:**

A __private IP address__ is an IP address used within a private network. Private IP addresses are not unique and cans be reused within different private networks. Some common private IP address ranges include 10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16.

A __public IP address__ is an IP address used to identify a device on the internet. Public IP addresses are unique and are assigned by Internet Service Providers (ISPs) to individual devices or networks.


# IPv4 exhaustion

__IPv4 exhaustion__ means we are running out of available IPv4 addresses, which are used to identify devices on the internet. This happened because the number of internet‑connected devices grew very fast.

To deal with this, NAT is used. Devices inside a private network use private IP addresses, and the router translates them into one public IP address when accessing the internet.

A __NAT translation table__ is used to keep track of the mapping between private IP addresses and public IP addresses. When a device with a private IP address sends a packet to the internet, the NAT device modifies the packet to replace the source IP address with a public IP address from the translation table.

__Double NAT__ occurs when two or more NAT devices are used in a network, creating two or more layers of private IP addresses. This can occur, for example, when a home router is connected to another router provided by an ISP or a network administrator.


*Alert: Sonos devices do not support Double NAT. To avoid issues, use only one NAT device or set the second router to bridge mode.*
<!--* Alert: Sonos devices do not support Double NAT. To avoid issues, use only one NAT device or set the second router to bridge mode. -->


### PT Activity
<!--! PT Activity -->
- check file: "075 PT simple nat"
- check file: "076 PT double nat"



# Class 08.1 
## class network ports: TCP vs. UDP

**Network ports** are like rooms inside a building. The building has **one address (IP address)**, but each room **(port number)** offers a **different service**. Let’s explore some of the **most common ports used by Sonos systems**.

<!-- 
* 0 - 1023 Well-know Ports
* 1024 - 49151 Registered Ports
* 49152 - 65535 Private Dynamic ports
-->


### common ports for SONOS:

- 80, 443 (TCP) Content services, radio, and Sonos account
- 445, 3445 (TCP) Music library
- 1400, 1410, 1443, 1843, 3400, 3401, 3500 (TCP) Sonos control
- 4070 (TCP) Spotify Connect
- 4444 (TCP) System updates
- 7000 (TCP) AirPlay
- 136–139 (UDP) Music library
- 1900, 1901 (UDP) Sonos app control
- 2869, 10243, 10280–10284 (UDP) Windows Media Sharing
- 5353 (UDP) Spotify Connect
- 6969 (UDP) Sonos setup


*Alert: The ports used by Sonos must be allowed on the network router (FIREWALL) for the system to work properly.*
*For more information on the ports Sonos uses, see this article:*
*https://support.sonos.com/en-us/article/configure-your-firewall-to-work-with-sonos*
<!--! Alert: The ports used by Sonos must be allowed on the network router for the system to work properly. For more information on the ports Sonos uses, see this article: https://support.sonos.com/en-us/article/configure-your-firewall-to-work-with-sonos -->




# Class 08.1 TCP vs. UDP

**TCP and UDP** are transport‑layer protocols that control how data is sent between devices. **TCP** prioritizes reliability and order, while **UDP** prioritizes speed and low latency, making each suitable for different types of network traffic.

| Feature          | TCP                                | UDP                                  |
| ---------------- | ---------------------------------- | ------------------------------------ |
| Connection type  | Connection‑oriented                | Connectionless                       |
| Reliability      | Reliable (guarantees delivery)     | Unreliable (no delivery guarantee)   |
| Order of data    | Data arrives in order              | Data may arrive out of order         |
| Speed            | Slower (more overhead)             | Faster (less overhead)               |
| Error checking   | Error checking: Yes                | Error checking: Minimal              |
| Best used when   | Accuracy matters more than speed   | Speed matters more than accuracy     |
| Common use cases | Web browsing, file transfer, email | Streaming, voice, discovery services |


### PT Activity - 
<!--! PT Activity - unblock / block ports on wireless router -->
- check file: "085 lab PT ports"


# Class 19.1 - More about WIFI

## Wireless technologies:
- **Bluetooth:** Some sonos speaker support bluetooth but initial setup is still shoud be via wifi
- **Celluar broadband:** (LTE) Sonos doesnt support LTE
- **Satellite broadband:** rural areas, expensive (starlink) Sonos doesnt support Satellite internet
- **WIFI:** (regular home use)


## Wireless Networks are classified by their range:
Wireless networks are grouped by how much area they cover. Understanding these categories makes it easier to know what kind of wireless connection is being used and why:

- **WPAN (Wireless Personal Area Network)**  
  Covers a **very small, personal space** around a user. Used for short‑range connections like **Bluetooth** between phones, headphones, or smartwatches.

- **WLAN (Wireless Local Area Network)**  
  Covers a **local area**, such as a **home, office, or school**. This is your typical **Wi‑Fi network** that connects devices to each other and to the internet.

- **WMAN (Wireless Metropolitan Area Network)**  
  Spans a **city or large campus**. Often used by **internet service providers or municipalities** to deliver connectivity across urban areas.

- **WWAN (Wireless Wide Area Network)**  
  Covers **large geographic areas**, such as **regions or countries**. Common examples include **cellular networks (3G, 4G, 5G)** that keep devices connected while moving long distances.


### Activity: sorting
<!--! Activities -->
- check: "093 offline activity"


## Antennas and Devices

- **Omnidirectional antenna**
Sends signal in all directions (360°).
Used in homes and offices.

- **Directional antenna**
Sends signal in one focused direction.
Used for long distance or targeted coverage.


*There is a Wi‑Fi feature that makes a router act like a **directional antenna**.*  
*It’s called **Beamforming**, and it **should be turned off** when using **Sonos devices***
<!--! There is a Wi‑Fi feature that makes a router act like a **directional antenna**.  It’s called **Beamforming**, and it **should be turned off** when using **Sonos devices**. -->



## Wireless access point (WAP) and Extenders
It is important to differentiate between autonomous access points, controller‑based access points, and wireless extenders, and to understand how each interacts with the wireless network. 

**Autonomous Access Point**
Works on its own.
Simple setup, small networks.

**Controller‑based AP (Lightweight AP)**
Managed by a central controller.
Used in large networks (offices, schools).

**Wireless Extender (EXT)**
A device that repeats or boosts Wi‑Fi signal to areas with weak or no coverage.
⚠️ Extenders increase range, not internet speed.

*ALERT: Sonos devices do not support connections through wireless extenders.*
<!--! ALERT: Sonos devices do not support connections through wireless extenders. -->



## Wireless Topologies
Different setups are used depending on whether devices connect directly to each other, through a router, or by sharing a mobile connection.

**Ad hoc mode**
Device‑to‑device connection.
No router. Devices talk directly to each other.

**Infrastructure mode**
Standard home or office Wi‑Fi.
Devices connect through a router / access point.

**Tethering**
Phone as a hotspot.
Your phone shares its internet with other devices.


*Alert: Sonos devices cannot be set up for the first time using tethering or mobile hotspots as the internet connection. Use a regular home Wi‑Fi network for the initial setup.*
<!--! Alert: Sonos devices cannot be set up for the first time using tethering or mobile hotspots as the internet connection. Use a regular home Wi‑Fi network for the initial setup. -->


# Class 19.2 -  WIFI REGULAR WIFI 

## Wifi Topologies blocks

- **Basic Service Set (BSS)**
A __single Wi‑Fi coverage area__ created by __one access point.__

- **Extended Service Set (ESS)**
__Multiple access points__ working together to create __one large Wi‑Fi network.__ Extended Service Sets (ESS)are used in __buildings and campuses__ to provide __one unified Wi‑Fi network__ across large areas


## **802.11 Standards**

Wi‑Fi standards determine the **frequency**, **speed**, and **coverage** of a wireless network.  
There are **two main options** to choose from: **2.4 GHz** and **5 GHz**.

*ALERT:  For some Sonos devices to work, the router must support both 2.4 GHz and 5 GHz.*
*Routers with only 5 GHz are not supported.*
<!--! **ALERT:**  For **some Sonos devices** to work, the router **must support both 2.4 GHz and 5 GHz**.  Routers with **only 5 GHz** are **not supported**. -->


- **2.4 GHz (802.11b)** → **Longer range**  
Here’s the updated version, clean and simple:

Better distance but **slower speeds**.  
Works **better through solid objects** like walls.  
Use **non‑overlapping channels** like **1, 6, and 11** to reduce interference.

- **5 GHz (802.11a)** → **Higher speed**  
Faster performance but **shorter range**.  
Common **non‑overlapping channels** include **36, 40, 44, and 48**.



### **Important settings to check for 2.4 GHz and 5 GHz**
- If both bands (5GHz and 2.4GHz) share the **same Wi‑Fi name (SSID)**, **rename them** and **separate the bands**. Disable Band Steering and Smart Steering if available. 
- Make sure the **wireless mode** is set to **b/g/n** (supports multiple Wi‑Fi standards).
- Set the **channel width** to **20 MHz**.
- **Not all Sonos devices support "Wi‑Fi 5" (802.11ac)**.


## Wireless concepts:

* SSID = wifi wireless name
* Network mode – 2.4GHz or 5.0GHz
* Security mode - security i.e. WEP, WPA, or WPA2.
* Channel settings – frequency bands in use.

### Activity Router simulators 
- check file: "096 Lab Finding wifi features"



# Class 19.3 - Wireless security: 

## WLAN Threats
Wireless networks are **easy to access**, which also makes them **vulnerable to attacks**.  
Understanding common **WLAN threats** helps us understand **which Wi‑Fi settings can interfere with connections and cause connectivity issues**.



**Denial of Service (DoS) Attacks**
  Overwhelms the WLAN with traffic, preventing legitimate users from accessing the network.

**Rogue Access Points (Unauthorized APs)**
  An unauthorized or fake access point that mimics a legitimate one, tricking users into connecting and exposing their data.

**Man‑in‑the‑Middle (MITM) Attack**
  An attacker intercepts communication between a user and the network, allowing data to be monitored or altered without detection.

<!-- ## Shared Key Authentication Methods

* WEP (Wired Equivalent Privacy) > legacy
* WPA (Wi-Fi Protected Access WPA) > Temporal Key Integrity Protocol (TKIP) 
* WPA2 > Advanced Encryption Standard (AES) 
* WPA3 > Protected Management Frames (PMF). -->

## Secure WLANs   
<!-- process with pictures -->
To protect a Wi‑Fi network from __WLAN threats__, several security features can be enabled. Be aware that __some of these features can cause compatibility issues with Sonos__.

- [ ] Hidden SSID / Network Cloaking This a Wi‑Fi feature that controls whether the network name (SSID) is visible. __Sonos doesnt support hidden SSID__

- [ ] **MAC Address Filtering** is a security feature that allows or blocks devices from connecting to a network based on their unique MAC address. If **“block any”** is enabled, it can prevent devices like Sonos from connecting.

- [ ] A VPN (Virtual Private Network) creates a secure tunnel over a public network, such as the internet. For SONOS proper operation, the VPN should be turned off.

- [ ] A **guest network** is a separate Wi‑Fi network created for visitors, isolated from the main network. **Sonos does not work on guest networks.**


*Alert: remember that on supported setups doesnt mean that sono will not work, it may work but it is not guaranteed and it may cause connectivity issues.*
<!--! Alert: remember that on supported setups doesnt mean that sono will not work, it may work but it is not guaranteed and it may cause connectivity issues. -->

<!--! Knowledge Check -->
<!--todo pending: picture... -->
select which wifi attack you can prevent with each security feature:




## Unsupported Setups (Sonos)

These network settings can **break Sonos** or cause **dropouts, missing speakers, or setup failures**.  
If any of these are enabled, **expect problems**.

### **UPnP (Universal Plug and Play)**
Sonos **needs UPnP** to let speakers discover each other and talk on the network.  
If UPnP is off, **devices won’t sync properly**.

### **QoS (Quality of Service)**
QoS tries to “prioritize” traffic but often does a **bad job with real‑time audio**.  
For Sonos, QoS should be **OFF** or it may cause **audio delays and cutouts**.

### **IGMP (Internet Group Management Protocol)**
Sonos relies heavily on **multicast traffic**.
- **IGMP Proxy: OFF** → prevents multicast from being misrouted  
- **IGMP Snooping: ON** → keeps multicast traffic controlled inside the network  
Wrong IGMP settings = **speakers disappear or don’t group correctly**.

### **WiFi Smart Connect**
Smart Connect automatically moves devices between 2.4 GHz and 5 GHz.  
Sonos hates this. It causes **random disconnects**.  
**Turn it OFF.**

### **Airtime Fairness**
Airtime Fairness limits older or slower devices.  
Sonos behaves like a **legacy device** and needs **constant data flow**.  
With Airtime Fairness ON, Sonos gets **throttled** → audio drops.  
**Disable it.**

### **Security & Blocking Features**
Any firewall rule, MAC filter, or “smart security” feature that blocks new devices can **stop Sonos from connecting**.  
If it can block something, **assume it blocks Sonos**—disable it or whitelist Sonos.


*Bottom line:  Sonos works best on a simple, stable network. Fancy router “optimizations” usually make things worse.*
<!--! **Bottom line:**  Sonos works best on a **simple, stable network**. Fancy router “optimizations” usually make things worse. -->



### Activity 
<!--! Sorting Activity -->
- Supported or not 
check file name: "094 offline activity"


