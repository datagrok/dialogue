# Interface Problems

Fixing the user interface for conversations may be an impossible morass. Luckily, since the protocol is agnostic about what data we ship through it, we might attack this last. Or there might be many viable solutions. It might be better considered an independent project. I include it here because my proposals depend on features of my proposed protocol.

- **Context in a conversation is fluid.**
	- An e-mail may contain one or several points that may elicit a response. An e-mail message is not an atomic unit of conversation, but most existing clients treat them as such.
	- An e-mail's subject or topic may vary over the course of the conversation, changing many times within one message or gradually over the course of multiple messages. Many traditional e-mail clients group messages by "subject" so it becomes important to avoid modifying the "subject" line even if the subject has changed.
	- Responses may be made to an abstract idea formed from the collection of many disparate points across times and sources, and may be presented out-of-order. Many do not take the trouble to reference text in their reply because user interfaces do not make it easy to do so. Even those who practice [interleaved posting][] sometimes find it difficult to manage which points within a message thread have and have not been replied to, and some may be unintentionally ignored.
	- A medium like instant messaging or IRC avoids this too-much state problem, but makes it difficult to coordinate multiple topics of conversation simultaneously.
- **References to other messages and published text.**
	- Hypertext links are one-way. 
	- One can't easily reference a specific version of published text.
	- One can't easily reference a specific location within published text unless that text provides anchor markup.
- **Managing multiple participants.** Large threads of messages quickly become unwieldy. 
- **Contact management.** "Buddy lists," "address books," and "keyrings" are all flavors of an abstract idea of a set of known contacts, and implementations rarely attempt to interoperate with each other or web-of-trust security systems. Attempts to merge these types of lists are often insufficient. Management of one's contacts should be an integral, second-nature feature of one's working environment, and should be uniform no matter what variety of communication one uses.

[interleaved posting]: http://en.wikipedia.org/wiki/Posting_style#Interleaved_style

## Other work

Project Xanadu includes a user interface specification. See [comparison to Xanadu][].

[comparison to Xanadu]: xanadu.md
