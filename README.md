# DocSumm

#### DocSumm is an automated document-summary generator with Mihalcea and Tarau's [(2004)](https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf) TextRank at its core.
TextRank is a graph-based ranking model for text processing based on Google's PageRank algorithm [(Brin and Page, 1998)](http://infolab.stanford.edu/~backrub/google.html).

## Dependencies:
* [NetworkX](https://networkx.github.io/)
* [Natural Language Toolkit](http://www.nltk.org/)
* [Goose](https://github.com/GravityLabs/goose)

## Running DocSumm
DocSumm can be used to summarize local text files or articles on the web. DocSumm takes three arguments. The first is the path to the target document or the URL of the target web page. The second is the desired length of the document-summary represented as a percentage of the length of the original document (expressed as a value between 0 and 1). The third is a flag indicating if this is a local text file (-l) or a web page (-w). The fourth is optional and specifies which stemming algorithm to use in the process of normalizing the text in the target document. The options are NLTK's Porter Stemmer (-p), Lancaster Stemmer (-l), Snowball Stemmer (-s), Regex Stemmer (-r), or the WordNet Lemmatizer (-w). If no stemmer is specified, the Porter stemming algorithm will be applied by default.


For example:
```
python doc_summ.py ./Document_to_Summarize.txt 0.25 -l -w
```
```
python doc_summ.py 'www.nytimes.com/...' 0.25 -w -w
```


DocSumm saves its automatically generated summaries in the same directory as the target document. Summaries are named Original_File_Name_Summary.txt.

For example:

```
Document_to_Summarize_Summary.txt
```

## Optimizing Your Target Document 
DocSumm works best on documents with a relatively small degree of thematic variation. Therefore, isolating thematically consistent portions of texts which otherwise deal with a wide range of subjects and running DocSumm on these individually will produce summaries that are more informative and structurally more similar to ones that a human might produce. These chunks of text don't need to be short (I've included some relatively long examples which do well), the point is that they ought to be relatively thematically consistent. I'm looking at ways of overcoming the problem of thematic variety within a document, but until then the best approach is probably to split your document up. 


