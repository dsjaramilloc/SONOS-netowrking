

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

# Activity
<!--! Knowledge Check -->
select which wifi attack you can prevent with each security feature:
check activity 097



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