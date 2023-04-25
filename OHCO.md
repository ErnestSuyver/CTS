## OHCO

By definition, XML has a tree structure. Nodes exist in a parent-sibling relation. It is therefore a basic assumption of TEI that text also has a tree structure. This assumption is formally expressed in the model of citable text as an _Ordered Hierarchy of Citation Objects_. The semantics of the CTS URN is based on it.

This is, alas, not the case. Take, for example, the problem of [overlapping markup](https://en.wikipedia.org/wiki/Overlapping_markup). Various problems result from this situation, and it has given rise to various solutions, i.e. more or less satisfactory work-arounds. An [alternative model](https://www.balisage.net/Proceedings/vol19/print/Dekker01/BalisageVol19-Dekker01.html) is being developed but is unfinished and so cannot be used in Brill’s TEI efforts. 

Brill therefore sticks to the solutions described in the [guidelines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html) of the TEI consortium. _Milestone elements_, for example, are one of several ways of dealing with non-OHCO compliance. (See also the note on how to capture the physical structure). Another example is _stand-off markup_ as a way to deal with multiple annotations. There is some overlap between this problem and glosses and parallels, which are also multiple annotations.

### See also
Raffaele Viglianti, "Why TEI Stand-off Markup Authoring Needs Simplification", _TEI_ 10 (2016-2019), URL https://journals.openedition.org/jtei/1838
