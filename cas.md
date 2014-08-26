# Content-Addressable Storage (CAS)

[Opinions][] and [Document][] both make heavy use of references to document content by hash value. [Messaging][] may rely entirely on the behavior of a distributed CAS to publish its content.

We should provide a simple interface to a variety of means of data storage and retrieval.

The most basic requests might be to store data locally for future retrieval:

    get(hash) -> data
    put(data) -> hash

Both of these functions may have additonal implications which require more arguments, return values, or environment settings. Let's explore them.

## Data retrieval

A `get` request might look first (or simultaneously) in local cache, then in all configured local storage areas, then it might query all configured network-based storage systems. Considerations:

- The client might have a set of URLs that may be employed to retrieve the data if it is not found locally.
    - The likelihood that data will be available from given URLs is higher than that of it being available on some general-purpose network CAS, so maybe prefer these methods of retrieval?
    - Allowing others to dictate which resources will be queried is an attack vector. There should be a carefully constructed policy about types of URLs, allowed domains and schemas, queries per unit time, etc.
- The user might not want to query the network, if doing so inappropriately reveals information about themselves to others.
    - This should be an option set per-call, default to not querying
- The user might want to query only a trusted subset of the network, like their Avatar's friends in a darknet. They might want to allow their request to propagate throughout the darknet using transitive trust, or to be limited to their Avatar's immediate friends only.
- The user might want to query only networks which are accessed through an anonymizing proxy like [Tor][].
    - This is probably equivalent to "not querying if doing so reveals information about themselves to others" when the user has no network CAS providers configured who declare anonymous=True.
- The user might not want to retrieve data above a certain size if they are using a metered or slow connection.
    - This implies that we might want to limit some queries to network CAS systems that can provide content-length metadata.
- "Querying the network" is distinct from "using Internet bandwidth." The user might maintain a private data store off-site.
- Any values returned should be cached.

Interfaces to network CAS systems should expose queriable properties representing:

- bandwidth: "local" vs. "local or network"
- query propagation: "private" vs. "friends only" vs. "public"
    - this could be boolean "trusted" vs. "public"
- secrecy: "identifiable" vs. "anonymous"

## Data storage

A `put` request might offer data first to local cache, then store in configured local storage areas according to some policy, and then offer the data to all configured network-based storage systems.

- Data to be stored might be critical to store for a long time, to backup, etc., while other data might be expirable. How do we manage this? (This is perhaps out of scope, to be dealt with by each subsystem.)
- The user might want to mark some data private, and not distribute it to the network. Furthermore, the user might wish to label this data "private" in some way, to prevent it from ever reaching the network in the future.
    - Rather than attempt a janky labelling or metadata scheme, maybe just provide a local storage with the queryable property "private."
- The user might want to # TBD FIXME

## Result

So far it seems that we need to provide an API like:

    get(hash, local_only=True, trusted_only=False, anonymous=False)
    put(data, private=False, expires=None)

[TOR]: https://www.torproject.org/
[Opinions]: /datagrok/opinions
[Document]: /datagrok/dialogue/blob/master/spec/document-v01.md
