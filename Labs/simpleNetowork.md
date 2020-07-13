# Lab - Simple Network
Simulate a simple Client-Server network. Observe to-and-from IP and MAC addresses and Port numbers when a packet is sent over a network.

## Procedure:
1.  Add a Server and a PC from the End Devices. These two devices cannot communicate with each other. We either need to communicate using a physical cable or we need to communicate using the air.
2.  Connect the devices using Copper Cross-Over making a FastEthernet0 to FastEthernet0 connection. The cross-over cable allows two PCs to talk directly to each other.
3.  To allow these two devices to communicate with each other we need to have two things:
    1.  MAC Address: primilarily assigned by device manufacturers, and are therefore often referred to as the burned-in address, or as an Ethernet hardware address. Each address can be stored in hardware, such as the card's read-only memory, or by a firmware mechanism. 
        *   PC0 MAC Address: `default: 000C.CF02.2802`; 
            `changed to: 0001.1111.1111`
        *   Server0 MAC Address: `default: 0040.0B7E.6673`; 
            `changed to: 0001.2222.2222`
    2.  The Dynamic Host Configuration Protocol (DHCP) is a network management protocol used on Internet Protocol networks whereby a DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks.
4.  Typically, a router will be allocating IP address to PCs using DHCP. As we don't have a router or another type of device, we have to manually configure the IP addresses.
    *   PC0 IP Address: `10.1.1.1` <br>
        PC0 Subnet Mask: `255.255.255.0`
    *   Server0 IP Address: `10.1.1.2` <br>
        Server0 Subnet Mask: `255.255.255.0`
5.  Ping Server0 from PC0. `ping 10.1.1.2` from PC0 to verify
    connectivity. It is used just to verify if the server is up and running.
6.  Notice the "Services" running on Server0 (Server0 > Services). We've got HTTP, DNS, EMAIL, FTP and various other. Leave HTTP as `on`.
7.  From PC0 > Desktop > Web Browser, type the URL: `http://10.1.1.2`. A small hello-world web page is displayed with a few links containing images. 
8.  This is an example of a network. **We've got a client (PC0) and a server (Server0). The server is configured with the HTTP Service and it's serving a web-page to the client when the client requested the web page.**
9.  Go to Server0 > Services > HTTP and turn `off` HTTP service while HTTPS is still `on`.
10. PC0 > Desktop > Web Browser and refresh. It **times out**. This is because the server is no longer listening on port 80. However, if we change the url to `https://10.1.1.2`, the same web-page is displayed.
11. Run Simulation Mode to see how a packet is sent/received from client to server and vice-versa. The packet contains all required information. MAC addresses (PC0 >> Server0), IP addresses (PC0 >> Server0), Port Numbers (PC0 >> Server0). <br>
Note that ">>" indicates the direction that the packet travels in.