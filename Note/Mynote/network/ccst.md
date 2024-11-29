## Table of Contents
- [fundamental Networking concept](#fundamental-networking-concept)

## Fundamental Networking Concept
1) Physical vs. Logical Topologies
- Physical Topology: Refers to the actual layout of cables and devices in a network. Examples include:
        - Bus Topology: Devices are connected along a single coaxial cable (common in older networks like 10BASE2/10BASE5). Only one device can transmit at a time, controlled by CSMA/CD to avoid collisions.
        - Star Topology: Devices are connected to a central hub or switch. The physical star is common in modern networks.
        - Ring Topology: Devices are connected in a circular fashion. This topology avoids collisions by using a token-passing mechanism, where devices transmit data only when they have the token.
- Logical Topology: Refers to how data flows within the network, which may differ from the physical layout. For example:
        - A logical bus topology can function over a physical star topology using Ethernet hubs.
        - A logical ring topology can function over a physical star by using a Media Access Unit (MAU), as in Token Ring networks.

2) Collision Detection and Avoidance
- Legacy networks relied on CSMA/CD (Carrier Sense Multiple Access with Collision Detection):
    - Devices "listen" to the wire before transmitting to ensure no other devices are transmitting.
    - If multiple devices transmit simultaneously, collisions occur, detected by a voltage spike on the wire.
    - Devices then use random backoff timers to delay retransmission, reducing the chances of another collision.
- Modern networks, especially those using switches, have largely eliminated collisions by providing dedicated bandwidth for each connection.

3) Wide-Area Network (WAN) Topologies
- Full-Mesh Topology:
    - Each node has a direct connection to every other node.
    - Provides the most optimal paths and redundancy.
    - High costs and scalability issues make it impractical for large networks.
    - Example: Requires 10 links to connect 5 nodes, calculated using the formula 𝑛×(𝑛−1)/2
- Partial-Mesh Topology:
    - Only critical connections are established based on traffic patterns, reducing cost while maintaining efficiency.
    - Example: Office A (headquarters) connects to all remote offices, while only certain remote offices connect to each other.
- Point-to-Point Topology:
    - A direct connection between two nodes, either physical or virtual.
    - Example: A virtual private network (VPN) creates a secure, encrypted connection between geographically distant offices.
- Point-to-Multipoint Topology:
    - A single physical connection (e.g., from a headquarters) supports multiple logical paths to remote sites using virtual circuits.

4) Network Classifications
The chapter explains various network types, categorized by their scope, speed, and purpose:
- LAN (Local Area Network):
    - High-speed network confined to a single building or department.
    - Common in offices for resource sharing, such as file servers and printers.
- WAN (Wide Area Network):
    - Interconnects geographically dispersed sites, such as between cities or countries.
    - Typically slower than LANs but increasingly faster with modern technologies.
    - Often uses service providers to establish connections.
- MAN (Metropolitan Area Network):
    - High-speed network within a city, such as a fiber ring connecting major buildings.
    - Redundancy is achieved through circular fiber layouts.
- CAN (Campus Area Network):
    - Used to connect nearby buildings on a campus, like office buildings or a university.
    - High-speed connections with redundancy, often through underground conduits.
- PAN (Personal Area Network):
    - Short-range connection between devices like Bluetooth-enabled controllers or remotes.
    - Typically low throughput and limited range but highly convenient.
- WLAN (Wireless Local Area Network):
    - Provides mobility by connecting devices via radio waves to wireless access points.
    - Key considerations include minimizing interference and optimizing frequency bands.

5) Summary: Network Performance Metrics
This section introduces essential metrics for evaluating and managing network performance. It highlights the key concepts of bandwidth, throughput, and latency:
- Bandwidth vs. Throughput
    - Bandwidth:
        - Refers to the theoretical maximum capacity of a network link, representing how much data can be transmitted per second under ideal conditions.
        - It’s the "maximum potential" of the network but not typically achieved in real-world scenarios due to various factors (e.g., noise, hardware limitations).
    - Throughput:
        - The actual amount of data successfully transmitted through a network link or device (like a router or switch) over a given period.
        - Throughput is usually lower than bandwidth due to issues like packet loss, network congestion, or protocol overhead.
    - Analogy:
        - Bandwidth is like the number of lanes on a highway, representing its capacity to carry traffic. Adding more lanes increases the theoretical capacity.
        - Throughput is the actual number of cars traveling on the road, which depends on real-world factors like accidents, road conditions, or traffic.
- Latency
    - Definition:
        - The total delay experienced when data travels from the source to its destination and back.
        - Measured in milliseconds (ms), latency includes all forms of delays (e.g., propagation, transmission, processing, and queuing delays).
    - Example:
        - In a speed test, latency might show as 19 ms for downloading and 20 ms for uploading. This total latency includes delays caused by the distance between devices, hardware processing, and network congestion.

6) iPerf
- What is iPerf?
    - iPerf measures actual network throughput, not theoretical bandwidth.
    - Used for troubleshooting and performance testing between a server and a client.
- How it Works:
    - Install iPerf on two devices (one acts as the server, the other as the client).
    - The client sends traffic to the server while iPerf calculates the actual throughput.
    - Results are provided for each interval, including transferred data and throughput (in megabits per second).
- Example Demonstration
    - Setup:
        - PC1 (Server): Runs the command ./iperf3 -s to start listening on port 5201.
        - PC2 (Client): Runs the command ./iperf3 -c <server_IP> to send traffic to the server for 10 seconds.