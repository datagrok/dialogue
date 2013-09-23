This is a specification for a messaging protocol with the following design goals:

- **A protocol, not a piece of software.** Like SMTP

- **No authorities.** Like SMTP

- **Encapsulate any format.** Like SMTP

- **Deployable locally or globally.** Like SMTP

- **Mail storage is the sender's responsibility.** Like IM2000

- **Messages are signed by default.** One of the main enablers of spam e-mail is untrustworthy SMTP mail headers. Messages sent under this protocol will be cryptographically signed by default, rejected by clients if not. In rare instances, one may wish to communicate with plausible deniability; a mechanism will be designed to enable this.

- **Messages are always encrypted.** Seasoned internet users know that it is unsafe to send credit card numbers through SMTP e-mail. New users do not and sometimes get burned. All messages sent under this protocol are encrypted. In the case where a message is intended for the general public, it is encrypted for a globally-known "public" user.

- **Not just "e-mail".** Instant messages, message boards, Usenet, SMTP e-mail, mailing lists, blogs, and RSS feeds are all variations on the theme of "send a message through the Internet to one or a number of recipients." This protocol is abstract enough for all of these use cases, within a single interface.

- **Design for manufacture.** It is notoriously difficult to build a parser and validator for an SMTP e-mail address. This spec is designed with ease of implementation in mind, and we insist on strict conformance.

- **DERAT (Default Encrypted with Retroactive Application of Trust):** Signed messages from unknowns should not trigger a "make a decision now!" dialog. Instead, the system should inform the user that the message remains unauthentic and possible viewable by others, provide simple instructions about how to securely authenticate a sender, and complain loudly if a certificate changes unexpectedly. See [DERAT][].

[DERAT]: derat.md
