## CITE Explained

### Background
The CITE architecture defines a framework for scholarly reference to texts and all other objects or phenomena of study in the humanities. Christopher Blackwell and Neel Smith originally developed the CITE architecture to meet the needs of the Homer Multitext project. Among those needs was the requirement for citing scholarly resources in a standard, machine-actionable yet technology-independent way. This led to the development of the CTS protocol and CTS URN notation, and later to the development of a RESTful service for retrieval of material identified by URN, and client software that talks to the service.

CITE is an acronym for “Collections, Indexes, Texts, and Extensions”. Collections can be collections of texts, but also objects (like manuscripts). Indexes are the connections between identifiers of collection objects (like  “this text can be found on this manuscript folio”). Extensions are APIs and other scripts.

### Components of the CITE architecture
The CITE architecture comprises:
1. standards for citing scholarly resources with a technology-independent but machine actionable URN notation
2. APIs for services to retrieve scholarly resources identified with the CITE architecture’s URN notation
3. some code libraries for working with URN notation, and the CITE services
Identification allows retrieval. CITE has an API (a RESTful service) for the retrieval of a text. This retrieval request has the form of a URL (something like: [http://SERVER/cts?request=GetPassage&urn=URNVALUE](http://SERVER/cts?request=GetPassage&urn=URNVALUE)). Likewise, there are URLs, or retrieval services, for CITE objects, images, and triples (that express relations between URNs).

All four services return XML (well-formed, name-spaced XML) that is transformed with XSLT into human-readable presentation. Machines can ignore the XSLT and simply grab and process the XML. The expected recipient of these XML responses, the “client” for these services, is a web-browser.

plaatje goes here

### CITE Code base
The APIs and code libraries can be found starting from here: http://cite-architecture.github.io/. See also here: https://github.com/cite-architecture. See especially here: http://cite-architecture.github.io/citecoll/.

### CITE2 MODEL
CITE includes the CITE2 model of data collections. In this model, citable objects are modelled as unique objects in versioned collections. Even if objects have identical contents, they are uniquely identified within a collection. A collection may be referred to in the abstract (as a “notional” collection), or concretely as a specific version of a notional collection. Each version of a collection defines a set of properties which apply to all objects within a given version. For this reason, individual objects may be canonically cited either as part of a notional or concrete collection, but individual properties can only be cited as part of a specific version of a collection.

To give one example: the sequence of folios in a manuscript. The folios are citable objects. The manuscript their collection. The notional ordering would be numerical, for example. But the concrete versions of the manuscript, the individual copies, may have a different order, or may have pages missing. So while we may make statements about ordered relations at the notional level, in the CITE2 model we can only make statements about the ordering of citable units in individual collection versions.

### CITE2 URN
CITE2 URNs provide permanent canonical references to discrete objects. Like CTS URNs, they are Uniform Resource Names in the sense of RFC 2141. CITE2 URNs refer to a notional collection, a specific version of a collection, or a specific property within a specific version of a collection. Optionally, they may uniquely identifies an individual object within a collection.

CITE2 URNs have the following syntax. They always begin with the string urn: followed by a protocol identifier, sc. cite2. Colons separate the top-level elements of a CITE2 URN. Then:
1. urn name space (required: always cite2)
2. CITE (or CITE2) namespace (required: a value that can be resolved to a unique URI)
3. collection component (required: a value registered in the designated registry)
4. object selector (optional)
5. subreference expressions (optional; are separated from the object selector by the @ sign)

**The general structure of a CITE2 URN is therefore `urn:cite2:CITE2namespace:collection:object@subreference`.**

Periods separate second-level hierarchical components of the collection component. The collection component must always include a unique collection identifier defined with the named cite2 namespace; it may optionally include version and property identifiers.

### Examples

* URN of pages in notional collection (manuscript): urn:cite2:hmt:msApages
* URN of a single page with notional collection: urn:cite2:hmt:msApages:1r
* URN of a single page with specific collection version: urn:cite2:hmt:msApages.v1:1r
* URN of a specific property within a version of a collection: urn:cite2:hmt:msApages.v1.side:
* URN of a specific value of a specific property within a version of a collection: urn:cite2:hmt:msApages.v1.side:1r

Explanation: The Homer Multitext project’s collections are in the group hmt (urn:cite:hmt). Since all objects in a CITE Collection share a common structure, individual collections resemble (and could be implemented with) databases. urn:cite:hmt:msA identifies a collection in the Homer Multitext group for pages of the Venetus A manuscript, and already implies that every object in that collection will have the same properties. urn:cite:hmt:msA.msA-12r uniquely identifies a single object in that collection, the folio 12 recto of the Venetus A manuscript.

The CITE URN syntax allows an optional, type-specific extension to the canonical identifier for a discrete object. For images, we extend the CITE URN notation with a scale-independent rectangle bounding a region of interest (RoI). The URN urn:cite:hmt:chsimg.VA012RN-0013:0.045,0.2225,0.135,0.0938 defines a rectangle on a digital image that includes the large initial letter Mu, the first letter of the first word of the Iliad on the Venetus A manuscript, for example. 

### Brill use of CITE URNs

When the development of the publication environment (in particular, the text editions end user interface) is in a more advance stage, a decision will be taken. At this moment, we’re not creating CITE URNs. However, we might want to use CITE URNs to identify fragments in a collection, such as Jacoby Online, LGGA, or SGG. This might even be useful for MONK.

Note also that from a syntax point of view, the difference between CTS and CITE URNS is small:

* CTS: `urn:cts:CTSnamespace:textgroup:work`
* CITE: `urn:cite:CITEnamespace:collection:object`

The ontology is different, however.


### See also

* CITE architecture: http://cite-architecture.github.io/ and http://www.homermultitext.org/hmt-doc/guides/urn-gentle-intro.html 
* Separation of concerns: D.N. Smith, C.W. Blackwell, Four URLs, Limitless Apps: Separation of Concerns in the Homer Multitext Architecture. URL: https://chs.harvard.edu/CHS/article/display/4846
