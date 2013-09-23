# DERAT: Default Encrypted with Retroactive Application of Trust

*(Suggestions for name/acronym improvements are welcome.)*

## Problem

Asymmetric encryption systems based on a peer-to-peer public-key infrastructure (as opposed to a central certificate authority) require the user to authenticate public keys through a secure channel. For example:

- Web browsers that encounter a self-signed SSL certificate ask the user to manually verify its authenticity before proceeding.
- `ssh` asks that the user verify the key fingerprint of servers it hasn't seen before, before it will continue to connect.
- `pidgin` will ask the user to verify a self-signed certificate upon every single connection, even if that certificate has not changed.
- FIXME: `pgp`/`gpg` example

However, users are frequently too busy or not knowledgeable enough to make this decision. These users will dismiss dialog boxes with a guess or with whichever answer allows them to continue working.

Some software exacerbates this problem by failing to remember the user's response, so the user becomes habituated to clicking "accept" without carefully re-verifying the certificate for every connection.

An attempt to address this problem called *Trust On First Use,* or TOFU, is to have client software simply remember the user's choice, and to complain loudly if a certificate changes after that initial choice. A changed certificate means either:

- The initial connection and all subsequent connections until now were compromised, or
- The initial connection and all subsequent connections until now were secure, but an attack is occurring now, or
- The server has changed its certificate without warning its clients.

Implementations of `ssh` have worked like this for a long time, but browsers have been slow to catch up.

*Trust On First Use* provides a modicum of better security since an attacker who wishes to go undetected would have to ensure they compromise the very first connection attempt the user makes. It allows the client software to complain more loudly and put more barriers in place against a user promiscuously accepting changed certificates.

However, the user interfaces provided to the user tend to do a poor job of explaining the risks and possible attack vectors involved, and users are already habituated to dismissing or ignoring them without verification. 

## Solution

I propose that asymmetric encryption systems adopt the following:

1. "Accept" all certificates by default, enabling encryption and signatures, but continue to present the connection as "insecure" or the data as "not verified authentic" to the user.

2. Provide a "secure this connection" mechanism that the user may take at any time after a certificate has been processed.

3. Guide the user with instructions for establishing a secure channel. Do not provide a "Yes/No" dialog; instead require user to enter a correct fingerprint code or other low-bandwidth human-friendly authentication mechanism. Remind the user not to receive such communications over unsecured e-mail or web, and to verify credentials such as government-issued IDs if possible, etc.

4. If the fingerprint is correct, the connection is presented to the user as secure *and so are all prior connections.*

5. If the certificate changes after having been accepted without a signed revocation, it should be *rather difficult* to repeat this process with a new certificate. If communications continue they should be marked as "insecure and possibly actively compromised."

With this system in place:

- `ssh` connections to other machines in your secure local LAN occur with no messing around with "accepting host certificates." You can confirm for yourself that the connection is authentic when you get around to it.

- `ssh` servers that wish to enforce secure connections may do so at their option, causing clients to display to users "you must authenticate this connection before proceeding."

- In most cases, authentic e-mail exchanges will occur in privacy with no mental overhead for users. They may one day retroactively verify the security of their conversation if it becomes important. If the first communication happened to be not under attack, their conversation will be private regardless of whether they confirm that it was.

- We sites may continue to use their "broken lock" iconography while providing more security for lazy users, until such time that e.g. credit card numbers or passwords are required. At that time they may invoke the "you must authenticate this connection before proceeding" along with recommendations of how to obtain their certificate fingerprint securely.

## More about Trust Upon First Use

- [Wikipedia: Dotdotike/Trust Upon First Use][]
- [Moxie Marlinspike mentions TUFU at Defcon 18][tufu-defcon-18]
- [Perspectives project][Perspectives]
- Wendlandt, Andersen, Perrig. _Perspectives_: [Improving SSH-style Host Authentication with Multi-Path Probing.][WeAnPe2008] Usenix ATC 2008.

[Wikipedia: Dotdotike/Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use
[tufu-defcon-18]: http://www.youtube.com/watch?v=DIPrkVys72I
[Perspectives]: http://www.networknotary.org
[WeAnPe2008]: http://www.networknotary.org/perspectives_usenix08.pdf
