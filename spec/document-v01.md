# Document Specification

Version 0x01

This document is intended to read like an IETF RFC, leaning toward brevity like that of the [Netstrings][] spec.

For information about the design decisions that resulted in this specification, see [DESIGN][]. 

[Netstrings]: http://cr.yp.to/proto/netstrings.txt
[DESIGN]: DESIGN

## Introduction

A Document is a simple rich-text document with a canonical representation and a mechanism for both referring to any range of its content, and including text from the interior of other documents.

It is not a "markup" format: text attributes are stored separate from the text itself, to facilitate canonicalization.

## Definition

A Document consists of one or more Corpora together with zero or more Annotations.

A Corpus (pl. Corpora) is a sequence of Unicode characters.

Corpora are uniquely identified by the SHA1 hash of the UTF-8 encoding of their content.

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
