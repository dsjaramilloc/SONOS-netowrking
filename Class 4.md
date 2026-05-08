

# Class 05.1- Number Systems  Comparing the Subnet Mask (how a router works)


## Private Address Range

**Private address ranges** are IP addresses reserved for use **inside local networks**. They are not **routable on the internet** and are reused across many networks.

| Network Address and Prefix | RFC 1918 Private Address Range |
|----------------------------|--------------------------------|
| 10.0.0.0/8                 | 10.0.0.0 - 10.255.255.255      |
| 172.16.0.0/12              | 172.16.0.0 - 172.31.255.255    |
| 192.168.0.0/16             | 192.168.0.0 - 192.168.255.255  |

*ALERT: SONOS devices connect ONLY to Private Address Range networks* 
<!--! ALERT: SONOS devices connect ONLY to Private Address Range networks -->


## IP address network and host portion

### Comparing the Subnet Mask and Prefix Length
```
| Subnet Mask     | 32-bit Address                      | Prefix Length |
|-----------------|-------------------------------------|---------------|
| 255.0.0.0       | 11111111.00000000.00000000.00000000 | /8            |
| 255.255.0.0     | 11111111.11111111.00000000.00000000 | /16           |
| 255.255.255.0   | 11111111.11111111.11111111.00000000 | /24           |
| 255.255.255.128 | 11111111.11111111.11111111.10000000 | /25           |
| 255.255.255.192 | 11111111.11111111.11111111.11000000 | /26           |
| 255.255.255.224 | 11111111.11111111.11111111.11100000 | /27           |
| 255.255.255.240 | 11111111.11111111.11111111.11110000 | /28           |
| 255.255.255.248 | 11111111.11111111.11111111.11111000 | /29           |
| 255.255.255.252 | 11111111.11111111.11111111.11111100 | /30           |
```

### IPv4 addresses 

>  Example 
192.168.2.38/24
|                   |                             |                               |
| ----------------- | --------------------------- | ----------------------------- |
| Network address   | 192.168.2.0                 | reserved                      |
| Broadcast Address | 192.168.2.255               | reserved                      |
| First usable host | 192.168.2.1                 | usually Default-gateway       |
| Last usable host  | 192.168.2.254               | usually the SVI               |
| subnetmask        | 255.255.255.0               |                               |
| usable range      | 192.168.2.1 - 192.168.2.254 | Ip that i can assign to hosts |


### Differentiating networks
By comparing each device’s IP address using an IP calculator, you can accurately determine whether the devices can communicate directly on the same subnet. This avoids confusion caused by network and broadcast addresses. **Here are the simple steps:**

1. Open https://www.calculator.net/ip-subnet-calculator.html and enter the IP address and subnet mask for the first device, then click Calculate.
2. Note the Usable Host IP Range shown in the results.
3. Repeat the calculation for the second IP address using its subnet mask.
4. Compare the Usable Host IP Ranges:
If both IPs fall within the same range → same network
If not → different networks

*Differentiating networks is especially useful in double NAT situations—keep in mind that Sonos devices don’t support double NAT (we’ll cover this later)*
<!--! NOTE: Differentiating networks is especially useful in double NAT situations—keep in mind that Sonos devices don’t support double NAT (we’ll cover this later). -->


### Activity: multiple choice questions

check files:
- 056 Activity numersystems practice.md
- 059 questions quiz
- 

# Class 05.1 Routing Concepts

```
                                          ISP
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
```

### Routers Segment Broadcast Domains
Here’s the blunt truth: broadcasts are noisy and dumb, and if you let them run wild, they’ll wreck network performance. Switches happily flood broadcasts out every port like they don’t care — because they don’t. Routers, on the other hand, actually do their job. **They stop broadcasts cold**. Every router interface creates a **separate broadcast domain**, and broadcasts stay trapped inside it.

* Switches propagate broadcasts out all interfaces except the interface on which it was received. 
* The only device that stops broadcasts is a __router__.
* Routers __do not__ propagate broadcasts. 
* Each router interface connects to a broadcast domain and broadcasts are only propagated within that specific broadcast domain.


* A problem with a large broadcast domain is that these hosts can generate excessive broadcasts and negatively affect the network.
* The solution is to reduce the size of the network to create smaller broadcast domains in a process called subnetting. 
* Dividing the network address 172.16.0.0 /16 into two subnets of 200 users each: 172.16.0.0 /24 and 172.16.1.0 / 24. 
* Broadcasts are only propagated within the smaller broadcast domains when using subnetting. 

### Activity: PT
check files:
055 LAB simple routing lite



**DHCP** Most of the time the devices already have the DHCP **enable**
Discovery (el device pide una ip)
Offer (el dhcp ofrece una ip)
Request (el device acepta la ip)
Acknowledge (el dhcp deja configurada esta ip)


# Class 06.1: DHCP


```
┌───────┐                       ┌────────┐
│ My PC │          ┌──┬─────────┤  DHCP  │
└───────┴──────────┤SW│         │ SERVER │
                   └──┘         └────────┘
```
### Dynamic Host Configuration Protocol (DHCP)

DHCP automatically hands out IP addresses and other network settings to devices on a network, so you don’t have to configure each one by hand. It streamlines setup, saves time, and cuts down on mistakes caused by manual configuration.

*Alert: The DHCP reservation feature must be disabled for Sonos to work properly.*
<!--! Alert: The DHCP reservation feature must be disabled for Sonos to work properly. -->



There are 4 basic steps DHCP follows to assign an IP address to a device: 

- **DHCP Discover (DHCPDISCOVER) CLIENT**
When a device is first connected to a network, it sends out a broadcast message requesting an IP address. This is a DHCP Discovery message.
- **DHCP Offer (DHCPOFFER) SERVER**
When a DHCP server receives a DHCP Discovery message, it responds with a DHCP Offer message. The Offer message contains an available IP address that the server can assign to the device, as well as other network configuration parameters.
- **DHCP Request (DHCPREQUEST) CLIENT**
The requesting device responds to the DHCP Offer message with a DHCP Request message, indicating that it wants to use the IP address offered by the DHCP server.
- **DHCP Acknowledgment (DHCPACK) SERVER**
Last, the server responds with a DHCP Acknowledgement message, indicating that the device can use the assigned IP address and other network configuration parameters.

(DHCP uses port service: UDP numbers 67 server 68 client)


* ## APIPA (Automatic provisioning of IP Address)
* *When DHCP fails: Link-local is assinged*
* APIPA is (169.254.0.1 to 169.254.255.254) having 65,534 usable IP addresses, with the subnet mask of 255.255.0.0.
* An ip address is always used so PCs on same broadcast domain can comunicate 



### PT activity Configure DHCP on a Wireless Router
<!--! Packet tracer ACTIVITY -->
* Check Files:
* 066 Configure DHCP on a Wireless Router
* 067 simple DHCP




# Class 06.2: DNS


Here’s a quick video explaining how DNS works, from the YouTube channel GetDevOpsReady.
https://www.youtube.com/shorts/h03rYRCrgEA



COMMAND: nslookup


#### Knowledge Check

Which TWO options best describe DNS? (Select 2)
- [ ] A. Translates human‑readable domain names into IP addresses
- [ ] B. Assigns IP addresses automatically to devices on a network
- [ ] C. Allows users to access websites using names instead of numbers
- [ ] D. Identifies devices using a physical hardware address
- [ ] E. Provides wireless connectivity between devices
- [ ] F. Maps IP addresses to MAC addresses on a local network
- [ ] G. Routes traffic between different networks


### PT activity Configure 
<!--! Packet tracer ACTIVITY -->
* Check Files:
* 067 simple DNS v2



# DHCP SERVER config 
```.txt
             ┌──────┐
             │Router│
             └───┬──┘
┌──────┐         │
│ DHCP │      ┌──┴─┐
│SERVER├──────┤SW01│
└──────┘      └┬───┤
               │   │
      ┌────┐   │   │  ┌────┐
      │PC01├───┘   └──┤PC02│
      └────┘          └────┘
```

### 1 Configure ip and default gateway under > Desktop > ip configuration (DHCP Server)

### 2 Configure DHCP services 
* Services > DHCP > turn it on > Add a diferrent pool name > click Add > speficy:
    * a. Default Gateway (pool's Default Gateway) ussually .1
    * b. DNS server (8.8.8.8)
    * c. Start IP address: 192.168.10.10 (ussually start at .10)
    * d. Subnet Mask 
    * e. Maximum Number of Users (100)
    * f. WCL address (Wireless Lan Controller ip address) -- Optional (if needed)
    * g. Save
### 3. make sure Default pool is all 0000 (zeros)





    




