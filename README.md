# Messaging

There are several annoyances with the state of electronic communication today. I think the problems and solutions may be conceptually divided into four areas:

1. Protocol
2. Security Infrastructure
3. User Interface for Contacts
4. User Interface for Conversations

The issues are interrelated. Fixing the protocol requires a useful security infrastructure in place. A useful security infrastructure requires an intuitive user interface for managing contacts. Et cetera.

Fixing the user interface for conversations may be an impossible morass. Luckily, since the protocol is agnostic about what data we ship through it, we might attack this last. Or there might be many viable solutions. It might be better considered an independent project. I include it here because my proposals depend on features of my proposed protocol.

## Problems

Traditional Internet e-mail suffers from problems in both protocol and user interface.

### Protocol Problems

- **Storage.** Traditional e-mail models a store-and-forward post office system. The burden is on the recipient to accept all mail and store it until processing. Per DJB's [Internet Mail 2000][], "mail storage should be the sender's responsibility."
- **Forged headers.** One of the main reasons spam e-mail is so difficult to deal with is because mail headers are completely untrustable. Mail should be authentic (cryptographically signed) by default.
- **Snooping**. Seasoned internet users know that credit card numbers cannot be sent through e-mail. New users do not and sometimes get burned. Mail should be private (encrypted) by default.
- **Abstractions.** Instant messages, message boards, Usenet, SMTP e-mail, blogs, and RSS feeds are all variations on the theme of "send a message through the Internet to one or a number of recipients." I propose that all of the use cases that these disparate protocols provide could be implemented using a single protocol, within a single interface.
- **Imprecise requirements.** It is notoriously difficult to build a parser and validator for an internet e-mail address. The base level of functionality should insist on strict conformance to the published spec. Spec should be designed with ease of implementation in mind.

### Interface Problems

The more I think about how to implement solutions, the more it seems like one must replace the whole Internet to fix them. Of course this is a fool's errand, but surely things must be able to be incrementally improved. 

- **Context in a conversation is fluid.**
	- A "message" may contain one or several points that may elicit a response. A "message" is not an atomic unit of conversation, but most existing clients treat them as such.
	- A message's subject or topic may vary over the course of the conversation, changing many times within one message or gradually over the course of multiple messages. Many traditional e-mail clients group messages by "subject" so it becomes important to avoid modifying the "subject" line even if the subject has changed.
	- Responses may be made to an abstract idea formed from the collection of many disparate points across times and sources, and may be presented out-of-order. Many do not take the trouble to reference text in their reply because user interfaces do not make it easy to do so. Even those who practice [interleaved posting][] sometimes find it difficult to manage which points within a message thread have and have not been replied to, and some may be unintentionally ignored.
	- A medium like instant messaging or IRC avoids this too-much state problem, but makes it difficult to coordinate multiple topics of conversation simultaneously.
- **References to other messages and published text.**
	- Hypertext links are one-way. 
	- One can't easily reference a specific version of published text.
	- One can't easily reference a specific location within published text unless that text provides anchor markup.
- **Managing multiple participants.** Large threads of messages quickly become unwieldy. 
- **Contact management.** "Buddy lists," "address books," and "keyrings" are all flavors of an abstract idea of a set of known contacts, and implementations rarely attempt to interoperate with each other or web-of-trust security systems. Attempts to merge these types of lists are often insufficient. Management of one's contacts should be an integral, second-nature feature of one's working environment, and should be uniform no matter what variety of communication one uses.

[interleaved posting]: http://en.wikipedia.org/wiki/Posting_style#Interleaved_style

## Advantages

Innumerable other communication systems have appeared since 1982, when the SMTP protocol was published in [RFC 821][], yet SMTP remains the standard for Internet mail and the basis which all other successful protocols build upon. There are several aspects of the legacy SMTP which I wish to maintain:

- **Internet mail is a protocol, not a piece of software.** The most important thing that I hope to produce with this project is an open and free specification that any programmer may use to create software compatible with any other implementation of the same specification.
- **Internet mail does not require an authority.** Anyone may compile and run an e-mail server. Anyone may send mail to anyone else with nothing more than an Internet connection. ISPs frequently provide e-mail servers as a convenience, but we could get by without them if necessary. Trust systems sometimes specify an authority, but I will employ those that make trust authorities optional at best by relying on networks of trusted peers.
- **Internet mail encapsulates messages of any format.** An SMTP message may contain a body of any content; there are no restrictions about what it may contain. Though I intend to also develop improved data formats that can support the improvement of user interfaces for messaging, a message delivery protocol will not insist that it be used.
- **Internet mail may be deployed locally or globally.** Organizations may run their own private mail systems which are disconnected from the Internet at large. No matter how good my implementation is, I'm not going to convince anybody while "everyone" still uses SMTP. I hope that, like XMPP, the system may be useful enough to deploy on smaller scales, perhaps with software bridges to traditional e-mail systems.

[RFC 821]: http://www.faqs.org/rfcs/rfc821.html

## Other work

[Project Xanadu][], like this project, criticizes the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

However, Xanadu has been churning since the 1960s with little results, something Wired magazine calls the [The Curse of Xanadu][]. With modern technology like Git and Python, and a slightly different set of goals (e.g. I don't care about a "3-D" interface), hopefully this project won't suffer the same fate.

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
[Project Xanadu]: http://xanadu.com
[Reinventing Email using REST]: http://www.prescod.net/rest/restmail/
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[email init]: http://inessential.com/2010/01/16/email_init
[StubMail]: http://www.stubmail.com

## Pervasive goals

- Messages should be private (encrypted) and authentic (signed) by default.
- [Trust Upon First Use][]: Signed messages from unknowns should not trigger a "make a decision now!" dialog. Instead, the system should inform the user that the message remains unauthentic, provide simple instructions about how to securely authenticate a sender, and complain loudly if a certificate changes unexpectedly.

[Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use

## Development plan

The first step is to break this into manageable parts.

- API: REST API for message storage and retrieval.
- Impl: message storage and retrieval.
- Impl: Adapter to allow traditional e-mail clients to send messages through this protocol.
- API: new message notification
- Impl: new message notification
- ...

## License

- All documentation herein is [GNU Free Documentation License][] v1.3 unless otherwise noted.
- All source code herein is [GNU Affero General Public License][] v3 unless otherwise noted.

[GNU Free Documentation License]: http://www.gnu.org/licenses/fdl.html
[GNU Affero General Public License]: http://www.gnu.org/licenses/agpl.html
