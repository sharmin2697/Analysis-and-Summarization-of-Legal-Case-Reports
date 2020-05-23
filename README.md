# Analysis And Summarization Of Legal Case Reports

## Introduction
Legal documents are difficult to parse through for knowledge and application in future cases due to their extensive theory. Hence, it is imperative to generate the main ideas by analyzing them. Manually classifying these legal documents in a large repository is a tremendous task. Therefore, we must find easier ways for summarization, using catchphrases and citations present in them. Through this project, we aim to analyze different legal case reports by grouping them based on common citations mentioned in these cases and summarizing them. This presents insights into the types of cases in each category and their differences.


## Scope of Project 
The scope of the project covers data preprocessing, clustering of legal case reports based on similar citations, and multi-document summarization of documents in different clusters. Generated summaries are evaluated against reference summaries to determine the quality of generated summaries.


## Dataset
The dataset was obtained from the Machine Learning Repository of the University of California Irvine (UCI), California. The corpus contains legal cases from the Federal High Court of Australia (FCA). The corpus contains 3890 full-text decisions from the Federal High Court of Australia (FCA) from 2006 – 2009. The legal case disputes are mostly civil cases, with minor criminal cases. The dataset is presented in an XML format. 
#### Link - https://archive.ics.uci.edu/ml/datasets/Legal+Case+Reports#


## Background 
Automatic summarization is the technique of reducing a text document with a system to create a summary that retains the most important information of the original document. A review of the literature revealed two methods of text summarization, which are abstractive and extractive. For the summarization of the legal case reports, we will be adopting the extractive summarization technique. Extractive summarization involves the summaries produced by extracting sentences from a source text. Furthermore, we will be applying multi-document summarization to generate summaries based on different clusters of legal case reports. The summary helps to quickly get familiarized with the information contained in a larger cluster of documents. To cluster the similar documents together, we assume that similar cases will have similar citations quoted, hence, clustering cases of cases will be based on similar citations. We shall implement the Infomap algorithm, a famous network clustering algorithm, to cluster the cases based on citations.


## Methodology
- Text Preprocessing: Each legal case report is an XML file that consists of 2 kinds of data – Catchphrases and Sentences. BeautifulSoup library was used to extract the catchphrases and sentences and stored in dictionaries and lists. Cleaned and tokenized catchphrases and sentences were saved as pickle files.

- Clustering: The citations document is used to extract the citations in each case report and stored in a directed graph data structure. Case report clusters are generated based on similar citations using the Infomap algorithm. The resulting clusters are stored in pickle files.

- Summarization: The pickle files storing the clusters and the reference summaries (catchphrases of respective case reports are taken as input for this step. Cases in each cluster were merged and summaries were generated for the entire cluster-based using the TextRank algorithm from the Gensim package. The summaries are stored for evaluation.

- Evaluation: Recall-Oriented Understudy for Gisting Evaluation or ROUGE-N Score is used to evaluate the summarization of texts. The Recall and Precision with respect to the ROUGE Score are calculated as follows:
         -  Recall = (Number of overlapping words)/(Total words in reference summary)    
         -  Precision = (Number of overlapping words)/(Total words in generated summary) 
