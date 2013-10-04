# Don't read the comments(?)

Have you ever heard the phrase, "never read comments on the Internet"?

Borne out of frustration with free comment systems, many people have given up on the idea that productive discussions might ever occur on the Internet. They say comments are always negative, rarely positive. And many use anonymity on the Internet to incite sadness, hatred, or dispair, often merely as a game.

We shouldn't give up on free speech. Neither should we give up on having productive discussions online.

[Dialogue][] is the answer. Dialogue includes a specification for a reputation system.

Every post made with Dialogue is cryptographically signed by its author. Dialogue helps you keep track of who is interesting, and who is a troll. It lets you easily filter the people and kinds of messages you don't like to see.

**Q.** But what about anonymity? I don't want to give my legal name on the Internet when discussing sensitive topics. I don't want prospective employers picking through my personal life.

**A.** Dialogue abhors "real name" initiatives. It encourages users to create pseudonymous *Avatars* to represent them in cyberspace.

**Q.** Won't trolls create lots of Avatars?

**A.** Yes, probably at first. But a new Avatar will have accrued no positive reputation, making it invisible to most people's filters.

**Q.** Won't trolls rate all of each other's Avatars highly, boosting their reputation?

**A.** Reputation is weighted: the score reported for any Avatar is only as trustworthy as the chain of trust leading to it. If none of the people you trust trust the troll, their FIXME


- When you send a comment, Dialogue keeps a copy. You can refer to it, or parts of it, from any other site that uses any compatible implementation of the Dialogue protocol.

- When you participate in conversation, Dialogue clients may automatically cache messages that respond or link to yours. That way if your interloqutor takes their ball and goes home, they don't wipe your work from the Internet.

- Dialogue is a protocol that works across sites and across mediums. Using Dialogue you may reply to a message in an NNTP newsgroup on a Reddit-like comment thread, while referencing other text from e-mail, mailing lists, and instant message conversations.

- You keep a copy of every message you send or post, making it easy to re-host conversations you care about even if other sites delete or lose them.

- A Dialogue Document provides a way for other documents to link to any sub-range of the text it contains. A blog post may elect not to provide a discussion interface built-in, but one may use a Dialogue client to establish a discussion thread for that post that references it just as easily as if they had.

[Dialogue]: http://github.com/datagrok/messaging/
