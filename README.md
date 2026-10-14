# Cybersecurity Homelab: Virtualised Corporate Network, Subnetting and Security Infrastructure
### cybersecurity_homelab
A virtualised corporate network homelab built with VirtualBox, Windows Server, Ubuntu, Kali Linux, and pfSense, focusing on departmental subnetting, IP address validation, infrastructure configuration, and troubleshooting.


# 1. Project Overview
This project involved building a virtualised corporate network homelab using Oracle VirtualBox to simulate the IT infrastructure of a small organisation. The environment was designed around two departments, IT and Operations, with separate subnets to support logical network segmentation.
The lab includes Windows client machines, a Windows Server, an Ubuntu Server, a Kali Linux machine, a pfSense firewall, a network switch, and a router representing the connection to the internet.
The primary focus was to understand how virtualised systems are deployed, how network devices communicate, and how subnetting can be used to organise departmental networks. Throughout the project, I also developed practical troubleshooting skills by resolving storage limitations and validating the IP addressing of machines within their intended subnets.
Rather than focusing solely on installing operating systems, I approached the project as an opportunity to understand the relationships between network infrastructure, system administration, and cybersecurity.



# 2. Project Objectives
The main objectives of this project were to:

- *PBuild a virtualised corporate network using Oracle VirtualBox.*
-	*Simulate an organisation with separate IT and Operations departments.*
- *Implement subnetting to organise the departmental networks.*
- *Deploy Windows Server as the intended platform for Active Directory, DNS, and DHCP services.*
- *Set up an Ubuntu Server to represent a Linux-based server environment.*
- *Include a pfSense firewall and router in the network architecture.*
- *Configure virtual machines and verify their IP addresses against the intended subnet assignments.*
- *Troubleshoot virtual machine storage and network configuration challenges.*
- *Develop practical skills relevant to network administration, infrastructure security, and entry-level SOC Analyst responsibilities.*



# 3. Network Architecture
The network was designed to represent a small corporate environment in which client devices and servers communicate through a virtualised network infrastructure.

### Core Components                              Component	Purpose
Oracle VirtualBox	                               Hosts and manages the virtual machines.
Windows Server	                                 Intended to provide Active Directory, DNS, and DHCP services.
Ubuntu Server	                                   Provides a Linux-based server environment for applications and other services.
Windows Client Machines	                         Represent departmental workstations, including Sales, Audit, and HR.
Kali Linux	                                     Provides a platform for authorised security testing within the lab.
Network Switch	                                 Represents the internal network connectivity between systems.
pfSense Firewall	                               Provides the intended network security boundary and traffic filtering.
Router	                                         Represents the connection between the firewall and the external network.
Operations Subnet	                               Groups the client systems assigned to the Operations department.
IT Subnet	                                       Provides a separate logical network for IT-related systems.


### Network Design
The architecture follows this general traffic path:

*Client Devices* → *Internal Network Switch* → *pfSense Firewall* → *Router* → *Internet*

The Operations and IT departments were organised into separate subnets to support logical network separation.
The Windows Server and Ubuntu Server provide the server infrastructure within the environment, while the Windows clients represent end-user systems. Kali Linux is included for controlled security testing.
The firewall is positioned between the internal network and the external connection to represent a security boundary. Actual traffic control depends on the configured firewall interfaces, routing, and rules.

### Important distinction: 
Grouping virtual machines in VirtualBox helps with organisation, but subnet separation is established through the virtual network configuration and IP addressing. Communication between subnets is also influenced by routing and firewall policies.



# 4. Implementation Process
## Step 1: Planning the Environment
I began by identifying the required virtual machines and network components based on the intended corporate architecture.
I planned the environment around two departments, IT and Operations, and identified the servers, client devices, firewall, and router required to represent the network.
This provided a clear structure for deploying the systems and configuring the network.

## Step 2: Creating Virtual Machines in VirtualBox
I created the virtual machines using Oracle VirtualBox and prepared them for the installation of their respective operating systems.
During this stage, I encountered storage limitations that affected the creation and installation of some virtual machines. I investigated how VirtualBox stores virtual machine files and addressed the issue by creating a separate storage partition and changing the virtual machine storage location.
This allowed me to continue the deployment without being restricted by the available space in the original storage location.

## Step 3: Installing and Preparing the Systems
I installed and prepared the operating systems required for the environment, including Windows Server, Windows client systems, Ubuntu Server, and Kali Linux.
Each system was assigned a role within the simulated network. The Windows Server was intended for centralised identity and network services, while Ubuntu Server provided a Linux-based server platform.
The Windows clients represented departmental workstations, and Kali Linux provided a platform for security testing.

## Step 4: Organising the Departmental Subnets
I organised the virtual machines according to their intended departmental roles and worked on configuring the Operations and IT subnets.
This involved grouping the machines for easier management, creating the intended subnet arrangements, and associating the relevant machines with their appropriate virtual networks.
The process helped me understand the difference between organising virtual machines within VirtualBox and configuring the actual network settings that determine how devices communicate.

## Step 5: Validating Subnet Assignments
Subnet validation formed part of the project implementation.
After configuring the network assignments, I used the ifconfig command on the relevant Linux machines to inspect their network interfaces and IPv4 addresses.
I checked the resulting addresses against the intended subnet assignments to confirm whether the machines were configured for their designated networks.
This validation was important because the correct subnet assignment could not be established simply by looking at how the machines were grouped in VirtualBox.
The checks helped me verify the IP addressing configuration and reinforced the importance of validating network settings after making configuration changes.

## Step 6: Incorporating the Security Infrastructure
The architecture also included pfSense and a router to represent the security boundary and external connectivity.
The intended arrangement places the firewall between the internal network and the router. This provides a basis for understanding how network traffic can be controlled and how security policies can be applied to internal and external communications.
The inclusion of these components helped me relate subnetting and network design to broader cybersecurity principles, particularly traffic filtering and network access control.



# 5. Challenges Encountered and Solutions

## Challenge 1: Insufficient Storage for Virtual Machines
### Problem
During the initial setup, I encountered storage limitations when creating and installing virtual machines. The available space in the original storage location was insufficient for the requirements of the lab.

### Solution
I researched how VirtualBox stores virtual machine files and located the directory where the virtual machines were being saved. I then created a separate storage partition with sufficient available capacity and changed the virtual machine storage location to the new partition.
This resolved the storage constraint and allowed me to continue setting up the environment.

### Key lesson
Virtualisation requires careful resource planning. Storage allocation and the location of virtual machine files can affect the successful deployment of multiple systems.

## Challenge 2: Network Segmentation and Subnetting
### Problem
The lab required the organisation to be divided into IT and Operations, with each department assigned to its intended subnet. I initially encountered difficulties organising the virtual machines and applying the appropriate network configuration.

### Solution
I approached the problem by organising the virtual machines according to their intended roles, configuring the Operations and IT subnet arrangements, and assigning the relevant machines to the appropriate virtual networks.
I then used ifconfig to inspect the IPv4 addresses of the relevant Linux machines and checked the addresses against the intended subnet configuration.
This process helped me verify the subnet assignments and develop a clearer understanding of the relationship between IP addressing and virtual network configuration.

### Key lesson
Subnetting requires more than grouping devices by department. The virtual network assignment, IP address, subnet mask, and routing configuration determine how systems communicate.
Verifying the resulting IP addresses was therefore an important part of the implementation process.



# 6. Skills Developed
This project provided practical experience in the following areas:
- **Virtualisation:** Creating and managing virtual machines in Oracle VirtualBox.
-	**Storage management:** Troubleshooting disk-space limitations and relocating virtual machine storage.
- **Networking fundamentals:** Working with IPv4 addressing, network interfaces, and subnetting.
- **Network segmentation:** Organising devices into separate departmental subnets.
- **Subnet validation:** Using ifconfig to inspect IP addresses and verify intended network assignments.
-	**Windows infrastructure:** Understanding the intended role of Windows Server in centralised identity and network services.
-	**Linux administration:** Working with Linux-based systems and command-line network tools.
-	**Network security architecture:** Understanding the roles of firewalls, routers, and network boundaries.
-	**Technical troubleshooting:** Researching issues, applying solutions, and checking the resulting configuration.
-	**Technical documentation:** Recording the architecture, implementation steps, challenges, and lessons learned.



# 7. Lessons Learned
Building this homelab reinforced several important lessons about infrastructure and cybersecurity.
Storage planning is essential. Running multiple virtual machines requires sufficient disk space and an understanding of where virtual machine files are stored. Resolving the storage issue taught me to investigate the underlying configuration rather than repeatedly attempting installations without addressing the cause.
Network segmentation must be configured and verified. Separating IT and Operations required me to consider virtual network assignments and IP addressing. I learned that grouping machines in a virtualisation platform does not, by itself, isolate their network traffic.
Configuration should always be validated. Using ifconfig to inspect IPv4 addresses helped me check whether the relevant machines were configured for their intended subnets. This reinforced the importance of verifying the actual system configuration rather than assuming that a change has worked.
Troubleshooting is an important technical skill. Both challenges required research, a structured approach to identifying the problem, and practical changes to the environment. These experiences helped me become more methodical when investigating technical issues.
Infrastructure design and cybersecurity are closely connected. Network structure, identity management, and firewall placement all influence how an organisation controls access to its systems and data. Understanding these relationships provides a useful foundation for practical cybersecurity work.



# 8. Project Outcome
The project established a virtualised corporate network environment with an architecture organised around IT and Operations, alongside Windows and Linux systems and the intended firewall and router components.
The storage limitation was addressed by relocating virtual machine storage to a separate partition. The departmental subnet configuration was also undertaken and validated by inspecting the IPv4 addresses of the relevant Linux machines using ifconfig.
The experience strengthened my practical understanding of virtualisation, network organisation, subnetting, IP address verification, and technical troubleshooting.
For me, the main value of this project was not simply getting the systems installed. It was learning how to investigate problems, understand the configuration behind them, apply solutions, and verify the results.
This homelab represents a practical step in my cybersecurity learning journey, providing hands-on experience with concepts relevant to network security, infrastructure administration, and SOC Analyst development.



# 9. Project Evidence
The project can be supported with the following evidence:
- Network architecture diagram showing the virtual machines, departmental subnets, firewall, router, and intended internet connection.
- Screenshots of the VirtualBox environment showing the created virtual machines.
- Screenshots of Linux network interfaces and IPv4 addresses used during subnet validation.
- Evidence of the separate storage partition and the updated virtual machine storage location.
- Relevant configuration screenshots demonstrating the departmental network assignments.

_________________________________________________________________________________________________________________________________

#### Project type: Cybersecurity Homelab / Virtualised Network Infrastructure
#### Technologies: Oracle VirtualBox, Windows Server, Windows client operating systems, Ubuntu Server, Kali Linux, pfSense
Core areas: Virtualisation, IPv4 addressing, subnetting, network segmentation, infrastructure troubleshooting, and security architecture

