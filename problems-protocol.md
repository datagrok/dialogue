# Protocol Design

## Problems with SMTP

- **Storage.** Traditional e-mail models a store-and-forward post office system. The burden is on the recipient to accept all mail and store it until processing. Per DJB's [Internet Mail 2000][], "mail storage should be the sender's responsibility."
- **Forged headers.** One of the main reasons spam e-mail is so difficult to deal with is because mail headers are completely untrustable. Mail should be authentic (cryptographically signed) at all times.
- **Snooping**. Seasoned internet users know that credit card numbers cannot be sent through e-mail. New users do not and sometimes get burned. Mail should be private (encrypted) by default.
- **Abstractions.** Instant messages, message boards, Usenet, SMTP e-mail, blogs, and RSS feeds are all variations on the theme of "send a message through the Internet to one or a number of recipients." I propose that all of the use cases that these disparate protocols provide could be implemented using a single protocol, within a single interface.
- **Imprecise requirements.** It is notoriously difficult to build a parser and validator for an internet e-mail address. The base level of functionality should insist on strict conformance to the published spec. Spec should be designed with ease of implementation in mind.

## Other Work

Most of the protocol ideas were spawned investigating DJB's proposal for [Internet Mail 2000][]. There have been many attempts to build an Internet Mail 2000 implementation:

- [Jonathan de Boyne Pollard, "Fleshing out IM2000"](http://homepages.tesco.net./~J.deBoynePollard/Proposals/IM2000/)
- [Aaron Swartz's Proposal](http://www.aaronsw.com/2002/im2000)
- [Jorge Lehner's Notes and Software](http://www.magma.com.ni/~jorge/index_2.html)
- [StubMail][] by Meng Weng Wong and Julian Haight.

Many others have hit upon similar ideas:

- [Reinventing Email using REST][]: "You can see how REST blurs the boundaries between applications and could obliterate the boundary between 'the web' and email."
- [email init][], a proposal by a blogger named Brent Simmons that saw a brief surge of interest. I think the proposal captures the feeling that many "power users" wish for better electronic mail, but it falls flat right out of the gate with a myopic insistence on a proprietary user interface toolkit and the reliance on an existing mail transfer protocol.
- ...

[Internet Mail 2000]: http://cr.yp.to/im2000.html
[Reinventing Email using REST]: http://www.prescod.net/rest/restmail/
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[email init]: http://inessential.com/2010/01/16/email_init
[StubMail]: http://www.stubmail.com

## Pervasive goals

- Messages should be private (encrypted) and authentic (signed) by default.
- [Trust Upon First Use][]: Signed messages from unknowns should not trigger a "make a decision now!" dialog. Instead, the system should inform the user that the message remains unauthentic, provide simple instructions about how to securely authenticate a sender, and complain loudly if a certificate changes unexpectedly.

[Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use
