# Dialogue Protocol

## Core concept

This mechanism is essentially [Internet Mail 2000]:

Messages are stored on the sender's always-online mail server.

The sender's mail server sends a small notification message to the recipient's mail server.

When the recipient wishes to retrieve their waiting message, they contact the sender's server and download the message.

The sender's server, upon confirming a successful transfer, may elect to delete the message to conserve disk space.

## Sending to a group

A message meant for a group of recipients may be stored just once on the sender's mail server.

The sender's server would not elect to delete the message until all the recipients confirm a successful transfer.

## Mailing lists

The sender's server might elect never to automatically clean up a message, instead making a set of messages able to be retrieved by recipients added later. "Mailing lists" become having your mail client periodically check for new messages at a particular location. 

## Content-addressable mail storage

If the server makes messages accessable by their hash value, it becomes trivial to distribute that data, and to serve it.

## Replies reference the original message

When one replies to a message, the hash value of the original message is included in the reply.

## Signatures and Privacy

All messages are signed and encrypted by default

## Partial message retrieval

Messages are collections of messages referenced by their hash value. A client may elect to retrieve only part of a message if it has already cached other parts, or none at all.

## Questions


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
