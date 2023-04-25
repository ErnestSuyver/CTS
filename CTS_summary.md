## Summary

### Why CTS
Scholars refer to texts - source texts - incanonical, i.e. non-manifestation specific, ways. So texts have canonical references, i.e identifiers. CTS builds on this tradition and makes these identifiers machine readable. This enables machines to retrieve or manipulate these texts. This enable digital editing, reading, publishing.

## What is CTS?
**Citable Text Services** - or CTS - is two things:

1. a system of persistent and unique identifiers for texts and data, the **CTS** and **CITE** **URNs**
2. an ecosystem of tools, such as the **Nautilus API**, the **CapiTainS** guidelines, and the **Scaife viewer**. 

### CTS URNs

* CTS URNs look like `urn:cts:namespace:textgroup.work.version:part.subpart@subreference`
* CITE URNS look like `urn:cite:namespace:collection:object.version`

The labels for namespace, textgroup, and work are normed, as is the language im the version identifier. A complete version identifiers consists of product acronym, cts flavor, edition, language ISO code, and version number.

### CTS ecosystem

Brill's [Scholarly Editions](https://gitlab.com/brillpublishers/scholarlyeditions) is part of the ecosystem, as the application itself makes use of Nautilus and Scaife. 

CapiTains as presented here is a complement to TEI. The XML fed to _Scholarly Editions_ is both TEI and CapiTainS compliant. However, the CTS principles are not limited to TEI. They can be applied to any text. At Brill, they also applied to _Brill Plain Text_, for example.

This is what CTs compliant TEI XML looks like

* Place URN in `@n` in first `<div>` in TEI P5 file
* Add `@type` to first `<div>` in TEI P5 file, with values “edition”, “translation” or “commentary”
* Add `@subtype` to first `<div>` in TEI P5 file, with values “introduction”, “prefaces”, “other_front_matter”, “commentaries”, “indexes”, “concordances”, “other_back_matter”, “toc”, to identify commentary type, if `div@type` has value “commentary”
* Add `@type` with value “textpart” to nested `<div>` or other elements that capture the part structure
* Add @subtype with part name as value to nested `<div>` or other elements that capture the part structure
* Add `@n` with incremental number to nested `<div>` or other elements that capture the part structure
* Add `@ana` with CTS URN to `<div>` of type “commentary”, or its subparts (like `<ab>`, if it pertains to a canonical text. (Cf `<ref cRef=”CTS URN”/>` in `<quote>`).
* Place edition information in `<teiHeader>`
* Place physical structure information in empty nodes
* Add `<refsDecl>` to `<teiHeader>`
* One folder per text group. Name: textgroup ID. This folder contains one metadata file (name: `__cts__.xml`) and one or more work folders
* One folder per work. Name: work ID. This folder contains one metadata file (name: `__cts__.xml`) and one or more work files
* One work file per version. Name: full urn minus namespace
* A work folder may also contain one or more commentary files. Name: full urn minus namespace
* One XML file per work, translation, commentary, etc.
* XML work file name derived from URN (e.g. `stoa0023.stoa001.brill-lat2.xml` and `stoa0023.stoa001.brill-comm1.xml`) 

These Brill CITE, CTS, CapiTainS guidelines from, together with the Brill TEI Guidelines, the generic set of instructions for the digitization and digital publication of text editions, translations, and commentaries. This generic set is always supplemented by a _specific_ set of instructions, detailing how the generic instructions are to be applied to an individual publication. 
