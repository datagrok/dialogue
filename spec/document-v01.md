# Document Specification

Version 0x01

This text is intended to read like an IETF RFC, leaning toward brevity like that of the [Netstrings][] spec.

For information about the design decisions that resulted in this specification, see [DESIGN][]. 

[Netstrings]: http://cr.yp.to/proto/netstrings.txt
[DESIGN]: DESIGN

## Introduction

A Document is a simple rich collection of text with a canonical representation and a mechanism for both referring to any range of its content, and including text from the interior of other Documents.

It is not a "markup" format: text attributes are stored separate from the text itself, to facilitate canonicalization.

## Definition

A Corpus (pl. Corpora) is a sequence of Unicode characters. Its hash value is the SHA-256 hash of the UTF-8 encoding of its content.

A Corpus Reference is the hash value of a Corpus together with a start index (0-indexed, inclusive) and end index (0-indexed, exclusive), counting in unicode codepoints.

A Corpus Reference whose start and end index are both 0 refers to the entire content of the Corpus.

An Annotaion 

A Document consists of an ordered collection of one or more Corpus References together with zero or more Annotations.


    document = ([corpus_1, ..., corpus_i], [annotation_1, ..., annotation_i])
    H(document) = H(H(corpus_1)|...|H(corpus_i)|H()

Corpora are uniquely identified by the SHA-256 hash of the

Separate stylesheet and refsheet?

Style separate from annotation?

Annotations for HASH
224-253:boldface
224-253:italics
223-435:highlight
we...people: boldface

Text Annotation set format

The referencing Document is responsible for providing the annotations 

Number of possible substrings of a string length N? (each could have a unique hash value)
