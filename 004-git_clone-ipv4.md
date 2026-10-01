### [001] - [git clone - ipv4 only]

- Date 2026-10-01
- Category: Networking/Linux/Deployment/NGINX/Docker/security/ e.t.c
- Status: Solved

## Context
I am trying to set up my code and tech stack on the vps via docker 
and most importantly getting my code onto the server was going to utilise 
git to clone my repo

## The Problem
the git clone command for cloning the repo kept
reporting not working.



## Symptoms
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
    git repo not reachable after 3s of trying to connect to the server
</div>

## Investigation

# What i checked
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
 ping -6 google.com - this succesfully pinged google.com

 ping -6 github.com - this kept failing at every run
</div>

# What i discovered
i had thought maybe my vps was having connectivity problems
but after pingin google accordingly. it was obvious that github
was the problem and must not support ipv6 connections and so
git wasnt a viable route to get my code unto my laptop.

## Solution
As git clone isn't an option via ipv6 connectivity.
i jxt decided to transfer my code and tech stack off my laptop unto 
the vps via scp and it worked


### THINGS WORTH REMEMBERING 
test connectivity to each of these serices to know which of them i can actually connect to
and make use of their services

## What i'd do next time
Ping and nslookup the dns of these core services if my server can actuall connect to them via
it constraint ipv6 connectivity.
