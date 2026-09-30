### [001] - [Postgres- wal limit crash-postmortem]

- Date 2026-09-30
- Category: Networking/Linux/Deployment/NGINX/Docker/security/ e.t.c
- Status: Solved


## Context
after my first attempt to optimising the url-shortener the postgres
container via docker kept failing


## The Problem
MY postgres container kept reporting that it was ubhealthy and not fit to run
wish led the whole app to fail as i set the app up to behave.

## Symptoms
<div style="padding:15px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); border-radius:5px; background-color:#f9f9f9;" >
    postgres - Unheathy 
    redis - healthy and ready for connections

</div>


## Investigation

# What i checked
i checked my docker apps logs to uncover what was actually up with
postgres

# What i discovered
i found out that due to the fixed memory limit and swap memory limit
i had set up against postgres's Write Ahead Log (WAL) and it was too
much of a constraint for postgres that it just did not launch.

## Solution
i removed the entire constraint on the Wal both swap mem limit and mem limit

### THINGS WORTH REMEMBERING 
by me removing these limits (**memory limit**, **swap memory limit**)
it introduced tradeoffs that i now have to leave with for this stack to run on the vps

## Trade-offs - that have been introduced
Postgres not having a limit on its Wal introduces the foresight of an OOM on the server
if postgres is put under write load, which will bring OOM killer to killing some of the vital processes
to run my app

## What i'd do next time
bigger ram, but this is a lab and the smaller ram is part of the labs constraints.