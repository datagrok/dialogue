# Dialogue

_draft/unfinished/vaporware_

*Dialogue* is a system for asynchronous conversation on the Internet, intended to replace all of these with a single, decentralized, user-centric open protocol:

- SMTP E-Mail
- NNTP newsgroups
- Web-based forums like phpBB, Discourse, YaBB/YaBBSE/SMF
- Blogs and micro-blogs like Twitter, Facebook, etc.
- Comment and discussion areas on websites, like those provided by Disqus, IntenseDebate, Juvia, etc.
- News aggregation sites with threaded discussion boards like Slashdot, Reddit, Digg, etc.

Dialogue is composed of:

- **Messaging:** A decentralized, asynchronous messaging system with push notification.
- **Opinions:** An abstraction for assertion data that enables a distributed network of trust, reputation, and quality for pseudonymous authors and their statements.
- **Storage**: A [content-addressable storage](cas.md) system, possibly including a decentralized, or distributed/peer-to-peer component.
- **Avatar:** A specification for one's pseudonymous identities. The core of every Avatar is a cryptographic public key.
- **Roster:** User interface recommendations for software that manages Avatars.
- **Document:** A rich-text document format that enables cross-site threaded discussions, external quotes,encryption, and signatures.

Each of these pieces may be interesting or useful alone, but to achieve the goal of better conversation on the internet, all are required.

## Motivation

I'm not happy with the state of conversations on the Internet.

- There are a glut of incompatible silos even though they're all [essentially the same thing](convergence.md).
- When they're not apathetic of the criminally abusive (Twitter), they destroy their users' privacy (Google Plus).
- They take ownership of their participants' words, and sometimes destroy them.
- Their user interfaces are insufficient to enable most people to engage in complex discussions.
- When they're not choked with spam, they demand tedious registration procedures (web-based forums and blog comments).
- If cryptographic authenticity and privacy is available at all, it is a poorly-bolted-on afterthought (SMTP E-Mail).
- If reputation exists at all, it serves only the majority group of participants, and the quality erodes as it gains in popularity (Slashdot, Reddit, Digg).

All of these issues can be fixed, by embracing reputation, filtering, and above all else giving the user tools to control what they see.

I align with the values stated in the [Indie Tech Manifesto][]. (However, this project is not supported by the ind.ie Foundation.)

[Indie Tech Manifesto]: https://ind.ie/manifesto/

## Versions

I've been noodling on this idea for a very long time. The earliest versioned writing I can find about it is dated Oct 22, 2003.

## License

- All documentation herein is [GNU Free Documentation License][] v1.3 unless otherwise noted.
- All source code herein is [GNU Affero General Public License][] v3 unless otherwise noted.

[GNU Free Documentation License]: http://www.gnu.org/licenses/fdl.html
[GNU Affero General Public License]: http://www.gnu.org/licenses/agpl.html
