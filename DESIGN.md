# Design

## Documents should be canonicalizable

- For every given representation of document and annotations, there should be only one way to serialize it.
    - A set of annotations must have a canonical order

## Hash of a document

- ~~`H(D) = H(H(C_1)|H(...)|H(C_i))`~~ No, because corpora could be split an arbitrary number of ways, destroying canonicalization.
- `H(D) = H(C_1|...|C_i)` The hash of a document includes the hash of the concatenation of all of its corpora. A Document might elect not to include all corpora, but the hash is still a function of it.
    - Does this imply the hash of a Document consisting of a single corpus could be equivalent to the hash of that corpus? Probably not, docs could contain more

## All messages MUST be encrypted, even when audience is "public."

- Hinders opportunistic eavesdropping.
- Simplifies implementation (but makes processing more expensive).
- Eliminates the temptation to be lazy about encryption.
- Make encrypted content the exception rather than a nefarious act that raises suspicion.
- A "public" avatar that anyone may use to send "open" messages will be included with spec.
- All weak-security messages are rejected, foiling social hacks like "really, it's me, I just lost my key."

## Data is authentic by default.

- Signatures on all messages make it easy to reject fraudulent messages and spam.
- "Off-the-record" communication is still important and must be possible, but it should be an edge-case.

## Addressing a document to a set of people

- Techniques exist to do this already; explore them
- Maybe: encrypt w/a symmetric key, encrypt symmetric key with asymmetric key to end users.
    - Non-group communication should work the same way, treat as 1-person group
- Maybe: user creates "groups" for their contacts, adding a user to group sends group symmetric key to them.
    - User is asked on membership add: should new member see past communications? (Otherwise, rekey, distribute new key to all members.)
    - User is asked on membership del: should removed member lose access to future communications? (If so, rekey, distribute new key to all members.)

## Recipients must check canonicalization and hashes for validity, and reject if invalid.

- Foils hacking attempts
- Forces client implementors to adhere to the spec

## Meaning of Signatures

- We don't want nefarious or stupid parties to assert that we have claimed authorship over something we haven't simply due to the existence of a digital signature.
- Signatures imply approval of the content, not an assertion of _original authorship_ or copyright.
- This doesn't mean such assertions are impossible; one may write: "I, (name), have written all the words herein." and sign _that_ statement.

## Data is distributed by default. "No expectation of rights management"

News journalism sites want to provide stories to paying customers (only) or create a sub-set that is free to all.

Photographers and graphic artists want to show their photos to people for free, but want to control or extract payment when their work is reused.

- The document store employed in Dialgoue is assumed to be distributed and redundant.
- Any data stored in it should be assumed to be widely distributed and publicly accessible, even if the original author's store goes offline. (However, the data may be encrypted.)
- Sites formerly paywalled must instead employ broadcast (or large recipient group) encryption. Redistribution of unencrypted content is a purely social and legal problem. 
- Limited access is possible: encrypt content (or part of content) to public keys of those who pay
- "Temporary access" and access revocation is impossible: if a recipient has read a Document once, it can be assumed they can read it forever.

## Scribbles / Notes

- Message transport: well-connected host sends a *short message* to an inbox informing them of available message. Individuals may be "well-connected hosts"

- Short message may not come from sender, may be copied, sent through tor, should still be authentic

- What prevents an attacker from DOSing a host by sending millions of notifications out with a target url? Auth cert?

- How does Dialogue align with Aral Balkan's Indie Tech? https://aralbalkan.com/notes/towards-an-indie-tech-manifesto/ https://aralbalkan.com/notes/2014-the-rise-of-indie-tech/ https://aralbalkan.com/notes/on-evolving-indieauth/

- How does Dialogue align with Indie Web? http://indiewebcamp.com/

- [Swift](http://libswift.org/) could be very useful for Dialogue; explore this
