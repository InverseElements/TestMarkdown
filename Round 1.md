# Play for Malware Download via Email
## Detection
Typical deection mechanisms incude:
1. IDS picking up signature or heuristics on endpoint or across network
1. IPS nuking comms back to CnC server or attempting to pull down payload
1. Users calling having opened something and only realising after the fact that it's bad (usually after several attempts to make it go)

### heading 3

## Reaction
1. Quarantine machine (advanced IP null routing if available, locking it down to just security PC's accessible via, or pull the network cable.)
1. Grab sample of bad and submit to sandbox (or get underling to run in sandbox and report results of execution / behavioural analysis / IOC list) 
1. Find entry point and close it off:
  1. Find sending email address, search logs for similar
  1. Find subject, search logs for similar
  1. Find attachment name, search logs for similar
 
  Once you have the above, build patterns, compare to legitimate traffic, and block it. Search back through logs as far back as you reasonably can to look for previous campaigns you may have missed. Speak to your exchange guys to find other maisl that made it through and have them removed from mailboxes, reporting on read / unread if possible.

1. Sandbox analysis complete, apply IOC to all machines and see if anyone else has opened it - quarantine further identified compromised machines as appropriate.
1. If it does attempt calls to external resources, block this access
1. If it talks to CnC, look for DGA's and apply to logs
1. If static calls, look for these entries in logs to identify further compromised machines.
