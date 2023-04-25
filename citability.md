## Citability

### Primary literature

CTS URNs provide universal citability.CTS as a system provides a method for processing and publishing data.

These huge benefits must be weighed against three drawbacks:

* the lack of a universal _resolver_ service for CTS URNs (like we have for DOIs).
* CTS URNs are not sufficiently strictly defined.
* CTS is labor intensive: learning the system and applying it to the content.

In all three areas, Brill can play an important role: setting up a resolver ssyste, setting up documentation, and creating (validation) tools.

### Secondary literature

In other words, journal articles, edited volumes, and monographs. 

The idea is to number paragraphs and combine them with "some other ID" to create a UID.

This is akin to how the DOIs of book chapters are formed at Brill: the DOI suffix combines the book's ISBN with the number of the chapter.

#### Two examples of Brill DOIs

```
Anderson, Greg, “Agaklytos (411)”, in: Brill’s New Jacoby, General Editor: Ian Worthington (Macquarie University).
Consulted online on 07 November 2019 <http://dx.doi.org/10.1163/1873-5363_bnj_a411>
First published online: 2016
```

```
A Tradition in the Plural: Reframing Sefer Yosippon for Modern Times
in Josephus in Modern Jewish Culture
Author: Andrea Schatz
DOI: https://doi.org/10.1163/9789004393097_005
```

What "other ID"? Possibly ISBN for books. ISSN are unsuitable for articles because they identify the journal, not the issue. DOIs are also unsuitable because they refer to entire publications rather than parts. It is possible - but costly - to register DOIS for textparts, but it is always a static process. There is no _system_ to identify _any_ part, on the fly or otherwise. Moreover, DOIs are not URNs (although they are very much like them). **On the other hand "versioning DOIs" are possible, dus hoe zit dat?**

The easiest thing seems to be to take the DOI suffix as work identifier and insert that into a CTS URN. Thus:

**syntax** `urn:cts:research:textgroup:work:version:part`

**example DOI** `https://doi.org/10.1163/9789004393097_005` has suffix `9789004393097_005`

**example paragraph** has number `3`

**result** `urn:cts:research:9789004393097_005:3`

Bonus is that thus URN is resolvable - not to the lower levels, but still to the work level - via the DOI which can be construed from the URN and vice versa.

### Citability of secondary literature

The point of CTS is citability of text parts. How does that work for secondary literature?

Same as for primary literature. 

1. Define main structure. Usually paragraphs, in the case of books also chapters
2. Add anchors for the units. This is technology dependent. Bookmarks in PDFs. @n in XML and HTML.

The site publishing the content needs to offer additional finctionality - additional to the DOI resolving services that is offered by DOI registrars - that looks for the anchors and resolves them. 

Should pages play a role in the structure? It is certainly a traditional way of citing, but tied to particular formats (print, PDF). What is there is no print or PDF, or when it comes later? Paragraphs seem a safe bet. This is how the [TEI journal](https://journals.openedition.org/jtei/) does it, for example.

For linking to places in PDF ("destinations"), see [here](https://helpx.adobe.com/nl/acrobat/kb/link-html-pdf-page-acrobat.html) and [here](https://kbpdfstudio.qoppa.com/create-pdf-destinations-weblink-bookmark/) and [here](http://mirror.koddos.net/CTAN/macros/latex/contrib/hyperref/doc/paper.pdf). <!-- More documentation of this package: https://ctan.org/pkg/hyperref -->

