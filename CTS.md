## CTS Explained

### Background
The requirement was to find identifiers – in this case for texts – that are semantically complete, machine-actionable, and technology independent. The Uniform Resource Name (URN) system provides such identifiers. As the Internet Engineering Taskforce says in RFC 2141: “Uniform Resource Names (URNs) are intended to serve as persistent, location-independent, resource identifiers”. See https://www.rfc-editor.org/rfc/rfc2141.txt and https://en.wikipedia.org/wiki/Uniform_Resource_Name. Note that CTS URNs, like CITE2 URNs, are part of the CITE architecture. 

CTS is an acronym for _Canonical Text Service_. “Canonical” are texts referred to at notional level (as in “the first line of the Iliad”), without specifying a particular version (as in “as quoted by the learned professor”). Formally identifying references makes it possible to analyze the relations between texts and to study the context and meaning of a citation. In a digital environment, numerous applications can be (and are) built that serve, connect, and help analyze such linked texts.

### URNs

There are several types of URNs, or [Universal Resource Names](https://en.wikipedia.org/wiki/Uniform_Resource_Name). Two well-known examples are ISBN and ISSN. For example:

`urn:isbn:0451450523` = The 1968 book _The Last Unicorn_
`urn:ISSN:0167-6423` = The scientific journal _Science of Computer Programming_

This section is specifically about CTS and CITE URNs. (DTS URNs don't exist; DTS is more about updating the CTS API).

The distinction between CTS and CITE URNs is that the former is for citable text, the latter for everything else. These two realms have very different ontologies, even if the syntax of the URN is similar.

In a previous interpretation, CTS URNs were only used for _canonical_ texts. This lead to problems with non-canonical texts, such as fragmentary texts. Following its decision to use the Scaife viewer for the publication of texts ("scholarly editions"), all texts receive CXTs URNs at Brill. Of course, not everything that is published is a text. There is also metadata, for example. This is where CITE comes in.

### CTS Semantics
CTS URNs are citations. They express the organization of a text according to the OHCO2 model. This means they presuppose that a text has a tree structure (hierarchy) as its data model. In fact, CTS URNs refer to a passage of text in terms of two hierarchies, sc. **organizational hierarchy** and **conceptual hierarchy**.

The conceptual hierarchy identifies a text in term of the conceptual model of the Functional Requirements for Bibliographic Records (FRBR). In this model, a text can either be a work at the notional level, or concretely a specific version of a work, for example a speech, a recording, or a webpage. This specific version is included in the CTS URN.

The organizational hierarchy is the attribution of a **work** (in the FRBR sense) to a **textgroup**, and the division of a work into smaller **parts**. This is expressed in the CTS URN. This hierarchy is very close, if not identical, to common citation practice in the humanities. For “textgroup” there is no no direct parallel in FRBR; it is not the same thing as authorship; any collection of works is a text group. Nor do “parts” play a role in FRBR. However, any notional work will have some version, and this is central to FRBR: the expression of a work in manifestations (generic expressions, like “Brill's Companion to Ancient Geography” or “ISBN 978-90-04-28471-5”, or items (specific expressions, like the individual copy of that work in my hand). Editions and translations are also versions.

Note that not all logical citation schemes are alike. A poem will have a different organizational hierarchy than a prose text. The parts (smallest citation unit) can therefore differ, and there may be multiple levels of citation unit. Also, a CTS URN does not only identify units, it can also cite ranges or substrings, down to individual characters. It may well be that such units and ranges differ per version, even if it is notionally the same work. CTS URNS with subreferences therefore are only valid when they have a work identifier that is specified to the level of a version (edition or translation), or item.

Remember, however, that CTS URNs have only one job: to identify texts. Their semantics is not relevant; we should not regard URNs as semantic.

### Syntax of a CTS URN
A minimal CTS URN must look like this: `urn:cts:namespace:work:part`.

We see here:
1. a urn prefix (required: always urn)
2. urn name space, or protocol identifier (required: always cts)
3. registrar namespace (required: a value that can be resolved to a unique URI in the GetCapabilities reply of a recognized CTS service; the registry identified by the CTS namespace component)
4. work (required)

Note how these four elements are separated by a colon. (Meaning that a semicolon as a data value must be escaped). 

Now, work can be further subdivided: `urn:cts:namespace:textgroup.work.version:part`

We see here:
1. textgroup identifier (optional; values must be registered within the namespace)
2. work identifier (required; values must be registered within the namespace))
3. Version (optional; 

Note how these three elements are separated by a full stop. Identifiers can be any combination of letters and numbers (as long as ASCII?). 

Know also that version can be further subdivided into a version identifier, a language identifier, and a version number: `urn:cts:namespace:textgroup.work.version-li1:part`

The language identifier must be a value from ISO 639-2. 

Part can be further subdivided:`urn:cts:namespace:textgroup.work. version-li1:part.subpart@subreference`

We see here:
1. part (optional; can indicate ranges)
2. subpart (optional; can indicate ranges; can be repeated as often as required: subsubparts, etc.)
3. subreference (optional; can indicate ranges)

Parts and subpart are separated by a full stop. Subreferences are separated by the @sign. A range is formatted as two (sub)parts or subreferences separated by a hyphen.

Some examples:
1. A reference to the textgroup of  “Homeric” texts: urn:cts:greekLit:tlg0012
2. A reference to the Iliad at notional level: urn:cts:greekLit:tlg0012.tlg001:
3. A reference to line 10 of book 1 of the Iliad: urn:cts:greekLit:tlg0012.tlg001:1.10 
4. A reference to lines 10-20 of book 1 of the Iliad (i.e. a ranges): urn:cts:greekLit:tlg0012.tlg001:1.10-1.20
5. A reference to the edition of the Iliad as found on Perseus (http://www.perseus.tufts.edu): urn:cts:greekLit:tlg0012.tlg001.perseus-grc1
6. A reference to the second word of line 10 of book 1 of the Iliad in the edition found on Perseus: urn:cts:greekLit:tlg0012.tlg001.perseus-grc1:1.10@ἄνα

These examples give but a hint of what is possible. Here is a more exotic example:

7. urn:cts:croala:tubero.commentarii.croala-loci:body1.div4.div1.p2.s3.placeName2

This is interesting because it uses natural language to identify textgroup (by author!) and work, and then follows the XML tree (X-path) in the part. See here for more examples: http://croala.ffzg.unizg.hr/basex/cp/list.

Just a reminder: uniform resource names are part of the information structure of the internet. ISSNs and ISBNs can be expressed as URNs (e.g., urn:isbn:0451450523), as can National Library Numbers (e.g., urn:nbn:de:kobv:b4-opus-24327).

### CTS server and API
This is an excellent explanation: http://dlib.nyu.edu/awdl/isaw/isaw-papers/7/almas-babeu-krohn/. Examples of CTS servers: https://github.com/Capitains (background), https://github.com/ThomasK81/LightWeightCTSServer, http://cts.dh.uni-leipzig.de/, and http://cts.perseids.org/ 

### See also
* CTS protocol: http://cite-architecture.github.io/cts/ 
* CTS urn notation: http://cite-architecture.github.io/about/ctsurn 
* CTS on Perseus: https://github.com/PerseusDL/catalog_pending/wiki/CTS-URNs-and-Work-Identifiers:-Overview-and-Perseus-Catalog-Usage 
* Digital Classicist Wiki: https://wiki.digitalclassicist.org/Canonical_Text_Services 
* More CTS services: https://www.scads.de/de/2-uncategorised/303-canonical-text-service (with explanation), and http://cts.informatik.uni-leipzig.de/CTS_URNs.html
* Another example of CTS: http://croala.ffzg.unizg.hr/. See for an (excellent) explanation: Jovanović, N., Simrell, A. (2016). Implementing Canonical Text Services in the Croatiae Auctores Latini Digital Collection. In Digital Humanities 2016: Conference Abstracts. Jagiellonian University & Pedagogical University, Kraków, pp. 588-590. URL: http://dh2016.adho.org/abstracts/229. Note sure where they keep the code: https://github.com/nevenjovanovic?tab=repositories?
* More examples: https://alraqmiyyat.github.io/OpenITI/ and http://divan-hafez.com/index.php 
* See also: https://github.com/PerseusDL/tei-conversion-tools/wiki/CTS-Compliance,-Basic-(and-Abstracted)-Markup-Requirements
