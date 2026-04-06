# Dynamic Routing Lab (OSPF)

## Overview  
This project consists of a dynamic routing lab implemented in GNS3, developed as part of the Network Administration course unit in the MSc in Network and Information Systems Engineering.

The lab focuses on the configuration and analysis of OSPF in a multi-area and multi-AS environment, including route redistribution, LSA analysis, and convergence behavior.


## Objectives  
- Configure OSPF in a multi-area topology  
- Implement inter-area routing using a backbone area (area 0)  
- Configure multiple OSPF processes on a single router (R2)  
- Perform route redistribution between autonomous systems  
- Apply route summarization for redistribution purposes  
- Analyze OSPF adjacencies and database exchange (LSDB)  
- Study LSA types and their role in network topology representation  
- Evaluate OSPF convergence and failure scenarios  


## Technologies Used  
- GNS3 (with GNS3 VM)  
- Cisco IOS (7200)  
- VPCS (Virtual PCs)  
- Wireshark  
- traceroute  
- VMware Workstation  


## Topology  
The lab topology consists of:

- 9 Cisco routers (c7200):
  - R1 to R9  

- 2 end devices:
  - PC1 (VPCS)  
  - PC2 (VPCS)  

- Autonomous Systems:
  - **AS1**: R1–R2  
  - **AS2**: R2–R9  

- OSPF Areas:
  - Area 0 (backbone): R1, R2, R3, R4, R5, R6  
  - Area 1: R6, R7, R9  
  - Area 2: R6, R8, R9  

- Key network segments:
  - 192.168.1.0/25  
  - 192.168.1.128/26  
  - 192.168.1.192/26  
  - 192.168.50.0/24  
  - 192.168.100.0/24 (multi-access network with DR/BDR election)  
  - 172.20.1.0/24  
  - 172.16.1.0/24  
  - 172.18.1.0/24  
  - 172.17.0.0/16  

- 1 serial link:
  - Between R6 and R8  

The topology includes a shared Ethernet segment (192.168.100.0/24) to simulate a broadcast network and enable DR/BDR election.


## Key Requirements  
- OSPF must be configured in all routers  

- Router IDs:
  - AS1: 1.0.0.n  
  - AS2: 2.0.0.n  

- R2 must:
  - Run two OSPF processes  
  - Redistribute routes between AS1 and AS2  
  - Apply metric 100 to redistributed routes  

- Route summarization:
  - Networks 192.168.1.x must be summarized for redistribution  

- Passive interfaces:
  - Interfaces connected to end devices must not send OSPF updates  

- OSPF cost:
  - Automatically calculated  
  - Reference bandwidth adjusted so FastEthernet = cost 10  

- Serial link:
  - R6–R8 uses synchronous serial interfaces  


## Main Tasks  

1. **OSPF Adjacency and Database Exchange**  
   - Capture OSPF packets between R2 and R3  
   - Analyze:
     - Database Description packets  
     - Link State Request packets  
   - Study adjacency states (LOADING → FULL)  

2. **LSDB Analysis**  
   - Inspect OSPF database using CLI  
   - Identify links advertised by routers in different areas  
   - Understand relationship between topology and LSAs  

3. **Failure and Convergence Analysis**  
   - Simulate router failures (R7, R9)  
   - Observe:
     - Neighbor state changes  
     - LSA propagation  
     - Network reconvergence  

4. **LSA Analysis**  
   - Capture LS Update packets  
   - Identify LSA types:
     - Router LSA  
     - Network LSA  
     - Summary LSA (if applicable)  
   - Analyze:
     - Link State ID  
     - Advertising Router  
     - Link descriptions  

5. **DR/BDR Election**  
   - Analyze multi-access network (192.168.100.0/24)  
   - Identify:
     - Designated Router  
     - Backup Designated Router  
   - Verify Network LSA generation  

6. **Routing Behavior and Path Analysis**  
   - Perform traceroute between PC1 and PC2  
   - Modify topology (link failures)  
   - Analyze path selection and OSPF limitations  

7. **Traffic Analysis**  
   - Capture ICMP traffic  
   - Compare request and reply paths  
   - Evaluate asymmetric routing scenarios  


## Skills Demonstrated  
- OSPF configuration (multi-area and multi-process)  
- Route redistribution between autonomous systems  
- Network design with hierarchical routing  
- OSPF troubleshooting and adjacency analysis  
- LSA interpretation and LSDB analysis  
- Failure simulation and convergence evaluation  
- Packet capture and protocol analysis  


## Repository Structure  
- `configs/` — router configuration commands  
- `lab/` — GNS3 project files  
- `results/` — answers, captures, and analysis  
- `topology/` — topology diagram  