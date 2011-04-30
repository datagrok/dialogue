# Messaging

There are several annoyances with the state of electronic communication today. The more I think about how to implement solutions, the more it seems like one must replace the whole Internet to fix them. Of course this is a fool's errand, and yet surely things must be able to be incrementally improved. This repository will collect all my half-baked ideas, and stabs at implementations, within this problem space.

## Problems

Messaging suffers from problems in both protocol and user interface.

### Protocol Problems

- **Storage.** Per DJB's [Internet Mail 2000][], mail storage should be the sender's responsibility.
- **Forged headers.** Mail should be secure and authentic by default.
- **Abstractions.** Instant messages, message boards, Usenet, SMTP e-mail, blogs, and RSS feeds are all variations on the theme of "send a message through the Internet." I propose that all of the use cases that these disparate protocols provide could be implemented using a single protocol, with a single interface.
- **Imprecise requirements.** It is notoriously difficult to build a parser and validator for an internet e-mail address. The base level of functionality should insist on strict conformance to the published spec. Spec should be designed with ease of implementation in mind.

### Interface Problems

- **Conversations.** A "message" is not an atomic unit of conversation. A "message" may contain one or several points that may prompt a response. Context is fluid; responses may be made to an abstract idea formed from the collection of many disparate points, and may be presented out-of-order. Some responses may be appropriate for points from a variety of times and sources. Even those who practice [interleaved posting][] sometimes find it difficult to manage which points within a message thread have and have not been replied to. On the other end of the spectrum, a medium like instant messaging or IRC avoids the too-much state problem, but makes it difficult to maintain multiple topics of conversation simultaneously.
- **References to other messages and published text.**
	- Hypertext links are one-way. 
	- One can't easily reference a specific version of published text.
	- One can't easily reference a snippet of a larger published text unless that text provides anchor markup.
- **Managing multiple participants.** Large threads of messages quickly become unweildly. 
- **Contact management.** "Buddy lists," "address books," and "keyrings" are all flavors of an abstract idea of a set of known contacts, and implementations rarely attempt to interoperate with each other or web-of-trust security systems. Attempts to merge these types of lists are often insufficient. Management of one's contacts should be an integral, second-nature feature of one's working environment, and should be uniform no matter what variety of communication one uses.

[interleaved posting]: http://en.wikipedia.org/wiki/Posting_style#Interleaved_style

## Advantages

Innumerable other communication systems have appeared since 1982, when the SMTP protocol was published in [RFC 821][], yet SMTP remains the standard for Internet mail and the basis which all other successful protocols build upon. There are several aspects of the legacy SMTP which I wish to maintain:

- **Internet mail is a protocol, not a piece of software.** The most important thing that I hope to produce with this project is an open and free specification that any programmer may use to create software compatible with any other implementation of the same specification.
- **Internet mail does not require an authority.** Anyone may compile and run an e-mail server. Anyone may send mail to anyone else with nothing more than an Internet connection. ISPs frequently provide e-mail servers as a convenience, but we could get by without them if necessary. Trust systems sometimes specifiy an authority, but I hope to employ those that rely on networks of trusted peers.
- **Internet mail encapsulates messages of any format.** An SMTP message may contain a body of any content; there are no restrictions about what it may contain. Though I hope to also develop improved formats for messaging in general, a message delivery protocol will not insist that it be used.
- **Internet mail may be deployed locally or globally.** Organizations may run their own private mail systems which are disconnected from the Internet at large. No matter how good my implementation is, I'm not going to convince anybody while "everyone" still uses SMTP. I hope that, like XMPP, the system may be deployed within organizations who may insist that its users use it instead of SMTP, and benefit from its security features.

[RFC 821]: http://www.faqs.org/rfcs/rfc821.html

## Other work

The most frightening example of a project with similar user-interface aims is [Project Xanadu][]. Xanadu, like this project, criticizes the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

However, Xanadu has been churning since the 1960s with little results. I have to hope that with modern technology like git and Python, and a slightly different set of goals, I won't wake up one day an old man who relived [The Curse of Xanadu][].

Before I learned of Xanadu, most of these ideas were spawned investigating DJB's proposal for [Internet Mail 2000][]. There have been many attempts to build an Internet Mail 2000 implementation:

- [Jonathan de Boyne Pollard, "Fleshing out IM2000"](http://homepages.tesco.net./~J.deBoynePollard/Proposals/IM2000/)
- [Aaron Swartz's Proposal](http://www.aaronsw.com/2002/im2000)
- [Jorge Lehner's Notes and Software](http://www.magma.com.ni/~jorge/index_2.html)

Many others have hit upon similar ideas:

- [RSS/Email and IM2000][], a Google TechTalk by Meng Weng Wong and Julian Haight 7/19/2006
- [Reinventing Email using REST][]: "You can see how REST blurs the boundaries between applications and could obliterate the boundary between 'the web' and email."
- [email init][], a proposal by a blogger named Brent Simmons that saw a brief surge of interest. I think the proposal captures the feeling that many "power users" wish for better electronic mail, but it falls flat right out of the gate with a myopic insistence on a proprietary user interface toolkit and the reliance on an existing mail transfer protocol.
- ...

[Internet Mail 2000]: http://cr.yp.to/im2000.html
[Project Xanadu]: http://xanadu.com
[RSS/Email and IM2000]: http://www.youtube.com/watch?v=Kp79SZaKcLg
[Reinventing Email using REST]: http://www.prescod.net/rest/restmail/
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[email init]: http://inessential.com/2010/01/16/email_init

## Pervasive goals

- Messages should be private (encrypted) and authentic (signed) by default.
- Security: Signed messages from unknowns should not trigger a "make a decision now!" dialog. Instead, the system should inform the user that the message remains unauthentic, and complain loudly if a certificate changes unexpectedly. See [Trust Upon First Use][].

[Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use

## Development plan

The first step is to break this into managable parts.

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
