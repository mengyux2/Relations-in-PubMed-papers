# Relations-in-PubMed-papers

CS410 course project: use spatial distance to represent research paper similarities

## Short Description

For this project, our team attempts to automate the open discovery model of Literature Based Discovery(LBD). The user will provide a term. Our app will query PubMed. Only the top 200 relevant abstracts will be processed. The abstracts will be tokenized and stop words will be removed using the PubMed stop word list (365 words) from the ArrowSmith Project. Dimension reduction will be performed using Doc2Vec. The vectors produced are then passed on to a plotter that uses t-SNE for visualization into 2D space.


## Package dependencies

```
unicode
nltk
os
gensim
biopython
codecs
sys
string
xml.etree.cElementTree
```

## Components

### Abstract Collector and Processor

queries PubMed using their **Entrez Programming Utilities**.
This component is made up of three parts:
1. An article fetcher, uses the efetch utility provided by PubMed. This returns the top 200 relevant abstracts (according to PubMed’s retrieval system) in XML format.
2. An article parser that extracts the article title, first author and abstract text from the retrieved articles.
3. A tokenizer that produces a bag-of-words representation for each abstract. This is done by first removing punctuation and non-alphanumeric characters. Second, stop words from the **PubMed stop word list** in the [ArrowSmith Project](http://arrowsmith.psych.uic.edu/cgi-bin/arrowsmith_uic/tokenizer.cgi) are removed, then words are stemmed using the **Snowball stemmer** from the nltk package.

### Abstract Plotter

plots the abstracts in 2D space based on the similarities of occurence frequencies of terms found in them. This is also made up to three parts:
1. An abstract vectorizer that runs **Doc2Vec** on the abstracts to create document vectors. The program will return a JSON object of abstract titles, x and y-coordinates for the website to display.
2. A points array creator that runs **t-Distributed Stochastic Nearest Neighbor Embedding
(t-SNE)**. This transforms the document vectors, ready for plotting into 2D space.

This all was packaged into a web app. A sample output and a demo can be found in folder /report-and-presentation


## Team Members and Contributions

* Abstract Collector and Processor: Menyu Xie and Adrian Bandolon
* Abstract Vectorizer and Plotter: Jun Liang and Michael Wang
* Website: Jun Liang

Web app and complete code repo are not currently accessible due to limited resource.
https://gitlab.textdata.org/spacial-relations-in-research-papers/spatial-relations-explorer

## Acknowledgments

* UIUC CS410 text-mining course instructors
* [ArrowSmith Project](http://arrowsmith.psych.uic.edu/cgi-bin/arrowsmith_uic/tokenizer.cgi)


