# Messaging

A protocol specification, document format specification, and set of user interface recommendations for asynchronous conversations through the Internet.

I indend for Messaging to be able to not only replace, but bring about the convergence of:
- SMTP e-mail
- NNTP newsgroups
- Web-based forums
- Blogs
- Comment sections on web-pages
- News aggregation sites with threaded discussion boards

_All of this is vaporware and brainstorming; watch for the removal of this notice._

## Problems

There are several annoyances with the state of electronic communication today. I think the problems and solutions may be conceptually divided into different areas:

1. [Protocol & data format](problems-protocol.md)
2. [Security & Identity](problems-security.md)
3. [User Interface](problems-interface.md)

The issues are interrelated. Fixing the protocol requires a useful public-key security infrastructure in place. A useful security infrastructure requires an intuitive user interface for managing contacts. A document format with a canonical representation may be hashed and referenced without a central authority. Et cetera.

## Solutions

Messaging on the Internet can be improved by:

1. Strong encryption, signatures, and web-of-trust reputation facilities enabled by default, with user interfaces that help users to manage them, including powerful filtering.
2. A new protocol that takes advantage of the reputation facilities to enable spam- and attack-resistance.
3. A new hypertext standard wherein documents have exactly one canonical representation, and provide for other documents a uniform way to reference sub-ranges of their content.

## Details

This repository (will eventually) provide(s):

- A [protocol specification](spec/protocol-v01.md) and the [rationale](protocol.md) behind the design decisions made therein;
- A [hypertext document format specification](spec/document-v01.md) and the [rationale](document.md) behind the design decisions made therein;
- A reference implementation of clients and servers using the protocol
- A reference implementation of a Document editor/converter/viewer

- **Protocol:** use cases | [rationale](protocol.md) | [specification](spec/protocol-v01.md) | implementation
- **Document:** use cases | [rationale](document.md) | [specification](spec/document-v01.md) | implementation

## License

- All documentation herein is [GNU Free Documentation License][] v1.3 unless otherwise noted.
- All source code herein is [GNU Affero General Public License][] v3 unless otherwise noted.

[GNU Free Documentation License]: http://www.gnu.org/licenses/fdl.html
[GNU Affero General Public License]: http://www.gnu.org/licenses/agpl.html
