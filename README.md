# SOHO-Network-Design
  Goal: Design and configure a realistic SOHO network for a small business (e.g. a consulting firm with around 20 users) that demonstrates CCNA-level networking concepts.

  Deliverables:
    Network Topology (Logical & Physical)
    Device Configurations (routers, switches, APs, PCs, servers)
    Documentation (Ip Addressing plan, VLAN map, routing tables, security config)

# Hardware & Logical Components
  - 1 router (edge device connecting to an ISP)
  - 2 switches
  - 1 wireless router or a WLC + AP
  - 4-6 PCs / Laptops (users in different departments)
  - 1 printer (networked)
  - 2 servers
    - Web/Email/DNS/DHCP Server
    - File/Backup Server
  - 4-6 VoIP phones

# Network Design & Addressing Requirements
  - IPv4 Addressing
    - Use private addressing (e.g. 192.168.10.0/24)
    - Subnet for 3 departments:
      - Management
      - Sales
      - IT
    - Include a server VLAN and a wireless VLAN
    - Use VLSM for efficient subnetting
  - IPv6 Addressing
    - Dual-stack configuration (IPv4 & IPv6)
    - Use global unicast addresses (e.g. 2001:DB8:ACAD::/64)
    - Configure static routes or use dynamic routing with IPv6
   

# Layer 2 Requirements
  - VLANs:
    - Minimum 4 VLANs: Management, IT, Sales, Server
    - VLAN 99 = Native VLAN
  - Trunking:
    - Configure trunk links between switches
    - Use 802.1Q encapsulation
  - Inter-VLAN Routing:
    - Utilize ROAS or Layer 3 switch configuration
  - Port Security:
    - Restrict MAC addresses on access ports
    - Enable Sticky MAC and violation modes
  - STP:
    - Configure STP (PVST+ or RSTP)
    - Make one switch the root bridge
   
  
# Layer 3 Requirements
- Static Routing:
  - Between internal VLAN networks
  - Default route to ISP
- Dynamic Routing:
  - Implement a routing protocol (OSPF, EIGRP, or RIPv2)
  - Include IPv6 routing (OSPFv3)
- NAT/PAT
  - Configure NAT Overload for internet access
- DHCP:
  - Centralized DHCP server or DHCP pools on router
  - Exclude static IPs for servers and network devices
 

# Wireless Requirments
- Configure a wireless network for mobile users:
  - SSID = SOHO_WIFI
  - WPA2 Personal (PSK)
  - Assign to Wireless VLAN
- Configure multiple SSIDs for Guest and Internal users


# Security Requirements
- Device Hardening:
  - Configure enable secret, console, and VTY passwords
  - Encrypt all passwords
  - Set a login banner (legal warning)
- ACLs (Access Control Lists)
  - Standard ACL to restrict acces to router management
  - Extended ACL to limit traffic between VLANs
- Port Secuirty: (Already Mentioned)
- SSH:
  - Enable remote management using SSH
  - Disable Telnet
- Firewall (optional):
  - Implement basic ACLs to simulate firewall behavior between LAN and WAN

# IP Services Requirements
- DHCP
  - Router or server assigns IP per VLAN
- DNS
  - Internal DNS server for local name resolution
- NTP
  - Configure router/switches to sync time with NTP server
- Syslog
  - Configure logging to a central Syslog server
- SNMP
  - Enable SNMP for network monitoring
- Static + Dynamic NAT / PAT
- QoS:
  - Prioritize VoIP or video traffic

# Network Management & Verification
- Backup Configs
  - Save starup-configs to TFTP Server
- Ping and Tracert tests
- Show commands for each device:
  - show ip route
  - show vlan
  - show interfaces trunk
  - show spanning-tree
- Documentation:
  - Network topology diagram
  - IP addressing table
  - VLAN map
  - ACL design

# Stretch Enhancements (11/3/2025)
- Implement HSRP with an expansion of a second router on the network
- Configure VPAN (Site-to-site or remote access) to simulate branch connectivity
- Add a Guest Wireless VLAN isolated from internal LAN'
- Simulate ISP connection using a second router as the ISP gateway
