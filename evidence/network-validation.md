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
-   **IT subnet:** IT-related systems and security-testing resources,
    including the Ubuntu Server, Parrot Security and Kali Linux machine.

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

  ---------------------------------------------------------------------------
  Department / Machine       IPv4        Subnet mask Default     Result
  subnet                     address     / prefix    gateway     
  ------------ ------------- ----------- ----------- ----------- ------------
Operations   Sales Windows *\[Enter    *\[Enter    *\[Enter    Consistent
               PC            observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review

  Operations   Audit Windows *\[Enter    *\[Enter    *\[Enter    Consistent
               PC            observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review

  Operations   HR Windows PC *\[Enter    *\[Enter    *\[Enter    Consistent
                             observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review

  Operations   Operations    *\[Enter    *\[Enter    *\[Enter    Consistent
               workstation   observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review

  IT           Windows       *\[Enter    *\[Enter    *\[Enter    Consistent
               Server        observed    observed    observed    with
               (Domain       value\]*    value\]*    value\]*    intended
               Controller)                                       subnet /
                                                                 Review

  IT           Ubuntu Server *\[Enter    *\[Enter    *\[Enter    Consistent
                             observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review

  IT           Kali Linux    *\[Enter    *\[Enter    *\[Enter    Consistent
                             observed    observed    observed    with
                             value\]*    value\]*    value\]*    intended
                                                                 subnet /
                                                                 Review
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
    └── network-validation/
        ├── operations-ip-configuration.png
        ├── it-ip-configuration.png
        └── gateway-configuration.png
```

### Evidence 1 --- Operations subnet

**File:** `evidence/network-validation/operations-ip-configuration.png`

**What it demonstrates:** The observed IPv4 configuration for the
Operations machines. The displayed address and subnet information should
be consistent with the intended Operations subnet.

**Observation:** *\[Add a short note describing what the screenshot
proves.\]*

### Evidence 2 --- IT subnet

**File:** `evidence/network-validation/it-ip-configuration.png`

**What it demonstrates:** The observed IPv4 configuration for the IT
machines. The displayed address and subnet information should be
consistent with the intended IT subnet.

**Observation:** *\[Add a short note describing what the screenshot
proves.\]*

### Evidence 3 --- Default gateway configuration

**File:** `evidence/network-validation/gateway-configuration.png`

**What it demonstrates:** The default gateway configured on the relevant
machine interfaces, where a gateway is required by the design.

**Observation:** *\[Add a short note describing what the screenshot
proves.\]*

If the evidence is split across more screenshots, add a subsection for
each image and identify the machine, interface, and configuration being
demonstrated. Ensure that screenshot filenames and repository paths
match exactly.

## 6. Results and Interpretation

Based on the IPv4 address and default gateway information collected, and
the supporting screenshots available, the machines' addressing
configuration was reviewed against the intended IT and Operations subnet
layout.

The captured evidence supports the conclusion that the addressing
configuration was consistent with the project's subnetting objectives
for the machines shown. The actual IP addresses, subnet masks/prefixes,
and gateway values should be listed in Section 4 so that another person
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
