## URNs at Brill

CTS URNs identify _texts_, thus making them _citable_ (There is no reason to limiting their use to _canonical_ texts; see also the appendices on fragmentary texts). 

CITE URNs identify _everything else_, for example subjects are index terms like places or persons.

Here is how they are used at Brill.

### CTS

This is the syntax of a CTS URN:

`urn:cts:CTSNAMESPACE:TEXTGROUP:WORK.VERSION:SUBREFERENCE`

#### CTSNAMESPACE

* Brill does **not** use its name here, or indeed anywhere in the URN. We want to keep the URNs "open", i.e free of branding.
* there is no central registrary. This is a problem. So far we have minted the following previously unused namespaces:

Namespace | Explanation
----- | -----
`brill` | for publications by, or relating to the publishing house
`humLit` | for secondary literature, i.e. scholarly monographs and articles
`akkLit` | for Akkadian texts
`anaLit` | for Anatolian texts
`egyLit` | for Egyptian texts
`nwsemLit` | for North-West Semitic texts
`suxLit` | for Sumerian texts
`engLit` | for English texts

#### TEXGROUP

* Can be an author name, or the name of a group of texts. 

In the latter casee, it may be identical to the name of a scholarly publication, such as `fgrh`. In the former case, if the name belongs to `arabicLit`, we put the date of death according to the Hijri calendar, e.g. `0601Maimonides`.

#### WORK.VERSION

The work may be a number or a name.

The version has this syntax:

PRODUCTACRONYM-EDITION-CTSFLAVOUR-LANGUAGE

* the product acronym is used for access management
* the edition is a number. For example, `jo-3-comm3-eng` denotes the third edition of the text.
* the CTS flavour is either `ed` or `tr` or `comm`. Nothing else. 
* the language is an ISO 639-2 code.

#### SUBREFERENCE

This is about textparts. Theoretically, there can be an endless hierarchy. In practice, we mostly see one, two, or three levels. (E.g. [book]-chapters; [book]-pages-lines; [papyri]-fragments-columns-lines).

Always give the entire subreference. E.g., not `1.1-2` but `urn:cts:greekLit:tlg0526.tlg003.fjo-ed1- grc:1.1-1.2`

<!-- 
Brill _does_ use the version identifier to cite its publications, however. Following the CapiTainS Guidelines, we use the version identifier to state 

1. product
2. language
3. number

For the product, Brill CTS URNs use the product acronyms as used in our administrative systems. For example, _Flavius Josephus_ online is the name of an (ongoing) series of commentaries on and translations of the works of Flavius Josephus, combined with a text edition. Its abbreviation, or "product acronym" is `fjo`, resulting in the following URN:

`urn:cts:greekLit:tlg0526.tlg003.fjo-grc1:1.1-1.2`
-->

### CITE

This is the syntax of a CITE URN:

`urn:cite:CITENAMESPACE:COLLECTION.OBJECT@SUBREFERENCE`

Brill uses CITE URNs to identify

1. people (and organizations)
2. places
3. periods
4. subjects

These are most of the [BOCS](https://brillpublishers.gitlab.io/documentation-workflow/bocs.html) categories. The last BOCS category, references, is expressed in CTS URNs rather than CITE.

Use of Brill CITE URNs does not exclude use of other persistent identifiers. Indeed, this is mandatory. URIs prevalent in scholary communities *must* be used in order to link Brill data to other resources.

The Brill CITE URNs for these BOMS categories look as follows:

`urn:cite:brill:indexTerm.Persons.00000001` = people
`urn:cite:brill:indexTerm.Places.00000001` = places
`urn:cite:brill:indexTerm.Periods.00000001` = periods
`urn:cite:brill:indexTerm.Subjects.00000001` = subjects

In this case, the Brill name **is** used in the namespace. This is because these identifiers are specific to Brill. They, and their schema, are published here, accessible to all.

* so we better stick to CTS. And even when Brill uses CITE URNs, they contain a version identifier. 
* Brill never uses `brill` as namespace.
* Brill always uses the product acronym in the version identifier.

<!--
It is possible to add object components, a version identifer and a subreference:

`urn:cite:CITENAMESPACE:COLLECTION.OBJECT.OBJECTCOMPONENT.VERSION@SUBREFERENCE`

Ranges are possible too:

`urn:cite:CITENAMESPACE:COLLECTION.OBJECT1-OBJECT2`
-->
<!--
"Collections" is taken in a broad sense. It includes the collections of index terms, for example. A CITE URN, in that case, identifies a Brill index term. For example:

`urn:cite:brill:indexTerm.Persons.00000001`

identifies the first person in the index of persons that Brill has built up.
-->
<!--
"Collections" can also have the more traditional meaning of a collection of fragmentary texts (e.g., _JO_, or _SGG_.) Example of an CITE URN that identifies a text fragment:

`urn:cite:brill:fgrh.1.F1.jo-grc2@οἱ[1]-γελοῖοι[1]`

See [here](https://brillpublishers.gitlab.io/documentation-jo/URIs.html) for more details on JO CITE URNs.
-->

<!--

## BOCS

## BOMS

<fragment id="1" dfhg_id="686" lofts_urn="urn:lofts:fhg.1.hellanicus.hellanici_fragmenta.phoronis:1" cite_urn="urn:lofts:fhg.1.hellanicus:1">
		<volume>Volumen primum</volume>
		<sub_volume></sub_volume>
		<sub_volume_note></sub_volume_note>
		<author>HELLANICUS</author>
		<section>HELLANICI FRAGMENTA</section>
		<work>ΦΟΡΩΝΙΣ</work>
		<work_note></work_note>
		<work_section></work_section>
		<work_section_note></work_section_note>
		<book></book>
		<book_note></book_note>
		<fragment_number>1</fragment_number>
		<fragment_letter></fragment_letter>
		<fragment_note></fragment_note>
		<witness>Dionys. Halic. Archaeol, I, 28:</witness>
		<text>Ἑλλάνικος ὁ Λέσβιος τοὺς Τυῤῥηνούς φησι, Πελασγοὺς πρότερον καλουμένους, ἐπειδὴ κατῴκησαν ἐν Ἰταλίᾳ, παραλαβεῖν ἣν ἔχουσι προσηγορίαν. Ἔχει δὲ αὐτῷ ἐν Φορωνίδι ὁ λόγος ὧδε· «Τοῦ Πελασγοῦ, τοῦ βασιλέως αὐτῶν, καὶ Μενίππης τῆς Πηνειοῦ, ἐγένετο Φράστωρ· τοῦ δὲ Ἀμύντωρ· τοῦ δὲ, Τευταμίδης· τοῦ δὲ, Νάνας. Ἐπὶ τούτου βασιλεύοντος, οἱ Πελασγοὶ ὑφ ̓ Ἑλλήνων ἀνέστησαν. καὶ ἐπὶ Σπινῆτι ποταμῷ ἐν τῷ Ἰονίῳ κόλπῳ τὰς νῆας καταλιπόντες, Κρότωνα πόλιν ἐν μεσογείῳ τὰς νῆας καταλιπόντες, Κρότωνα πόλιν ἐν μεσογείῳ εἷλον· καὶ ἐντεῦθεν ὁρμώμενοι τὴν νῦν καλουμένην Τυῤῥηνίαν ἔκτισαν.»</text>
		<translation>At vero Hellanicus Lesbius dicit, Tyrrhenos, qui ante vocabantur Pelasgi, postquam in Italia coeperunt habitare, nomen id assumsisse quod nunc habent. In libro autem quem Phoronidem inscripsit, ita loquitur: «Ex Pelasgo ipsorum rege et ex Menippe Penei filia natus est Phrastor; ex hoc, Amyntor; ex Amyntore, Teutamides; ex Teutamide, Nanas. Hoc regnante Pelasgi a Graecis ex suis sedibus pulsi fuerunt, et, navibus ad Spinetem fluvium in Ionico sinu relictis, urbem Crotonem in locis mediterraneis sitam ceperunt: atque, hac belli sede usi, eam quae nunc Tyrrhenia vocatur, condiderunt.»</translation>
		<commentary></commentary>
		<note></note>
		<page>45</page>
	</fragment>
	
	

<div type="edition" subtype="book" n="vol.i">
<div type="textpart" subtype="chapter" n="1">
<pb n="1"/>
<head>PARS I ZENO CITIEUS</head>
<pb n="3"/>
<head>1 De Zenonis vita, moribus, scriptis
testimonia.</head>
<p>1 Diog. Laërt. VII 1. Ζήνων Μνασέου ἢ Δημέου , Κιτιεὺς ἀπο
Κύπρου, πολίσματος Ἑλληνικοῦ, Φοίνικας ἐποίκους ἐσχηκότος.
<lg><l>Τὸν τράχηλον ἐπὶ θάτερα νενευκὼς ἦν, ὥς φησι Τιμόθεος ὁ</l> <lb n="5"/>
<l>Ἀθηναῖος ἐν τῷ περὶ βίων· καὶ Ἀπολλώνιος δέ φησιν ὁ Τύριος</l>
<l>ὅτι ἰσχνὸς ἦν, ὑπομήκης, μελάγχρως — ὅθεν τις αὐτὸν εἶπεν</l>
<l>Αἰγυπτίαν κληματίδα, καθά φησι Χρύσιππος ἐν πρώτῳ Παροιμιῶν</l>
<l>— παχύκνημός τε καὶ ἀπαγὴς καὶ ἀσθενής· διὸ καί φησι</l>
<l>Περσαῖος ἐν ὑπομνήμασι συμποτικοῖς τὰ πλεῖστα αὐτὸν δεῖπνα</l> <lb n="10"/>
<l>παραιτεῖσθαι. ἔχαιρε δέ, φασί, σύκοις χλωροῖς καὶ ἡλιοκαΐαις.</l></lg>
Διήκουσε δέ, καθάπερ προείρηται, Κράτητος· εἶτα καὶ Στίλπωνος
ἀκοῦσαί φασιν αὐτόν· καὶ Ξενοκράτους ἔτη δέκα, ὡς Τιμοκράτης ἐν
τῷ Δίωνι· ἀλλὰ καὶ Πολέμωνος. Ἑκάτων δέ φησι καὶ Ἀπολλώνιος
ὁ Τύριος ἐν πρώτῳ περὶ Ζήνωνος, χρηστηριασαμένου αὐτοῦ, τί πράττων <lb n="15"/>
ἄριστα βιώσεται, ἀποκρίνασθαι τὸν θεόν, εἰ συγχρωτίζοιτο τοῖς
νεκροῖς· ὅθεν ξυνέντα τὰ τῶν ἀρχαίων ἀναγινώσκειν. τῷ γοῦν Κράτητι
παρέβαλε τοῦτον τὸν τρόπον. πορφύραν ἐμπεπορευμένος ἀπὸ
τῆς Φοινίκης πρὸς τῷ Πειραιεῖ ἐναυάγησεν. ἀνελθὼν δὲ εἰς τὰς Ἀθήνας
ἤδη τριακοντούτης ἐκάθισε παρά τινα βιβλιοπώλην. ἀναγινώσκοντος <lb n="20"/>
δὲ ἐκείνου τὸ δεύτερον τῶν Ξενοφῶντος ἀπομνημονευμάτων,
ἡσθεὶς ἐπύθετο ποῦ διατρίβοιεν οἱ τοιοῦτοι ἄνδρες. ἄνδρες. δὲ
2 παριόντος Κράτητος ὁ βιβλιοπώλης δείξας αὐτόν φησι· „τούτῳ παρακολούθησον.“
ἐντεῦθεν ἤκουε τοῦ Κράτητος, ἄλλως μὲν εὔτονος πρὸς
φιλοσοφίαν, αἰδήμων δὲ ὡς πρὸς τὴν Κυνικὴν ἀναισχυντίαν. ὅθεν ὁ <lb n="25"/>
Κράτης βουλόμενος αὐτὸν καὶ τοῦτο θεραπεῦσαι δίδωσι χύτραν φακῆς
διὰ τοῦ Κεραμεικοῦ φέρειν. ἐπεὶ δὲ εἶδεν αὐτὸν αἰδούμενον καὶ
παρακαλύπτοντα, παίσας τῇ βακτηρίᾳ κατάγνυσι τὴν χύτραν· φεύγον-
<note type="footnote">3 μνασαίου P. || δημαίου PF. 9 εὐπαγὴς ΒFD. <lb n="15"/>
PFD. 18 οὖν F. 18 παρέβαλλε B. 24 ἄλλο B. 26 τούτου BD, τούτ////
P; αὐτοῦ—τοῦτο F. 28 περικαλύπτοντα DF.</note>

<pb n="4"/>
τος δὲ αὐτοῦ καὶ τῆς φακῆς κατὰ τῶν σκελῶν ῥεούσης, φησὶν ὁ Κράτης·





<div type="edition" subtype="book" n="vol.">
<div type="textpart" subtype="chapter" n="1">
<pb n="3"/>
<head>AESCHYLVS</head>
<head>ΑΘΑΜΑΣ</head>
<p>Huic fabulae probabiliter adesp. fr. 1 adscribitur.</p>
<p>1</p>
<lg>
<l>τὸν μὲν τρίπους ἐδέξατ’ οἰκεῖος λέβης</l>
<l>αἰεὶ φυλάσσων τὴν ὑπὲρ πυρὸς στάσιν</l>
</lg>
<p>Ath. II p. 37 F (Eust. II. p. 740, 10): ἦν γὰρ τὸ ἀρχαῖον δύο
γένη τριπόδων, οὓς καλεῖσθαι λέβητας συνέβαινεν ἀμφοτέρους, ἐμπυριβήτης
ὁ καὶ λοετροχόος· Αἰσχύλος ‘τὸν μὲν — στάσιν᾿· ὁ δ’ ἕτερος
κρατὴρ καλούμενος. cf. Ath. VII p. 316 Β: καὶ τρίπουν δὲ λέβητα
Αἰσχύλον εἰρηκέναι ἐν Ἀθάμαντι. Eust. Od. p. 1541, 29: καὶ τὸν
τρίπουν λέβητα παρ’ Αἰσχύλῳ. Hesych. 3 p. 19: λέβης· χάλκειος ποδονιπτήρ,
τρίπους. v. 1 τρίπουν ἐδέξατ’ οἶκον 0. εὔθετος λέβης coni.
Emperius Orusc. philol. p. 345 coll. Agam. 444.</p>
<p>2</p>
<lg>
<l>χαλκοῖσιν ἐξαυστῆρες χειρούμενοι</l>
</lg>
<p>Etym. Μ. p. 346, 56: ἐξαυστήρ· σημαίνει σκεῦός τι. παρὰ τὸ αὔω
αὔσω, αὐστήρ καὶ ἐξαυστήp. Αἰσχύλος. ubi Αἰσχύλος om. V, Αἰσχύλος
Ἀθάμαντι χαλκέοισιν ἐξαυστῆρες χειρούμενοι praebet Etym. Flor.
p. 116. cf. Hesych. 2 p. 117: ἐξαυστήρ· κρεάγρᾳ. χαλκέοισιν cod. Flor.,
χαλκοῖσιν scripsi. ἐξαυστῆρσιν ἐξαιρούμενοι coni. Dindorf. ἐξαυτήρ formam
probat Lehrs de Arist. Stud. Hom. ed. alt. p. 291.</p>
<p>3</p>






<div type="edition" subtype="book" n="vol. i">
<div type="textpart" subtype="chapter" n="1">
<head>PINDARI CARMINA</head>
<pb n="3"/>
<head>PEOLEGOMEKA</head>
<p>I De libris manu scriptis. II Obaervatiunculae grammaticae. m De
fastis Panhellenicis. IV Index carminum epiniciorum. Y Fasti Pindarici.</p>
</div>

<div type="textpart" subtype="chapter" n="2">
<head>I</head>
<head>DE LIBRIS MANV SORIPTIS</head>
<p>Artis criticae in Pindari carminibus factitandae fundamenta
iecit Augustus Boeckh et periodos metricas hiatu vel syllaba ancipiti




A CTS URN might look like urn:cts:greekLit:bra0001.brw0001.jo-grc1:1 (where the subreference is to the fragment number, at least in this edition)
Of course, a CTS URN already exists in many cases. In this example, it is urn:cts:greekLit:tlg0081.tlg001:1.28.3 This is the identifier of the source!
A CITE URN might look like urn:cite:jo.2.4:F4 (where the number after JO refers to the edition)

I suppose we could replace CITe with BRILL and make this more generic, including bibl refs etc?

we hadden al die urns van de seg!





<div type="edition" subtype="book" n="vol.i">
<div type="textpart" subtype="chapter" n="1">
<pb n="1"/>
<head>PARS I ZENO CITIEUS</head>
<pb n="3"/>
<head>1 De Zenonis vita, moribus, scriptis
testimonia.</head>


fragment id="1" 
dfhg_id="686" 
lofts_urn="urn:lofts:fhg.1.hellanicus.hellanici_fragmenta.phoronis:1" 
cite_urn="urn:lofts:fhg.1.hellanicus:1"


The LOFTS URN seems to give collection, vol. nr, historian's name, ?, work, fragment number

The CITE URN seems to skip the ? and the work

Muellers FGH is not in TEI XML, but in "Berti XML"
von Arnim is an attempt to digitize the print. the div follow the print structure

neither is suitable for us.


full cite urn: urn:cts:CITENAMESPACE:COLLECTION.OBJECT.OBJECTCOMPONENT.VERSION@EXTENDEDREFERENCE
range: urn:cts:CITENAMESPACE:COLLECTION.OBJECT1-OBJECT2
example from bnj2: urn:cts:brill:jo.1F1a.jo-grc3@῾Εκαταῖος[1]
example from JC4: urn:cts:brill:jo.1130F1.15.jo-grc1@Λυκοῦργον[1]

Note that the fragmentary text identified by urn:cts:brill:jo.1F1a.jo-grc3 is identified in the source text by urn:cts:greekLit:tlg0613.tlg001.perseus-grc1@῾Ἑκαταῖος[1]-περιόδοις[1]
Note also that the fragmentary text identified urn:cts:brill:jo.1130F1.15.jo-grc1 is identified elsewhere by P.Oxy. 50 3542 = Trismegistos 64177 = LDAB 5396 = (e.g.) urn:cite:P.Oxy.50.3542

Note also that the generic Brill URN scheme is urn:cite:brill:[category]:[object_number]

JO
urn:cite:brill:[category]:[object_number]

-->
