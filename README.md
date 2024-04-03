# Modern Information Retrieval
This repository contains the project code for the course Modern Information Retrieval at Sharif University of Technology. The project is about implementing a information retrieval system and other related works on data like clustering, classification, recommendation, ranking using machine learning methods.

The data used in the project are scientific articles extracted from the <a href="https://www.semanticscholar.org/">Semantic Scholar</a> website. The project is implemented using `Python` and its libraries.

**The project is separated into 3 phases:**
## Phase 1:
**Implementing a simple information retrieval system.**

The purpose of the first phase of the project is to design and implement an information retrieval system for the provided dataset. First the dataset is preprocessed and then it will be indexed using an inverted index, I have implemented both simple inverted index , storing only the document ids and the term frequencies, and also positional inverted index, storing the positions of the terms in the documents. 

After indexing the dataset, compressing and storing the index, and impelemnting query correction, it is time to implement the retrieval part. For search part I used 2 scoring functions: `TF-IDF` and `BM25`. I also used WAND algorithm for efficient retrieval of the top-k documents. You can See the Evaluation of the implemented system in the `Evaluation` section which is in the end of the `phase1.ipynb` notebook.

## Phase 2:
**Machine Learning methods to improve the retrieval system.**

1. **Classification:** 

In this part, different classifiers are used to classify the documents into different categories. First classifier is `Naive Bayes` classifier and the second one is a simple `Neural Network`. The input to model is the embeddings of the documents extracted using `fasttext` library. The loss function used for training the model is `CrossEntropyLoss` and the optimizer is `Adam`. 
You can see the model architecture here:
```python
|-------------------------------| 
|      Input_features(100)      |
|-------------------------------| 
               ↓               
|-------------------------------| 
|         BachNorm(100)         | 
|-------------------------------| 
               ↓
|-------------------------------| 
|        Linear(64, gelu)       |
|-------------------------------| 
               ↓                
|-------------------------------|
|        Linear(32, gelu)       |
|-------------------------------|
               ↓                
|-------------------------------|
|      Linear(num_classes=3)    |
|-------------------------------|
               ↓           
```
   The last classifier is a language model classifier. i used `bert-base-uncased` which is a transformer model. The model is fine-tuned on the dataset and the output is the probability of the document belonging to each class.

2. **Clustering:**

In this section, we will cluster documents using embedding vectors extracted from a language model using two methods, Kmeans and hierarchical clustering. After clustering, we will be able to cluster the result documents of a query and also find similar documents to a given document.


## Phase 3:
**Crawling and analyzing articles**

In this phase of the project, our focus will be on crawling and analyzing articles extracted from the Internet. We will start by examining various web crawling techniques to extract articles and other relevant information from the web.

In the next step, we will apply link analysis algorithms such as PageRank and HITS to determine the importance of these articles based on quotes, references, or other forms of links. We will also learn how to implement a personalized PageRank algorithm that takes user preferences into account to provide more relevant results.