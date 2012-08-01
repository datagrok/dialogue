# Messaging

A protocol for sending messages over the Internet.

There are several annoyances with the state of electronic communication today. I think the problems and solutions may be conceptually divided into three areas:

1. [Protocol](problems-protocol)
2. Public-key Security Infrastructure
3. [User Interface](problems-interface)

The issues are interrelated. Fixing the protocol requires a useful public-key security infrastructure in place. A useful security infrastructure requires an intuitive user interface for managing contacts. Et cetera.

## Protocol Design Decisions

- Messages are private (encrypted) by default.
- Messages must be authentic (signed).
- [Trust Upon First Use][]: Signed messages from unknowns should not trigger a "make a decision now!" dialog or immediate rejection of the message. Instead, the system should inform the user that the message remains unauthentic, provide simple instructions about how to securely authenticate a sender after-the-fact, and complain loudly if a certificate changes unexpectedly.
- Mail storage is the sender's responsibility. Per DJB's [Internet Mail 2000][]. Messages are held by the sender until the recipient elects to retrieve them.

## SMTP features to keep

Innumerable other communication systems have appeared since 1982, when the SMTP protocol was published in [RFC 821][], yet SMTP remains the standard for Internet mail and the basis which all other successful protocols build upon. There are several aspects of the legacy SMTP that I maintain:

- **Internet mail is a protocol, not a piece of software.** The most important thing that I hope to produce with this project is an open and free specification that any programmer may use to create software compatible with any other implementation of the same specification.
- **Internet mail does not require an authority.** Anyone may compile and run an e-mail server. Anyone may send mail to anyone else with nothing more than an Internet connection. ISPs frequently provide e-mail servers as a convenience, but we could get by without them if necessary. Trust systems sometimes specify an authority, but I will employ those that make trust authorities optional at best by relying on networks of trusted peers.
- **Internet mail encapsulates messages of any format.** An SMTP message may contain a body of any content; there are no restrictions about what it may contain. Though I intend to also develop improved data formats that can support the improvement of user interfaces for messaging, a message delivery protocol will not insist that it be used.
- **Internet mail may be deployed locally or globally.** Organizations may run their own private mail systems which are disconnected from the Internet at large. No matter how good my implementation is, I'm not going to convince anybody while "everyone" still uses SMTP. I hope that, like XMPP, the system may be useful enough to deploy on smaller scales, perhaps with software bridges to traditional e-mail systems.

[RFC 821]: http://www.faqs.org/rfcs/rfc821.html

[Internet Mail 2000]: http://cr.yp.to/im2000.html
[Project Xanadu]: http://xanadu.com
[Reinventing Email using REST]: http://www.prescod.net/rest/restmail/
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[email init]: http://inessential.com/2010/01/16/email_init
[StubMail]: http://www.stubmail.com
[Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use

## License

- All documentation herein is [GNU Free Documentation License][] v1.3 unless otherwise noted.
- All source code herein is [GNU Affero General Public License][] v3 unless otherwise noted.

[GNU Free Documentation License]: http://www.gnu.org/licenses/fdl.html
[GNU Affero General Public License]: http://www.gnu.org/licenses/agpl.html
