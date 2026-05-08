


CLASE 1

---------------------------------------------------------------------------
Local Area Network (LAN): Small area, un dueno, se conecta a un ISP dentro del WAN


Wide Area Network (WAN): Large area, the "internet", cuenta con ISP (Internet service providers) within the network

Metropolitan Area Network (MAN):  interconnecting network devices within a metropolitan area like a city


Controller Area Network (CAN): Commonly used in vehicles to enable communication between various electronic control units (ECUs)


Personal Area Network (PAN) *MUY IMPORTANTE*: located within the personal space of an individual, can be used to connect a variety of devices


Wireless Local Area Network (WLAN): Uses wireless communication technologies such as Wi-Fi to connect devices


---------------------------------------------------------------------------

PHYSICAL TOPOLOGIES: Identifies the space where the device is


LOGICAL NETWORK TOPOLOGIES: # that identifies where the devices is within a network

----------------------------------------------------------------------------
END devices: User friendly such as tablet, phone, laptop


Inter/Network devices: Router, access point, wifi extender, modem


Network media type: Ethernet, coarial (metal)/ fibra optica (plastic, glass) and wireless (wifi, radio, bluetooh)

---------------------------------------------------------------------------
Client vs Server

A port is a # of service

--------------------------------------------------------------------------

P2P (PEER-TO-PEER): Two devices that can be connected without using a internet connection


-----------------------------------------------------------------------
MEDIA TYPES:


EMI (Electromagnetic interference): Unwanted noise or disruption in an network

RFI (Radio Frequency Interference): Dealing with high-frequency disturbances


-----------------

Metal wires

-Metal

RJ11 & RJ45 (Ethernet)
Coaxial (TV cable)

-Glass or plastic fiber: it is not affected by EMI or RFI
-Wireless transmission: codigo estandar de producto = 802.11
---
Puedo verlos con windows+cnd+ipconfig y ipconfig/all

MAC ADDRESS (# DE CEDULA DE IDENTIDAD):
-Puedo indentificar la marca del dispositivo
-# unique (first 6 digists) + # specific
-It uses numbers 0-9 and leters A-F (hexadecimal)
-12 characters
-they can divided by dots, dashes, colon points

IP ADDRESS (# DE TELEFONO)
-4  numbers
PRIVATE PREFIXES (used para LAN)
-192.168.0.0/16-192.168.255.255  (las rayas hacen referencia a la cantidad de 1s que encontramos en numeros binarios, se conoce como prefix)
*es importante menionar que la primera ip address nose usa ya que esa es la red itself ni (NETWORKS ADDRESS) ni la ultima porque es el NETWORK BROADCAST, la primera utilizable es usually the default gateway
-10.0.0.0/8-10.255.255.255
-172.16.0.0/12-172.31.255.255
FORMAT= 000.000.000.000
*los numeros pueden llegar hasta 255, los cerosno son necesarios ponerlos*

---
UNICAST: Se manda el mensaje a solo 1 dispositivo

MULTICAST: Se manda el mensaje a ciertos dispositivos
BROADCAST: Se envia el mensaje a todos los dispositivos bajo las misma red




# Class 01.1 types of networks 


## [ ] 1.3. Differentiate between LAN, WAN, MAN, CAN, PAN, and WLAN.


- **LAN: Local Area Network**
A LAN connects devices within a relatively small geographic area, such as a single building or campus. It usually belongs to a single owner.
- **WAN: Wide Area Network**
A WAN, or Wide Area Network, is a type of computer network that spans a large geographic area, such as a city, region, or even multiple countries and are usually managed by one or several Internet Service Providers (ISP). A WAN is typically composed of multiple interconnected LANs.
- **MAN: Metropolitan Area Network**
Metropolitan Area Network is a network used for interconnecting network devices within a metropolitan area like a city, urban area, or rural area.                                       
- **CAN: Controller Area Network**
The Controller Area Network (CAN) is commonly used in vehicles to enable communication between various electronic control units (ECUs), such as engine control, transmission, and safety systems
- **PAN: Personal Area Network**
These networks connect devices that are typically located within the personal space of an individual, such as a room or small area. A PAN is designed for personal use and can be used to connect a variety of devices, including smartphones, tablets, laptops, and wearable devices.
- **WLAN: Wireless Local Area Network**
A Wireless LAN, or WLAN, is a type of local area network that uses wireless communication technologies such as Wi-Fi to connect devices within a relatively small geographic area.

### Activity: simple questions
*check file: "019 questions.md"*
<!--! check file: "019 questions.md" -->

### __SOHO__: Small Office and Home Office Networks
A SOHO (Small Office/Home Office) network typically supports 1 to 10 users and combines both wired and wireless connections. This setup is designed for small businesses or remote professionals.



## Physical topologies
Physical topology describes how devices are physically connected to each other and the network, and how data is transmitted between them.


## Logical network topologies.   
Logical topology refers to the logical or virtual arrangement of devices and how data is transmitted between them. Logical topology describes the configuration of data through the network, and how devices communicate with each other regardless of their physical location or arrangement.


### Devices&Media
<!-- alt+z para ordenar la tabla-->

| End Devices      | Network Devices   | Media                  |
| ---------------- | ----------------- | ---------------------- |
| Desktop Computer | Firewall          | Wireless connectivity  |
| Laptop           | Access Point (AP) | Copper cables          |
| Smartphone       | Switch            | Fiber or plastic cable |
| IP Phone         | Home router       |                        |
| WirelessPrinter  |                   |                        |
| Wireless speaker |                   |                        |


#### Activity:  
Pictionary with Devices&Media




## Class 1.2: Client vs Server
Understanding the difference between a client and a server is critical in network troubleshooting because problems don’t happen “on the network” in general—they happen on one side or the other. A client requests services, a server provides them. If you can’t clearly identify which role is failing, you waste time chasing the wrong issue.

```
             ┌──────────┐
  ┌──────────┤ INTERNET ├───────────┐
  │          └──────────┘           │
┌─┴──┐                           ┌──┴───┐
│ PC │                           │SERVER│
└────┘                           └──────┘
```

**Clients (request services):**
- Web browser (Chrome, Firefox) → requests web pages
- Email app (Outlook, Gmail app) → requests mail from a mail server
- PC connecting to a file share → requests files


**Servers (provide services):**
- Web server → serves websites
- File server (NAS, Windows Server) → stores and serves files
- DHCP server → assigns IP addresses to clients




## Peer-to-peer   
* The simplest P2P network consists of two directly connected computers using either a wired or wireless connection. Both computers are then able to use this simple network to exchange data and services with each other, acting as __either a client or a server as necessary__

    - Printing
    - Bluetooth data transmition

                        
### Activity:  
* *Sorting Activity:  Network Connection Types*
* check file: "017 Sorting Activity.md" 
<!-- check file: "017 Sorting Activity.md"  -->
-----------------------------------