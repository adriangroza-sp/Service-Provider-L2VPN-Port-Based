## Port based L2 VPN Point to Point /Pseudowire
Port-based L2VPN service implemented in EVE-NG. Includes topology, configuration, verification and troubleshooting

## Overview
The service extends a customer VLAN across the provider network, allowing geographically separated customer sites to communicate as if they were connected to the same Layer 2 domain.

## Objectives
Design and deploy a point-to-point Layer 2 VPN service across a service provider network.
Provide transparent Ethernet connectivity between geographically separated customer sites.
Implement a pseudowire-based service to emulate a dedicated leased Ethernet circuit.
Transport customer Layer 2 traffic across a shared MPLS backbone while preserving Ethernet frame transparency.
Establish secure and isolated customer connectivity independent of the provider infrastructure.

## Limitations
Port consumption and limited service density. Because a port-based VPWS maps one attachment circuit to one pseudowire, scaling customer services may require additional physical interfaces on both PE and CE devices. VLAN-based services can achieve higher interface utilization by multiplexing multiple services over the same physical port.

## Lab Environment
- EVE-NG

  Lab Components
  -2 Provider Edge devices
  -1 P/Core device 
  -2 Customer Edge devices

## Vendors Used 
-Cisco
-Juniper

## Software Release Version 
-21.3R1.9 Junos
-15.9(3)M9 Cisco

## Topology 
<img width="1626" height="365" alt="Port Based L2 VPN Point to Point" src="https://github.com/user-attachments/assets/5ade0d48-aed7-4a8f-aa7b-9c3df629d84a" />

## Configuration 
The complete configuration for this Port based solution can be found below 

[L2VPN POINT TO POINT FULL CFG.txt](https://github.com/user-attachments/files/29291181/L2VPN.POINT.TO.POINT.FULL.CFG.txt)



## Verification

show mpls interfaces - confirmed MPLS and LDP operation on the core-facing interface (Gi0/1), while the customer-facing interface (Gi0/0) remained a pure attachment circuit.

show mpls forwarding-table - verified transport label forwarding towards the remote PE loopback (3.3.3.3/32) and the presence of the local Layer 2 circuit entry associated with VC ID 4.

show mpls l2transport vc - confirmed the pseudowire was operational with VC ID 4 in an UP state between PE1 and PE2.

show mpls l2transport summary - showed a single active virtual circuit, consistent with a point-to-point VPWS service.

show mpls l2transport binding - verified the correct exchange of local and remote VC labels, Ethernet VC encapsulation, and MTU parameters.





