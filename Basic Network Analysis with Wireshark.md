# Context of the Exercise

### Objective

The goal was to analyze different types of network traffic from a target device on your local network using Wireshark. By capturing and filtering specific protocols, you aimed to understand the types of services running on the network, identify any potential security concerns, and document the findings.

### What I Did

1. Initial Capture of UDP and SSDP Traffic:

- You started by capturing network traffic on the main network interface. You applied a filter to capture traffic involving your target device, focusing initially on SSDP (Simple Service Discovery Protocol) and UDP packets.
- Observation: The SSDP traffic revealed devices announcing their presence on the network via multicast messages (sent to addresses like 239.255.255.250). This is common for devices using UPnP, such as routers, smart TVs, or IoT devices, trying to make their services discoverable.

![Capture d'écran 2024-10-31 152349](https://github.com/user-attachments/assets/80421a10-ea34-418f-9a67-3971a0efcfaf)

2. Analysis of a Specific UDP Stream:

- By following a particular UDP stream, you captured a message indicating a BSDP (Bootstrap Protocol) search, with fields like DEVICE=0 and SERVICE=1.
- Observation: This likely indicates a device on the network searching for specific services, possibly for auto-configuration purposes. BSDP is often used for discovering network services or devices.

![Capture d'écran 2024-10-31 153501](https://github.com/user-attachments/assets/6f9af4ea-bfd8-4705-b7eb-80c2643651c1)

3. Further SSDP Analysis:

- You captured a large volume of SSDP NOTIFY messages, which are used by devices to announce available services. The messages contained fields like NOTIFY * HTTP/1.1, showing that devices on the network were broadcasting service availability.
- Observation: These broadcasts are typical in environments with multiple networked devices using UPnP to communicate their functionality. Each packet likely contained details about the device and service type.

![Capture d'écran 2024-10-31 154352](https://github.com/user-attachments/assets/e586fca6-20f2-40a9-9715-43f2934bec75)


### What I Achieved

- Understanding of Local Network Traffic: You successfully identified various network services being announced on the network via SSDP. This included learning about how devices communicate their availability and the types of services running on the network.
- Detailed Packet Analysis: By following specific UDP streams, you delved deeper into individual communications, revealing service discovery protocols (BSDP and SSDP) in action.
- Documentation and Findings: Your captures provide a snapshot of a network with active service discovery protocols. This documentation, along with packet captures, helps illustrate how UPnP and similar protocols function in real-time on a local network.
