# Design

## Hash of a document

- ~~`H(D) = H(H(C_1)|H(...)|H(C_i))`~~ No, because corpora could be split an arbitrary number of ways, destroying canonicalization.
- `H(D) = H(C_1|...|C_i)` The hash of a document includes the hash of the concatenation of all of its corpora. A Document might elect not to transmit all corpora, but the hash is still a function of it.
    - Does this imply the hash of a Document consisting of a single corpus could be equivalent to the hash of that corpus? Probably not, docs could contain more

## Encrypted by default, even when audience is "public."

- Hinders opportunistic eavesdropping.
- Simplifies implementation (but makes processing expensive).
- Eliminates the temptation to be lazy about encryption.
- Make encrypted content the exception rather than a nefarious act that raises suspicion.
- "Public" avatar will be included with spec.

## Addressing a document to a set of people

- Techniques exist to do this already; explore them
- Maybe: encrypt w/a symmetric key, encrypt symmetric key with assymetric key to end users.
    - Non-group communication should work the same way, treat as 1-person group
- Maybe: user creates "groups" for their contacts, adding a user to group sends group symmetric key to them.
    - User is asked on membership add: should new member see past communications? (Otherwise, rekey, distribute new key to all members.)
    - User is asked on membership del: should removed member lose access to future communications? (If so, rekey, distribute new key to all members.)
