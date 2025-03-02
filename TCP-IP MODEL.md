History and Development of TCP/IP
During the 1960s, the Defense Advanced Research Projects Agency (DARPA) developed the TCP/IP model. The following are some significant events that led to the popularity of TCP/IP:

In 1975, there were two-network TCP/IP communication tests between Stanford and University College London.
The US Department of Defense, in March 1982, declared TCP/IP as the standard communication protocol for all their military computer networking .
A year later, ARPANET adopted this model as a standard communication protocol.
In 1989, the University of California also declared TCP/IP as its standard protocol.
Later, many IT companies, including IBM and DEC, adopted this model as their standard communication protocol.
TCP/IP then emerged as a standard communication protocol or a comprehensive framework for computer networking and internet communication across the world.

Features:
TCP/IP is a reliable communication protocol. Whenever the sender transmits a data packet to the receiver, the receiver responds with an acknowledgment that can be positive or negative. Therefore, the sender can know whether the data packet has reached its destination. If not, the sender will resend it.
It ensures that the data reaches its destination in the same order the sender has sent it.
It is connection-oriented, meaning that it requires establishing a connection between two remote points before the data transfer takes place.
TCP/IP provides end-to-end communication.
It also provides error-checking and recovery mechanisms.
You can implement flow control with TCP/IP so that the receiver will not overload with the data the sender transmits.
TCP operates in client-server point-to-point mode.

How Does TCP/IP Work?
Today, TCP/IP is the default communication protocol on the internet. The United States Department of Defense developed this model with the aim to enable the accurate and correct transfer of data between devices located far from each other.

Consider that a specific computer system wants to send a message to another remote system. If it sends the whole message in one go and encounters an issue while transmitting, it has to resend the whole message. Resending the whole message is not feasible.

The TCP/IP model breaks the whole message into small data packets. All these data packets get reassembled when they reach the destination. Each data packet takes an alternative way to reach the destination if a particular way is not available or congested.

Furthermore, the sender has to resend only those data packets that encountered an issue while transmitting rather than resending the whole message.

TCP/IP carries out the communication tasks in four layers. As a result, data packets have to go through four layers before reaching their destination. Each layer has its own function.

Since TCP/IP is connection-oriented, it maintains the connection between two systems until they finish data exchange.

The primary purpose of carrying out communication in layers is to standardize the process. It eliminates the need for various hardware and software vendors to manage the communication process on their own.
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Advantages
Here are some notable benefits of TCP/IP:

This model allows you to establish a connection between different types of computer systems.
It is interoperable, i.e., it supports communication among heterogeneous networks.
It is a highly scalable client-server architecture.
This model assigns the ID address to each computer system on the network. As a result, it becomes possible to uniquely identify each device over the network.
It supports a wide range of routing protocols.
It is an open communication protocol suite. Therefore, anyone can use TCP/IP.
Disadvantages
The following are some major pitfalls of TCP/IP:

This model does not provide the distinction between services, protocols, and interfaces. Therefore, it would not be suitable to introduce any new technology in the network.
Though the data link and physical layers have different functionalities, there is no separation of these layers in TCP/IP.
It is not optimized for a local area network (LAN) and personal area network (PAN).
This model is pretty complicated to set up.
The transport layer of TCP/IP does not assure the delivery of data packets.
----------------------------------------------------------------------------------------------------------------------------------------------------
Unlike its predecessor, i.e., the OSI model , the TCP/IP model consists of only four layers, namely Application, Transport, Internet, and Network Access. Each layer has its own function. Let us discuss each of these TCP/IP layers in detail below.

1. Network Access/Link Layer
The network access layer or link layer is the combination of the data link layer and physical layer of the OSI model. It is the bottom-most layer of the TCP/IP architecture.

At this layer, the ***"physical transmission of data"*** takes place. In addition, the mapping of IP addresses into physical addresses also takes place in this layer. However, the primary function of the Network Access/Link layer is to transmit data between two devices connected over the same network.

2. Internet Layer
On the top of the network access layer, there is the internet layer. This layer is parallel to the network layer of the OSI model. The primary function of this layer is to transmit data packets to their destination. Moreover, this layer involves the ***logical transmission of data***.

This layer leverages three different protocols that are as follows:

IP: IP stands for Internet Protocol. It detects the IP address of a device, which can later be utilized for internetwork connections. The primary function of this protocol is to transmit data packets from source to destination by using the IP addresses in the packet headers. Furthermore, there are two common versions of IP, namely IPv4 and IPv6 .
ARP: ARP is an acronym for Address Resolution Protocol. The principal goal of ARP is to find the hardware address of the hosts through the known IP address. There are various types of ARP, including Proxy ARP, Reverse ARP, Inverse ARP, and Gratuitous ARP.
ICMP: Internet Control Message Protocol is the full form of ICMP. Its primary goal is to notify the users about the issues associated with the network. However, it does not rectify those issues.
3. Transport/Host-to-Host Layer
The transport layer is above the internet layer in TCP/IP. It is parallel to the transport layer of the OSI model. The major function of this layer is to ensure end-to-end communication and deliver error-free data from the source to the destination.

Furthermore, there are two protocols in this layer that are as follows:

TCP: Transmission Control Protocol (TCP) is an error-free and reliable communication protocol that ensures end-to-end communication between two hosts. Also, it performs sequencing and segmentation of data. It comes with the control flow mechanism that controls the flow of data between two systems. In addition, it provides the acknowledgment feature, i.e., the sender knows whether the data packets have reached the destination or not.
UDP: User Datagram Protocol (UDP) is a cost-effective but less reliable protocol. Like TCP, UDP does not provide acknowledgment and control flow features. Moreover, it is a connectionless protocol and not connection-oriented like TCP.
4. Application/Process Layer
The topmost layer of TCP/IP is the application or process layer. This layer carries out the functions of the top three layers of the OSI model, namely the Application, Presentation, and Session layers. The primary responsibility of this layer is to ensure node-to-node communication and control user-interface specifications.

Moreover, this layer uses various protocols, as given below:

HTTP/HTTPS: HTTP is an acronym for HyperText Transfer Protocol, while HTTPS is an acronym for HTTP-Secure. The World Wide Web (WWW) leverages the HTTP protocol to facilitate communication between web browsers and servers. On the other hand, HTTPS is the amalgamation of HTTP and SSH (Secure Shell). It protects the confidentiality and integrity of data being transmitted from the source to the destination over the network.
SSH: SSH stands for Secure Shell. It is also known as Secure Socket Shell, which is a cryptographic network protocol that carries out network services over unsecured networks. The primary reason TCP/IP uses this protocol is its capability to maintain encrypted connections.
NTP: NTP is an acronym for Network Time Protocol. This protocol synchronizes the system’s clock to time sources in a network. Also, it is very helpful in bank transactions.
Telnet: Telnet stands for TErminaL NETwork. It enables one system to access a local computer virtually and provides two-way, text-based communication between them. The computer that starts the connection is the local computer, and the computer that accepts the connection is called the remote computer.
FTP: File Transfer Protocol is the full form of FTP. It is a widespread communication protocol used for transferring files between the client and the server over a network.
Besides these protocols, there are many others, such as Network File System (NFS), Simple Mail Transfer Protocol (SMTP), and Trivial File Transfer Protocol (TFTP).

  
