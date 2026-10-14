# Lessons Learned: Cybersecurity Homelab

## Overview

Building this homelab provided practical experience in planning a virtualised corporate network, managing virtual machine storage, organising departmental subnets, and troubleshooting infrastructure issues.

The lab was designed to represent a small organisation with separate IT and Operations networks. Its planned components include Oracle VirtualBox, Windows Server, Windows client machines, Ubuntu Server, Kali Linux, a pfSense firewall, and a router.

The most valuable lessons came from resolving storage limitations and working through the network organisation and subnetting requirements. These experiences reinforced that a successful lab depends not only on installing systems, but also on understanding how they are stored, connected, configured, and tested.

## 1. Virtual Machine Storage Troubleshooting

### Challenge

During the initial setup, the available storage at the original virtual machine location was insufficient for the space required by the planned virtual machines. This caused problems while creating and installing the systems and prevented the setup from progressing as expected.

### Investigation

I researched how VirtualBox stores virtual machine files and reviewed the directory in which the existing virtual machines were saved. This helped me understand that the storage location could be changed rather than keeping every virtual machine on the original partition.

### Solution

I created a separate storage partition with sufficient available capacity and configured VirtualBox to use the new location for virtual machine storage. Moving the storage location addressed the space limitation and allowed me to continue with the lab build.

### Lessons learned

- **Plan storage before deployment.** Multiple virtual machines can require substantial disk space, particularly when virtual disks grow dynamically or snapshots are retained.
- **Understand where virtualisation files are stored.** Knowing the location of virtual disks, configuration files, and snapshots makes storage problems easier to diagnose.
- **Address the underlying cause.** Repeatedly retrying an installation would not resolve a lack of disk space; changing the storage arrangement was a more appropriate solution.
- **Allow room for growth.** Future capacity planning should account for operating system updates, logs, snapshots, and additional security tools.



## 2. Network Segmentation and Subnetting

### Challenge

The intended network architecture separated the organisation into two departments: IT and Operations. The challenge was to organise the virtual machines and configure them so that each system belonged to the appropriate logical subnet.

At first, it was not clear how virtual machine grouping, virtual network assignment, and IP addressing worked together. These are related but distinct parts of the setup.

### Investigation

I grouped the virtual machines to make the lab easier to manage, then worked on creating two NAT networks with specified IPV4 address ranges; the Operations and IT subnet arrangements and assigning the relevant machines to their intended networks.

After installing and configuring the systems, I used the `ifconfig` command on Linux machines to inspect their network interfaces and IPv4 addresses. This gave me a way to check whether the addresses were consistent with the intended subnet configuration.

### Solution

I organised the machines by department, configured the intended subnet arrangements, and checked the IPv4 configuration on the relevant Linux systems. This helped me identify whether the machines appeared to have the expected network addresses.

The address check was a useful initial validation step. However, an IP address alone does not prove that two networks are properly isolated. Isolation also depends on the VirtualBox network mode, subnet masks, routing, and firewall rules.

### Lessons learned

- **Grouping is not the same as segmentation.** Organising virtual machines into groups in VirtualBox improves administration, but does not automatically separate their network traffic.
- **Subnetting requires a consistent plan.** Each subnet needs a defined network address, subnet mask or prefix, and suitable host address range.
- **Check the actual interface configuration.** Tools such as `ifconfig` and `ip addr` help verify interface addresses on Linux; `ipconfig` serves a similar purpose on Windows.
- **Consider routing and security together.** Devices on different subnets may still communicate if routing permits it. Firewall rules are needed when communication should be restricted.
- **Validate behaviour, not just configuration.** Successful segmentation should be demonstrated with connectivity tests and firewall-rule checks, not inferred from labels or IP addresses alone.


## 3. Understanding How the Components Work Together

### Challenge and learning

The lab includes several different infrastructure components: a Windows Server, Windows and Linux clients, an Ubuntu server, a firewall, and a router. Each has a different role, and a problem in one area can affect communication elsewhere.

Planning the architecture and referring back to the diagram helped me think about the purpose of each component and the intended traffic path between internal systems and external networks.

### Lessons learned

- A network diagram is useful only when it reflects the configuration that is actually implemented.
- IP addresses, subnet masks, default gateways, DNS settings, and firewall rules all influence connectivity.
- A firewall needs correctly configured interfaces and rules to enforce the intended security boundary.
- Installing Windows Server does not automatically mean that Active Directory, DNS, or DHCP is fully configured; each service must be installed, configured, and tested.
- Troubleshooting is more effective when performed methodically, changing one relevant setting at a time and recording the outcome.



## 4. A More Structured Troubleshooting Approach

These experiences reinforced the value of a repeatable troubleshooting process:

1. **Define the symptom.** Record what failed, the affected system, and any error message.
2. **Check the basics.** Verify available disk space, virtual machine settings, network adapter attachment, and IP configuration as relevant.
3. **Form a hypothesis.** Identify the most likely cause before making changes.
4. **Research and implement a controlled change.** Use reliable documentation and change one relevant setting at a time.
5. **Retest.** Check whether the original problem has been resolved and whether the change caused any unintended effects.
6. **Document the result.** Record the cause, the solution, and evidence that supports the conclusion.

This process makes troubleshooting more repeatable and produces useful evidence for technical documentation and future investigations.


## Conclusion

This homelab taught me that building a virtualised network involves more than installing operating systems. It requires planning, understanding dependencies, checking configurations, and validating that the environment behaves as intended.

The storage issue taught me to investigate how VirtualBox manages its files and to plan capacity before expanding a lab. The subnetting work improved my understanding of IP addressing and the distinction between organising virtual machines and enforcing genuine network separation.

My next focus is to validate the subnet boundaries, configure and test firewall policies, complete the intended server services, and introduce centralised security logging. These improvements will provide stronger technical evidence and help turn the homelab into a more useful environment for practising network security and SOC-related investigations.


