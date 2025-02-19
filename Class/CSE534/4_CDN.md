---
layout: post
title: CDN
tags:
  - networks
---
# Local Caching
- stores in local cache; no need to visit origin server.
# Proxy Cache
- cached by ISP, institutions

```mermaid
flowchart LR

Client --> Intermediate["Proxies"]
Intermediate --> Origin_Server[Origin Server]
Origin_Server --> Intermediate
Intermediate --> Client

```

# CDN
- Global cluster of caches that can server as a local cache for static objects.

It uses DNS to find the nearest server to serve content.

![[CDN]]

The client IP is then compared to find the nearest server.