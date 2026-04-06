# Static Routing Lab

## Overview
This project consists of a static routing lab implemented in GNS3, developed as part of the Network Administration course unit in the MSc in Network and Information Systems Engineering.

The lab focuses on the configuration and analysis of static routing in a multi-network environment composed of Linux hosts, a Linux-based router, and Cisco routers. It also includes failure simulation and packet-level analysis.


## Objectives
- Configure static routing across multiple subnets
- Implement routing between Linux and Cisco devices
- Validate connectivity using traceroute
- Analyze routing behavior under different configurations
- Evaluate the impact of a router failure scenario
- Understand limitations of static routing and motivation for dynamic routing


## Topology
The lab topology consists of:

- 2 Linux hosts:
    - Term1 (single interface)
    - Term2 (dual-homed, no IP forwarding)
- 1 Linux router:
    - RLin (3 interfaces, IP forwarding enabled)
- 2 Cisco routers:
    - RCis1
    - RCis2
- 3 LAN segments:
    - 170.2.0.0/16
    - 192.180.30.0/24
    - 192.180.40.0/24
- 1 point-to-point link:
    - 195.70.40.24/30 between RCis1 and RCis2

The topology is implemented using Ethernet switches in GNS3 to correctly model shared network segments.


## Key Requirements
- All routing is performed using static routes
- Term2 does not perform routing, despite having two interfaces
- RLin acts as a router (IP forwarding enabled)
- No default routes configured on:
    - RLin
    - RCis2
- Specific routing requirements:
    - RCis1: route to 192.180.40.0/24 via RCis2
    - RCis2: route to 170.2.0.0/16 via RCis1
    - Term1:
        - default route via RLin
        - route to 192.180.40.0/24 via RCis1
    - Term2:
        - default route via RCis2
- RCis1 is later shut down to simulate a failure scenario


## Main Tasks
1. Connectivity Analysis
    - Perform traceroute between nodes under different routing configurations
    - Compare behavior:
        - With missing routes
        - With correct static routes
        - With alternative routing paths
    - Simulate failure by disabling RCis1 and analyze impact

2. Routing Behavior Analysis
    - Evaluate how static routing behaves under topology changes
    - Identify limitations of static routing
    - Justify scenarios where dynamic routing would be advantageous

3. ARP Analysis
    - Capture ARP and ICMP traffic using Wireshark/tcpdump
    - Analyze:
        - ARP requests and replies
        - Timeouts and retransmissions
        - Relationship between ARP and IP communication

4. Traffic Capture and Filtering
    - Capture TCP traffic with specific characteristics:
        - PUSH flag enabled
        - Packet size < 128 bytes
    - Use:
        - tcpdump (CLI filtering)
        - Wireshark (display filters)
    - Establish SSH communication between Term1 and Term2 for traffic generation


## Technologies/Tools Used
- GNS3 (with GNS3 VM)
- VMware Workstation
- Alpine Linux (hosts and Linux router)
- Cisco IOS (7200)
- Wireshark
- tcpdump
- traceroute


## Skills Demonstrated
- Static routing configuration (Linux & Cisco)
- Multi-subnet network design
- Network troubleshooting and path analysis
- Failure simulation and impact analysis
- ARP protocol analysis
- Packet capture and filtering
- Understanding of forwarding vs routing behavior

## Repository Structure
- `configs/` — base configuration commands used in the lab
- `lab/` — GNS3 project files
- `results/` — answers, outputs, and supporting material
- `topology/` — topology diagram


