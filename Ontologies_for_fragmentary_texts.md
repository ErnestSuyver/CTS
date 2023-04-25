## Ontologies for fragmentary texts
Fragmentary texts are texts that are preserved as fragments rather than as entire works. These fragments are often preserved as parts of other texts. Such parts can be regarded as “citations”, such as quotation, paraphrase, or allusion. Identifying fragments is an act of interpretation. 

(Critical editions of fragmentary texts tend to reconstitute the lost text and compile fragments to form a lost work. This neglects the aspect of citation (= repetition, i.e. variation of the same). This can be mitigated by focus on context and variation. Hence BNJ2. A digital publication therefore needs an interface that supports this).

Citing is a relation between texts, in this example between lost work and preserving work. (In _Jacoby Online_, the preserving work is called "source work). CTS URNs do not express such relations. (They do express relations, for example the isPartof relation between textgroup and work, or the isVersionof relation between work and manifestation. But CTS URNS are not to be taken semantically). Instead, such relation are expressed in a triple. A triple is a relation between subject and object. The predicate is the expression of the relation. Unlike URNs, triples are not about identity. They are about meaning. 

### FRBRoo, CIDOC-CRM, SAWS
The creation of triples requires well-defined relations between well-defined subjects and objects. In other words, an ontology. Using standards and profiting from experience is preferable to reinventing the wheel. Is there a ready ontology we can turn to when modelling fragmentary texts? Before we look into that, let’s have another look at some characteristic relations of fragmentary texts.

As texts, fragmentary texts exist in relation to textgroup, historical context, style, subject, etc. As fragments, fragmentary texts exist in a few special relations:

a. Whole-part relation: fragmentary texts are parts of a (lost) whole
b. Unpreserved-preserved relation: fragmentary texts are preserved in works other than the unpreserved whole
c. Citation relation: fragmentary texts are preserved as citations (of unpreserved texts) in preserved texts

Of course, more relations result from the reconstruction of lost works, such as fragment collections and the relation between the preserving text and fragment. 

Which ontology models there relations?

1. [CIDOC-CRM](http://www.cidoc-crm.org/).
 a. E33 Linguistic Object - P106 is composed of (forms part of) - E33 Linguistic Object
 b. E33 Linguistic Object - P1 is identified by (identifies) - E64 End of Existence versus E33 Linguistic Object - P1 is identified by (identifies) - E77 Persistent Item
 c. n/a

It is clear that only relation a. is properly modelled in CRM. 

2. FRBR. Or rather, [FRBRoo](http://www.cidoc-crm.org/frbroo/home-0). FRBRoo is an extension of CIDOC-CRM. Where CRM has E (classes) and P (properties), FRBRoo has F (classes) and R (properties). 
 a. F22 Self-Contained Expression - R15 has fragment - F23 Expression Fragment
 b. n/a
 c. n/a

Ad a. FRBRoo F23 Expression Fragment is a subclass of FRBRoo F2 Expression, which itself is a subclass of CIDOC-CRM E73 Information Object, which is a superclass of E33 Linguistic Object. It will come as no surprise that R15 has fragment is a subproperty of CIDOC-CRM P106 is composed of.
FRBRoo presents a refinement of CIDOC-CRM, but does not help us further. 

3. [SAWS](https://ancientwisdoms.ac.uk/). SAWS itself uses CIDOC-CRM and FRBRoo, but adds its own classes and properties. (The venerable SAWS project also uses CTS).
 a. This means this relation can be expressed in SAWS along the lines of CRM or FRBRoo. However, SWAS has useful properties of its own, such as isTransmittedBy, isVariantOf, isVariantTranslationOf, isVerbatimOf, isVerbatimTranslationOf, isVersionInAnotherLanguageOf, and isVersionOf.
 b. ?
c. See a.

Brill can use SAWS. And, like SAWS, we can mint our own classes and properties if needs be. We need to ask the users, when the time comes, what they need. And we need to consider more closely what relations we need to model. We also need to consider to what extent we can model generically (i.e. holding true for all fragments) vs. specifically (i.e. holding true for individual cases, e.g. with complex tradition histories).

The creation of triples expressing textual relations is but part of the larger job of expressing all Jacoby Online metadata in triples. This job has yet to be completed. 

### Open Annotation

Every reference is a relation between the citing text and the cited text. Relations can be expressed in linked data as triples. If we then add who is saying that text a relates to text b in a certain manner, we arrive at the _Open Annotation Model_. See https://www.w3.org/blog/news/archives/6156 . (This allows for the combination with other relevant ontologies, such as FRBRoo, CIDOC-CRM, and HuCit. HuCit is an ontology aimed at the formal representation of humanities citation structures). Note that such linked data can already be found in the _Classical Works Knowledge Base_ (http://cwkb.org/).

Triples belong to the core of CITE. For example, connections between objects and texts are expressed as triples. Homer Multitext have produced URNs for each line of the Iliad as work; e. g. book 6, line 119 is described by urn:cts:greekLit:tlg0012.tlg001:6.119. An RDF triple connects this to URN of a line in the edition of the Venetus A codex (urn:cts:greekLit:tlg0012.tlg001.msA:6.119). It is not necessary (nor allowed) to have triples connecting URLs with URNs, (e.g. chs.hardvard.edu/datans/mss/msA-012r with urn:cts:greekLit:ltg0012.tlg001.msA:1.1). URNs are not hyperlinks: they need to be resolved to do that. So choose wisely. Moreover, URLs are not stable identifiers and cannot be used in RDF.

This principle also applies to the testimonia in _Jacoby Online_. They will already have a CTS URN because the belong to a “source work”. What is missing is the attribution to a textgroup. The URN does not say they are a testimony to a certain “historian” (= textgroup). Such information about the relation between texts is not expressed in CTS URNs, but in triples, for example in a schema like Open Annotation. The attribution can be expressed like: instance X of the class XX (where X is the URN and the class is a work in the FRBR ontology) hasProperty (where the property is: isTestimonyof) instance Y of class YY (where Y is again a URN, but now of a textgroup, and the class is again a FRBR class, according to Z  of the class ZZ (where Z is a VIAF or ORCID instance, and ZZ is perhaps dc:author.).

### Automation

Such annotations can be created automatically from the texts and their URNs. Likewise, references can be extracted automatically from texts, in a two-step process: (1) identification of a reference as a reference; (2) identification of this instance of reference. This results in the formal expression of a reference, including correct tagging and URN. Scripts with comparable functions are already developed for Brill.

### See also

* CIDOC-CRM: http://www.cidoc-crm.org/Version/version-6.2.3 
* FRBRoo: http://www.cidoc-crm.org/frbroo/sites/default/files/FRBRoo_V3.0.pdf (I also rather like the graphic representation on the old CIDOC site: http://old.cidoc-crm.org/frbr_graphical_representation/graphical_representation/graphical_representation.html )
* SAWS: http://www.ancientwisdoms.ac.uk/media/ontology/doc/ 
* Christopher W. Blackwell and D. Neel Smith, The Homer Multitext and RDF-Based Integration, ISAW Papers 7.5 (2014) URL: http://dlib.nyu.edu/awdl/isaw/isaw-papers/7/blackwell-smith/ 
* Matteo Romanello and Michele Pasin,“Using Linked Open Data to Bootstrap a Knowledge Base of Classical Texts”, Proceedings of the Second Workshop on Humanities in the Semantic Web (WHiSe II) co-located with 16th International Semantic Web Conference (ISWC 2017), 3-14 URL: https://infoscience.epfl.ch/record/232930/files/paper-01.pdf 
* Linked data: http://cwkb.org/ 
* Example of automatically created triples expressing citations: http://dlib.nyu.edu/awdl/isaw/isaw-papers/7/romanello/
* Web Annotation Data Model: https://www.w3.org/TR/annotation-model/ 
* HuCit: https://www.researchgate.net/figure/HuCit-ontology-assignment-of-a-CTS-URN-to-the-corresponding-TextElement-instance-with_fig24_295861998 and https://bitbucket.org/56k/hucit/ and https://bitbucket.org/56k/hucit/raw/tip/hucit.owl
