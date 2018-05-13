# 2018 May

### 2018-05-09
- Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates

Subword units are an effective way to alleviate the open vocabulary problems in NMT.

A common approach for dealing with the open vocabulary issue is to break up rare words into subword units: BPE(Byte-Pair-Encoding), WPM(Wordpiece Model)

BPE encodes a sentence into a unique subword sequence. However, a sentence can be represented in multiple subword sequences even with the same vocabulary.

At training time of NMT, multiple segmentation candidates will make the model robust to noise and segmentation errors, as they can indirectly help the model to learn the compositionally of words, e.g, “books” can be decomposed into “book” + “s”.

In this study, a new regularization method for open-vocabulary NMT, called subword regularization, which employs multiple subword segmentations to make the NMT model accurate and robust is proposed.

2 sub-contributions:
1. simple NMT training algorithm to integrate multiple segmentation candidates. (Can be applied to any NMT system without changing the model structure
2. subword segmentation algorithm based on a language model, which provides multiple segmentations with probabilities.

---

### 2018-05-12
- Distributed Representations of Sentences and Documents

Quoc Le, Tomas Mikolov, 2014

In text fields, common fixed-length features is bag-of-words. But bag-of-words cannot represent ordering of words and semantic similarity.

Proposed algorithm in this paper learns fixed-length feature representations from raw texts, such as sentence, paragraphs, and documents by a dense vector which is trained to **predict word in the document**. 

Concatenate the paragraph vector with several word vectors from a paragraph and predict the following word in the given context.
At prediction time, the paragraph vectors are inferred by fixing the word vectors and training the new paragraph vector until convergence.
Some models to represent phrase, sentence or documents

Using a weighted average of all the words in the document. (Loses the word order)
A more sophisticated approach is combining the word vectors in an order given by a parse tree of a sentence, using matrix-vector operations(Socher et al, 2011b) (using a parse tree has been shown to work for only sentences because it relies on parsing) 

Paragraph Vector: A distributed memory model

The paragraph vectors are asked to contribute to the prediction task of the next word given many contexts sampled from the paragraph. The paragraph vector and word vectors are averaged or concatenated to predict the next word in a context.

The only change in this model compared to the word vector framework is constructed vector h from W to D. The paragraph matrix acts as a memory that remembers what is missing from the current context - or the topic of the paragraph.


Paragraph Vector without word ordering: Distributed bag of words

Force model to predict words randomly sampled from the paragraph in the output. At each iteration of stochastic gradient descent, we sample a text window, then sample a random word form the ‘text window’ and ‘form a classification task’ given the Paragraph Vector. (This model is similar to the Skip-gram model)