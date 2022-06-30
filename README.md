## MSDS 631 - Final Project

### Project description

The patent review process involves searching for past filed patents in the same domain of a new patent application. The search keywords used by legal analysts depend on context of the patent application. For example, "strong material" could mean "steel" for construction purposes or "denim" for textiles. This Kaggle competition aims to find a relevance score (five levels from 0 to 1) of a target keyword with a given ancho r word in the context of a domain

### Training data description

The train dataset has ~36,000 labelled instances. The dataset contains an anchor word along with a domain specific context id. The goal is to find a relevance score of a target word. To augment the training data, we added the text description of the context ids to the training dataset. The attached notebook details the EDA steps and the presentation contains more details on the training dataset.

![Class Imbalance](classimb.png)

### Preprocessing steps

Initially we were working with RNN based sequence models. Therefore, we performed lemmatization with SpaCy and used Pytorch's dataset class to generate training batches. 

For our BERT based model, we used the Autotokenizer from the Pytorch checkpoint after converting all text to lower case and removing stop words and punctuation.

### NLP model selection

Our initial RNN based model did not perform very well. We assumed that given the simplistic and short nature of the sequences a simple architecture would work well. However, training the embeddings from scratch did not help as they did not have any contextual information from a large corpus of text.

We shifted to a BERT based architecture, specifically patent BERT which was released to public domain by Google in 2020. Thanks to the rich embedding, we were able to significantly improve upon the results from a RNN based model. 

### Results
