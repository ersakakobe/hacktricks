---
description: >-
  Windows New Technology LAN Manager (NTLM) is a suite of security protocols
  offered by Microsoft to authenticate users’
---

# What Is NTLM Used For?

* NTLM is a **single sign on (SSO)** tool that relies on **a challenge-response protocol** to confirm the user without requiring them to submit a password.
* Despite known vulnerabilities, NTLM remains deployed even on new systems in order to maintain compatibility with legacy clients and servers.&#x20;
* Kerberos protocol is Microsoft’s default authentication method today, NTLM serves as a backup. If Kerberos fails to authenticate the user, the system will attempt to use NTLM instead.



**NTLM authentication** process:

1. The user shares their username, password and domain name with the client.
2. The client develops a scrambled version of the password — or hash — and deletes the full password.
3. The client passes a plain text version of the username to the relevant server.
4. The server replies to the client with a challenge, which is a 16-byte random number.
5. In response, the client sends the challenge encrypted by the hash of the user’s password.
6. The server then sends the challenge, response and username to the domain controller (DC).
7. The DC retrieves the user’s password from the database and uses it to encrypt the challenge.
8. The DC then compares the encrypted challenge and client response. If these two pieces match, then the user is authenticated and access is granted.



### The Difference Between NTLM and Kerberos? <a href="#ntlm-vs-kerberos" id="ntlm-vs-kerberos"></a>

* NTLM relies on a three-way handshake between the client and server to authenticate a user.&#x20;
* NTLM relies on **password hashing**, which is a one-way function that produces a string of text based on an input file
* Kerberos uses a two-part process that leverages a ticket granting service or key distribution center.
* Kerberos leverages **encryption**, which is a two-way function that scrambles and unlocks information using an encryption key and decryption key respectively.



#### Why Was NTLM Replaced by Kerberos?

In NTLM, passwords stored on the server and domain controller are not “**salted**”&#x20;

* meaning that a random string of characters is not added to the hashed password to further protect it from cracking techniques.&#x20;
* adversaries who possess a password hash do not need the underlying password to authenticate a session.&#x20;
* systems were vulnerable to **brute force attacks**, which is when an attacker attempts to crack a password through multiple log-in attempts. If the user selects a weak or common password, they are especially susceptible to such tactics.



### NTLM Challenges <a href="#benefits-and-challenges" id="benefits-and-challenges"></a>

* **Single authentication.** NTLM is a single authentication method. It relies on a challenge-response protocol to establish the user. It does not support [multifactor authentication](https://www.crowdstrike.com/cybersecurity-101/multifactor-authentication-mfa/) (MFA), which is the process of using two or more pieces of information to confirm the identity of the user.
* **Security vulnerabilities.** The relatively simplistic form of password hashing makes NTLM systems vulnerable to several modes of attacks, including [pass-the-hash](https://www.crowdstrike.com/cybersecurity-101/pass-the-hash/) and [brute-force attacks](https://www.crowdstrike.com/cybersecurity-101/brute-force-attacks/).
* **Outdated cryptography.** NTLM does not leverage the latest advances in algorithmic thinking or encryption to make passwords more secure.

#### How Can You Protect Your Network Using NTLM?

Given the known security risks associated with NTLM, CrowdStrike recommends that organizations try to reduce NTLM usage in their network as much as possible.

For organizations still relying on NTLM for compatibility reasons, CrowdStrike offers the following recommendations to enhance security and minimize risk.

1. **Enforce NTLM mitigations.** To be fully protected from NTLM relay attacks, you will need to enable server signing and EPA on all relevant servers.
2. **Patch!** Make sure your systems are fully protected with the latest security updates from Microsoft.
3. **Use advanced techniques.** Apply advanced NTLM relay detection and prevention techniques similar to the ones disclosed by Preempt (now CrowdStrike) in our Black Hat 2019 talk.
4. **Identify weak variations.** Some NTLM clients use weak NTLM variations (e.g., don’t send a MIC). This puts your network at a greater risk of being vulnerable to NTLM relay.
5. **Monitor NTLM traffic in your network.** Try to restrict insecure NTLM traffic.

Get rid of clients sending LM responses and set the Group Policy Object (GPO) network security: LAN Manager authentication level to refuse LM responses.

\
[https://www.crowdstrike.com/cybersecurity-101/ntlm-windows-new-technology-lan-manager/](https://www.crowdstrike.com/cybersecurity-101/ntlm-windows-new-technology-lan-manager/)\
