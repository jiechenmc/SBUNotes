---
layout: post
title: Event Loop
tags: node.js
---

setTimeOut won't be exact

the poll phase controls the timer phase

check phase comes right after poll phase

**Typical event loop run**

if poll queue is empty:
   run any immediate calls in the check phase
   wait for timer phase
   
else:
  run things in the poll queue
  as things are getting ran, check for time has passed
  if a time has been met for a timeout, then that timeout will be ran
  
  IMMEDIATES WILL ALWAYS RUN BEFORE TIMER
  
  run immediate calls in the check phase
  clear out timer queue

