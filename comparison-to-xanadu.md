# Comparison to Xanadu

Dialogue is similar in some ways to Ted Nelson's hypertext project [Xanadu][].

Xanadu, like this project, criticizes the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

However, there are some significant differences between Dialogue and Xanadu as well.

## Similarities

**Xanadu's "Transclusion".** The immutable nature of Documents provides a means to reliably cite text without necessarily duplicating that text. However, we do not insist that every Document is a composition of references to content.

**"Xanalink overlay," "Links [and markup] are not embedded, but applied."** Dialogue Documents eschew embedded mark-up by design. It is crucial to canonicalized representations of Documents that they not be littered with arbitrary design elements.

**"Permanized" or "stabilized" content.** Documents are immutable and content-addressable by the hash value of their canonical representation. Changing a Document changes its hash value and thus its name. Xanadu's documents are not content-addressable, but they are unchangeable once named. Documents accomplish the same goal as Xanadu's "stabilized" content.

**All content exists in a universal namespace.** The namespace of the cryptographic hashes used to name documents, and any sub-document fragment of any document, is large enough that all possible content may be named with low risk for collision. No explicit namespacing is required, and a global content cache and lookup system may be established. Xanadu too envisions an "ever-growing addressable pool, or indexable carpet," but does not use cryptographic hashes to reference the content within.

**Xanadu is vaporware.** Ted Nelson has been struggling to bring the Xanadu project to life since the 1960s with little to show for it, something Wired magazine calls the [The Curse of Xanadu][]. Likewise, I have been fruitlessly toying with Dialogue since the early '00s, and being bitter at the unfulfilled potential of the Internet for free and enjoyable communication.

## Differences

**Xanadu conflates file format and user interface concerns.** One of the expressed goals for Xanadu's "Transclusion" is to allow various versions of documents to be assembled from snippets, as a human editor might with cut-up bits of paper before computers existed. Dialogue documents may accomplish the same linking, using semantic referencing, without the imposition that the underlying file format must itself be *only* a list of references.

**Dialogue is and always will be DRM-free.** Xanadu contains several interesting and some good ideas, but it includes as well at least one stupendously horrible idea: "[Transcopyright][]," which proposes a micropayment pay-per-view model and restrictions on the use of published text. DRM is evil and ruinous. I feel much empathy toward Nelson, but that Transcopyright is core to Xanadu makes me wish for Xanadu to linger in obscurity until it disappears from human memory.

**Dialogue is open.** I suspect part of the reason that Xanadu has languished in obscurity for decades is Nelson's fervent belief that his ideas must be hoarded. Many parts of Xanadu were, until recently, trade secret. Many are not described on the Internet, published only in a very hard-to-find, overpriced, and poorly-typeset book, [Literary Machines][]. Dialogue and all its contained projects aim to become IETF Standard; all reference software implementation will be GPLv3-licensed.

**Dialogue is a protocol and format specification only.** The Xanadu project dictates a document format, data structures, version control specification, micro-transaction payment, and user interface minutiae (including a three-dimensional document representation as a requirement), collecting it all into an implementation called "XanaSpace." Dialogue is a loosely-bound collection of open protocol and document format specifications that encourage a variety of implementing software and user interface designs.

**Dialogue Documents are content-addressable.** Dialogue documents are simply named by their cryptographic hash value. Xanadu documents are compositions of chunks named with "[tumblers][]." Tumblers are an attempt to enable a hierarchical unique numerical naming system for every document snippet in the network, however their names are in no way derived from their content.

**Dialogue Documents are unicode strings.** Xanadu documents are collections of references to text chunks that are retrieved (using "[tumblers][]") and assembled at load time, possibly requiring a micro-payment transaction for every chunk. Dialogue Messaging can be data-agnostic; Dialogue Documents are Unicode strings. 

**Dialogue does not specify a version-control system.** Xanadu documents specify their own system of versioning, the "hypertime oplist." Since each version of a Dialogue Document has a unique hash value it is simple to implement a git-like structure of revisions on top of it, but this is not a requirement.

**Dialogue does not specify editor behavior.** Xanadu demands a particular scheme for undo/redo and traversal of a version tree, implemented in the "XanaSpace" document editor/viewer.

[Xanadu]: http://xanadu.com/
[Transcopyright]: http://xanadu.com/tco
[Project Xanadu]: http://xanadu.com
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
[tumblers]: http://en.wikipedia.org/wiki/Tumbler_(Project_Xanadu)
[Literary Machines]: http://en.wikipedia.org/wiki/Literary_Machines
