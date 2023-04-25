# URNS for fragmentary texts

How is the CTS/CITE system applied to fragmentary texts?

We may distinguish between two types of fragmentary texts: logical and physical.

1. logical: fragments of works that are lost, but parts of which are preserved because they are cited in other works. These works sit in manuscripts of which multiple copies may have survived. 
2. physical: fragments of texts on papyri and inscriptions. Possibly, scholia fit here as well. Here, usually only one copy exists, so the text and the information carier are united. Of course, such texts can also be preserved whole, i.e complete. 

### logical

There are basically three options:

1. Mint new CTS URNs. Example: [The Perseus Catalog](http://catalog.perseus.org/?utf8=%E2%9C%93&utf8=%E2%9C%93&search_field=all_fields&q=fragment). In my opinion, though, these URNs are random and confusing.
2. Mint new version of existing CTS URNs. The version identifier expresses that a scholar interprets a certain passage as being a fragment. I could not find an example of this.
3. Mint new CITE URNs. Example: [LOFTS](https://www.dh.uni-leipzig.de/wo/lofts/).This CITE URN, for example, identifies a fragment by Hecataeus in Müller's FHG:

 `urn:lofts:fhg.1.hecataeus.hecataei_fragmenta.genealogiae.liber_secundus:350`. 

(To be precise: fragment 350 of the second book of Hecataeus' Γενεαλογίαι in FHG 1). Note that this is not, strictly speaking, a CITE URN but a LOFTS URN, but the CITE syntax is followed. 

Note: in the past, there was an argument that lost works cannot have CTS URNs, because they are neither canonical nor citable. The fragments, at the other hand, are objects in a collections, hence can (and should) have CITE URNs. While LOFTS does not subscribe to this argument, it was nevertheless found conventient to mint CITE URNs for fragmentary texts.

Brill wanted to follow the LOFTS example. This proved impossible, however. The reason is that the _Nautilus API_, which is the cote of the _Scaife Viewer_, does not except CITE URNs. So the choice was: use CITE and don't publish, or use CTS and start publishing JO, LGGA, SGG, etc. We choose the latter...

### physical

These are basically papyri and inscriptions. Here, scholia are included as well.

##### Papyri

The CTS specifications suggest the Oxyrhynchus papyri constitute a [textgroup](http://cite-architecture.github.io/ctsurn_spec/). This would make a single papyrus a work. I could find no example of this. However, I could find two examples of other papyri identified by CTS URNs. 

1. The _Coptic Scriptorium_ project also uses CTS URNs. For example, the papyrus with print ID CPR 2 2237 (_Corpus Papyrorum Raineri_, cpr 2 = the second volume: _II, Koptische Texte_, ed. J. Krall. 1895. Nos. 1—255) an inventory number P.Vindob. K 2572 (in the Österreichische Nationalbibliothek) gets this CTS URN `urn:cts:copticDoc:papyri_info.tm82127.cpr_2_237`. Note that this same text can be found in [Trismegistos](https://www.trismegistos.org/) and in [papyri.info](http://papyri.info) but with local identifiers, not URNs. However, the TM number is included in the CTS URN, as is a mention of papyri.info, as is the print ID. 

2. This is also how the _Homer Multitext_ project does it. There, the so-called Bankes Homer, a long papyrus fragment (B.M. Papyrus cxiv), containing Homer, Iliad 24.127–24.804, was published with CTS URN `urn:cts:greekLit:tlg0012.tlg001.bankes-01`. Note how the edition is hooked on to the familiar CTS textgroup and work IDs.

The difficulty with this approach is that a papyrus, or a collection of papyri, has more affinity with the physical structure than with the logical structure of a work. In many cases, the papyrus is the text, there is no other text, no variant to be compared. The difference between the papyrus as an object (e.g. with an inventory number) and as an edited and published text is important; more so than with preserved literary texts, for example, which tend to have a longer tradition history and hence more text variants. Hence, one could argue that the Oxyrhynchus papyri and such like form a **collection**. However, I could find no example of this.

It should be noted that only very few papyri have a CTS URNs. Papyri.info, for example, doesn't use them. It seems that local identifiers are important in papyrology, with Trismegistos identifiers acring as a kind of glue, linking the local identfiers. (Here is an example `basp.50.40 = HGV P.Tebt. 2 519 = Trismegistos 13594 = berkeley.apis.836 = p.tebt.2.519`).

##### Inscriptions

The CTS specifications suggest inscriptions from a given site constitute a [textgroup](https://www.homermultitext.org/hmt-doc/cite/texts/ctsoverview.html). This would make a single inscription a work. I could find no example of this. 

The DTS people claim CTS is [unsuitable](https://distributed-text-services.github.io/specifications/) for inscriptions at all... 

One could argue that inscriptions, either in a site or in a text corpus, form a **collection**. But I could find no examples of CITE URNs for inscriptions. 

I have to do some research... and this book: _Digital Classical Philology: Ancient Greek and Latin in the Digital Revolution_ edited by Monica Berti.

##### Scholia

For scholia, CTS URNS are used. Two examples below. I could find no examples of CITE URNs.

1. The _Homer Multitext project_ was created to deal with scholia. For example:

`urn:cts:greekLit:tlg0012.tlg001.msA:1.4`. 

See [here](http://www.homermultitext.org/hmt-digital/scholia?urn=urn:cts:greekLit:tlg0012.tlg001.msA:1.4) for ore information. All HMT URNs are on [GitHub](https://github.com/hmteditors/closed-2015office9/wiki/Scholia-CTS-URNs).

2. the [First One-Thousand Years of Greek project](https://opengreekandlatin.github.io/First1KGreek/). publishes digitally the scholia on Euclides's _Catoptrica_, edited and published in print in 1895. This project aims to publish at least one edition of every Greek work composed between Homer and 250CE, in Open Access. It is a complement to the Perseus project, focusing on texts that are not already present in the Perseus Digital Library. An example:

`urn:cts:greekLit:tlg5022.tlg005.1st1K-grc1` 

You can find the texts [here](http://cts.dh.uni-leipzig.de/text/urn:cts:greekLit:tlg5022.tlg005.1st1K-grc1/passage/1-5/ancient-greek-scholia-in-euclidem-scholia-in-euclidis-catoptrica-scholia-vetera-scholia-in-euclidis-catoptrica-scholia-vetera). The textgroup is that of _Scholia in Euclidem_, the work is _Scholia in Euclidis catoptrica_. (The textgroups of Euclides's works has ID `tlg1799`, while the _Catoptrica_ has `tlg011`). The edition information (“1st1K”) speaks for itself. Lastly, check the nice XML you get from the [site](http://cts.dh.uni-leipzig.de/api/cts?request=GetPassage&urn=urn:cts:greekLit:tlg5022.tlg005.1st1K-grc1:1-5).

In conclusion: minting CTS URNs seems to be the way forward for scholia.

### Conclusion: CTS URNs for Brill's fragmentary texts

* Where CTS/CITE URNs do not exist, Brill has to mint them within the context of a given publication. The local guidelines will contain instructions in such cases.
* CITE URNs seems scarse in the wild and are not supported by Nautilus. We therefore **must** use CTS.

<!-- If inscriptions have not CTS URN, we need to mint them. CTS URNs for SEG inscriptions may look as follows:

1. Example of URN for inscription: `urn:cts:brill:sego.54-1415`
2. Example of URN for inscription part: `urn:cts:brill:sego.54-1415:A`
3. Example of URN for inscription line: `urn:cts:brill:sego.54-1415:1`
4. Example of URN for inscription line in SEG Online: `urn:cts:brill:sego.54-1415.sego-grc1:1`

The choice of "brill" for the CTS namespace is perhaps debatable. Note that the use of SEGO as textgroup identifier.

The problem with the above is that not all inscriptions have parts, so there is no fixed part (in the OHCO2 sense) structure. Perhaps it is better to leave out those parts.

It is also possible to capture the SEG inscriptions as a CITE collection. The fourth example above would then become: `urn:cite2:brill:sego54:1415`. I’m not sure what’s preferable. -->