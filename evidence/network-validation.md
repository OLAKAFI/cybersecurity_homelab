# Network Validation Report

## Cybersecurity Homelab --- IPv4 Addressing, Default Gateways, and Subnet Validation

**Project:** Virtualised Corporate Network Homelab\
**Platform:** Oracle VirtualBox\
**Validation focus:** Departmental subnet configuration and IP
addressing\
**Status:** Addressing evidence captured; screenshots available\
**Date tested:** *\[Add date\]*

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

This report records the configuration evidence available. It does not,
by itself, claim that inter-subnet firewall enforcement or all routing
paths have been tested; those require separate connectivity and
firewall-rule tests.

## 2. Network Segmentation Objectives

The network was designed to organise the lab into two logical
departmental subnets:

-   **Operations subnet:** Workstations representing the Operations
    department, including the relevant user endpoints.
-   **IT subnet:** IT-related systems and security-testing resources,
    including the relevant servers and Kali Linux machine.

The purpose of this separation was to organise devices by their intended
role and establish a foundation for applying different network access
and security policies.

> **Important:** A device's IPv4 address and default gateway should be
> assessed against the subnet plan. In VirtualBox, grouping virtual
> machines is not sufficient to isolate their traffic; the virtual
> network attachment, subnet configuration, routing, and firewall rules
> determine actual connectivity and isolation.

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

On Linux systems, `ifconfig` or `ip addr` can be used to inspect
interface addressing. The default route can be checked with `ip route`.
On Windows systems, `ipconfig` can be used to review IPv4 addresses,
subnet masks, and default gateways.

## 4. Addressing and Subnet Evidence

Complete the table below with the actual values recorded in the lab. Do
not include credentials, public IP addresses, or other sensitive
information in a public portfolio repository.

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

**Notes for completing the table**

-   Use the actual values shown in your screenshots or console output.
-   If a machine has multiple network interfaces, identify the interface
    relevant to the lab subnet.
-   If a server is intentionally connected to more than one network,
    document each relevant interface separately.
-   If a default gateway is not configured for a particular isolated
    network, record `Not configured` rather than assuming a value.
-   Mark a result as successful only where the observed address, subnet
    mask/prefix, and gateway match the intended design.

## 5. Screenshot Evidence

The screenshots captured during implementation support the addressing
and subnet validation recorded in this report. Add the screenshots to
the repository and update the paths below to match their actual
filenames.

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

Addressing evidence is an important validation step, but it is not the
only test needed to establish effective network segmentation. Two
machines can have addresses in different subnets and still communicate
if routing and firewall policies allow it. Conversely, a missing or
incorrect gateway may prevent traffic from reaching other networks even
when local addressing is correct.

## 7. Recommended Follow-up Tests

The following tests can provide stronger evidence that the intended
segmentation and security controls operate correctly:

-   [ ] **Same-subnet connectivity:** Test expected communication
    between devices in the same subnet.
-   [ ] **Cross-subnet connectivity:** Test whether communication
    between IT and Operations behaves according to the design.
-   [ ] **Gateway reachability:** Where appropriate, test whether each
    machine can reach its configured gateway.
-   [ ] **Routing review:** Check the route table and confirm that
    routes point to the intended next hop.
-   [ ] **Firewall-rule validation:** Confirm that pfSense allows
    required traffic and denies traffic that should be restricted.
-   [ ] **DNS validation:** If DNS is configured, confirm that clients
    resolve the intended hostnames.
-   [ ] **Evidence capture:** Save screenshots or command output showing
    the test, result, and date.

Use only systems and networks within the authorised lab. A failed ping
alone does not prove that a firewall rule is working, because ICMP may
be disabled or another configuration issue may prevent a response.
Validate the relevant rule and test the intended service or protocol as
appropriate.

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

Further connectivity and firewall-rule tests will provide additional
assurance that the separation works as intended at the traffic level.

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
