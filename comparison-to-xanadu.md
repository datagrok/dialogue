# Comparison to Xanadu

Dialogue is similar in some ways to Ted Nelson's hypertext project [Xanadu][].

Xanadu, like this project, criticizes the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

However, Xanadu has been churning since the 1960s with little results, something Wired magazine calls the [The Curse of Xanadu][]. With modern technology like Git and Python, and a very different set of goals. For example: we don't care about a "3-D" interface, we encourage others to implement clients which speak our protocol, and we abhor all flavors of DRM. Hopefully this project won't suffer the same fate as Xanadu.

## Similarities

**Xanadu's "Transclusion"**. The immutable nature of Documents provides a means to reliably cite text without necessarily duplicating that text.

**"Xanalink overlay," "Links [and markup] are not embedded, but applied."** Dialogue Documents eschew embedded mark-up by design. It is crucial to canonicalized representations of Documents that they not be littered with arbitrary design elements.

**"Permanized" or "stabilized" content.** Documents are immutable and content-addressable by the hash value of their canonical representation. Changing a Document changes its hash value and thus its name. Hashed Documents accomplish the same goal as Xanadu's "stabilized" content.

## Differences

**Dialogue is and always will be DRM-free.** Xanadu contains several interesting and good ideas, but it includes as well one stupendously horrible idea: "[Transcopyright][]," which proposes a micropayment pay-per-view model and restrictions on the use of published text. DRM is evil and ruinous.

**Dialogue is a format specification only.** The Xanadu project dictates a document format, data structures, and user interface minutiae, and collects it all into an implementation called "XanaSpace." It should be possible to have a wide variety of software that may author Documents and a similar variety of user interface designs for doing so.

**Dialogue documents are content-addressable.** Dialogue documents are named by their hash value. Xanadu documents are named with "tumblers," which is an attempt to enable a hierarchical unique numerical naming system for every document in the network.

**Documents are unicode strings.** Xanadu documents are collections of references to text chunks that are retrieved and assembled at load time. 

**Dialogue does not specify a version-control system.** Xanadu documents specify their own system of versioning, the "hypertime oplist." Since each version of a Dialogue Document has a unique hash value it is simple to implement a git-like structure of revisions on top of it, but this is not a requirement.

**Dialogue does not specify editor behavior.** Xanadu demands a particular scheme for undo/redo and traversal of a version tree, implemented in the "XanaSpace" document editor/viewer.

[Xanadu]: http://xanadu.com/
[Transcopyright]: http://xanadu.com/tco
[Project Xanadu]: http://xanadu.com
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html
