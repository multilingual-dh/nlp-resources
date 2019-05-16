# Multilingual NLP 
This list of free and open-source NLP resources, and pointers to language-specific directories of resources, was originally created for a presentation at UCLA on teaching multilingual digital humanities, on May 15, 2019.

This is *not a directory* but a moderately-opinionated, potentially one-time list of resources that might be of use to digital humanities folks working with languages other than English. That said, if you have suggestions, you can make a pull request.

&ast; indicates resources I've tried out, ^ indicates resources I've created.

## Language-agnostic tools & methods
These tools and methods are not tied to any particular language. The caveat is that words have to be separated by a space (and what a "word" is may vary language-to-language, and not all languages put spaces between languages). A further caveat is that highly-inflected languages (e.g. languages with a lot of grammatical cases, like Latin, Russian, or Finnish) may perform poorly without lemmatization (using the "dictionary form" of words, versus whatever inflected form is actually present in the text), especially for smaller text corpora.

- [Voyant](https://voyant-tools.org/)
- [Lexos](http://lexos.wheatoncollege.edu)
- Topic modeling - like [Mallet](http://mallet.cs.umass.edu/topics.php); if you use the [topic modeling tool](https://github.com/senderle/topic-modeling-tool) for a GUI-based interface, be sure to go into the "optional settings" and remove the text in the "Tokenize with regular expression" field. Also, your text files **must be saved as UTF-8** otherwise it won't work.
- Word vectors - Ryan Heuser has a [nice set of blog posts introducing word vectors for literary analysis](http://ryanheuser.org/word-vectors-1/), and you can adapt this [Jupyter notebook for Russian text cleaning & word vectors](https://github.com/quinnanya/dlcl204/blob/master/harry_potter_tanya_grotter_project_2019/russian_text_cleanup_word_vectors.ipynb) to most languages (more generalized word vector notebook / tutorial coming this summer!)
- Word counting, keyword-in-context, and similar approaches (many of which are included in Voyant and Lexos, but you could also write Python or R code)

## Modern languages

If you're comfortable working with Python, the [Polyglot library](https://pypi.org/project/polyglot/) provides language detection for 196 languages, tokenization in 165 languages, named entity recognition in 40 languages, part-of-speech tagging in 16 languages, sentiment analysis in 136 languages, and morphological analysis in 135 languages. It can also manage text in multiple languages at once. If you're working a lot with one particualr language, it's probably best to find more language-specific tools, but as a better-than-nothing option for highly underresourced languages, it's an option.

A few other general thoughts & notes:

- Be very wary of stopword lists. Make sure you have someone who can read the language review it before you pick it up and use it, or worst case, start running it through Google Translate. Stopword lists often include all sorts of words that only count as "stopwords" in the domain they're being used for, and you might inadvertently be exclusing, for instance, all words about computers. The longer the stopword list, the more suspicious you should be.
- For very underresourced languages (endangered languages, languages with very small speaker groups, especially languages with unique writing systems) you may find scholarly articles about NLP, but in most cases, whatever proof-of-concept is presented in the paper is a long way from being usable, and odds aren't great that it will get there.

### Arabic
Arabic has to be segmented (clitic segmentation) before it can be used well with language-agnostic tools. The [Stanford Word Segmenter](https://nlp.stanford.edu/software/segmenter.shtml) supports Arabic; usage should be similar to the Chinese segmenter tutorials. 

- NLP resource directory: Github has a [tag for Arabic NLP](https://github.com/topics/arabic-nlp) including pointers to repos for [sentiment analysis for tweets, reviews, and standard Arabic](https://github.com/iamaziz/ar-embeddings), [named entity recognition](https://github.com/linuxscout/mishtar), etc.
- Part-of-speech tagger: Stanford NLP has a [part-of-speech tagger for Arabic](https://nlp.stanford.edu/software/tagger.shtml)
- OCR: Tesseract 4.0 has [training data for Arabic](https://github.com/tesseract-ocr/tessdata/blob/master/ara.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis (standard and Egyptian Arabic), transliteration, and sentiment analysis (standard and Egyptian Arabic)


### Armenian
I stumbled onto Armenian recently while looking at full-text PDFs in HathiTrust. The OCR for all the Armenian books I came across was Latin or Greek jibberish, though I was able to get (what looked to me, playing match-the-squiggles) reasonable OCR out of Tesseract. I had a nice exchange with HathiTrust about it, suggesting that I report the errors I came across. In the meantime, though, plan to re-OCR the text if you're getting Armenian from HathiTrust.

- OCR: Tesseract 4.0 has *[training data for Armenian](https://github.com/tesseract-ocr/tessdata/blob/master/hye.traineddata)
- Named-entity recognition: [training data for Armenian NER](https://github.com/ispras-texterra/pioner) using Wikipedia
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Armenian

### Chinese
Chinese needs to be segmented (spaces artificially inserted between words) before it can be used with language-agnostic tools. Stanford NLP Group has a [Chinese segmenter](https://nlp.stanford.edu/software/segmenter.html). Michelle Fullwood has written a [tutorial on using the segmenter](http://michelleful.github.io/code-blog/2015/09/10/parsing-chinese-with-stanford/).

- Tutorial: ^[Chinese part-of-speech tagging with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/chinese/pos_chinese.md) using Stanford NLP tools
- Tutorial: ^[Chinese named-entity recognition with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/chinese/ner_chinese.md) using Stanford NLP tools
- Python: *[xpinyin](https://pypi.org/project/xpinyin/) (for Mandarin) and [python-jyutping](https://github.com/imdreamrunner/python-jyutping) (for Cantonese), for transliterating Chinese into a phonetic representation, with or without tones. (Example: ^[Taiwanese rap analyzer Jupyter notebook](https://github.com/quinnanya/dlcl204/blob/master/chinese/taiwanese-rap-analyzer.ipynb) for identifying lines of Taiwanese rap lyrics that include repeated tones.)
- Python: *[PyCantonese](http://pycantonese.org/): includes jyutping converter/search, stopwords, and part-of-speech tagging for Cantonese.
- OCR: Tesseract 4.0 has training data for [simplified Chinese Characters](https://github.com/tesseract-ocr/tessdata/blob/master/chi_sim.traineddata), [vertical simplified Chinese characters](https://github.com/tesseract-ocr/tessdata/blob/master/chi_sim_vert.traineddata), [traditional Chinese characters](https://github.com/tesseract-ocr/tessdata/blob/master/chi_tra.traineddata), and [vertical traditional Chinese characters](https://github.com/tesseract-ocr/tessdata/blob/master/chi_tra_vert.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis (Chinese and Gan Chinese), transliteration, and sentiment analysis (Chinese and Gan Chinese)

### French
French is partly supported by Stanford Core NLP, so the instructions for doing part-of-speech tagging should be almost identical to other languages that can use that software. Stanford Core NLP doesn't support French named-entity recognition, but there are other tools you can use like OpenNER.

- Tutorial (with modifications): ^[Part-of-speech tagging with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/german/pos_german.md): this is the German tutorial, but in step 3, replace *german-hgc.tagger* with *french.tagger* in the code that you run. You can also use a Universal Dependencies-based tagger (also described in the German tutorial) by replacing *german-hgc.tagger* with *french-ud.tagger*. The standard French tagger uses tags from the [French treebank](http://www.llf.cnrs.fr/Gens/Abeille/French-Treebank-fr.php).
- Named-entity recognition: [OpenNER](https://www.opener-project.eu/) supports French
- Python: SpaCy offers [POS tags, dependency parse and named entities for French](https://spacy.io/models/fr) based on a news corpus
- OCR: Tesseract 4.0 has [training data for French](https://github.com/tesseract-ocr/tessdata/blob/master/fra.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for French

### German
There is a large community of DH folks doing text analysis on German under the "[Digital Humanities im deutschsprachigen Raum](http://dig-hum.de)" organization. Projects include [QuaDramA – Quantitative Drama Analytics](https://quadrama.github.io/) and [Rhythmicalizer. A digital tool to identify free verse prosody](https://www.geisteswissenschaften.fu-berlin.de/v/rhythmicalizer/).

- Tutorial: ^[German part-of-speech tagging with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/german/pos_german.md)
- Tutorial: ^[German named-entity recognition with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/german/ner_german.md)
- Book & code: Andrew Piper's *Enumerations: Data and Literary Study* (Chicago 2018) includes numerous German examples. The data and code from the book are [available on Github](https://github.com/piperandrew/enumerations)
- Jupyter notebooks: [Example code for doing German NLP with different packages](https://github.com/goerlitz/nlp-german)
- Directory: [NLP resources and tools for German](https://github.com/adbar/German-NLP)
- Python: SpaCy offers [POS tags, dependency parse and named entities for German](https://spacy.io/models/de) based on a news corpus
- OCR: Tesseract 4.0 has [training data for German](https://github.com/tesseract-ocr/tessdata/blob/master/deu.traineddata) as well as [Fraktur](https://github.com/tesseract-ocr/tessdata/blob/master/deu_frak.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for German
- Blog post: [Common pitfalls with the pre-processing of German text for NLP](https://medium.com/idealo-tech-blog/common-pitfalls-with-the-preprocessing-of-german-text-for-nlp-3cfb8dc19ebe) - geared towards commercial applications, but provides a useful overview and comparison of different part-of-speech taggers, stopword lists, compound splitting, etc.

### Hebrew
I've recently been working on a Hebrew NLP project, and should have more experience with these tools soon. Because Hebrew is a right-to-left language, I've noticed a few challenges, including file-renaming when the file names include both Hebrew and Latin characters. You may also have to navigate the [right-to-left mark Unicode character](https://en.wikipedia.org/wiki/Right-to-left_mark) when processing the text.

- Directory: [Hebrew NLP resources](https://github.com/NLPH/NLPH_Resources)
- Topic modeling: [LemLDA: an LDA Package for Hebrew](https://www.cs.bgu.ac.il/~elhadad/nlpproj/LDAforHebrew.html) - you'll probably need to run the rule-based Hebrew tokenizer (below) on your text before trying it with this tool-- punctuation like parentheses breaks it.
- Python: *[rule-based Hebrew tokenizer](https://www.cs.bgu.ac.il/~yoavg/software/hebtokenizer/) - I've had some problems with this (Mac, Python 3.7) with regard to successfully saving the output file, but I've stuck the core functions in a Jupyter notebook and added my own input/output code, and it's worked well.
- OCR: Tesseract 4.0 has [training data for Hebrew](https://github.com/tesseract-ocr/tessdata/blob/master/heb.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Hebrew

### Hindi
- Jupyter notebooks: [Tokenizer and classifier (positive/neutral/negative) for Hindi based on Wikipedia, movie reviews, BBC news](https://github.com/goru001/nlp-for-hindi)
- Jupyter notebook: [Training Hindi word embeddings using Wikipedia data](https://github.com/NirantK/hindi2vec)
- Python: [Tokenizer and stemmer for Hindi](https://github.com/taranjeet/hindi-tokenizer)
- Python: [Hindi dependency parser](https://bitbucket.org/sivareddyg/hindi-dependency-parser/src/master/)
- Tutorial/Python: [Hindi part-of-speech tagging using NLTK](https://github.com/pemagrg1/Hindi-POS-Tagging-and-Keyword-Extraction)
- OCR: Tesseract 4.0 has [training data for Hindi](https://github.com/tesseract-ocr/tessdata/blob/master/hin.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis (Hindi and Fiji Hindi), transliteration, and sentiment analysis for Hindi

### Indonesian
- Directory: [Indonesian NLP resources](https://github.com/kmkurn/id-nlp-resource)
- Directory: [Bahasa Indonesia Natural Language Processing](https://github.com/keyreply/Bahasa-Indo-NLP-Dataset)
- OCR: Tesseract 4.0 has [training data for Indonesian](https://github.com/tesseract-ocr/tessdata/blob/master/ind.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Indonesian

### Italian
The major tool available for Italian is *[Tint](http://tint.fbk.eu/), which is based on (and depends on) Stanford NLP, but not all of the features work well. If you try one output format and it doesn't work, try another. (I can vouch for the .conll format.)

- Tutorial: ^[Italian part-of-speech tagging with Tint](https://github.com/quinnanya/dlcl204/blob/master/italian/pos_italian.md)
- Tutorial: ^[Italian named-entity recognition with Tint](https://github.com/quinnanya/dlcl204/blob/master/italian/ner_italian.md)
- Python: SpaCy offers [POS tags, dependency parse and named entities for Italian](https://spacy.io/models/it) based on a news corpus
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Italian

### Japanese
Japanese has to be segmented before it can be used with language-agnostic tools, though Japanese segmentation is built into [Voyant](https://voyant-tools.org) in theory (your mileage may vary, it just crashed for me when I tried it with a small corpus).

The most commonly used tool for Japanese text processing is [MeCab](https://taku910.github.io/mecab/), which provides segmentation and part-of-speech tagging. There are options for [using it with Python](https://pypi.org/project/mecab-python3/), [with Python on Mac](https://github.com/ellie-icekler/MeCab-python) and [with R](http://rmecab.jp/wiki/index.php?RMeCab), but it depends on a library in C++ that may be a problem to get running. (I failed to get any version of MeCab working on a Mac, but I've seen others using it successfully on Windows.) A number of the people I've worked with haven't been very happy with the quality of its segmentation, and have preferred RakutenMA, which is what I've used.

- Directory: [Japanese text analysis](https://guides.library.upenn.edu/japanesetext) by Molly Des Jardin
- Jupyter notebook: [Japanese segmentation with RakutenMA](https://github.com/quinnanya/japanese-segmenter) - doesn't work yet on Windows due to Unicode issues
- Tutorial: [Japanese part-of-speech tagging with RakutenMA](https://github.com/quinnanya/dlcl204/blob/master/japanese/pos_japanese.md) - uses the demo web interface for RakutenMA
- Tutorial: [Japanese named-entity recognition with Apache OpenNLP](https://github.com/quinnanya/dlcl204/blob/master/japanese/ner_japanese.md)
- OCR: Tesseract 4.0 has [training data for Japanese](https://github.com/tesseract-ocr/tessdata/blob/master/jpn.traineddata) and [vertical Japanese](https://github.com/tesseract-ocr/tessdata/blob/master/jpn_vert.traineddata) but Japanese OCR isn't great. For her PDFs, Adobe Acrobat Professional performed best, but all the tools had problems especially with [half-width characters](https://en.wikipedia.org/wiki/Half-width_kana) and [furigana](https://en.wikipedia.org/wiki/Furigana).
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Indonesian

### Korean
- Python: [KoNLPy: Korean NLP in Python](http://konlpy.org/en/latest/), includes part-of-speech tagging, corpora, dictionaries
- R: [KoNLP](https://github.com/haven-jeon/KoNLP), part-of-speech tagging
- Directory: [Awesome-Korean-NLP](https://github.com/datanada/Awesome-Korean-NLP), a curated directory of resources, hasn't been updated in about two years
- OCR: Tesseract 4.0 has [training data for Korean](https://github.com/tesseract-ocr/tessdata/blob/master/kor.traineddata) and [vertical Korean](https://github.com/tesseract-ocr/tessdata/blob/master/kor_vert.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Korean

### Mongolian
- Directory: [Mongolian NLP](https://github.com/tugstugi/mongolian-nlp) - includes named-entity recognition, data sets (e.g. with personal and clan names)
- OCR: Tesseract 4.0 has [training data for Mongolian](https://github.com/tesseract-ocr/tessdata/blob/master/mon.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, morphological analysis, and sentiment analysis for Mongolian


### Portuguese
Portuguese is comapratively underresourced for text analysis relative to other colonial languages. While there's materials for training named-entity recognition for Portuguese, you need larger-than-laptop compute to train it. I mean to get back to it as an excuse to learn how to use our local high-performance computing cluster.

- Tutorial: ^[Brazilian Portuguese part-of-speech tagger](https://github.com/quinnanya/dlcl204/blob/master/portuguese/pos_portuguese.md)
- Incomplete tutorial: ^[Portuguese named-entity recognition](https://github.com/quinnanya/dlcl204/blob/master/portuguese/ner_portuguese.md), based on [this tutorial](https://github.com/arop/ner-re-pt/wiki/Stanford-CoreNLP) by André Pires and using [materials from his master's thesis](https://github.com/arop/ner-re-pt)
- Python: SpaCy offers [POS tags, dependency parse and named entities for Portuguese](https://spacy.io/models/pt) based on a news corpus
- Tutorial: [Portuguese examples](http://www.nltk.org/howto/portuguese_en.html) for [Natural Language Processing with Python](http://www.nltk.org/book/) (NLTK)
- OCR: Tesseract 4.0 has [training data for Portuguese](https://github.com/tesseract-ocr/tessdata/blob/master/por.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Portuguese


### Russian
*[MyStem](https://tech.yandex.ru/mystem/) from Yandex (Russia's equivalent to Google) is the best NLP toolkit for Russian, and can be downloaded as standalone code. There's a wrapper for Python with [PyMyStem3](https://github.com/nlpub/pymystem3).

Because Russian is highly inflected (i.e. a word can appear in many forms depending on how it's used in a sentence), and each word form is treated as a separate "word" for language-agnostic tools and methods, you may get better results by lemmatizing Russian text before using it with these tools. MyStem can do this, and Python code for doing it is included in the *Russian text cleaning & word vectors* Jupyter notebook.

- Tutorial: ^[Russian part-of-speech tagger](https://github.com/quinnanya/dlcl204/blob/master/russian/pos_russian.md)
- Tutorial: ^[Russian named-entity recognition](https://github.com/quinnanya/dlcl204/blob/master/russian/ner_russian.md), uses Natasha Python module
- Jupyter notebook: ^[Russian text cleaning & word vectors](https://github.com/quinnanya/dlcl204/blob/master/harry_potter_tanya_grotter_project_2019/russian_text_cleanup_word_vectors.ipynb)
- Python: *[Natasha](https://github.com/natasha/natasha) module for named-entity recognition
- OCR: Tesseract 4.0 has [training data for Russian](https://github.com/tesseract-ocr/tessdata/blob/master/rus.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Russian


### Spanish
- Tutorial: ^[Spanish part-of-speech tagging with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/spanish/pos_spanish.md)
- Tutorial: ^[Spanish named-entity recognition with Stanford NLP](https://github.com/quinnanya/dlcl204/blob/master/spanish/ner_spanish.md)
- Python: SpaCy offers [POS tags, dependency parse and named entities for Spanish](https://spacy.io/models/es) based on a news corpus
- Directory: [Spanish NLP](https://github.com/dav009/awesome-spanish-nlp)
- OCR: Tesseract 4.0 has [training data for Spanish](https://github.com/tesseract-ocr/tessdata/blob/master/spa.traineddata) and [Old Spanish](https://github.com/tesseract-ocr/tessdata/blob/master/spa_old.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, part-of-speech tagging, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Spanish

### Tagalog
- Part-of-speech tagger: [Filipino tagger for use with Stanford NLP tagger](https://github.com/matthewgo/FilipinoStanfordPOSTagger)
- Sentiment analysis: [Sentiment analysis for Filipino tweets](https://github.com/rrmina/Sentiment-Analysis-of-Filipino-Tweets)
- OCR: Tesseract 4.0 has [training data for Tagalog](https://github.com/tesseract-ocr/tessdata/blob/master/tgl.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Tagalog

### Thai
- Directory: [Thai NLP](https://github.com/kobkrit/nlp_thai_resources)
- Directory: Github has a [Thai NLP tag](https://github.com/topics/thai-nlp)
- Python: [PyThaiNLP](https://github.com/PyThaiNLP/pythainlp) - transliteration, tokenizing, part-of-speech tagger, collation, and other features.
- R: [thainltk: Thai National Language Toolkit](https://rdrr.io/github/pichaio/thainltk/)
- OCR: Tesseract 4.0 has [training data for Thai](https://github.com/tesseract-ocr/tessdata/blob/master/tha.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Thai


### Tibetan
- Python: [Pybo Tibetan tokenizer](https://github.com/Esukhia/pybo)
- Transliteration: [Wylie  converter](https://github.com/Esukhia/wylieconvert), a wrapper for an existing Perl tool
- Transliteration: [Tibetan Phonetics Engine](https://github.com/Esukhia/bophono), transliteration based on different schemes / dialects
- Part-of-speech tagger: [Universal Dependencies Part-of-Speech Tagger for Tibetan](https://github.com/buda-base/ud-pos-tagger-bo)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, morphological analysis, and sentiment analysis for Tibetan

### Vitenamese
- [VnCoreNLP: A Vietnamese natural language processing toolkit](https://github.com/vncorenlp/VnCoreNLP) (Java) - provides word segmentation, POS tagging, named entity recognition (NER) and dependency parsing
- Directory: Github has a [Vietnamese NLP tag](https://github.com/topics/vietnamese-nlp)
- Sentiment analysis: [Vietnamese sentiment analysis for tweets](https://github.com/linkpp/vietnamese-sentiment-analysis)
- OCR: Tesseract 4.0 has [training data for Vietnamese](https://github.com/tesseract-ocr/tessdata/blob/master/vie.traineddata)
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, named entity extraction (using Wikipedia data), morphological analysis, transliteration, and sentiment analysis for Vietnamese


### Yiddish
The [Yiddish Book Center](https://www.yiddishbookcenter.org/) has thousands of scanned PDFs of books in Yiddish, but without OCR. To get plain text versions of the books (OCR'd using Jochre), you can [create an account here](https://ocr.yiddishbookcenter.org).

- OCR: [Jochre](https://github.com/urieli/jochre) does Yiddish OCR using supervised machine learning techniques
- Python: the [Polyglot library](https://pypi.org/project/polyglot/) supports language detection, morphological analysis, transliteration, and sentiment analysis for Yiddish


## Historical languages
NLP tools for historical languages make the most sense when the language is attested in many (thousands+) documents, and the documents haven't already received a lot of scholarly attention for manual markup and analysis. Akkadian cuneiform tablets continue to be unearthed, and many of those found in archaeological digs over the last century have not yet been published in any usable form. In contrast, there have been far fewer new discoveries of texts in Old Church Slavonic, and the known manuscripts have already been thoroughly marked up by experts. As such, Akkadian is a better target for developing NLP than Old Church Slavonic.


### Classical Languages Toolkit (multilingual)
[CLTK](http://cltk.org/) provides NLP for the languages of Ancient, Classical, and Medieval Eurasia. While Greek, Latin, Akkadian, and the Germanic languages are the most complete, there is also some support for Arabic, Chinese, Ancient Egyptian, Ottoman Turkish, and various classical languages of India. [Read the documentation](http://docs.cltk.org/en/latest/) for more information about the extent and nature of the library's coverage.

- Jupyter notebooks: CLTK offers [Jupyter notebook tutorials](https://github.com/cltk/tutorials) for how to use its functionality


### Latin
- Linked data: [LiLa - Linking Latin](https://lila-erc.eu/output/) is developing a linked data knowledge base for Latin
- Texts: [Digital Latin Library](https://digitallatin.org/) publishes critical editions of Latin texts, and facilitates finding texts online that are written in Latin
- Texts: [Perseus Digital Library](http://www.perseus.tufts.edu/hopper/), a longstanding digital humanities project, with texts in Greek, Arabic, and English along with Latin
- OCR: Tesseract 4.0 has [training data for Latin](https://github.com/tesseract-ocr/tessdata/blob/master/lat.traineddata)


## Other language families & groups

### Languages of Africa
[Kathleen Siminyu](https://www.linkedin.com/today/author/kathleen-siminyu-7356b810?trk=public_profile_articles_see_all) has been working on developing NLP resources for languages of Africa, and posting update on LinkedIn. A February 2019 post describes work on a [Luganda-Kinyarwanda translation model based on word vector embeddings](https://www.linkedin.com/pulse/nlp-resources-african-languages-lugandakinyarwanda-model-siminyu?trk=portfolio_article-card_title).


### Indigenous languages of the Americas
"[Challenges of language technologies for the indigenous languages of the Americas](https://www.aclweb.org/anthology/papers/C/C18/C18-1006/)" (Manuel Mager, Ximena Gutierrez-Vasques, Gerardo Sierra, & Ivan Meza) in *Proceedings of the 27th International Conference on Computational Linguistics*, 2018) has an excellent overview of the current state of NLP for a variety of indigenous languages of the Americas.

The authors also [maintain an updated directory of NLP resources for indigenous languages of the Americas](https://github.com/pywirrarika/naki).

- Cherokee OCR: Tesseract 4.0 has [trained data for Cherokee](https://github.com/tesseract-ocr/tessdata/blob/master/chr.traineddata)
- Inuktitut OCR: Tesseract 4.0 has [trained data for Inuktitut](https://github.com/tesseract-ocr/tessdata/blob/master/iku.traineddata)
