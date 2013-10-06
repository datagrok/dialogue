# "Don't read the comments" is wrong

Have you heard the phrase, "never read comments on the Internet"? Have you agreed with it?

Borne out of our frustration with free comment systems, many have given up on the idea that productive discussion might ever occur on the Internet.

- **Agreements are clutter.** If someone agrees with you, they might not be motivated to comment. If they do, a simple "me too" is often seen as clutter and not contributing to a discussion.

- **Disagreements are abusive.** Those who disagree are often very motivated to post, lest your incorrect position go unchallenged. But with anonymity these missives are often abusive rather than constructive.

- **Trolling.** Many use anonymity on the Internet to incite reactions of anger, sadness, hatred, or dispair, purely as a game.

I maintain that we shouldn't give up on free speech. Neither should we give up on having productive discussions online.

[Dialogue][] is the answer.

Dialogue includes a specification for a reputation system. Every post made with Dialogue is cryptographically signed by its author. Dialogue helps you keep track of who is interesting and who is a troll or legitimately carries offensive opinions. It lets you easily filter out the kinds of messages you don't like to see, and the people who post them.

Dialogue also includes a specification for opinions, which one might think of as a "distributed 'upvote/downvote' button." Where one is tempted to post "me too," they may instead employ the opinions framework to avoid clutter. Or they might do both, and readers can be configured to hide "me too" posts. I suspect that providing an implicit "I disagree" button will decrease the amount of vitriol dumped into comment areas.

**Q.** But what about anonymity? I don't want to give my legal name on the Internet when discussing sensitive topics. I don't want prospective employers picking through my personal life. I don't want my opponents to look up where I live and harass my family.

**A.** Dialogue abhors "real name" initiatives. It encourages users to create pseudonymous *Avatars* to represent them in cyberspace.

**Q.** Won't trolls create lots of Avatars?

**A.** Yes, probably at first. But a new Avatar will have accrued no positive reputation, making it invisible to most people's filters.

**Q.** Won't trolls rate all of each other's Avatars highly, boosting their reputation?

**A.** Reputation is weighted: the score reported for any Avatar is only as trustworthy as the chain of trust leading to it. If none of the people you trust trust the troll, the troll's sockpuppets will also remain untrustworthy. Trolls might create whole networks of sockpuppets but they will remain invisible to the legitimate network.

Dialogue's reputation system is inspired by Raph Lieven's [Attack-Resistant Trust Metrics](http://www.levien.com/thesis/compact.pdf) as implemented on [Advogato.org](http://www.advogato.org/trust-metric.html).

[Dialogue]: http://github.com/datagrok/messaging/
