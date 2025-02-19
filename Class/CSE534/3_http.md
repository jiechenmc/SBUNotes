---
layout: post
title: HTTP
tags:
  - networks
---
Networks are "best effort".
- Try to send a packet, but if it cannot, then no packet is sent.
- More scalable because you won't be stuck in a retry loop for a packet that cannot be sent.

# Redirection

If something that changes often, we would abstract it so lower levels can change freely

# Hierarchy

Makes things scalable.

# HTTP
![[HTTP]]

HTTP/1.0 1 RTT per request
HTTP/1.1 parallel, pipeline, persistent


## HTTP/1.1

In practice, only parallel and persistent is used.

Parallel - make multiple TCP connections at once (up to 6). 
Persistent - keep-alive
Pipeline - allows next request(s) to be sent without waiting for response.

### HOL Blocking

- Servers respond in FCFS order and if you request for a big object before a smaller one, the bigger object may block the entire transmission.

## HTTP/2

- Instead of making 6 parallel TCP connections, the packets are sliced up and multiplexed in 1 TCP connection.
- Allows servers to initialize web object transfer
- Can compress headers and payloads

# What are some performance metrics?

1. RTT - latency, request to first bit from response; Fiber go fast, Satellites are slow.
2. Accuracy
3. Throughput - how fast and how much
4. Bandwidth - how much

* If 1 bit transfers fast, but 100 bits slow it down, then the throughput is low.