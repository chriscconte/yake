========================================
Yet Another Keyword Extractor (Yake)
========================================

Unsupervised Approach for Automatic Keyword Extraction using Text Features.

We propose a lightweight approach for keyword extraction and ranking based on an unsupervised methodology to select the most important keywords of a single document. To understand the merits of our proposal, we compare it against RAKE, TextRank and SingleRank methods (three well-known unsupervised approaches) and the baseline TF.IDF, over four different collections to illustrate the generality of our approach. The experimental results suggest that extracting keywords from documents using our method results in a superior effectiveness when compared to similar approaches. 
See details at https://link.springer.com/chapter/10.1007/978-3-319-76941-7_63

Main Features
-------------

* Unsupervised approach
* Multi-Language Support
* Single document

Rationale
-------------

Extracting keywords from texts has become a challenge for individuals and organizations as the information grows in complexity and size. The need to automate this task so that texts can be processed in a timely and adequate manner has led to the emergence of automatic keyword extraction tools. Despite the advances, there is a clear lack of multilingual online tools to automatically extract keywords from single documents. Yake! is a novel feature-based system for multi-lingual keyword extraction, which supports texts of different sizes, domain or languages. Unlike other approaches, Yake! does not rely on dictionaries nor thesauri, neither is trained against any corpora. Instead, it follows an unsupervised approach which builds upon features extracted from the text, making it thus applicable to documents written in different languages without the need for further knowledge. This can be beneficial for a large number of tasks and a plethora of situations where the access to training corpora is either limited or restricted.


Please cite the following works when using YAKE
------------

Campos, R., Mangaravite, V., Pasquali, A., Jorge, A., Nunes, C., & Jatowt, A. (2018).
A Text Feature Based Automatic Keyword Extraction Method for Single Documents
Proceedings of the 40th European Conference on Information Retrieval (ECIR'18), Grenoble, France. March 26 – 29.
https://link.springer.com/chapter/10.1007/978-3-319-76941-7_63

Campos, R., Mangaravite, V., Pasquali, A., Jorge, A., Nunes, C., & Jatowt, A. (2018).
YAKE! Collection-independent Automatic Keyword Extractor
Proceedings of the 40th European Conference on Information Retrieval (ECIR'18), Grenoble, France. March 26 – 29
https://link.springer.com/chapter/10.1007/978-3-319-76941-7_80

Requirements
-------------
Python3


Installation
-------------

To install Yake using pip ::

	pip install git+https://github.com/LIAAD/yake

To upgrade using pip::

	pip install git+https://github.com/LIAAD/yake –upgrade

Usage
---------

Command line
************************
How to use it on your favorite command line::

		Usage: yake [OPTIONS]

		Options:
		  -ti, --text_input TEXT          Input text, SURROUNDED by single quotes(')
		  -i, --input_file TEXT           Input file
		  -l, --language TEXT             Language
		  -n, --ngram-size INTEGER        Max size of the ngram.
		  -df, --dedup-func [leve|jaro|seqm]
		                                  Deduplication function.
		  -dl, --dedup-lim FLOAT          Deduplication limiar.
		  -ws, --window-size INTEGER      Window size.
		  -t, --top INTEGER               Number of keyphrases to extract
		  -v, --verbose
		  --help                          Show this message and exit.

Python
************************
How to use it on Python::

	import yake

	text_content = """
		Sources tell us that Google is acquiring Kaggle, a platform that hosts data science and machine learning
		competitions. Details about the transaction remain somewhat vague , but given that Google is hosting
		its Cloud Next conference in San Francisco this week, the official announcement could come as early
		as tomorrow.  Reached by phone, Kaggle co-founder CEO Anthony Goldbloom declined to deny that the
		acquisition is happening. Google itself declined 'to comment on rumors'.
	"""

	# assuming default parameters
	simple_kwextractor = yake.KeywordExtractor()
	keywords = simple_kwextractor.extract_keywords(text_content)

	for kw in keywords:
		print(kw)

	# specifying parameters
	custom_kwextractor = yake.KeywordExtractor(lan="en", n=3, dedupLim=0.8, windowsSize=2, top=20)
	keywords = custom_kwextractor.extract_keywords(text_content)

	for kw in keywords:
		print(kw)


Related projects
-------------

yake-dockerfile
************************
https://github.com/feup-infolab/yake-dockerfile - Dockerfile for building an image for this package. 

Credits to https://github.com/silvae86


`pke` - python keyphrase extraction
************************



https://github.com/boudinfl/pke - `pke` is an **open source** python-based **keyphrase extraction** toolkit. It
provides an end-to-end keyphrase extraction pipeline in which each component can
be easily modified or extended to develop new models. `pke` also allows for 
easy benchmarking of state-of-the-art keyphrase extraction models, and 
ships with supervised models trained on the SemEval-2010 dataset (http://aclweb.org/anthology/S10-1004).

Credits to https://github.com/boudinfl
