# Wireshark Basics – TCP Packet Analysis
## 📌 Project Overview

This repository demonstrates the analysis of Transmission Control Protocol (TCP) packets using Wireshark.

TCP is one of the core protocols of the TCP/IP suite and is responsible for providing reliable, ordered, and error-checked communication between devices on a network.

In this project, we inspect a captured TCP packet and explain some of the most important TCP control flags, including:

SYN
ACK
FIN
RST
PSH

These flags control how TCP connections are established, maintained, and terminated.

# 📸 Packet Capture

Below is a captured TCP packet analyzed using Wireshark.


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f36fd64-1004-40b7-a7d1-04d89c9684be" />


# What is TCP?

Transmission Control Protocol (TCP) is a Layer-4 (Transport Layer) protocol that provides reliable communication between two devices.

Unlike UDP, TCP guarantees:

Reliable packet delivery
Ordered packet delivery
Error detection
Flow control
Congestion control

Most web browsing (HTTP/HTTPS), email, SSH, FTP, and many other services rely on TCP.

# Packet Information

The selected packet in this capture shows a TCP segment exchanged between a client and a server.

Example values from the capture:

Source Port: 54701

Destination Port: 443 (HTTPS)

Flags: ACK

Sequence Number: 52

Acknowledgement Number: 41

The destination port 443 indicates encrypted HTTPS communication.

# Understanding TCP Control Flags

TCP uses control flags to manage the entire lifecycle of a connection.

Think of these flags as instructions that tell the receiving device what should happen next.

# 1. SYN (Synchronize)
## What is SYN?

The SYN flag is used to start a new TCP connection.

It synchronizes the sequence numbers between the client and the server before data transmission begins.

A TCP connection starts with the famous Three-Way Handshake.

Client -------- SYN --------> Server

Client <---- SYN + ACK ------ Server

Client -------- ACK --------> Server

After this process, both devices are ready to exchange data.

## Purpose
Initiates a TCP connection
Synchronizes sequence numbers
Begins the Three-Way Handshake
# 2. ACK (Acknowledgement)
## What is ACK?

The ACK flag confirms that data has been successfully received.

Whenever a device receives data, it sends an ACK back to the sender.

This is how TCP guarantees reliable communication.

In the captured packet:

Flags: ACK

This means the receiver is acknowledging previously received data.

## Purpose
Confirms successful packet delivery

Ensures reliable communication

Used in almost every TCP packet after the connection is established

# 3. FIN (Finish)
## What is FIN?

The FIN flag is used to gracefully terminate a TCP connection.

When one device has finished sending data, it sends a FIN packet.

The receiving device acknowledges it before closing the connection.

Example:

Client ------ FIN ------> Server

Client <----- ACK ------ Server

Server ------ FIN ------> Client

Server <----- ACK ------ Client

This process ensures that all remaining data is delivered before the connection closes.

## Purpose
Gracefully closes a TCP connection

Prevents data loss during connection termination
# 4. RST (Reset)
## What is RST?

The RST (Reset) flag immediately terminates a TCP connection.

Unlike FIN, it does not wait for remaining data.

RST packets are commonly seen when:

The destination port is closed
An application crashes
An invalid connection is detected
A firewall blocks the connection
## Purpose
Immediately aborts a TCP session
Used for unexpected or invalid connections
# 5. PSH (Push)
## What is PSH?

The PSH (Push) flag instructs the receiver to immediately deliver the received data to the application instead of waiting for additional packets.

This is useful for interactive applications such as:

SSH
Telnet
Remote Desktop
Chat applications

Without PSH, TCP may buffer data before passing it to the application.

## Purpose
Sends data immediately to the receiving application
Reduces latency for interactive communication

# Packet Analysis

From the captured packet, we can observe:

✔ Protocol: TCP

✔ Destination Port: 443 (HTTPS)

✔ TCP Flag: ACK

✔ Sequence Number: 52

✔ Acknowledgement Number: 41

✔ Header Length: 20 Bytes

✔ TCP Segment Length: 0 Bytes

This indicates that the packet is acknowledging previously received data, and no additional payload is being transmitted in this segment.

# Understanding the TCP Three-Way Handshake

Before data transmission begins, TCP establishes a reliable connection using the Three-Way Handshake.

Step 1

Client ---------------- SYN ----------------> Server

Step 2

Client <----------- SYN + ACK -------------- Server

Step 3

Client ---------------- ACK ----------------> Server

After the handshake is complete, both devices begin exchanging application data.

# Learning Outcomes

After completing this project, you will understand:

The role of TCP in network communication
How TCP establishes reliable connections
The purpose of the SYN, ACK, FIN, RST, and PSH flags
How to identify TCP control packets in Wireshark
How Wireshark decodes TCP packet headers for analysis
# Tools Used
Wireshark

Windows 11

TCP/IP Protocol Suite

HTTPS Traffic Capture
