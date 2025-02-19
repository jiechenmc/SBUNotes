---
layout: post
title: TCP Congestion Control
tags:
  - networks
---
# What is congestion?

When processing time in the router >> incoming rate of packets.
- Congestion occurs and there is packet loss

If you have too much retransmission and congestion, the network will collapse.

# Flow Control

Receiver tells the sender how big their buffer is, this is called advertised window.

# Router Queues

If the queue size is big, then the queueing delay is higher.
- Your packets will sit in queue longer, waiting for transmission

If the queue size is small
- More packet loss will occur

# TCP Congestion Control

TCP uses dynamic adjustment
- Uses probes to estimate level of congestion

Speeds up when congestion is low, and slows down when congestion is high. Packet loss are used as an indicator for congestion.

### TCP Tahoe
![[TCP-Tahoe]]
1. Slow start
2. Congestion Avoidance
3. When RTO, ssthresh = cwnd/2 and cwnd = icwnd

RTO is about 2RTT
 
Why not ssthresh = ssthresh/2? Because we now have more information about the network!  The old threshold is useless.

In this example, icwnd = 1 and ssthresh = 64

After you hit the threshold, you start incrementing by 1.

# TCP Reno

Basically TCP Tahoe, but When a Triple-Duplicate-ACK (TDA) is received ssthresh = cwnd / 2 and cwnd = cwnd /2. This change is called fast retransmit.

 