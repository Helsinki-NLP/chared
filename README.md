
# chared


Chared is a tool for detecting the character encoding of a text in a known language. The language of the text has to be specified as an input parameter so that correspondent language model can be used. The package contains models for a wide range of languages. In general, it should be more accurate than character encoding detection algorithms with no language constraints.

The original code is available from http://code.google.com/p/chared/

This fork adjusts the code for python3.



## Installation

Make sure you have Python 3 and lxml library version 2.2.4 or later installed.

```
git clone https://github.com/Helsinki-NLP/chared
cd chared/
pip install .
```

## Quick start

Detect the character encoding for a file or URL:
`chared -m czech http://nlp.fi.muni.cz/cs/nlplab`

Create a custom character encoding detection model from a collection of HTML pages (e.g. for Swahili): `chared-learn -o swahili.edm swahili_pages/*.html ...` or if you have a sample text in Swahili (plain text, UTF-8) and want to apply language filtering on the input HTML files (recommended): chared-learn -o swahili.edm -S swahili_sample.txt swahili_pages/*.html

For usage information see: `chared --help` and `chared-learn --help`


## Python API

```python
import urllib2
import chared.detector
page = urllib.urlopen('http://nlp.fi.muni.cz/cs/nlplab').read()
cz_model_path = chared.detector.get_model_path('czech')
cz_model = chared.detector.EncodingDetector.load(cz_model_path)
cz_model.classify(page) ['utf_8']
```

## Acknowledgements

This software is developed at the Natural Language Processing Centre of Masaryk University in Brno with a financial support from PRESEMT and Lexical Computing Ltd, a corpus tool company.

