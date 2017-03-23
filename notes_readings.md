# Introduction to XML for Text - Kevin Hawkins

- [Link](http://ultraslavonic.info/intro-to-xml/).

1. Every XML file contains a first line that's called "declaration" (it states what kind of XML file the file is).

- For example: `<?xml version="1.0" encoding="UTF-8" ?>`

2. __Tags__ are _instances of_ __elements__; between the tags we find the _content_ of the elements; __elements__ also have __attributes__ with __values__.

- For example: `<type_of_element attribute='value'>content</type_of_element>`

  - And: `<sentence type="declarative" xml:lang="it">Il gatto è nel cestino.</sentence>`

3. XML documents need to be _validated_ against a _schema_ (this contains the specifications for the kinds of elements and their organization); the most common schema type is __DTD__ (Document Type Definition). _Validation_ helps avoiding syntax errors.

# What Is XML and why should humanities scholars care? - David Birnbaum

- [Link](http://dh.obdurodon.org/what-is-xml.xhtml).

1. __Document analysis__ is the step of the process when we determine _what kind of structure_ our XML document should have (the kind of structure that we most care about - paragraphs or pages?), and what sort of information we wish to foreground or describe.

2. DH markup is _descriptive_ (it describes what a component _is_, not what it _looks like_). [Note: doesn't this pose a problem when we are, instead, describing or digitizing primary sources - manuscripts, for instance - where the _looking like_ might matter more - and be more accessible - than the _being_?]

3. _Type of elements_ (the labels of the tags, such as "sentence") are also called __generic identifiers__ (gi).

4. Different _types of element_ can have different _types of content_; some elements can only contain __other elements__; other elements can only contain __plain text__; other elements may contain __mixed content__ (other elements and plain tex); other elements can be __empty elements__ (_milestones_; bookmarks, page breaks).

5. Birnbaum makes a curious distinction between __tree__ and __serialization__; an XML file is, in fact, a __tree__; the written string of characters that we transcribe and edit is, instead, the __serialization__. The serialization needs to abide by the rules imposed by the tree (a __single root__; properly __nested__ elements); otherwise the document does not work - it is not __well formed__.

  - The distinction is important because the __document is read as a tree__ (that must be it), although it looks like a string of characters (in its serialization).

  > Tags are the way elements are serialized by inserting angle brackets and other text into data content, but XML is really a hierarchy of elements and the tags are just a way of representing that hierarchy in a linear (serial) fashion.

6. _Well-formed_ and _valid_ are two different concepts (well-formed is general, for all XML docs; valid is specific to a DTD - a _schema_ or _document grammar_).

  - Birnbaum also introduces the concept of __well-balanced__, distinct from _well-formed_. _Well-formed_ documents have a __single root__ and are __nested properly__; well-balanced documents only need to be __nested properly__ (the root doesn't count). It's a useful term to describe __fragments of XML__ (where we cannot see the root).

7. Birnbaum explains that, in order to represent characters used by XML syntax, we have __entities__ (strings that stand for these characters).

  - Replacing these characters is the first thing one should do when preparing a text for XML encoding.

  - One can also use _numerical character references_ (which refer to the ASCII or Unicode table); the last example in the table refers to that (it's a "non-breaking space character," for when the words need to stay together, despite the size of the window).

|Character|String|
|:---|:---|
|<|&lt;|
|>|&gt;|
|&|&amp;|
|"|&quot;|
|'|&apos;|
|_Non-breaking space_|&#xa0;|

8. The steps of creating a XML file are:

  1. _Document analysis_ (deciding hierarchy and structure);
  2. _Document grammar_ (preparing a _schema_ where the rules of elements and structure are declared);
  3. _Mark-up_ (with iterative __validation__ of the document).

# Tutorial 0: Introduction to Text Encoding and the TEI and Example 0

- [Link](www.teibyexample.org).

1. SGML was created in 1986; it can be considered the dad of XML; like XML, it is a metalanguage, devised to be as comprehensive and as simple as possible.

2. Comments in XML are delimited by the strings `<!--` and `-->`

  - Example: `<!-- Qui mettiamo Mauricio. -->`

3. We can create shortcuts for __entity references__ by including __entity declarations__.

  - Example: `<!ENTITY oslash "#x00F8">`
  - Example: `<sentence>Mauricio looks like a slashed ball, an &oslash;.</sentence>`

  - The `<!` tag is inherited from SGML; it indicates a _declaration_.

  - Entities can also be used for __strings of characters__.

    - Example: `<!ENTITY a_secret "Mauricio ha bevuto tutta l'acqua bonga.">`

  - And this can be useful when I have documents where I need to systematically fill out strings of characters (contracts, letters, adlibs).

    - Example: `<sentence>I've seen &char1; beating up &char2; in &city;.</sentence>`
    - Example: `<!ENTITY char1 "Chuck Norris"> <!ENTITY char2 "Mauricio"> <!ENTITY "Freiburg">`

  - __NB__: ENTITY declarations are all placed after the _XML Declaration_ at the beginning of the document.

    - Example:

    ```
    <?xml version="1.0" encoding "UTF-8"?>
    <!DOCTYPE rootelement [
    <!ENTITY char1 "Mauricio's Mum">
    <!ENTITY char2 "Mauricio's butt">
    <!ENTITY city "Buenos Aires">
    ]>
    ```

    - In this example, also note the _doctype_ declaration: it describes what kind of document this XML document is (for TEI it is `TEI`).
