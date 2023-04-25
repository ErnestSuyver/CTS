## CITE, CTS, CapiTainS

### Why CITE
The following document is about CITE, a system for the identification of texts and any other object. CTS is the name for the identification system itself. CapiTainS is the name for the software suite built around it. Before we go into details, we need to ask two questions:
1. What is the use of CITE?
2. How can Brill benefit from it?

#### Uses of CITE
There are uses of CITE as an identification system, and as a standard.
1. CITE is an identification system. It can be used to identify any text, or any place in a text. We’re talking here about primary sources, including text editions. For the question of URNs for secondary literature, see the note below. CITE can also be used to identify objects: people, places, entities, photographs, down to the individual pixel or region of interest. This is a cornerstone of any academic endeavour. 
2. Identification of texts allows identification of references: one text referring to another. CITE allows us to capture and study these references. This is an area of enormous scholarly interest.
3. CITE is a standard. Not the standard; no such thing exists in the humanities. It is used in Classics, Medieval Studies, Early Modern History, Persian Studies, and Arabic studies. A number of institutions are committed to it, such as the Perseus project, the TLG, the Center for Hellenic Studies, and Digital Humanities departments at University College London, Leipzig University, and Vienna University. Several largescale project are using it, the oldest being Homer Multitext.
4. CITE allows for the automation of various tasks, among them quality control. 
5. On CITE, a software suite is built. (CapiTainS being the most recent version). This is software for storing and serving CITE compliant files and texts, API’s, scripts for processing of such files, and software for publishing them. The new Perseus interface, the Scaife Viewer, is a primary example.
6. An identification system like CITE makes the alignment of texts (for example, alignment of text and commentary, or text and translation) and the annotation of text (for example, text and notes, or text and critical apparatus) much easier.

#### Costs and Gains for Brill
Brill can benefit from the adoption of CITE as an identification system and standard.
1. Professionalization. The adoption of a standard provides Brill with guidelines in the areas for digitization, file processing, and storing and publishing texts. To date, no systematic method was applied, although a huge and rich body of knowledge has been built up, and no systematic description or instruction & control methods were set up. CITE can help create the required methodic rigour and shared knowledge.
2. Flywheel effect. CITE goes hand-in-hand with TEI. Much effort was invested in TEI. Brill gets more return on this investment when adopting CITE too. (We’re still underutilizing TEI, IMO).
3. Interoperability. Adoption of a standards allows Brill to interact with resources using the same standard. Brill could call-up texts from Perseus, in our own interface, leading to extra traffic. It is also good PR.
4. Cost saving. Why commission third parties to design and create platforms, when all of the heavy lifting has already been done? All Brill needs to do is use the existing software (after checking licenses) and adopt it to its own needs, building on the data infrastructure that is being created within the company. There is sufficient knowledge in the company (about standards, methods, coding, system architecture, etc.) to do so.

What will it cost Brill to adopt CITE? In monetary terms, probably nothing. It will save money. But there are a few issues that need to be decided beforehand.
* Where is CITE to be applied? See below for a suggestion.
* How is the knowledge of CITE to be shared and maintained? The Brill wiki?
* How is the CITE-based  infrastructure to be created and maintained? This question is answered elsewhere: in the investment proposals for the individual (large-scale) conversion/text edition projects

#### Where to use CTS URNS?
CTS URNs are designed for use in connection with primary sources, including text editions. Can they also be used in secondary literature? That is, Brill’s other publication types, such as journals, monographs, or reference works? The answer is: yes, unequivocally, for references to primary sources in such publications. (CTS URNs can be included in PDF and HTML as well as XML). For the question of whether CTS URNS can also be used to identify that secondary literature itself, see the note on URNs for secondary literature. For the question how to identify and tag references, see the section on “Automation”.
(HTML can use the @data-* attribute to store custom data, like `<div data-ctsurn="[some cts urn]/>` etc. Remember that URNs are not hyperlinks: they need to be resolved).

#### How Brill uses CITE
Brill uses CITE in the version of CapiTainS. See below. 
At this moment, CITE URNs are used to identify LGGA grammarians (as authors, not as textgroups). See the appendix on URNs for fragmentary texts.

#### How Brill uses CTS
Brill uses CTS URNs to identify texts (works), parts of works, and textgroups, both notionally and in specific versions. For the use of CTS servers and APIs, see the section on CapiTainS below.
The syntax of CTS URNs is explained below. This is just an example:

#### Examples:
```
Base URN: 		urn:cts:latinLit:stoa0023.stoa001
Text editions		Clark 1910 = brill-lat1
Seyfarth 1978 = brill-lat2
Random example	urn:cts:latinLit:stoa0023.stoa001.brill-lat1:19.5.3@postremo-19.5.3@tribunis
```

#### To sum up
* For each textgroup, an ID needs to be established
* For each work, an ID needs to be established
* For each version (edition), an ID needs to be established
* Before anything else, the namespace needs to be registered (but only once)

#### CTS and TEI
CTS is complementary to TEI. TEI tells us how to structure text and it allows for multiple identification methods, but it doesn’t specify how to identify. CTS URNs follow the logical structure of a work (in a given version, or even at notional level), and therefore have a tree structure. Likewise, XML has a tree structure. (Whether all texts do in fact have a tree structure is a different matter. See the note about empty TEI nodes.) Therefore, the TEI XML should to follow the logical structure. Using X-path, any part can be identified. Brill uses `<div>` elements (mostly) to capture the parts of the logical structure.

**The logical structure of a work is brought in line with the tree structure of the XML (X-path). This ensures valid CTS URNs and sound XML.**

We thus get:

**Aligning XML and logical structure of a work**

logic | XML | description
------- | ------- | ----------        
textgroup | n/a | CapiTainS requires textgroup to go into a folder consisting of files, one per version of a work.
work | `<div>` and `@n` and @type | CapiTains requires one file per version of a work. This a file of TEI XML. In the `<body>`, the first `<div>` contains the work as a whole. The `<div>` has an `@n` attribute with the work URN. The `<div>` has a @type attribute with the value “edition” to make it Epidoc compliant.
version | n/a | This information should be included in the `<teiHeader>`. See the section on TEI below.
part (and subparts, etc.) | Ideally, `<div>`. And always @subtype and `@n` | Parts (and subparts, etc.) vary per work. A `<div>` is the tag of choice, but this may not always be suitable. The @subtype attribute is mandatory. As value, it contains the name of the subtype. This can simply be “part”, but it could be something like “caput” or “stanza”. This would be explained in the publication specific digitization guidelines. Add `@n` with incremental number to nested `<div>` or other elements that capture the part structure.
subreference | n/a | Subreferences form part of the logical structure, but can vary, so receive no tag of their own. Unicode is the only requirement here. 

Remark about part: `<p>` is not allowed as a tag for part, because a paragraph is a typographical rather than a logical unit. `<l>` is not allowed either. Although a line is a part of a work (such as a poem), the `<l>` elements do not receive the @subtype attribute. Instead, the role of subpart identifier is played by the `@n` attribute that is used to number the lines. (Unnumbered lines are possible, but not as part of the logical structure).

#### Note on how to capture the physical structure
The aim is to bring the logical structure and the XML structure inline. However, in digitization projects, we’re dealing with versions (editions) rather than a notional work. These versions contain much information that is scholarly relevant, such as version information, commentaries, or things like sequence and selection. This is discussed in the section on how Brill uses CapiTainS.

Here, we focus on the physical structure of a work (version). By this, we mean the orthographic and typographic elements in the version containing the work. In a printed book, this is mainly confined to pages and lines. Such information is placed in empty node tags such as `<pb/>` and `<lb/>`. The `@n` attribute captures the number. In this way, the information is preserved without affecting the logical structure. Note that such elements mark the beginning of a unit of interest. `<pb>` means page beginning, not page break. (This is also how `<lb>` is used in Epidoc: at the beginning if a line). 

Empty elements like `<lb/>` are called “milestone elements” in TEI. (There are others: `<milestone>`, `<gb>`, and `<cb>`, for example). They can be used to indicate non-hierarchical structure structures, or to encode multiple, potentially conflicting or overlapping, reference systems. The typographical lines of a poem, for example, are not necessarily identical to metrical unit, to the grammatical unit, or to the units of narrative or speech. Likewise, a poetic line may attract multiple analytical views: syntactic, semantic, hermeneutic, etc. See [TEI chapter 3.10.3 Milestone Elements](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html#CORS5). There is some overlap between this situation, the situation of non-OHCO compliancy, and the situation of multiple annotations. For now, we confine ourselves to `<pb>` and `<lb>` and place them in the XML file containing the work (version).

There is some overlap between the situation of physical vs. logical structure and print vs. online publication. However, we dealing with structure here, not representation, and even the choice for a dominant hierarchy (the logical structure) predisposes nothing in this respect.

#### How Brill uses CapiTainS
Brill uses the CapiTainS Software suite for storing, serving, and publishing citable texts. The section on software etc. still needs to be written. The [CapiTains Guidelines](http://capitains.org/pages/guidelines) contain instructions on the position URNs, directory structure, and metadata files. We cover them here in as far as they are relevant to Brill.

#### URN insertion
First off: there is no need to stuff an TEI file full of URNs. We only need a single URN to identify the work and ensure that any possible URN can be created from it. The CapiTains Guidelines don’t clearly state where the URNs should sit in the XML, but the accompanying literature does: in an `@n` attribute in the first `<div>` element.

#### Example:
```
…
<text><body>
         <div xml:lang="lat" type="edition" n="urn:cts:latinLit:stoa0023.stoa001.perseus-lat1">
            <head>Ammiani Marcellini Rerum Gestarum libri qui supersunt</head>
    …
```

Of course, this is relevant only for URNs identifying a work. For references, or the use of URNs in other contexts, it is a different matter. The TEI Guidelines and publication-specific digitization guidelines state how to include URNs in such cases.

So: **To identify a work, insert CTS URN in `/tei:TEI/tei:text/tei:body/tei:div@n`**

#### Version identification
CapiTainS recommends (but doesn’t require) that the version is identified with a project name, followed by a dash, an ISO 639-2 code, and an incremental number (e.g. ciham-fro1, perseus-eng1, opp-lat1, etc.). Brill follows this recommendation. Hence we have urn:cts:latinLit:stoa0023.stoa001 as the base URN for the Res Gestae by Ammianus Marcellinus, a work written in Classical Latin, and urn:cts:latinLit:stoa0023.stoa001.brill-lat1 for the Clark edition of 1910 that Brill intends to publish together with the commentary on that work. Likewise, urn:cts:latinLit:stoa0023.stoa001.brill-lat2 is the Seyfarth edition of 1978. 

So: **To identify a version, add brill hyphen ISO language code incremental number to the work identifier in the CTS URN**

Note that the ISO 639-2 codes are not identical to the IANA codes that Brill uses to indicate languages as values of @xml:lang. For Ammianus, we might have @xml:lang=”la-Latn”, whereas the version bit in the URN might read “lat1”.

#### Citation information: refsDecl
The citation scheme is reflected in a refsDecl node, in the `<encodingDesc>` element of the `<teiHeader>` of the edition. In this `<refsDecl>` element, cRefPattern nodes are used to define citations levels and their xpaths. A quick overview:

* refsDecl should be in /TEI/teiHeader/encodingDesc.
* refsDecl should have its `@n` property set on “CTS”
* refsDecl contains as many cRefPattern as there are levels
* cRefPattern elements are ordered from deeper node to highest node
* the matchPattern should give an information about the number of level. Traditionally, we use (\w+) regexp to match identifiers
* the replacementPattern should contain $[1-9] which represents depth of a level, i.e. a work part like “caput 1 section 9” should match the following xpath: `/tei:TEI/tei:text/tei:body/tei:div/tei:div[@n=’1’]/tei:div[@n=’pr’]/tei:div[@n=’9’]`

The point of the `<refsDecl>` is to transform a CTS URN into an XPath. It is the connection between the technology-independent CTS scheme and the XML, in this case TEI.

#### Example
```
<refsDecl n="CTS">
  <cRefPattern n="level3" matchPattern="(\w+).(\w+).(\w+)"       replacementPattern="#xpath(/tei:TEI/tei:text/tei:body/tei:div/tei:div[@n='$1']/tei:div[@n='$2']/tei:div[@n='$3'])">
      <p>This pointer pattern extracts level1 and level2 and level3</p>
  </cRefPattern>
</refsDecl>
```

These `@n` attributes are not to be confused with the `@n` attribute in the first `<div>`, containing the work URN.

In short: *Add CapiTainS-style `<refsDecl>` to `<teiHeader>`**.

#### Structured Metadata
CapiTainS allows for the inclusion of additional structured metadata to any type of object. In TEI files, this information is stored in the `<teiHeader>`. For example, `<dc:publisher>`. This requires the inclusion of a namespace declaration. The declaration for the CapiTainS namespace should appear as the first attribute on the root tag of the XML tree of the metadata file, followed by any other namespaces. For example: `<TEI xmlns:cpt="http://purl.org/capitains/ns/1.0#" xmlns:dc="http://purl.org/dc/elements/1.1/">`. 

If you do this, then you should add a `<cpt:structured-metadata>` node as a child of the node belonging to the object that the structured metadata describes, i.e. the textgroup, work, edition, translation, or commentary. This in fact creates a triple (which may be expressed in RDF). If, for example, the subject is an edition node, than the Dublin Core publisher tag is a the predicate and its value the object. In this way, we can say that Brill published the edition.

We have yet to implement this.

#### Directory structure
CapiTainS requires that a text repository be built with a main data folder. The data folder should contain directories which are named after the textgroup identifier. So `urn:cts:latinLit:phi1294.phi002.perseus-lat2` would have a directory `phi1294`. The textgroup directory contains a `__cts__.xml` file containing metadata about the textgroup. It also contains directories which are named after the work identifier. So `urn:cts:latinLit:phi1294.phi002.perseus-lat2` would have a directory `phi002`. The work directory contains the edition and commentary files. It also contains a `__cts__.xml` file containing metadata about the work, i.e iets  editions. Edition, translation, and commentary files are named after their urn using every component except the namespace. So `urn:cts:latinLit:phi1294.phi002.perseus-lat2` would be `phi1294.phi002.perseus-lat2`.

#### Recap 
* One folder per text group. Name: textgroup ID. This folder contains one metadata file (name: `__cts__.xml`) and one or more work folders
* One folder per work. Name: work ID. This folder contains one metadata file (name: `__cts__.xml`) and one or more work files
* One work file per version. Name: full urn minus namespace
* A work folder may also contain one or more commentary files. Name: full urn minus namespace

#### Metadata Files – Textgroup
The metadata files aren’t TEI XML, but nodes specific to CapiTainS coming from its own namespace.
The textgroup metadata file looks as follows. The URN of the textgroup node contains only the URN up to the textgroup component. Groupname is the name of the textgroup. There needs to be at least one groupname node, with a @xml:lang declaration.

```
<ti:textgroup xmlns:ti="http://chs.harvard.edu/xmlns/cts" urn="urn:cts:latinLit:phi1294">
    <ti:groupname xml:lang="eng">Martial</ti:groupname>
    <ti:groupname xml:lang="lat">Marcus Valerius Martialis</ti:groupname>
</ti:textgroup>
```

#### Metadata Files – Work
The work metadata file looks as follows. The work node has three attributes: (1) a groupUrn, containing only the URN up to the textgroup component; (2) the URN, containing only the URN up to the work component; (3) an @xml:lang attribute, reflecting the language of the work in the edition. 

Work must have at least one title node. The title node needs a xml:lang declaration, it reflects the language of the title. 

Next follows an ti:edition node. It has two attributes: (1) workUrn, containing only the URN up to the work component; (2) URN, containing the full URN. Edition must have at least one label node, representing the title of the edition. The label node needs xml:lang declaration, reflecting the language of the title. Edition must also have at least one description node. It needs a xml:lang declaration, reflecting the language of the description.

CapiTainS allows for the inclusion of translation and commentary nodes as well. It is unclear to me whether they regard them as version of a work. In any case, there can be ti:translation and ti:commentary nodes, that operate much the same as ti:edition. Translation has three attributes:(1) workUrn, containing only the URN up to the work component; (2) URN, containing the full URN; (3) xml:lang, containing the language of the translation. Commentary has the same attributes, but it has an extra node: the ti:about node, with one attribute: (1) URN, containing the URN of the textgroup, work (edition, translation, or commentary) that this commentary is about.

Note how “edition”, translation”, and “commentary” are mandatary values for @type in Epidoc. We are using @type accordingly, see above.

```
<ti:work xmlns:ti="http://chs.harvard.edu/xmlns/cts" groupUrn="urn:cts:latinLit:phi1294" urn="urn:cts:latinLit:phi1294.phi002" xml:lang="lat">
    <ti:title xml:lang="lat">Epigrammata</ti:title>
    <ti:edition workUrn="urn:cts:latinLit:phi1294.phi002" urn="urn:cts:latinLit:phi1294.phi002.perseus-lat2">
        <ti:label xml:lang="lat">Martialis Epigrammata</ti:label>
        <ti:description xml:lang="lat">M. Valerii Martialis Epigrammaton libri / recognovit W. Heraeus</ti:description>
    </ti:edition>
    <ti:translation workUrn="urn:cts:latinLit:phi1294.phi002" urn="urn:cts:latinLit:phi1294.phi002.perseus-eng2" xml:lang="eng">
        <ti:label xml:lang="eng">Martial's Epigrammata</ti:label>
        <ti:description xml:lang="eng">[Some translation information]</ti:description>
    </ti:translation>
    <ti:commentary workUrn="urn:cts:latinLit:phi1294.phi002" urn="urn:cts:latinLit:phi1294.phi002.perseus-eng3" xml:lang="eng">
        <ti:label xml:lang="eng">Introduction to the English translation of Epigrammata</ti:label>
        <ti:description xml:lang="eng">[Some commentary information]</ti:description>
        <ti:about urn="urn:cts:latinLit:phi1294.phi002.perseus-eng2"/>
    </ti:commentary>
</ti:work>
```

#### Commentary files
The commentaries deserve further specification, because text editions can be manifold and contain all manner of information that can be termed “commentaries”. The CapiTainS Guidelines state: “[Commentaries are] modern texts that comment on other texts. This could include the front or back matter of an edition or translation, e.g., the introduction, glossary, appendix, etc. It could also include modern volumes that were written specifically as commentaries on a text”.

We can distinguish the following types of commentary: 
1. introductions
2. prefaces
3. other_front_matter
4. commentaries
5. indexes
6. concordances
7. other_back_matter
8. toc – this is a file that gives a certain grouping or sequence of a work or its parts according to a given edition. Such information is scholarly significant and needs to be captured

Note that
* The critical apparatus is not a commentary and therefore does not get its own file. Instead, it sits in the work file (version)
* A translation is not a commentary but does sit in its own file. Note that we are talking about contemporary scholarly translations. Translations that belong to the textual tradition are treated as primary sources
* Previous text editions that belong to the textual  tradition of a work are treated as primary sources
* Works that are plagiarized, or works that are variants of other works (e.g. in respect to style or theme) are likewise treated as primary sources. (This includes fragments, see below)

Each commentary
* sits in its own file
* gets in its first `<div>` element a @type attribute with the value “commentary” and a @subtype attribute with one of the eight values listed above
* gets in its main `<div>` element a @ana attribute with a CTS URN to connect it to the work to which the commentary pertains (@ref would be better but is not allowed, alas)
* is structured in accordance with the Epidoc, TEI, CTS, CITE, and CapiTainS guidelines

The name of a commentary file is `stoa0023.stoa001.brill-eng1.xml`, etc.

I wonder if we should replace the -eng etc. identifier in the version identifier by -comm? There is no way to distinguish commentaries from translations (nor modern translations from older ones) in the file name.

#### Other files
To be decided: how to deal with illustrations and such like.

#### How Brill uses TEI
This is out of scope of this document, but needs to be mentioned here, since we’re laying down requirements for our files:

* mandatory: reference to TEI schemas in `<teiHeader>`
* mandatory: tagging as described in the [Brill TEI Guidelines](??????)
* inclusion of information about the edition in the `<teiHeader>`

About the last point: this concerns the `<titleStmt>` element and the `<biblStruct>` in the `<sourceDesc>` element. For example:

```
<teiHeader>
    <fileDesc>
        <titleStmt>
            <title type="work">Rerum Gestarum</title>
            <title type="sub">Machine readable text</title> 
            <author>Ammianus Marcellinus</author> 
            <editor role="editor" n="Rolfe">John C. Rolfe, Ph.D., Litt.D.</editor>
            <sponsor>Perseus Project, Tufts University</sponsor> 
            <principal>Gregory Crane</principal> 
            <respStmt>
                <resp>Prepared under the supervision of</resp>
                <name>Lisa Cerrato</name>
                <name>William Merrill</name>
                <name>Elli Mylonas</name>
                <name>David Smith</name>
            </respStmt>
            <funder n="org:AnnCPB">The Annenberg CPB/Project</funder>
        </titleStmt>
        <extent>About 100Kb</extent>
        <publicationStmt>
            <publisher>Trustees of Tufts University</publisher>
            <pubPlace>Medford, MA</pubPlace>
            <authority>Perseus Project</authority>
        </publicationStmt>
        <sourceDesc>
            <biblStruct>
                <monogr>
                    <author>Ammianus Marcellinus</author> 
                    <title>With An English Translation</title>
                    <editor role="editor" n="Rolfe">John C. Rolfe, Ph.D., Litt.D.</editor>
                    <imprint> 
                        <pubPlace>Cambridge</pubPlace> 
                        <publisher>Cambridge, Mass., Harvard University Press; London, William Heinemann, Ltd.</publisher>
                        <date>1935-1940</date>
                    </imprint>
                </monogr>
            </biblStruct>
        </sourceDesc>
    </fileDesc> 
```


#### How Brill uses Epidoc
This is out of scope of this document, but needs to be mentioned here, since we’re laying down requirements for our files:

* mandatory: reference to Epidoc schemas in `<teiHeader>`
* mandatory: div@type [fixed values: edition | apparatus | bibliography | commentary | textpart | translation ] This goes into the *first* `<div>` in the `<body>`

No other tag from Epidoc is mandatory. Epidoc is but a selection from TEI tags. There are no extra tags. Note, however, how Brill uses an attribute that is often used in Epidoc, @subtype, to create a human and machine readable tree structure for the part element in the URN syntax, and for specifying the type of commentary. In other words, Brill is making the XML and the URN structurally consistent. See above. This is possible because in Epidoc, @subtype has no mandatory values. 

Please refer to the [Brill TEI Guidelines](https://brillpublishers.gitlab.io/documentation-tei-xml/epidoc.html) for a section on Epidoc.

@subtype specifies
* the textpart, if @type has the value “textpart”. In that case, @subtype takes a value that name a textpart, like “caput” or “section”. Such names will be found in the publication-specific digitization guidelines (never in the first `<div>`)
* the type, if @type has the value “commentary”. In that case, @subtype takes one of the eight values listed above (always in the first `<div>`)

