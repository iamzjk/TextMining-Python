# TextMining-Python
a text mining project written in Python

##1. read MS .doc/.docx file

Install  

	conda install docx2txt

From python:

	import docx2txt  
	
	# extract text  
	text = docx2txt.process("file.docx")

extract text and write images in /tmp/img_dir  

	text = docx2txt.process("file.docx", "/tmp/img_dir")
	

##2. get pycorenlp and set up corenlp server
	pip install pycorenlp
	
[pycorenlp documents](https://github.com/smilli/py-corenlp)

Must have a CoreNLP server running, in order to use pycorenlp.

Stanford CoreNLP ships with a built-in server, which requires only the CoreNLP dependencies. To run this server, simply run:

#### Run the server using all jars in the current directory (e.g., the CoreNLP home directory)
	java -mx4g -cp "*" edu.stanford.nlp.pipeline.StanfordCoreNLPServer [port] [timeout]

If no value for port is provided, port 9000 will be used by default. You can then test your server by visiting

	http://localhost:9000/

You should see a website similar to corenlp.run, with an input box for text and a list of annotators you can run. From this interface, you can test out each of the annotators by adding/removing them from this list. (Note: The first use will be slow to respond while models are loaded – it might take 30 seconds or so, but after that the server should run quite quickly.) You can test out the API by sending a POST request to the server with the appropriate properties. An easy way to do this is with wget. The following will annotate the sentence “the quick brown fox jumped over the lazy dog” with part of speech tags:

	wget --post-data 'The quick brown fox jumped over the lazy dog.' 'localhost:9000/?properties={"annotators":"tokenize,ssplit,pos","outputFormat":"json"}' -O -
 
##3. Make NLTK work with StanfordNLP
[nltk.tag.stanford module](http://www.nltk.org/api/nltk.tag.html#module-nltk.tag.stanford)

[Script to prepare Stanford NER to work with your Python and NLTK](https://gist.github.com/troyane/c9355a3103ea08679baf)

[StanfordNLP in NLTK with **custom trained** classifier/model](http://stackoverflow.com/questions/34037094/setting-nltk-with-stanford-nlp-both-stanfordnertagger-and-stanfordpostagger-fo)

[在 NLTK 中使用 Stanford NLP 工具包](http://www.zmonster.me/2016/06/08/use-stanford-nlp-package-in-nltk.html)

##4. Work with MongoDB
Using a python API -- PyMongo  
[PyMongo Tutorial](http://api.mongodb.com/python/current/tutorial.html)