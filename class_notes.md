[Link to resources.](http://tinyurl.com/DEMMR-CUL17)

# Introduction to _The O's of Saint Bridget_

1. Affective Piety; the 15 O's;

  - Suffering of characters, empathy; __participation through prayer__;

  - Related to the idea of empathy and participation, we find a strange __preoccupation for numbers__ (listing, numbering; __the five joys of the virgin__; __the seven last utterances of Jesus on the Cross__);

    - The _15 O's_ contains the seven utterances, for instance (folded into the text);

    - We also find a certain obsession for __the number of Christ's wounds__ (wound on the side, wound in the heart);

    - __5480__ (15 * 365 = 5475 - plus the __5__ wounds);

    - _a female solitary obsessed with the number of wounds of Christ_; in the same vision, the solitary receives a vision of prophecies involving the number __15__ (in 1954 the Church determined that, although the O's could be printed, the promises shouldn't);

    - the idea is that these 15 O's should be _portable_, hence the small roll (and the very small format of the first printed edition);

    - _Bridget of Sweden_ - visionary, spent some time in Rome; had seven children; she founded an order, thanks to a pope who spent some time in Rome during the _Avignonese_ period;

    - translated into English and German (pretty unusual in its Northern tradition);

    - vernacular theology is suppressed in the Arundel constitutions of 1408; __but__ suppression of doctrinal writing __does not coincide__ with suppression of _deviotional writing_; therefore, there is very little that's _dangerous_ about the 15 O's.

  2. __Rolls__ are of course typical in the antique tradition; but we shouldn't assume that they disappear with the introduction of the codex; an example is, for instance, is the __exalted roll__ - with images reproduced __upside-down__ (so that the audience could see them, when the the speaker went through it);

# Working on the Roll

1. LLEM (Linguistic Atlas of Middle English)

2. The script: gothic bookhand formata; a high level script. But this is a crammy practitioner (and one who rarely cuts his pen);

3. Very little abbreviation (basically no abbreviation); also, only a single non-Latin character (Yogh, and apparently only once);

4. weird characters: a majuscule _K_ used for a minuscule _K_ (looks like a regular k to me);

  - a peculiar _y_ with a little dot over it (might be confused with a pendule abbreviation for __r__; but it's simply an otiose dot).

    - therefore, be careful whether letters are __y__ or __p__;

    - (also, be careful when you look at _a_ - it has the middle stroke; nothing more than two minims with a cross stroke);

  - also, we find very often fused __de__ letters;

  - we also have a huge minuscule __w__;

  - __IHU__ for Jesus Jhesu (?);

  - straight line over a vowel - _n_ letter (another kind of abbreviation);

5. Many otiose lines;

6. Look for abbreviations (there aren't many); it's either __n__ (the stroke on top of a letter) or __er__ (probably the top curl);

7. A single non-Latin letter, it appears only in initial position (as a capital letter) - it's a seven with a cross stroke;

# Transcription

> O Jh(es)u dulcedo cordium. Pater noster. Aue Maria.  
> O Jh(es)u of mannys and hert mannys mynde  
> Art the very perfide floured swetnes
> Thous suffrest and day...th for manne kynd;  
> Of galle and eyesselle the foule bytternesse.  
> ...

# Cataloguing

- Various lengths and degrees of detail for various kinds of purposes; book sellers, for instance, provide lots of detail (because they need to sell the thing);

- Three categories:

  - material - physical condition (what it is...);

    - binding (contemporary to the creation);

  - intellectual (contents...);

    - language, script;

    - text, images...

    - absence or presence of marginalia;

  - provenance (where it's from, when, who...);

    - some people distinguish between __origin__ and __provenance__ (the place and time of creation, and the history of its transmission);

    - binding (later);

    - absence or presence of marginalia;

  - So, the difference between __provenance__ and __object content__ is apparently crucial.

  - A good standard is that of the __digital scriptorium__ (you have to consider time/convenience/thoroughness);

    - it takes one three days per manuscript, according to CD.

# Introduction to Encoding

1. TEI is constantly in flux;

2. _text is an abstraction_;

3. _one should always keep in mind purpose and audience when making decisions about what and how to mark up_ (it's always debatable - e.g., italicized - emphasis - or date, person...);

  - there's always interpretation and decision involved;

# More advanced TEI

1. Not only we have a root element and a number of nested elements; we also have a series of __nodes__ (actually everything that is found within a root);

2. What do we do with special characters?

  - yogh, ash, wyn, thorn?

  - capital letters?

  - tyronian et?

    - For abbreviations, we do something like this:

    ```
    <choice>
    <abbr>qd</abbr>
    <expan>q<ex>uo</ex>d</expan>
    </choice>
    ```

    - The _choice_ tags offers the computer a choice between showing the abbreviation and the expanded word; we distinguish between the characters that are there and the characters (letters) that are added, so that - in case - the software might represent those differently (for instantly, italicizing the letters introduced by the editor).

3. In XML we have _nameplace declarations_ when we need to __link__ the document to an external (remote) set of rules.

# TEI projects

1. Many kinds of sources (visual...).

2. Examples:

  1. _Lancelot_ (Princeton Charrette);

  2. _Van Gogh Letters_;

  3. _Ibsen's Writings_;

  4. _Map of Early Modern London_;

  5. _Digital Archives and Pacific Cultures_.

# Advanced encoding

1. __Divisions__.

```
<pb n="5"/>
<div type="chapter">
  <div type="paragraph">
  </div>
</div>
```

  - Divisions have __attributes__; kinds of attributes are indicated by using the __@__ sign.

  - So, __<div>__ can have:

    - @type (to classify what kind of division this is);

    - @n (to have a single identifier for the kind of division - so, for instance, they all refer to the same idea or person).

  - Divisions can also be numbered - <div1>, <div2>...

  - Divisions, when nested, can only contain __elements__ (not pure content).

  - An alternative to divisions are __floating text__ sections (different from divisions - text that simply stands out).

2. __The core__ contains many elements, but not all the ones that we need (manuscript description, poetry...).

  - In the core we find __paragraph__; alternatives to paragraph are, for instance __<ab>__ (anonymous block), for cases when paragraph is not a useful category (the divisions seem random...).

  - highlighting: for rubrics, headings... (this is problematic because it seems to contradict the idea of __descriptive__ vs. __procedural__);

  - __<choice>__ is used to offer options for _corrected_ and _sic_ (or _abbreviated_ and _expanded_);

  - any sort of editorial (or scribal) manipulation can be added by using _<add>_, _<del>_, _<gap>_...

# msDesc

- The TEI header is metadata; it's useful for people who are looking for stuff; it's useful for people who need to understand what an entry is (as a bibliographical entry); it's useful for people who need to analyze stuff;

- Two many kinds of keaders:

  1. the librarian's header (very extensive, precise - useful for advanced, refined researches);

  2. everyman's header: explains only the essential details, but it varies a lot (people seldom agree about what it needs to contain/accomplish);

- The TEI header contains four things:

  1. __<fileDesc>__ (what the file is - this is _the only required part_);

  2. __<encodingDesc>__ (explains what the principles of the encoding are);

  3. __<profileDesc>__ (describes the non-bibliographic aspects of the text - languages, creation, setting... _this is a little confusing_; apparently, in our case, this would be _15th s._ - _unsure_);

  4. __<revisionDeesc>__ (revision history of a text).

- Types of content:

  1. free prose;

  2. grouping;

  3. descriptions...;

  4. probably statements (declaration).

- This becomes incredibly (excessively) detailed.

- _msDesc_:
