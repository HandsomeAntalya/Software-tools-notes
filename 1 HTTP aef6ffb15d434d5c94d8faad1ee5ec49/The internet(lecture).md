# The internet(lecture)

This document provides an overview of the internet's protocols, including IP, TCP, TLS, and HTTP. It explains how these protocols work together to provide secure and reliable communication between devices. The document also discusses the three main properties of information security (confidentiality, integrity, and authentication) and how they relate to TLS. Finally, it explains the role of Certificate Authorities in establishing trust and maintaining security in the public key infrastructure.

![截屏2023-04-21 20.08.42.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.08.42.png)

These protocols are in descending order, each one on the top depends on the on below, so HTTP relies on TLS, TCP  relies on IP.

**The network stack**, also known as the networking protocol stack, is a set of layered protocols that work together to facilitate communication between devices over a network. The layered approach allows each layer to focus on a specific aspect of the communication process, and each layer interacts with the layers above and below it. The most common model for the network stack is the OSI (Open Systems Interconnection) model, which has seven layers, although the Internet Protocol Suite (TCP/IP model) is another widely-used model with four layers. 网络协议栈，也被称为网络协议栈，是一组分层协议，共同促进网络上设备之间的通信。分层的方法使每一层都专注于通信过程的一个特定方面，每一层都与它上面和下面的层互动。网络堆栈最常见的模型是OSI（开放系统互连）模型，它有七个层次，尽管互联网协议套件（TCP/IP模型）是另一个广泛使用的模型，有四个层次。

The protocols you mentioned (HTTP, TLS, TCP, and IP) are part of the Internet Protocol Suite, and they operate at different layers of the network stack. Here's a brief overview of each protocol and their relationships: 你提到的协议（HTTP、TLS、TCP和IP）是互联网协议套件的一部分，它们在网络堆栈的不同层运作。下面是对每个协议和它们之间关系的简要概述：

1. **IP (Internet Protocol 互联网协议)**: IP operates at the Network Layer (Layer 3 in the OSI model) or I**nternet Layer in the TCP/IP mode**l. It is responsible for routing packets of data across networks, from the source to the destination device, based on their **IP addresses.** IP provides an unreliable, connectionless service, which means that it does not guarantee the delivery of packets, their order, or the avoidance of duplicates. IP在网络层（OSI模型中的第3层）或TCP/IP模型中的互联网层运行。它负责在网络上路由数据包，根据它们的IP地址，从源头到目的地设备。IP提供了一种不可靠的、无连接的服务，这意味着它不保证数据包的交付、它们的顺序或避免重复的情况。
2. **TCP (Transmission Control Protocol 传输控制协议)**: TCP operates at the **Transport Layer** (Layer 4 in the OSI model) or Transport Layer in the TCP/IP model. It provides a reliable, connection-oriented service built on top of the IP protocol. TCP establishes a connection between the sender and the receiver and ensures that the data is transmitted reliably, **in the correct order,** and without errors. If packets are lost or arrive out of order, TCP is responsible for retransmitting them or reassembling them in the correct order. TCP在传输层（OSI模型的第4层）或TCP/IP模型的传输层运行。它提供一个可靠的、面向连接的服务，建立在IP协议之上。TCP在发送方和接收方之间建立连接，并确保数据以正确的顺序可靠地传输，并且没有错误。如果数据包丢失或不按顺序到达，TCP负责重新传输或按正确顺序重新组合。
3. **TLS (Transport Layer Security 传输层安全)**: TLS is a **cryptographic** **protocol** that operates between the Transport Layer and the Application Layer. It provides secure communication by encrypting the data transmitted between the client and the server. TLS is commonly used with other application layer protocols, such as HTTP, to secure web browsing, email, and other communications. When used with HTTP, the combination is referred to as HTTPS (HTTP Secure). TLS是一个在传输层和应用层之间运行的加密协议。它通过对客户端和服务器之间传输的数据进行加密来提供安全通信。TLS通常与其他应用层协议一起使用，如HTTP，以确保网页浏览、电子邮件和其他通信的安全。当与HTTP一起使用时，这种组合被称为HTTPS（HTTP安全）。
4. **HTTP (Hypertext Transfer Protocol 超文本传输协议)**: HTTP operates at the Application Layer (Layer 7 in the OSI model) or Application Layer in the TCP/IP model. It is a high-level protocol that defines how clients (usually web browsers) and servers exchange information, such as web pages, images, and other resources. HTTP uses a request-response model, in which the client sends a request for a resource, and the server sends back a response containing the requested resource or an appropriate status code. HTTP在应用层（OSI模型的第7层）或TCP/IP模型的应用层运行。它是一个高级协议，定义了客户（通常是网络浏览器）和服务器如何交换信息，如网页、图像和其他资源。HTTP使用一个请求-响应模型，其中客户端发送一个资源请求，而服务器发送一个包含请求资源或适当状态代码的响应。

The relationship between these protocols can be visualized as a stack, with IP at the bottom, TCP on top of IP, TLS on top of TCP, and HTTP on top of TLS. When a client wants to access a secure web page, for example, it sends an HTTP request over a TLS-encrypted connection, which in turn is built on a TCP connection, which itself is built on top of IP. Each layer adds its functionality and communicates with the layers above and below it, ultimately providing a secure and reliable way to exchange information between devices on the internet. 这些协议之间的关系可以被看作是一个堆栈，IP在底部，TCP在IP的顶部，TLS在TCP的顶部，HTTP在TLS的顶部。例如，当一个客户想要访问一个安全的网页时，它通过TLS加密的连接发送HTTP请求，而TLS又是建立在TCP连接之上的，而TCP连接本身是建立在IP之上的。每一层都增加了它的功能，并与它上面和下面的层进行通信，最终提供了一种安全可靠的方式在互联网上的设备之间交换信息。

![截屏2023-04-21 20.11.54.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.11.54.png)

![截屏2023-04-21 20.12.37.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.12.37.png)

In the context of network communication, IP (Internet Protocol), path, data packet, source address, destination address, and data are interrelated components that facilitate the exchange of information between devices over a network. Here's an explanation of each component and their relationships:在网络通信方面，IP（互联网协议）、路径、数据包、源地址、目标地址和数据是相互关联的组成部分，它们促进了网络上设备之间的信息交流。下面是对每个组件及其关系的解释：

1. **IP (Internet Protocol** 互联网协议**)**: IP is a network-layer protocol responsible for routing packets of data between devices over the internet or other networks. It defines the structure of the data packets and how they should be addressed to reach their destination. IP是一个网络层协议，负责在互联网或其他网络的设备之间进行数据包的路由。它定义了数据包的结构，以及它们应该如何寻址以到达目的地。
2. **Data packet** 数据包: A data packet is a unit of data transmitted over a network. In the context of IP, a packet consists of a header and a payload. The header contains important information like the source and destination IP addresses, the protocol used (e.g., TCP or UDP), and other metadata. The payload contains the actual data being transmitted, such as a portion of an email or a piece of a file.：数据包是通过网络传输的数据单元。在IP的上下文中，一个数据包由头部和有效载荷组成。头部包含重要信息，例如源IP地址、目标IP地址、使用的协议（例如TCP或UDP）和其他元数据。有效载荷包含实际正在传输的数据，例如电子邮件的一部分或文件的一部分。
3. **Source address 源地址**: The source address, in the context of IP, is the IP address of the device sending the data packet. It is included in the packet header so that the receiving device knows where the packet originated and can send a response, if necessary.：在IP的上下文中，源地址是发送数据包的设备的IP地址。它包含在数据包头中，以便接收设备知道数据包的来源并且可以在必要时发送响应。
4. **Destination address目的地地址**: The destination address, in the context of IP, is the IP address of the device to which the data packet is being sent. It is also included in the packet header and is used by routers along the path to determine where to forward the packet.在IP的上下文中，目的地地址是数据包被发送到的设备的IP地址。它也包含在数据包头中，并被沿途的路由器用于确定将数据包转发到何处。
5. **Path** 路径: The path refers to the series of network nodes (such as routers and switches) that a data packet traverses between the source and the destination devices. The path may involve multiple intermediate networks and devices, and the data packet may be forwarded several times before it reaches its destination. The path is determined by the IP routing process, which uses the destination address in the packet header to decide how to forward the packet through the network. 路径是指数据包在源设备和目标设备之间经过的一系列网络节点（如路由器和交换机）。路径可能涉及多个中间网络和设备，数据包可能在到达目标之前被多次转发。路径是由IP路由过程确定的，该过程使用数据包头中的目标地址来决定如何通过网络转发数据包。
6. **Data 数据**: Data refers to the actual information being transmitted between devices over the network. In the context of IP, the data is encapsulated in the payload of the data packets. As the packet traverses the network, the routers and other devices along the path do not typically inspect or modify the payload, focusing instead on the packet header to determine how to forward the packet. 数据是指在网络中设备之间传输的实际信息。在IP的上下文中，数据被封装在数据包的有效载荷中。随着数据包在网络中的传输，路由器和其他设备通常不会检查或修改有效载荷，而是专注于数据包头以确定如何转发数据包。

In summary, when two devices communicate over a network using IP, the data to be transmitted is divided into packets, each containing a portion of the data in its payload. The packets are then sent from the source device to the destination device along a path determined by the IP routing process, with the source and destination addresses in the packet header guiding the routing decisions. Once the packets reach the destination device, they are reassembled, and the data is extracted from the payloads, completing the communication process.

总之，当两个设备使用IP在网络上通信时，要传输的数据被分成数据包，每个数据包都包含其中一部分数据的有效载荷。然后，数据包根据IP路由过程确定的路径从源设备发送到目标设备，数据包头中的源和目标地址指导路由决策。一旦数据包到达目标设备，它们就被重新组装，数据从有效载荷中提取出来，完成通信过程。

*when I want to check my ip route* 

![截屏2023-04-21 20.17.52.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.17.52.png)

1. **`default via 172.23.255.254 dev en0`**: This line shows the default route for your system, meaning that any traffic not destined for a specific network in the routing table will be sent to this IP address (172.23.255.254) via the **`en0`** network interface. This is typically the IP address of your default gateway (router).
2. **`127.0.0.0/8 via 127.0.0.1 dev lo0`**: This line represents the loopback address range (127.0.0.0/8) which is routed via the loopback interface **`lo0`**. Loopback addresses are used for local communication within the device, and any traffic sent to these addresses is redirected back to the device itself.
3. **`127.0.0.1/32 via 127.0.0.1 dev lo0`**: This line is similar to the previous one but specifies a more specific route for the loopback address 127.0.0.1.
4. **`169.254.0.0/16 dev en0 scope link`**: This line represents the link-local address range (169.254.0.0/16) which is assigned to the **`en0`** network interface. Link-local addresses are used for communication between devices on the same local network segment without requiring a router or DHCP server.
5. **`172.23.0.0/16 dev en0 scope link`**: This line shows the route for the local network (172.23.0.0/16) that your device is connected to via the **`en0`** network interface. Traffic destined for IP addresses within this network range will be sent directly to the destination device on the local network.
6. **`172.23.216.17/32 dev en0 scope link`**: This line represents a specific route for your device's IP address (172.23.216.17) on the **`en0`** network interface.
7. **`172.23.255.254/32 dev en0 scope link`**: This line represents a specific route for your default gateway's IP address (172.23.255.254) on the **`en0`** network interface.
8. **`224.0.0.0/4 dev en0 scope link`**: This line shows the route for the multicast address range (224.0.0.0/4) which is assigned to the **`en0`** network interface. Multicast addresses are used for one-to-many communication, where a single sender can transmit data to multiple receivers.
9. **`255.255.255.255/32 dev en0 scope link`**: This line represents the broadcast address (255.255.255.255) on the **`en0`** network interface. Broadcast addresses are used for one-to-all communication within a local network segment.

In summary, your routing table specifies how traffic should be routed based on the destination IP address. It includes routes for your local network, loopback addresses, link-local addresses, multicast addresses, broadcast address, and a default route for any traffic not matching specific routes in the table.

![截屏2023-04-21 20.17.32.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.17.32.png)

TCP packet 

![截屏2023-04-21 20.20.28.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.20.28.png)

whether or not the message has been received.

server can also tell client to slow down 

TCP (Transmission Control Protocol 传输控制协议) is a **transport layer protocol** that provides reliable, connection-oriented communication between devices over a network. It is widely used for transmitting data over the Internet, and it's the underlying protocol for many applications such as HTTP, email, file transfer, and more. Here's an overview of how TCP works:是一种传输层协议，提供可靠的、面向连接的设备之间的通信。它被广泛用于在互联网上传输数据，并且是许多应用程序的基础协议，例如HTTP、电子邮件、文件传输等等。以下是TCP的工作原理概述：

1. **Connection establishment 连接建立**: To start communication, TCP establishes a connection between the sender and the receiver using a three-way handshake. The sender initiates the handshake by sending a SYN (synchronize) packet to the receiver. The receiver responds with a SYN-ACK (synchronize-acknowledge) packet, acknowledging the SYN and sending its own SYN. The sender then sends an ACK (acknowledge) packet to acknowledge the receiver's SYN. After the three-way handshake is complete, a connection is established, and data transfer can begin. 为了开始通信，TCP使用三次握手在发送方和接收方之间建立连接。发送方通过向接收方发送SYN（同步）数据包来启动握手。接收方回应一个SYN-ACK（同步-确认）数据包，确认SYN并发送自己的SYN。然后发送方发送一个ACK（确认）数据包来确认接收方的SYN。三次握手完成后，建立了一个连接，数据传输可以开始。
2. **Data transmission** 数据传输: Once the connection is established, the sender starts transmitting data in the form of segments. Each segment consists of a header (containing metadata such as sequence and acknowledgment numbers, flags, and more) and a payload (containing the actual data). The sender assigns a sequence number to each byte of data it sends, which helps the receiver to reassemble the data in the correct order and detect any missing or duplicate segments. 一旦连接建立，发送方开始以段的形式传输数据。每个段由头部（包含序列号，确认号，标志等元数据）和有效载荷（包含实际数据）组成。发送方为它发送的每个字节分配一个序列号，这有助于接收方按正确顺序重新组装数据并检测任何丢失或重复的段。
3. **Flow control 流量控制**: TCP uses a flow control mechanism to prevent the sender from overwhelming the receiver with data. The receiver has a buffer to store incoming data temporarily before processing it. The receiver advertises a window size to the sender, indicating how much buffer space is available. The sender then adjusts its data transmission rate based on the advertised window size. If the receiver's buffer becomes full, it sets the window size to zero, signaling the sender to stop transmitting data until the buffer is cleared.：TCP使用流量控制机制以防止发送方用数据压倒接收方。接收方具有缓冲区，在处理数据之前暂时存储传入的数据。接收方向发送方广告窗口大小，表示可用的缓冲区空间。然后，发送方根据广告窗口大小调整其数据传输速率。如果接收方的缓冲区变满，它将窗口大小设置为零，表示发送方停止传输数据，直到缓冲区被清除为止。
4. **Error detection and recovery 错误检测和恢复**: TCP employs error detection mechanisms to ensure that the data **transmitted is received correctly**. The sender calculates a checksum for each segment and includes it in the segment header. The receiver also calculates a checksum for the received segment and compares it with the one in the header. If the checksums do not match, the receiver discards the segment, and it will not be acknowledged. To recover from lost or corrupted segments, the sender uses a timer to detect unacknowledged segments. If a segment is not acknowledged within a specified time, the sender assumes it was lost or corrupted and retransmits it. TCP采用错误检测机制来确保传输的数据正确接收。发送方为每个片段计算一个校验和，并将其包含在片段头中。接收方也为接收到的片段计算一个校验和，并将其与头部的校验和进行比较。如果校验和不匹配，则接收方丢弃该片段，并且不会被确认。为了从丢失或损坏的片段中恢复，发送方使用计时器来检测未确认的片段。如果一个片段在指定的时间内没有被确认，发送方假设它已经丢失或损坏，并重新传输它。
5. **Acknowledgment and retransmission** 确认和重传: To confirm the receipt of data, the receiver sends ACK packets back to the sender, acknowledging the sequence numbers of the received segments. If the sender does not receive an acknowledgment for a segment within a certain time (determined by a retransmission timer), it assumes the segment was lost and retransmits it. This mechanism ensures that lost or corrupted segments are retransmitted, providing reliable data transmission. 为了确认数据的接收，接收器向发送器发送ACK数据包，确认接收到的分段的序列号。如果发送器在一定时间内（由重传计时器确定）未收到分段的确认，则认为该分段已丢失并重新发送。该机制确保丢失或损坏的分段得以重传，从而实现可靠的数据传输。
6. **Congestion control** 拥塞控制: TCP uses congestion control algorithms to adjust the data transmission rate in response to network congestion. When the sender detects packet loss (using duplicate ACKs or a retransmission timer), it assumes that the network is congested and reduces its transmission rate to alleviate the congestion. The sender then gradually increases the rate as long as no further congestion is detected. TCP使用拥塞控制算法来根据网络拥塞情况调整数据传输速率。当发送方检测到数据包丢失（使用重复ACK或重传计时器）时，它会认为网络拥塞并降低其传输速率以缓解拥塞。只要没有检测到更多的拥塞，发送方就会逐渐增加速率。
7. **Connection termination 连接终止**: When the sender and receiver have finished exchanging data, they close the connection using a four-way handshake. The sender sends a FIN (finish) packet to the receiver, signaling its intention to close the connection. The receiver acknowledges the FIN with an ACK packet and sends its own FIN packet to the sender. The sender then acknowledges the receiver's FIN with a final ACK packet, completing the four-way handshake and closing the connection.当发送方和接收方完成数据交换后，它们使用四次握手关闭连接。发送方向接收方发送一个FIN（结束）数据包，表示其意图关闭连接。接收方用ACK数据包确认FIN，并向发送方发送自己的FIN数据包。然后，发送方用最后的ACK数据包确认接收方的FIN，完成四次握手并关闭连接。

In summary, TCP provides reliable, connection-oriented communication by establishing a connection, transmitting data with error detection

![截屏2023-04-21 20.21.15.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.21.15.png)

TLS:  more secure 

![截屏2023-04-21 20.21.57.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.21.57.png)

TLS is a protocol that built on TCP

3 main properties about safety: 

***confidentiality*** 

***integrity*** 

***authentication*** 

Safety in the context of information security refers to the protection of information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction. The three main properties of information security, often referred to as the CIA triad, are confidentiality, integrity, and authentication. They provide a framework for ensuring the secure handling of data:在信息安全上下文中，安全性是指保护信息和信息系统免受未经授权的访问、使用、披露、干扰、修改或破坏的能力。信息安全的三个主要属性，通常称为CIA三要素，分别是保密性、完整性和认证。它们提供了确保数据安全处理的框架：

1. **Confidentiality保密性**：Confidentiality refers to the protection of sensitive information from unauthorized access and disclosure. Ensuring confidentiality means that only authorized individuals or systems can access and view the data. Confidentiality can be achieved using various mechanisms, such as encryption, access controls, and secure data storage. Encryption, for example, transforms the data into an unreadable format, ensuring that even if an unauthorized party intercepts the information, they cannot understand its content without the proper decryption key. (nobody see your message) 保密性是指保护敏感信息免受未经授权的访问和披露。确保保密性意味着只有经过授权的个人或系统才能访问和查看数据。可以使用各种机制来实现保密性，例如加密、访问控制和安全数据存储。例如，加密将数据转换为不可读格式，确保即使未经授权的人拦截信息，他们也无法在没有正确的解密密钥的情况下理解其内容。（没有人看到你的信息）
2. **Integrity 完整性**： Integrity refers to maintaining the accuracy and consistency of data over its entire life cycle, ensuring that it has not been tampered with or altered by unauthorized parties. Data integrity is crucial for maintaining trust in information systems and ensuring that the data used for decision-making is accurate and reliable. Integrity can be achieved through various techniques, such as checksums, digital signatures, and version control. Checksums and hash functions, for example, can be used to detect unintended data corruption or unauthorized modifications by comparing the computed value against a stored value.(nobody ) 完整性是指在整个数据生命周期中维护数据的准确性和一致性，确保未经授权的各方未篡改或修改数据。数据完整性对于维护对信息系统的信任以及确保用于决策的数据准确可靠至关重要。可以通过各种技术来实现完整性，例如校验和、数字签名和版本控制。例如，可以使用校验和和哈希函数来检测意外的数据损坏或未经授权的修改，方法是将计算出的值与存储的值进行比较。（没有人）
3. **Authentication 认证**：Authentication refers to the process of verifying the identity of a user, device, or system before granting access to sensitive information or resources. It ensures that only authorized parties can perform actions or access data within a system. Authentication can be achieved using various methods, such as passwords, security tokens, biometrics, or digital certificates. In some cases, multi-factor authentication (MFA) is employed, which requires a user to present two or more independent pieces of evidence (e.g., something they know, something they have, or something they are) to verify their identity. 认证是指在授予对敏感信息或资源的访问之前，验证用户、设备或系统的身份的过程。它确保只有经过授权的各方才能在系统内执行操作或访问数据。可以使用各种方法来实现认证，例如密码、安全令牌、生物识别或数字证书。在某些情况下，还采用多因素认证（MFA），需要用户提供两个或更多独立证据（例如，他们知道的事情、他们拥有的东西或他们的身份）来验证其身份。

Together, these three properties form the foundation of a secure information system. By ensuring confidentiality, integrity, and authentication, organizations can protect their sensitive data from unauthorized access, maintain the accuracy and reliability of their information, and establish trust in their systems and communications.这三个属性共同构成了安全信息系统的基础。通过确保保密性、完整性和认证，组织可以保护其敏感数据免受未经授权的访问，维护其信息的准确性和可靠性，并在其系统和通信中建立信任。

## Why is TLS more secure?

TLS (Transport Layer Security) is a cryptographic protocol that provides secure communication over a network, primarily used for securing connections on the Internet. TLS is an evolution of the older SSL (Secure Sockets Layer) protocol and has several enhancements and improvements that make it more secure. Some reasons why TLS is considered more secure include:传输层安全（TLS）是一种密码协议，主要用于保护互联网上的连接，提供安全通信。TLS是旧版SSL（安全套接层）协议的升级版，有几个增强和改进，使其更加安全。TLS被认为更安全的一些原因包括：

1. **Stronger cryptographic algorithms 更强的加密算法**: TLS supports more modern and robust cryptographic algorithms for encryption, hashing, and key exchange. This includes the use of stronger ciphers like AES (Advanced Encryption Standard) and more secure key exchange methods like ECDHE (Elliptic Curve Diffie-Hellman Ephemeral). These improvements make it harder for attackers to break the encryption and gain access to the transmitted data. ：TLS支持更现代和强大的加密算法，包括使用更强的密码，例如AES（高级加密标准），更安全的密钥交换方法，例如ECDHE（椭圆曲线Diffie-Hellman短暂）。这些改进使攻击者更难以破解加密并访问传输数据。
2. **Improved protocol design 改进的协议设计**: TLS includes several enhancements in its design that help to prevent known attacks and security vulnerabilities. For example, TLS uses explicit IVs (Initialization Vectors) to prevent the Cipher Block Chaining (CBC) attacks that affected SSL. Additionally, TLS has improved its handling of padding, making it more resistant to padding oracle attacks.：TLS在其设计中包含了几个增强功能，可帮助防止已知的攻击和安全漏洞。例如，TLS使用显式IV（初始化向量）以防止影响SSL的CBC（密码块链接）攻击。此外，TLS已改进了其填充处理，使其更抵抗填充泄露攻击。
3. **Perfect Forward Secrecy (PFS) 完美前向保密（PFS）**: TLS supports PFS through the use of ephemeral key exchanges like DHE (Diffie-Hellman Ephemeral) and ECDHE. With PFS, even if an attacker manages to compromise a server's private key, they cannot decrypt past communications because a unique session key is generated for each connection. This feature provides long-term protection for encrypted data, even if the long-term private key is compromised at a later point. TLS通过使用短暂密钥交换（如DHE（Diffie-Hellman短暂）和ECDHE）来支持PFS。使用PFS，即使攻击者设法破坏了服务器的私钥，他们也无法解密过去的通信，因为为每个连接生成了唯一的会话密钥。这个功能为加密数据提供了长期保护，即使长期私钥在以后被破坏。
4. **Extensibility**.**可扩展性:** TLS is designed with extensibility in mind, allowing for the easy addition of new features, algorithms, and security improvements through the use of extensions. This extensibility ensures that TLS can stay up-to-date with the latest cryptographic advancements and adapt to new security threats. TLS的设计考虑到可扩展性，可以通过扩展轻松添加新功能、算法和安全改进。这种可扩展性确保TLS可以跟上最新的加密进展并适应新的安全威胁。
5. **Widespread adoption and support 广泛采用和支持**： TLS is widely adopted and supported by modern web browsers, servers, and applications. This widespread support means that it is continuously being reviewed, updated, and improved by the security community, making it more secure over time. TLS被现代Web浏览器、服务器和应用程序广泛采用和支持。这种广泛的支持意味着它正在不断地被安全社区审核、更新和改进，从而使其随着时间的推移变得更加安全。

In summary, TLS is more secure than its predecessor, SSL, due to the use of stronger cryptographic algorithms, improved protocol design, support for Perfect Forward Secrecy, extensibility, and widespread adoption. These factors contribute to making TLS a reliable and robust security protocol for securing communications over the Internet.总之，与其前身SSL相比，TLS由于使用更强大的加密算法、改进的协议设计、支持完美前向保密、可扩展性和广泛采用而更加安全。这些因素有助于使TLS成为保护互联网通信的可靠和坚固的安全协议。

![截屏2023-04-21 20.27.22.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.27.22.png)

CA stands for Certificate Authority, which is a trusted third-party organization that issues and manages digital certificates for public key infrastructure (PKI) systems. Digital certificates are used to establish secure connections over the internet, primarily through the use of protocols like TLS (Transport Layer Security). CA代表证书授权机构，是一家受信任的第三方组织，为公钥基础设施（PKI）系统发行和管理数字证书。数字证书用于通过诸如TLS（传输层安全）等协议在互联网上建立安全连接。

证书授权机构的作用包括：

The role of a Certificate Authority includes:

1. **Verification of identity 身份验证**： Before issuing a digital certificate, the CA verifies the identity of the applicant (usually a website or organization) to ensure that they are the legitimate owner of the domain or entity they claim to represent. This verification process can vary in rigor depending on the type of certificate being issued (e.g., Domain Validation, Organization Validation, or Extended Validation).在发行数字证书之前，CA验证申请人的身份（通常是网站或组织），以确保他们是他们声称代表的域或实体的合法所有者。根据发行的证书类型（例如，域验证、组织验证或扩展验证），此验证过程的严格程度可能会有所不同。
2. **Issuance of digital certificates 发行数字证书**： Once the applicant's identity is verified, the CA issues a digital certificate that contains the applicant's public key, domain name or organization details, and the CA's digital signature. This certificate is used to establish secure connections with clients (like web browsers) and to enable encrypted communication. 一旦确认申请人的身份，CA将发行一个包含申请人公钥、域名或组织详细信息以及CA数字签名的数字证书。此证书用于与客户端（如Web浏览器）建立安全连接并启用加密通信。
3. **Revocation and management of certificates 吊销和管理证书**：The CA maintains a database of issued certificates and is responsible for managing their life cycle. If a certificate needs to be revoked due to reasons like key compromise, domain ownership changes, or other security concerns, the CA updates the Certificate Revocation List (CRL) or provides information through the Online Certificate Status Protocol (OCSP). Clients can check the revocation status of a certificate using these mechanisms to ensure that they are connecting to a secure and trusted entity.CA维护已发行证书的数据库，并负责管理证书的生命周期。如果需要由于密钥泄露、域所有权更改或其他安全问题而吊销证书，CA将更新证书吊销列表（CRL）或通过在线证书状态协议（OCSP）提供信息。客户端可以使用这些机制检查证书的吊销状态，以确保他们连接到一个安全和可信赖的实体。
4. **Establishing trust** **建立信任**： The CA acts as a trusted intermediary between clients and servers. Clients trust the CA to verify the identities of servers and to issue valid certificates. Web browsers and operating systems include a list of trusted CAs (also known as root certificates) to enable secure connections to websites and services that use certificates issued by those CAs.CA充当客户端和服务器之间的可信中介。客户端信任CA验证服务器的身份并发放有效证书。Web浏览器和操作系统包括一份可信CA列表（也称为根证书），以启用连接到使用这些CA发行的证书的网站和服务的安全连接。
5. **Maintaining security standards 维护安全标准**：CAs are expected to adhere to strict security standards and practices to maintain the integrity and trustworthiness of the PKI system. This includes protecting their private signing keys, following proper validation procedures, and staying up-to-date with the latest security threats and vulnerabilities.CA应遵守严格的安全标准和实践，以维护PKI系统的完整性和可信度。这包括保护其私有签名密钥、遵循适当的验证程序并及时了解最新的安全威胁和漏洞。

In summary, the role of a Certificate Authority is to verify the identity of entities, issue and manage digital certificates, establish trust, and maintain security standards within the public key infrastructure. CAs play a crucial role in ensuring the security and integrity of communications over the internet.总之，证书授权机构的作用是验证实体的身份、发行和管理数字证书、建立信任并维护公钥基础设施的安全标准。CA在确保互联网通信的安全性和完整性方面发挥着至关重要的作用。

![截屏2023-04-21 20.29.56.png](The%20internet(lecture)%2026a10e8dd9684eb8a033fa02523df0f2/%25E6%2588%25AA%25E5%25B1%258F2023-04-21_20.29.56.png)

We can see from this icon that if the connection is using the TLS

## Conclusion

This document discusses the internet and its security features, including confidentiality, integrity, and authentication. It also compares the security of TLS (Transport Layer Security) to its predecessor SSL (Secure Sockets Layer) and explains the role of Certificate Authorities (CAs) in establishing trust and maintaining security in public key infrastructure systems.

MCQ questions:

1. What are the three foundational properties of a secure information system?
A. Confidentiality, integrity, and authentication
B. Confidentiality, availability, and authentication
C. Confidentiality, integrity, and authorization
D. Confidentiality, availability, and authorization

1. What is the role of a Certificate Authority (CA)?
A. To issue and manage digital certificates for public key infrastructure systems
B. To provide secure communication over a network
C. To encrypt data using modern cryptographic algorithms
D. To prevent known attacks and security vulnerabilities

1. What is TLS (Transport Layer Security)?
A. A cryptographic protocol that provides secure communication over a network
B. A method of verifying the identity of a user, device, or system
C. A trusted third-party organization that issues and manages digital certificates
D. A type of encryption used to protect sensitive information

1. Why is TLS considered more secure than SSL?
A. TLS uses stronger cryptographic algorithms and improved protocol design
B. TLS supports Perfect Forward Secrecy (PFS)
C. TLS is extensible, allowing for the easy addition of new features and security improvements
D. All of the above

1. What is the role of multi-factor authentication (MFA)?
A. To verify the identity of a user, device, or system
B. To prevent known attacks and security vulnerabilities
C. To provide long-term protection for encrypted data
D. To require a user to present two or more independent pieces of evidence to verify their identity

1. A
2. A
3. A
4. D
5. D

1. What is the purpose of explicit IVs in TLS?
A. To prevent the Cipher Block Chaining (CBC) attacks
B. To establish secure connections with clients
C. To enable encrypted communication
D. To establish trust between clients and servers
2. What is the purpose of Certificate Revocation List (CRL)?
A. To update security standards and practices
B. To verify the identity of entities
C. To issue and manage digital certificates
D. To revoke digital certificates due to security concerns
3. What is the purpose of the Online Certificate Status Protocol (OCSP)?
A. To issue and manage digital certificates
B. To verify the identities of servers
C. To check the revocation status of a certificate
D. To enable secure connections with clients
4. What is Perfect Forward Secrecy (PFS)?
A. A method of verifying the identity of a user, device, or system
B. A protocol that provides secure communication over a network
C. A technique that ensures that past communications cannot be decrypted even if a private key is compromised
D. A database of issued certificates that are revoked due to security concerns
5. What is the role of multi-factor authentication (MFA)?
A. To verify the identity of a user, device, or system
B. To prevent known attacks and security vulnerabilities
C. To provide long-term protection for encrypted data
D. To require a user to present two or more independent pieces of evidence to verify their identity

Answer list:

1. A
2. D
3. C
4. C
5. D