# Raspberry Pi Router Configuration with OpenWrt

### Project Overview
This project involves configuring a Raspberry Pi to function as a home router using OpenWrt. The setup includes configuring static IP addresses, DNS servers, custom routing rules, and ensuring secure remote access via SSH. This solution provides a reliable and customizable network setup, suitable for small home networks.

### Objectives
- Set up a Raspberry Pi as a router using OpenWrt.
- Configure static IP addresses and DNS for efficient network management.
- Implement security measures for remote access via SSH.
- Ensure automatic reconnection to mobile hotspots after reboots.

### Key Features
- **Customizable Network Settings:** Configure static IPs, DNS, and routing rules.
- **Secure Remote Management:** Access and manage the router remotely using SSH.
- **Auto-Reconnection:** Automatically reconnects to the mobile hotspot after power cycles or reboots.

### Technologies Used
- **OpenWrt**
- **Raspberry Pi**
- **Linux, SSH, TCP/IP, DNS, DHCP**

### Setup Guide
#### 1. Prerequisites
- Raspberry Pi 3 B+ (or compatible model)
- OpenWrt installed on the Raspberry Pi
- Access to a mobile hotspot or home Wi-Fi network
- SSH client for remote management (e.g., PuTTY or terminal)

#### 2. Configuration Steps
1. **Initial Setup:**
   - Install OpenWrt on your Raspberry Pi.
   - Connect to the OpenWrt web interface and set up initial settings (e.g., password).
  
2. **Configure Static IPs and DNS:**
   - Modify `/etc/config/network` to set up static IP addresses.
   - Ensure DNS is properly configured using `/etc/resolv.conf` or OpenWrt settings.
  
3. **Configure Wi-Fi Connection:**
   - Edit `/etc/config/wireless` to automatically connect to your desired Wi-Fi network.
  
4. **Set Up Remote Access via SSH:**
   - Ensure the SSH service is enabled and configured for secure remote management.

#### 3. Code Snippets & Configuration Files
Here are some key configuration examples:

**Sample Network Configuration (`/etc/config/network`):**
```code
config interface 'wwan'
    option proto 'static'
    option ipaddr '192.168.244.50'
    option netmask '255.255.255.0'
    option gateway '192.168.244.1'
    option dns '8.8.8.8 8.8.4.4'
```

**Sample Wireless Configuration to connect to your network (`/etc/config/wireless`): **
```code
config wifi-iface
    option device 'radio0'
    option mode 'sta'
    option ssid 'Your_Hotspot_SSID'
    option encryption 'psk2'
    option key 'Your_Hotspot_Password'
    option network 'wwan'
    option disabled '0'
```

