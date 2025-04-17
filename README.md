# WAN Technologies Final Networking Project

## Summary
For our final networking project, my classmates and I worked collaboratively to design this 
fully functional enterprise-level network. This process required significant teamwork and 
planning as we collectively designed the network topology and configurations. 

We worked together to design the network to meet the project’s requirements. Each group  contributed ideas and different aspects of the design. Frequent meetings, shared  documentation,
and hands-on lab sessions allowed us to remain as a team and troubleshoot effectively.

## Network Features

### Port Security In Shutdown Mode
We implemented port security in shutdown violation mode to enhance network security. 
This ensures that if an unauthorized device attempts to connect, the port will be automatically disabled. 

### Cisco Unified Communications Manager
For voice services, we utilized Cisco CUCM to manage VoIP phones across our network 
and outside networks. Call manager handled internal and external communications with 4-
digit and 10-digit numbers along with video calling and caller ID assigned. 

### Windows Server 2019 - Active Directory
We deployed two Windows Server 2019 virtual machines as domain controllers to provide 
redundancy. These servers manage user authentication, Group Policy, DNS, and NTP 
services. 

### EtherChannel For Link Redundancy 
EtherChannel prevents single points of failure and increases bandwidth. This was 
configured on our core and distribution layer switches, allowing multiple physical links to 
bundle into one logical link. 

### VLAN Configuration
* VLAN 99 – Management: 192.168.2.0/27
* VLAN 10 – Data: 192.168.2.32/27
* VLAN 15 – Voice: 192.168.2.64/27
* VLAN 20 – Remote User/DSL: 192.168.2.96/27
* VLAN 25 – Guest: 192.168.2.128/27

### Link Descriptions
Link descriptions enhance clarity of a network. All switch and router interfaces were 
configured with link descriptions to identify the connected device and its purpose. Link 
descriptions are critical for documentation and troubleshooting. 

### Basic Device Security
* **Banner MOTD**: A message of the day (MOTD) banner was added to all routers and 
switches to provide warning notices for unauthorized users.
* **Password Protection**: Console and VTY lines were protected with passwords. 
Password encryption was applied to hide plain-text passwords. Since this was a lab 
exercise, all passwords were simple. It is recommended to use stronger passwords 
than the ones used in this lab. 

### SSH Configuration
SSH was enabled on all routers to allow secure remote access. 
* Domain name and hostname were set.
* Local user account created. 
* Cypto keys generated

## Logical Topologies
Due to the scale and complexity of this network, the logical topology will be split up into 
separate sections based on pod numbers. The full physical topology will be shown after. 
This allows each portion of the network to be more easily understood. This helps ensure 
that each pod’s configuration and function are clearly presented without overwhelming the 
viewer. 

### Pod 2 Overview: IT Closet
Pod 2 will be separated into two parts to maintain visual clarity. The remote user and DSL 
modem will be displayed separately due to its physical and logical separation from the 
main network infrastructure. 

![image](https://github.com/user-attachments/assets/32ca7363-f794-49f1-aac3-184f5116ab7c)

* **HSRP Routers**:  Configured with Hot Standby Router Protocol for gateway 
redundancy. 
* **VLAN Router and DHCP Services**: Acts as the inter-VLAN router and serves as a 
DHCP server.
* **VTP Server Switch**:  Operates as the central VLAN Trunking Protocol server.
* **Access Point**: Offers wireless access to users.

## Pod 2 - Part 2
This section simulates a remote office/teleworker scenario.
![image](https://github.com/user-attachments/assets/0b01fb32-5a6c-4680-ac40-d7392ff432c1)

* **DSL Modem**:  A remote user connecting through a DSL modem, emulating a typical 
home office connection.
* **VoIP Phone**: VoIP Phone registered with Cisco Unified Communications Manager 
providing voice functionality over the WAN link.

### Pod 1 Overview
Pod 1 builds upon the core infrastructure provided by Pod 2. Like Pod 3 and 4, it 
demonstrates the implementation of switch-level redundancy, voice, and server 
functionality. 

![image](https://github.com/user-attachments/assets/8eb250df-8dff-4d82-8a44-b90161e24ba4)

* **Windows Server 2019 - LAB.LOCAL**: A Windows Server 2019 instance is deployed 
in Pod 1, operating under the lab.local domain. This server supports Active  Directory, DNS, NTP, and serves as a secondary domain controller, providing Active 
Directory server redundancy.
* Like other pods, VoIP phones are registered using Cisco CUCM and operate within 
VLAN 15 to ensure proper traƯic prioritization.

### Pod 3 Overview
Pod 3 contains the main domain controller for the LAB.LOCAL domain. 

![image](https://github.com/user-attachments/assets/c0695e8b-ac89-41b6-905c-e1bf1c739670)

### Pod 4 Overview
Pod 4 serves as the central hub for unified communications across the network. This pod 
hosts Cisco Unified Communications Manager.
* Includes registering phones and handling call routing using SCCP. 

![image](https://github.com/user-attachments/assets/c800659b-3f33-4ba7-b8d8-922499aa49a5)

## Full Physical Topology

![image](https://github.com/user-attachments/assets/0e5766e6-7343-4e66-9b75-cecced824960)

## Conclusion
The full configuration files are included in this repo for anyone who wants a deeper look into how this project was built.

This project was a team effort. We spent hours collaborating, whiteboarding, configuring, testing, and troubleshooting this design to a working enterprise-level network. We are not claiming that it is perfect, and we're aware that we still have a lot to learn and do not know all of the answers, but we put in a lot of work and effort. We used real Cisco equipment, getting hands on with routers, switches, servers, and phones. This helped us learn more than we ever could from a textbook.

This past year, I have learned more than I ever thought I could from this program. I'm thankful for my professor, my classmates, and myself for putting in the work to learn. 






