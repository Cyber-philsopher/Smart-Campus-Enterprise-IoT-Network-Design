# Smart-Campus: Enterprise-IoT-Network-Design

## Objective

**Status:** Completed 

This project involves the design and simulation of an enterprise-grade Smart Campus Network using a Hierarchical Star Topology. Moving beyond simple connectivity, the architecture features a Distributed Server Farm that isolates critical services (DNS, DHCP, IoT) from user traffic to ensure high availability.

The system integrates Zonal Wireless Gateways to segment traffic across three distinct operational zones: Academic (Lecture Hall), Environmental (Smart Library), and Administrative (Staff Quarters). A key innovation is the implementation of a local Domain Name System (DNS), abstracting complex IP management into a user-friendly domain `(iotserver.com)` for centralized network control.

## Skills Learned

- Network Architecture Design.
- Core Service Configuration.
- IoT Orchestration & Automation.
- Network Security & Segmentation.

## Tools Used

- <img src="https://img.shields.io/badge/-Cisco%20Packet%20Tracer-1BA0D7?&style=for-the-badge&logo=cisco&logoColor=white" /> For simulation, configuration, and testing. 
- <img src="https://img.shields.io/badge/-Draw.io-F08705?&style=for-the-badge&logo=diagramsdotnet&logoColor=white" /> For high-level network topology mapping.
- <img src="https://img.shields.io/badge/-Python-3776AB?&style=for-the-badge&logo=python&logoColor=white" /> For programming IoT Microcontroller Units (MCUs).

## Network Topology

<img width="2325" height="1417" alt="4" src="https://github.com/user-attachments/assets/0c7d02b2-ffe6-4b1b-a7ed-cfca8c052c1d" />

**(The diagram above perfectly illustrates the Hierarchical Star design and the separation of the Administrative Block)**


The backbone relies on a Main Router `(10.10.10.1)` and Main Switch acting as the central aggregator. A dedicated Administrative Switch offloads the "Power Center" (Server Farm), ensuring that high traffic in public zones (like the Library) does not impact backend server performance.

## Project Execution Roadmap
### Step 1: Architectural Design & Topology Planning
- Defined the network requirements and selected a Hierarchical Star Topology to ensure scalability and fault isolation.
  Segmented the campus into three functional zones: Lecture Hall, Smart Library, and Staff Quarters, ensuring traffic from high-density student areas did not impact administrative operations.

- Designed a dedicated **Administrative Block** to host critical infrastructure, physically separating the server farm from the main data plane.
  <img width="581" height="468" alt="image" src="https://github.com/user-attachments/assets/1524550f-795c-4314-b709-1e42a1c217c8" />

### Step 2: Core Infrastructure & Service Configuration
Deployed the "Power Center" of the network—a distributed server farm hosted on an Administrative Switch.
- Configured a Class A Private Network `(10.0.0.0/8)` to accommodate a massive pool of future IoT devices.

- Implemented a DHCP Server `(10.10.10.3)` to manage dynamic addressing for transient devices like student smartphones.

- Established a DNS Server `(10.10.10.4)` to map the IoT Registration Server to `iotserver.com`, abstracting IP complexity for network administrators.

