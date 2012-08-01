This is a specification for a messaging protocol with the following design goals:

- **A protocol, not a piece of software.** Like SMTP

- **No authorities.** Like SMTP

- **Encapsulate any format.** Like SMTP

- **Deployable locally or globally.** Like SMTP

- **Mail storage is the sender's responsibility.** Like IM2000

- **Messages are always signed.** One of the main enablers of spam e-mail is untrustworthy SMTP mail headers. Messages sent under this protocol must always be cryptographically signed.

- **Messages are encrypted by default.** Seasoned internet users know that it is unsafe to send credit card numbers through SMTP e-mail. New users do not and sometimes get burned. All messages sent under this protocol are private (encrypted) by default.

- **Not just "e-mail".** Instant messages, message boards, Usenet, SMTP e-mail, mailing lists, blogs, and RSS feeds are all variations on the theme of "send a message through the Internet to one or a number of recipients." This protocol is abstract enough for all of these use cases, within a single interface.

- **Design for manufacture.** It is notoriously difficult to build a parser and validator for an SMTP e-mail address. This spec is designed with ease of implementation in mind, and we insist on strict conformance.

- **(Pseudo-)Trust Upon First Use.** Signed messages from unknowns should not trigger a "make a decision now!" dialog. Instead, the system should inform the user that the message remains unauthentic, provide simple instructions about how to securely authenticate a sender, and complain loudly if a certificate changes unexpectedly.

[Trust Upon First Use]: http://en.wikipedia.org/wiki/User:Dotdotike/Trust_Upon_First_Use



- Message transport: well-connected host sends a *short message* to an inbox informing them of available message. Individuals may be "well-connected hosts"

- Message

- short message may not come from sender, may be copied, sent through tor, should still be authentic

What prevents an attacker from DOSing a host by sending millions of notifications out with a target url? Auth cert?
