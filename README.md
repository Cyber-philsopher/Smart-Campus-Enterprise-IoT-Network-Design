# Smart-Campus: IoT-Network Design

## Objective

**Status:** Completed 

For this project, I take the role of an **IoT Cloud Networking Specialist**, to create a smart digital university campus network that leverages IoT, edge devices, and cloud resources to enhance teaching, learning, safety, and sustainability.

The university’s vision is to create a connected, sustainable, and student-friendly environment where digital services are integrated into campus life. My role involves designing and simulating the IoT infrastructure using Cisco Packet Tracer, while also documenting how network and cloud resources are orchestrated to support reliable and secure services.

This project involves the design and simulation of a Smart Campus Network using a Hierarchical Star Topology. Moving beyond simple connectivity, the architecture features a Distributed Server Farm that isolates critical services (DNS, DHCP, IoT) from user traffic to ensure high availability.

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

### Step 3: Zonal IoT Deployment & Automation Logic
Implemented specific automation scenarios using Microcontroller Units (MCUs) programmed with JavaScript/Python logic.


- Smart Library: Created an environmental feedback loop where CO2 Detectors trigger Ventilation Fans and Air Coolers when air quality drops.
<img width="960" height="636" alt="image" src="https://github.com/user-attachments/assets/f35f70f7-000d-445b-bb65-5f6df824ae16" />



- Lecture Hall: Programmed energy efficiency logic using Occupancy Sensors to automatically cut power to lights and projectors when the room is empty.

<img width="806" height="678" alt="image" src="https://github.com/user-attachments/assets/0026214c-4528-4cd7-a71a-4aba27750e3b" />

- Access Control: Integrated RFID Readers and Siren Actuators to secure physical entry points.

### Step 4: Security Implementation & Traffic Segmentation
Secured the network edge and optimized traffic flow.

- Deployed Zonal Wireless Gateways at the fringe of each zone to act as NAT boundaries, preventing broadcast storms from propagating across the campus.

- Enforced WPA2-PSK (AES) encryption on all wireless access points to prevent unauthorized packet injection.

- Configured Security Cameras on hardwired connections to reduce wireless congestion and latency.

<img width="1049" height="923" alt="image" src="https://github.com/user-attachments/assets/f9efc938-e381-4542-bc55-10389e63da7d" />

### Step 5: Simulation Evidence
#### Admin Dashboard Access
The network enables seamless management via the Admin PC. As shown below, the administrator can access the IoT control panel using the domain iotserver.com rather than the IP address.
<img width="1047" height="383" alt="image" src="https://github.com/user-attachments/assets/9d068521-418b-44ed-93de-d062f9f94149" />
*(Screenshot showing Admin PC web browser to access the IoT registration server)*

<img width="1044" height="690" alt="image" src="https://github.com/user-attachments/assets/21729d61-4e65-460c-8641-2f860fa41930" />
*(Admin PC logged into the server successfully - showing all the registered IoT devices)*

<img width="1049" height="923" alt="image" src="https://github.com/user-attachments/assets/d5d7cc26-4652-4d4d-98fc-aa9f9e4aa210" />
*(Some IoT devices can be controlled from Admin PC)*

## Challenges & Troubleshooting
During implementation, a significant challenge involved the Spanning Tree Protocol (STP) on the redundant links between the Staff Room and Core Switch.

- **Issue:** Links appeared "blocked" (Orange lights), initially interpreted as a connection failure.

- **Resolution:** Analysis confirmed this was correct STP behavior preventing Layer 2 loops. The redundant links remain in a blocking state to serve as automatic failover paths, ensuring High Availability.

## How to Run the Simulation
- Download and install Cisco Packet Tracer (Version 8.2 or higher).

- <a href="https://drive.google.com/file/d/1iptL4WFefUVyKMgwswIGkY7olm0OmT4X/view?usp=drive_link" target="_blank">
  <img src="https://img.shields.io/badge/Download-Packet%20Tracer%20File-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white" />
</a>

- Open `SmartCampus_Design_Final.pkt`.

- Wait for STP convergence (approx. 30 seconds for lights to turn green).

- **Test:** Open the browser on the Admin PC and navigate to iotreg.com
