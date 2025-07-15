# Lab: Demystifying the OSI Model with Odroid

## Introduction
In this lab, we will explore the seven layers of the OSI (Open Systems Interconnection) model using my Odroid as a monitoring station and `tshark` to capture network traffic in real time.

---

## Layer 1: Physical

* **Concept:** The physical layer is responsible for the transmission of pure bits through a physical medium (copper cables, fiber optics, radio waves). It defines the electrical and mechanical specifications.
* **In my Lab:** The Ethernet cable connecting my Odroid to my router, or Wi-Fi waves if the Odroid were to use a wireless connection.
* **Observation:** We cannot “see” the individual bits with `tshark`, but we know that the traffic we capture travels through here.

---

## Layer 2: Data Link

* **Concept:** Organizes bits into frames, manages access to the physical medium, and provides physical addressing (MAC addresses).
* **Tools:** ARP (Address Resolution Protocol), Ethernet, Wi-Fi.
* **Observation Lab (ARP):**The MAC address is an important element because it is the essential basis of communication, along with the IP address. ARP gives you a clear view of the communication and conversion of the IP and MAC addresses. 
1.  Make sure your Odroid's network interface (`eth0`) is in promiscuous mode: `sudo ip link set eth0 promisc on`
    2.  Start capturing ARP traffic: `sudo tshark -i eth0 -f “arp”`
3.  From your MacBook (or any other device on the same network), `ping` another device other than the Odroid (e.g., your Smart TV or your router if you haven't pinged it recently).
    * **What will you see?** Analyze the ARP frames. You will see requests for “Who has X.X.X.X? Tell Y.Y.Y.Y” and responses of “X.X.X.X is at A:B:C:D:E:F”. This demonstrates how IPs are resolved to MACs on the local network.

---

## Next Steps in this Lab
* Explore Layer 3: Network (IP, ICMP)
* Explore Layer 4: Transport (TCP, UDP, Ports)
* ... and so on for each layer.

