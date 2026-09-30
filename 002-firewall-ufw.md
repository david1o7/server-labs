### [002] - [Firewall- setup & ufw]

- Date 2026-09-30
- Category: Networking/Linux/Deployment/NGINX/Docker/security/ e.t.c
- Status: Solved

## Context
i had SSH'ed in my server just yesterday, my main goel was to explore the system: 
its processes, its ip address, its file system but today my goal is to setup
security atleast basic security

## The Problem
My server was completely an open box, anything could gain or get access 
into it via ports and thats a problem.

## Symptoms
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
    no firewall configs

    no firewall setup

    no baseline ACL

    naked ports which allow incoming traffic

</div>

## Solution
i started digging online for linux firewall set-up ubuntu preferrably
as i run ubuntu and i stumbled on **ufw** Aka (uncomplicated firewall)
which comes shipped with ubuntu but it's defaulty disabled and needs the
user to enable it within their server.

I read some documentation on it from the ubuntu official webpage
and also some help from some custom tutorial reads

### THINGS WORTH REMEMBERING 
**configuring firewalls is imprtant and helps to ensure you have the right ports blocked**
and what is allowed within your systems network and what isnt.

## What i'd do next time
Maybe next time i would spend more time learning about the lower level kernel firewall implementions
like: **iptable & nftable**
which Ufw extands as a frontend to making firewall configuration easier