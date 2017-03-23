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
|&lt;|`&lt;`|
|&gt;|`&gt;`|
|&amp;|`&amp;`|
|&quot;|`&quot;`|
|&apos;|`&apos;`|
|_Non-breaking space_: &#xa0;|`&#xa0;`|

8. The steps of creating a XML file are:

  - _Document analysis_ (deciding hierarchy and structure);

  - _Document grammar_ (preparing a _schema_ where the rules of elements and structure are declared);

  - _Mark-up_ (with iterative __validation__ of the document).

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

4. The text contained in an XML can be either processed by the XML parser (which will turn the __serialization__ into the tree), or not. Text to be processed (the body of the document) is called __PCDATA__ (parsed character data); unparsed character data is simply _CDATA_ (for instance, snippets of code).

5. The TEI guidelines are __massive__; there is a _TEI Lite_ version that is sufficient to cover 90% of the cases. The TEI are also organized into __modules__, which group related elements and attributes (parts of the TEI and specific cases).

  - The module for manuscript description is #10.

  > Definition of specific header and structural elements and attributes for the encoding of manuscript sources. Header elements include provisions for detailed documentation of a manuscript's or manuscript part's identification, heading information, contents, physical description, history, and additional information. Dedicated text elements cover phenomena like catchwords, dimensions, heraldry, watermarks, and so on.

  - Also keep in mind that there is a module #11 dedicated to "primary sources" (and which includes "deletions, substitutions and restorations, document hands...").

6. TEI has no specific _document grammars_ associated to it; that is, TEI provides guidelines to create a TEI-compliant schema, but the schema can - and should - be prepared every time from scratch.

  - A TEI schema can, itself, abide by the rules of a TEI text (this is not a very easy concept).

  - This is not very clear for now. Here is the example they provide:

  ```
  <TEI xmlns="http://www.tei-c.org/ns/1.0" xml:lang="en">
    <teiHeader>
      <fileDesc>
        <titleStmt>
          <title>Story Time</title>
          <author>Mauricio</author>
        </titleStmt>
        <publicationStmt>
          <p>Pay royalties to Mauricio.</p>
        </publicationStmt>
        <sourceDesc>
          <p>Document found inside Mauricio's head.</p>
        </sourceDesc>
      </fileDesc>
    </teiHeader>
    <text>
      <front>
        <divGen type="toc"/>
      </front>
      <body>
        <p>Mauricio wants this document to have: TEI, core, header, and textstructure.</p>
        <schemaSpec ident="mauricioTEI" docLang="en" xml:lang="en" prefix="">
          <moduleRef key="tei"/>
          <moduleRef key="header"/>
          <moduleRef key="core"/>
          <moduleRef key="textstructure"/>
        </schemaSpec>
      </body>
    </text>
  </TEI>
  ```
  - We assume that the _Stmt_ stands for "__statement__"; and that the actual _schemamaking_ occurs within the "schemaSpec" element.

    - In fact, the _schemaSpec_ element is the one that makes this document a "TEI customization file."

      - These are the necessary elements of a TEI structure:

        - tei (infrastructure; the least clear for now);
        - core (all common TEI elements);
        - header (how the TEI header works);
        - textstructure (the structure common to all TEI texts).

      - Besides, most TEI schema doc files (TEI customization files) also contain _prose descriptions_ of how the schema works (like this one, where we find Mauricio's own words). This format is called ODD (One Document Does it all)

      - TEI offers a specific word processor, __Roma__, dedicated to the preparation of documents like this.

7. The examples that this website provides seem to do something very strange with _footnotes_. Apparently TEI P5 (in XML) is the only version that allows us to properly represent them (with opening and closing tags).

# 10. Manuscript Description - From TEI P5 Guidelines

- [Link](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/MS.html).

1. Name of the module: "msdescription."

2. There's a _msDesc_ element that needs to be included in the header, within _sourceDesc_; here we include all the preliminary metadata (place, dimensions, contents...  ).

# P5-MS: A general purpose tagset for manuscript description - M. J. Driscoll

- [Link](http://www.digitalmedievalist.org/journal/2.1/driscoll/)

1. Apparently, the MSdesc module is somehow unique in that it allows for _both_ structured and unstructured data; that is, one can describe contents and measurements either through precise elements (width and length, for instance), or through unstructured, simple paragraphs (`<p></p>`).

  - So that MSdesc is an _exceptionally flexible_ module, because of its many possible needs.

  - All the elements of MSdesc - with the exception of `<msIdentifier>` - are optional; but they can appear __only once__, and only __in the recommended order__.

    - One needs to _copy paste_ each part of the catalog entry into a preexisting TEI structure (following its order and requirements); not vice versa (that is, not add tags to the catalog entry).
