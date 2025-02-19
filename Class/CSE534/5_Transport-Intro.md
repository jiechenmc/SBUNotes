---
layout: post
title: Transport Layer
tags:
  - networks
---
# Properties

- Bi-directional
- Stream based/connection orientated
- Maintains state per connection

# Abstractions of the Transport Layer

### End to End Connection
- Provides an abstraction that 2 computers are connected.

On the sender side, there is a `send buffer` that holds data until NIC is free.

On the receiver side, there is a `recv buffer` that will wait for packets. Say if packet #2 arrived, it will wait for #1 before sending it up to the applications.

#### How can we avoid duplicates and delayed packets?
- ACK
- The server responds with what packets it expects next.

![[TCP-CumAck]]

### De-multiplexing
- Figures out what where the packet should go to by using 
the ports from the packet. Precisely <src_ip, dest_ip, src_port, dest_port>.

### Teardown

TCP provides a “symmetric” close  
– both sides shutdown independently  
– Why? This ensures that data is delivered.

### Reliability

- Will try to send reliably 
- If not, then it will not send at all

There's 2 main ways to ensure reliability:
- Forward Error Correction (FEC) - Mostly on the lower layers
	- Sends extra information to reconstruct a packet when packets get lost.
- Automatic Repeat Request (ARQ) - Mostly on the higher layers
	- No ACK? Retransmit.
	- Pipeline and send all packets.

# Bandwidth Delay Product
- The theoretic maximum number of packets you can send before getting an ACK.

# Sliding Window Size
- How many packets to send before I get an ACK.

Finding the right sliding window size is hard: 
- **too small and you need to stop and wait**
- **too big, there will be buffer issues and packet loss.**

# State maintained by TCP
- What packets has been sent, active connections, cwnd, ssthresh, etc.


