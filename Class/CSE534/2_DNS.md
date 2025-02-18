---
layout: post
title: DNS
tags:
  - networks
---
If the answer is not cached in the local DNS server, then the typical resolution will go as follows: Root -> TLD -> ... -> Authoritative NS

![[DNS-Query]]

There's 2 methods of querying: iterative and recursive. In an iterative query, the NS will tell the client where to go next. In a recursive query, the load will be on the NS because they will ask each other and return the answer to the client.