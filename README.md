# Messaging

There are several annoyances with the state of electronic communication today. The more I think about how to implement solutions, the more it seems like one must replace the whole Internet to fix them. A fool's errand, but yet surely things could be made incrementally better. This repository will collect all my notes, ideas, and implementations toward that unachevable grand vision.

# Problems

Messaging suffers from problems in both protocol and user interface.

## Protocol

- Forged headers. Mail should be secure and authentic by default.
- Mail overload. Mail storage should be the sender's responsibility.
- Abstractions. Instant messages, message boards, Usenet, SMTP e-mail, blogs, and RSS feeds are all variations on ways to send a message over the Internet. I propose that all of the use cases that these provide could be implemented using a single protocol with a single interface.

## Interface

- Conversational interface. A "message" is not an atomic unit of conversation. Many people do not bother to reply point-by-point to each part of a message. Even those who do find it difficult to manage which parts of a message have been replied to. On the other end of the spectrum, a medium like instant messaging or IRC makes it difficult to maintain multiple topics of conversation simultaneously.
- Managing multiple participants. Large threads of messages quickly become unweildly. 
- Contact management. We have "buddy lists" "address books" and "keyrings" are all flavors of a contact list, and rarely attempt to interoperate with web-of-trust security systems. Attempts to merge these types of lists are often insufficient. Management of one's contacts should be an integral feature of one's environment, and should be uniform no matter what variety of communication one uses.

# Other work

The most frightening example of a project with similar aims is [Project Xanadu][]. They, too, criticize the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

That my lofty goals and current rate of progress for this software so closely resembles that of Project Xanadu is one of my greatest fears. I have to hope that with modern technology like git and a slightly different set of goals I won't wake up one day an old man who relived [The Curse of Xanadu].

Before I learned of Xanadu, much of these ideas were spawned reading DJB's [Internet Mail 2000][]. There have been many attempts to build an Internet Mail 2000 implementation: 

Many others have hit upon similar ideas:

- [Reinventing Email using REST][]: "You can see how REST blurs the boundaries between applications and could obliterate the boundary between 'the web' and email."


[Internet Mail 2000]: http://cr.yp.to/im2000.html
[Project Xanadu]: http://xanadu.com
[Reinventing Email using REST]: http://www.prescod.net/rest/restmail/
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[email init]: http://inessential.com/2010/01/16/email_init

# Development plan

The first step is to break this into managable parts.

- REST API for message storage and retrieval.

