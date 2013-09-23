# Comparison to Xanadu

Documents are similar in some ways to Ted Nelson's hypertext project [Xanadu][].

Xanadu, like this project, criticizes the hypertext status quo:

> The World Wide Web trivializes our original hypertext model with one-way ever-breaking links and no management of version or contents.

However, Xanadu has been churning since the 1960s with little results, something Wired magazine calls the [The Curse of Xanadu][]. With modern technology like Git and Python, and a slightly different set of goals (e.g. I don't care about a "3-D" interface), hopefully this project won't suffer the same fate.

## Similarities

**Xanadu's "Transclusion"**. The immutable nature of Documents provides a means to reliably cite text without necessarily duplicating that text.

**"Xanalink overlay," "Links [and markup] are not embedded, but applied."** Documents eschew embedded mark-up by design. It is crucial to canonicalized representations of documents that they not be littered with arbitrary design elements.

**"Permanized" or "stabilized" content.** Documents are immutable and content-addressable by the hash value of their canonical representation. Changing a Document changes its hash value and thus its name. Hashed documents accomplish the same goal as Xanadu's "stabilized" content.

## Differences

**Document is and always will be DRM-free.** Xanadu contains several interesting and good ideas, but it includes as well one stupendously horrible idea: "[Transcopyright][]," which proposes a micropayment pay-per-view model and restrictions on the use of published text. DRM is evil and ruinous.

**Document is a format specification only.** The Xanadu project dictates a document format, data structures, and user interface minutae, and collects it all into an implementation called "XanaSpace." It should be possible to have a wide variety of software that may author Documents and a similar variety of user interface designs for doing so.

**Documents are unicode strings.** Xanadu documents are collections of references to text chunks that are retrieved and assembled at load time.

**Documents do not specify a version-control system.** Xanadu documents specify their own system of versioning, the "hypertime oplist."

**Documents do not specify editor behaviors.** Xanadu demands a particular scheme for undo/redo and traversal of a version tree, implemented in the "XanaSpace" document editor/viewer.

[Xanadu]: http://xanadu.com/
[Transcopyright]: http://xanadu.com/tco
[Project Xanadu]: http://xanadu.com
[The Curse of Xanadu]: http://www.wired.com/wired/archive/3.06/xanadu_pr.html

