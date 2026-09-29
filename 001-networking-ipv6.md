### [001] - [Networking - ipv6 only/ ipv4 only]

- Date 2026-09-29
- Category: Networking/Linux/Deployment/NGINX/Docker/security/ e.t.c
- Status: Solved

## Context
This is the first time i'm trying to connect to my server or the first time connecting to a server in my life but i
quickly realised that my $6 VPS as stated at purchase was an ipv6-only vps
which meant neither my laptop nor my mobile phone by themselves cannot access it because they both 
only supported ipv4 connections

## The Problem
the main problem was out the box my laptop didnt support ipv6 which
i thought a quick fix could be to set-up **HYPER-V MANAGER** and 
set-up a virtual switch so i could port to ipv6 via it.
Both my laptop was ipv4 native and that virtual switch just didnt work.

## Symptoms
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
<b>ping -6 2606:4700:4700::1111</b>

Pinging 2606:4700:4700::1111 with 32 bytes of data:
PING: transmit failed. General failure.
PING: transmit failed. General failure.
PING: transmit failed. General failure.
PING: transmit failed. General failure.

Ping statistics for 2606:4700:4700::1111:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

</div>

## Investigation

# What i checked
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
    ping -6 google.com - failed repeatedly

    ping -4 google.com - passed at every instance

    Test-NetConnection 1.1.1.1 -Port 443 - Passed the first 5 TCP hops then i quit it

    curl.exe -6 https://ifconfig.me - Failed at every instance
</div>

# What i discovered
i originally thought that because i had set-up a virtual ipv6 switch
i could maybe run TCP connections via ipv6 but i was completely wrong
and **curl.exe -6 https://ifconfig.me** proved it to me.

## Solution
1st solution i came up with was so run a ipv4 -> ipv6 Tunnel via
**Hurricane Electric's** 6in4 tunnel but with some digging i discovered
to run it i need to have ipv4 protocol 41 allowed and that won't be possible 
because my home router has me under a NAT and will block such a protocol

2nd Solution i landed at sticking to mt ipv4 only laptop and ipv6 only server
both seperate from each other but introduce **tailscale** which can handle communication
between both machines even with NAT involved.


### THINGS WORTH REMEMBERING 
**ipv4 are ipv6 two very different things and don't communicate with each other**

## What i'd do next time
i would check the VPS connectivity and brace myself to wire up the
suitable networling to work with the machine or decide on another 
architecture for accessing the system, maybe a second Vps and split my services amongst them.

