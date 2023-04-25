## FRBR
The _Functional Requirements for Bibliographic Records_ (FRBR) is an ontology for intellectual endeavour developed by the _International Federation of Library Associations and Institutions_ (IFLA). FRBR comprises multiple groups of entries, but in this context, we're only concerned with the first. Group 1 entities are work, expression, manifestation, and item, as the four products of intellectual or artistic endeavour.

Each entity is more concrete, more tangible than the former. A work is a distinct intellectual or artistic creation, such as Beethoven's Ninth Symphony. An expression is the realization of such a work: the musical score Beethoven wrote; the melody he whistled. A manifestation is likewise an expression, but taken in its physical aspect: musical scores, performances, recordings. An item is a single exemplar of a manifestation: this particular recording; this particular sheet of music in my hand. 

a plaatje goes here

This ontology is fraught with difficulties. However, the point is that the ontology can be used – through insertion in the CTS URN – to **identify a particular version of a work**. Such information is inserted after the work identifier; version and exemplar are separated by a full stop. For example:

1. URN of work: urn:cts:greekLit:tlg0027.tlg001
2. URN of expression: n/a
3. URN of manifestation: urn:cts:greekLit:tlg0059.tlg030.perseus-grc1
4. URN of item: urn:cts:greekLit:tlg0012.tlg001.msA.thosJeff

A few remarks:

* FRBR _work_ is implied identified by having no other identifier than work and textgroup (“notional level”).
* FRBR _expression_ has no place in the URN. 
* FRBR _manifestation_ in the URN often refers to the institute that has published a digital version of a print work, and adds the language of the work that is critically edited and a version number. **This is a lot of complex information, that is in no way formally and structurally expressed in the URN. This makes the URN unfit for machine-reading, IMO. Hence the additional XML instructions in this document.**
* FRBR _item_ is doubly expressed: msA is not a manifestation, but an item, as there is only one. I assume this is a mistake by the people of the Homer Multitext project, who give this example. They also claim .msAVill is a manifestation, which by their logic ought to be a manifestation and an item (“.msa.Vill”). Moreover, the item (msA) is a physical object. According to CITE, such objects are identified by CITE2 URNs, so it has no place here. 

### Physical structure and digital
There is more to this. Version has a physical aspect. Take, for example, a printed text edition: Burnet's edition of Plato's Republic in the Oxford Classical Texts series, published between 1902 and 1906. This is clearly a version of a canonical text, a work by Plato. It contains a number of Plato’s works; has a certain lay-out and hence certain page numbers and certain line numbers. 

This physical aspect is not expressed in the CTS URN. `urn:cts:greekLit:tlg0059.tlg030.perseus-grc1` refers to the digitized version of the print edition. This is contrary to the pretension of CTS URNs. The problem is hard to solve, as the version information sits before the part information, and the part information pertains only to the logical structure. This is also the reasons why CTS URNs for print works, are hard. See also the note on URNs for secondary literature. 

Furthermore, the difference between manifestation and exemplar is meaningless in a digital context, but the importance of version grows. Version and edition are different things. It is unpredictable what the difference between two editions might be. But it is certain that within one edition, difference versions can occur. After all, online publications excel in dynamic publication of new content, additional content, corrections, etc. Moreover, the version can depend on the user. In a freemium business model, for example, a paying user would see more content than others. In the academic world, this has problem is solved in the **citation**, which gives time stamp and user details in addition to more traditional bibliographic data. However, the addition of such dynamism will make CITE as a citation system impractical, if not completely unusable. **We therefore need to stick to manifestation**. For Brill, this means we'll add the edition, following the pattern of “perseus-grc1”.

It is the responsibility of the publisher to decide on the difference between editions and identify them accordingly. Brill uses DOIs to identify digital documents. 10.1163/1873-5363_boj_a34 and 10.1163/1873-5363_bnj_a34 therefore identify different editions. (With Jacoby Online, it’s a problem that publication and edition are confused, but that is a different matter. It underlines the need for clarity and responsibility). Note that DOIs operate on the level of manifestations, as do ISBNs and ISSNs.

Last remark: where the conceptual model of FRBR aims to represent bibliographic entries as they are cataloged by librarians, CTS URNs aim to model works as they are cited by scholars.

### Physical structure and semantic
A CTS URN combines organizational hierarchy with conceptual hierarchy: work structure with FRBR-based version. We said that work structure is logical, meaning it operates at notional level. Does this make the versions a matter of physical structure? That would make us blind for the semantic structure. Take the example of Burnet’s edition mentioned above. Is the selection and sequence of Plato’s work in this edition physical? Yes, but also scholarly meaningful, i.e. semantic. The same can be said for layout and typography. (Calligraphy and calligrams make clear how logical, physical, and semantic structure are not sharply distinguishable).

Physical structure needs to be captured in XML; at the very least in cases where the print edition existed prior to the online, and references based on the physical structure are prevalent. The note about empty TEI nodes makes a start with documenting how this information should sit in TEI P5 XML. The XML structure follows the logical structure (both are trees) and the physical structure is represented by milestones in the XML (empty nodes). We still have to begin doing this for semantic information. If we want to include such features in our publications, we need to instruct the digitizing parties accordingly.

### A note on URNs for secondary literature
Semantics aside, two structures can be distinguished in a work: logical and physical. The logical structure is the division of the work in smaller parts: chapters, poems, sections, lines, phrases, etc. The physical structure is volume, page, line. To keep it simple, we place typographical features in the physical structure: marginalia, chapter division, sequence of sections, etc. The front matter and the back matter belong here, too. 

Digital publications have exactly the same two structures. But while the logical structure remains the same, independent of the medium (although it may differ per version!), the physical structure varies unpredictably. This is because the representation (“display”) depends on the user's device, and that cannot be known in advance. (Besides, there is an ever growing multitude of devices). Physical features of previous (print) version – such as page and line numbers - can be persevered in the digital version, but as information (sitting in empty odes), not a (stable) physical structure. However, print editions also have physical variety. They deal with this trough the logical structure of a work. 

How does this relate to CTS URNs for secondary literature? Secondary literature has physical structure, but no explicit logical structure. There is no canonical text, hence no CTS is possible. Fortunately, this problem can be solved: add paragraph markers to secondary literature. Paragraphs are typeset in a certain way, so seem to belong to the physical structure. But in fact they represent chunks of an argument and therefore can be said to belong to the logical structure. The addition of such markers enables inclusion in a URN and hence the use of URNS for secondary literature. This solution would allow Brill to add translations, commentaries, and related monograph and journal content to a CapiTainS infrastructure for the publication of primary sources (text editions). 
