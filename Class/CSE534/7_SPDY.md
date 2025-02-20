---
layout: post
title: SPDY
tags:
  - networks
---
# TCP Performs Poorly In...

- In wireless networks where loss are not due to congestion
- When bandwidth is large and RTT is large
	- A large more packets can fit in the pipe but TCP is too slow
- In datacenters that require small delays
- During buffer bloat
	- Network queues are long, keep sending packets under the perception that there is no congestion

# Random Early Detection (RED)
- Routers proactively drop packets in queues to reduce congestion

# SPDY
- Multiplexing keeps the pipes full
	- Better utilization of the pipe

However, SPDY does not perform that well when there is loss. On loss, the entire pipe's cwnd is reduced by half while in HTTP, each flow gets its own pipe with its own cwnd.

SPDY always run with SSL.

# BBR

The goal of BBR is to calculate how fast the router can process packets so that the queue size is always 0. 


![[BBR]]

The optimal point is MAX(DELIVERY_RATE) * MIN(RTT).

BBR can be unfair to TCP cubic flows
- Cubic will take less thinking the bandwidth is low while BBR takes more thinking there's more when cubic backs off
Cubic can takeover in high buffer conditions
- It will keep increasing.