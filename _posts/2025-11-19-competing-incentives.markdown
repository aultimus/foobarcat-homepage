---
layout: post
title: "Security vs Engineering - Competing Incentives"
---

This morning I tried to upload a custom camera-firmware build via Slack to unblock a colleague. Instead of a normal upload, Slack responded with:


!['Your file couldn't be uploaded:This file may contain a virus or other malware and can’t be uploaded to Slack.']({{ site.baseurl }}/images/slack_file_upload_error.png)


A workplace admin had seemingly disabled binary uploads to slack. 
I tried renaming the file: blocked.  
I tried zipping it: blocked.

So I explored alternatives. After a short detour into external tools and public file-sharing services, it became clear that many of the quickest options were actually **less secure** than simply letting engineers share binaries via slack. The “approved” options — enterprise shared drives and permission-managed portals — were workable but cumbersome. What should have been a routine 10-second action turned into a small productivity sink.

Rather than treat this as a complaint, I realised it’s a clean, real-world illustration of a broader dynamic: **how misaligned incentives inside an organisation can produce outcomes nobody intended.**

Consider the two functions involved:

- **Engineering**, incentivised to move quickly, unblock teammates, ship features and provide value to the user.
    
- **Security**, incentivised to reduce risk and prevent incidents.
    

Both incentives are legitimate. Both responsibilities matter. But they naturally pull in different directions. And when a policy like “block all binaries” is introduced, the tradeoff becomes asymmetric:

- To security, the change looks entirely beneficial: fewer risky files, fewer vectors.
    
- To engineering, the change carries a hidden cost: added friction, slower iteration, and the temptation to route around official channels.
    

Because security incidents are highly visible and inefficiency is largely invisible, organisations often treat these decisions as if they were cost-free. From a non-technical perspective, “more security” sounds like purely positive progress. But every safeguard has a price — not in money, but in time, momentum, and behavioural side-effects.

This is how systems drift, quietly and unintentionally, toward over-restriction.  
No one chooses that endpoint; the incentives simply nudge the organisation in that direction.

And once friction gets high enough, people start creating workarounds. Not because they’re reckless, but because they’re trying to do their jobs. Ironically, these workarounds often introduce more risk than the original behaviour the policy attempted to prevent.

Security lives on a curve of diminishing returns:

- Too little security → real danger
    
- Just enough security → a healthy, productive organisation
    
- Too much security → stagnation and shadow tools
    

We see the same pattern in many domains: well-intentioned controls create knock-on behaviours that undermine the original goal. It’s not a failure of individuals — it’s a consequence of how incentives shape behaviour.

So what breaks the cycle?

Leadership that understands the tradeoff — leadership that can see both the visible risks and the invisible costs.
Leadership that invites Engineering and Security to challenge creeping friction before it calcifies into culture.
And Security and Engineering working as partners, not opponents.

This article is just a small introduction. In future pieces, I’ll explore incentives more deeply — showing how they quietly shape organisational behaviour, and how thoughtful incentive design can resolve undesirable outcomes and help organisations achieve their goals far more effectively.