# The convergence of asynchronous messaging

**Thesis:** _all forms of asynchronous messaging on the Internet are essentially the same, and so could converge into a single protocol._

## Blogs and "vanity mailing lists"

Some mailing list software can be configured to store an archive of all mail sent through it as HTML pages on the Internet.

Before WordPress, Facebook, Twitter, and LiveJournal were popular, some people preferred to create "vanity mailing lists" rather than employing blog software or services, for the purpose of publishing the kind of content one would normally publish in a blog.

> This is a mailing list set up for me to randomly send messages to, and for my "fans" to discuss me. It's like an interactive weblog that's text-only, no HTML. —[glyph-discuss]

[glyph-discuss]: http://twistedmatrix.com/cgi-bin/mailman/listinfo/glyph-discuss

Some blogs allow visitors to comment on their content. Similarly, "vanity mailing lists" can support a kind of comment system: if others are allowed to send mail to the list, then any messages sent in reply to a topic message appears in its context when viewed in the HTML archive.

Consider that both of these forms of communication, abstractly, are the same:

1. **Topic message:** Someone creates a message and gives it a topic, title, or subject.
2. **Online storage:** The message is stored in an always-online location where others may retrieve it at their convenience.
3. **Notification:** According to some policy, subscribers may be notified (e.g. by polling an RSS feed, or their mailbox) that a new message is available to read.
4. **Comments:** Others may reply to that message, and their replies are collected under and displayed with that same topic.
5. **Discussion:** Others may further reply to the replies in the same manner.

## A modern e-mail protocol

The current store-and-forward system of SMTP E-Mail does not fit into this abstraction. However, a different and arguably much better e-mail protocol could.

D. J. Bernstein's [Internet Mail 2000][IM2000] project proposes: _"e-mail storage is the sender's responsibility."_

Consider IM2000-style e-mail, abstractly, as we did earlier with blogs and mailing lists. If mail storage is the sender's responsibility, then e-mail becomes:

1. **Topic message:** Someone creates a message and gives it a subject line and a specific set of recipients.
2. **Online storage:**The  message is stored in an always-online location where recipients may retrieve it at their convenience.
3. **Notification:** According to some policy, recipients are notified that a new message is available for them.
4. **Comments:** Others may reply to that message, and their replies are collected under and displayed with that same topic.
5. **Discussion:** Others may further reply to the replies in the same manner.

The only major difference between IM2000-style e-mail and an abstraction of a web-based forum is the notion of "recipients." If our abstraction tolerates the notion of a "public" recipient, then it can serve as _both_ an e-mail system and a discussion system.

## All things are Dialogue.

We have seen how blogs with comments, vainity mailing lists, and IM2000-style e-mail are all isomorphisms of one another, in the abstract. In the same way we can see all of the following as concrete implementation of this abstraction of an asynchronous dialogue:

- Facebook updates and wall posts
- LinkedIn posts
- USENET newsgroup posts
- News websites with comment areas like CNN, Huffington Post, or Fox News
- Independent web-based discussion forums
- Slashdot posts and comment sections
- Posts and discussion areas of Slashdot, Kuro5hin, Reddit, Digg, MetaFilter, Hacker News

# The benefits of convergence

Vanity lists have something that modern blogs don't have: interoperability with all other forms of e-mail.

## A glut of incompatible options.

There are today a disparate glut of incompatible messaging systems in widespread use on the Internet. SMTP e-mail, USENET, forums like those on Slashdot, Kuro5hin, Digg, Reddit, and MetaFilter. Comments on WordPress and other blogs. Disqus comments on various webpages. Facebook and LinkedIn have their own systems. Every website seems to have its own private-silo messaging and commenting infrastructure.

Without "pingback" software specifically designed to do it, there is no way to reply to a comment on one blog from another blog, or to merge a conversation taking place on Reddit with one on Digg about the same topic or URL.

## No local copies, versioning, or individual control.

If you do participate in any of these systems, it is entirely possible that your words will be hidden or deleted. It's under someone else's control, and systems that allow you to keep a "local copy" of the discussion are rare. Only with e-mail or USENET newsgroups is it likely that you will have a local copy of your words, should they vanish from the Internet.

Some web-based forum software allows one to edit their posts. This means that the statement you reply to might be edited after you've replied to it. You can be made to appear to agree or disagree with something you do not, with this bait-and-switch.

Many webpages that one might wish to have a discussion about do not offer a comment system, or they explicitly disable their comment system.

A great deal of discussion happens on "mailing lists" that would benefit various discussions on the same subjects happening in web-based forums, and vice versa.

## How it could be different

I propose that all of these things could be replaced by a single, open, secure, decentralized protocol that puts the individual user in control. A single global namespace would mean that a comment left on a blog about a particular subject could be mirrored to other sites discussing the same topic. Cross-site discussions could be merged. Referencing content by hash value eliminates bait-and-switch edits. Combined with a reputation system, poisonous participants could be filtered away according to the individual user's preferences.

Having e-mail use the same protocol enables private conversations to evolve into group discussions easily, and allows quoting between what are now different mediums. A market could emerge for the creation of the best native e-mail clients, and those same high-quality clients could be used for internet discussions instead of webpage comment-boxes.

Dialogue [Messaging][] exists to define an open, secure, decentralized protocol and a software reference implementation that implements the abstraction described above, to convey a message in an unspecified format to a specific set of recipients, a group, or the general public.

However, convergence of all asynchronous messaging to a single protocol is woefully insufficient to fix some the more egregious problems with Internet conversations, especially: harassment, spam, irrelevence, anonymity, citation tools, conversation splitting, etc. To address these, see other Dialogue subprojects, including:

- [Opinions][]: implements a reputation system that could be used to filter spam and harassment;
- [Document][]: a format specification with improved citation;
- [Avatar][]: a pseudonymous identity that encapsulates a public encryption key, which, together with Opinions, could provide distributed user-controlled profiles, reputation filtering, and interest-clustering for content.

[Avatar]: /datagrok/dialogue/blob/master/avatar.md
[Document]: /datagrok/dialogue/blob/master/document.md
[IM2000]: http://cr.yp.to/im2000.html
[Messaging]: /datagrok/dialogue/blob/master/messaging.md
[Opinions]: /datagrok/dialogue/blob/master/opinions.md
