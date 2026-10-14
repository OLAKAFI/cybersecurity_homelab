# Network Validation Report

## Cybersecurity Homelab --- IPv4 Addressing, Default Gateways, and Subnet Validation

**Project:** Virtualised Corporate Network Homelab\
**Platform:** Oracle VirtualBox\
**Validation focus:** Departmental subnet configuration and IP
addressing\
**Status:** Addressing evidence captured; screenshots available\
**Date tested:** *\[14th October 2026\]*

------------------------------------------------------------------------

## 1. Purpose

This document records the validation of the homelab's network
configuration against the project objective of separating the simulated
company environment into two departmental networks: **Operations** and
**IT**.

The IPv4 address and default gateway information collected from the
machines, together with the supporting screenshots, provides evidence
that the machines were configured in line with the intended subnet
layout.


## 2. Network Segmentation Objectives

The network was designed to organise the lab into two logical
departmental subnets:

-   **Operations subnet:** Workstations representing the Operations
    department, including the relevant user endpoints. This include 
	the HR Window PC, Audit Window PC, Sales Window PC and Windows Server.
	The Operation subnet is configured with IPv4 addresses within the **10.0.2.0/24 range**.
 
-   **IT subnet:** IT-related systems and security-testing resources,
    including the Ubuntu Server, Parrot Security and Kali Linux machine.
    The IT subnet is configured with IPv4 addresses within the **10.0.3.0/27 range**.

The purpose of this separation was to organise devices by their intended
role and establish a foundation for applying different network access
and security policies.



## 3. Validation Method

The following process was used to review the network configuration:

1.  Checked each relevant machine's network configuration and recorded
    its IPv4 address and default gateway.
2.  Compared the observed addressing information with the intended
    departmental subnet layout.
3.  Used the available screenshots as supporting evidence of the machine
    configurations.
4.  Reviewed whether each machine's address and gateway were consistent
    with the subnet to which it was intended to belong.

On Linux systems, `ifconfig` was used to inspect
interface addressing. The default route can be checked with `ip route`.
On Windows systems, `ipconfig` was used to review IPv4 addresses,
subnet masks, and default gateways.


## 4. Addressing and Subnet Evidence

The table below are the actual values recorded in the lab.

 ----------------------------------------------------------------------------
  | Department / subnet | Machine | IPv4 address | Subnet mask / prefix | Default gateway | Result |
|---|---|---|---|---|---|
| IT | Ubuntu Server | 10.0.3.6 | 255.255.255.0 (/27) | 10.0.3.1 | Consistent with intended subnet |
| IT | Kali Linux | 10.0.3.7 | 255.255.255.0 (/27) | 10.0.3.1 | Consistent with intended subnet |
| IT | Parrot Machine | 10.0.3.9 | 255.255.255.0 (/27) | 10.0.3.1 | Consistent with intended subnet |
| Operations | Sales Windows PC | 10.0.2.3 | 255.255.255.0 (/24) | 10.0.2.1 | Consistent with intended subnet |
| Operations | Audit Windows PC | 10.0.2.5 | 255.255.255.0 (/24) | 10.0.2.1 | Consistent with intended subnet |
| Operations | HR Windows PC | 10.0.2.15 | 255.255.255.0 (/24) | 10.0.2.1 | Consistent with intended subnet |
| Operations | Windows Server (Domain Controller) | 10.0.2.4 | 255.255.255.0 (/24) | 10.0.2.1 | Consistent with intended subnet |
  ---------------------------------------------------------------------------



## 5. Screenshot Evidence

The screenshots captured during implementation support the addressing
and subnet validation recorded in this report. 

Suggested repository structure:

``` text
cybersecurity-homelab/
├── README.md
├── diagrams/
│   └── network-architecture.png
└── evidence/
    └── IT subnet/
		├── kalimachine-ip-configuration.png
		├── parrotmachine-ip-configuration.png
		└── Ubuntuserver-configuration.png
	└── Operation Subnet/
		├── Auditwindowspc-ip-configuration.png
		├── HRwindowspc-ip-configuration.png
		├── Saleswindowspc-ip-configuration.png
		└── Windowsserver-ip-configuration.png
```

### Evidence 1 --- IT Subnet IP configuration

**File:** `evidence/IT subnet/kalimachine-ip-configuration.png`
**File:** `evidence/IT subnet/parrotmachine-ip-configuration.png`
**File:** `evidence/IT subnet/Ubuntuserver-configuration.png`


**Observation:** *\[The screenshots shows the  Ubuntu Server, Kali Linux, 
and Parrot machines configured with IPv4 addresses in the
10.0.3.0/27 range (10.0.3.6, .7, and .9 respectively), each
with a subnet mask of 255.255.255.0 and default gateway 10.0.3.1.
This confirms the machines are correctly placed within the IT subnet.\]*


### Evidence 2 --- Operations Subnet IP configuration

**File:** `evidence/Operation subnet/Auditwindowspc-ip-configuration.png`
**File:** `evidence/Operation subnet/HRwindowspc-ip-configuration.png`
**File:** `evidence/Operation subnet/Saleswindowspc-ip-configuration.png`
**File:** `evidence/Operation subnet/Windowsserver-ip-configuration.png`


**Observation:** *\[The screenshots shows the Sales Windows PC, Windows Server, Audit Windows PC, and HR Windows
PC configured with IPv4 addresses in the 10.0.2.0/24 range
(10.0.2.3, .4, .5, and .15 respectively), each with a subnet mask of
255.255.255.0 and default gateway 10.0.2.1. This confirms the
machines are correctly placed within the Operations subnet.\]*




## 6. Results and Interpretation

Based on the IPv4 address and default gateway information collected, and
the supporting screenshots available, the machines' addressing
configuration was reviewed against the intended IT and Operations subnet
layout.

The captured evidence supports the conclusion that the addressing
configuration was consistent with the project's subnetting objectives
for the machines shown. The actual IP addresses, subnet masks/prefixes,
and gateway values is listed in Section 4 so that another person
can independently review this conclusion.



## 8. Conclusion

The homelab's network configuration was reviewed using the IPv4 address
and default gateway information collected from the machines, supported
by screenshots captured during implementation. This provided practical
evidence for assessing whether the machines were addressed in line with
the intended separation between the IT and Operations subnets.

The exercise strengthened my understanding of IP addressing, default
gateways, subnet planning, and configuration verification in a
virtualised environment. It also reinforced the importance of supporting
network design decisions with observable evidence rather than relying on
the diagram or virtual machine grouping alone.



------------------------------------------------------------------------

## Portfolio publication checklist

Before publishing this file:

-   [ ] Replace all placeholders with the actual IP addresses, subnet
    masks/prefixes, gateway values, and observations.
-   [ ] Confirm the machine names and departmental assignments match the
    final architecture.
-   [ ] Add the actual screenshots to the repository and correct the
    evidence paths.
-   [ ] Remove or redact usernames, hostnames, public IP addresses, MAC
    addresses, or other details you do not want to disclose.
-   [ ] Distinguish clearly between tests completed and tests planned.
-   [ ] Update the status and date to reflect the actual validation
    performed.
