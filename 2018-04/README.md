# 2018 April

### 2018-04-01 
- Neural Machine Translation by Jointly Learning to Align and Translate  [(link)](https://arxiv.org/pdf/1409.0473.pdf)

Well known as 'Bahdanau Attention Model', including good introduction and instruction for beginners with historical flow 
and details in neural machine translation. The contribution of this paper is applying alignment model which scores how well the inputs around position j 
and the output at position i match to training each conditional probability p(y|x).
 
Proposed model compresses input sentence more efficient way by considering words matching information compared 
the previous state-of-art model like RNN encoder-decoder which encodes sentence to fixed-length vector. Hence, proposed
model shows better performance at experiments with long sentences.

### 2018-04-03
- Memory Networks

As a class of learning model, Memory networks reason with inference components combined with a long-term memory component.
The central idea is to combine the successful learning strategies for inference with a memory component that can be
read and written to. The model is trained to learn how to operate effectively with the memory component.

A memory network consists of a memory m (an array of objects indexed by m_i) and four components I, G, O and R

- I: (input feature map) - converts the input to the feature representation. (e.g. pre-processing)
- G: (generalization) - updates(forget, replace) old memories given the new input. (m_i = G(m_i, I(x), m))
- O: (output feature map) - produces a new output, given the new input and the current memory state. (o = O(I(x), m))
- R: (response) - converts the output into the response format desired.

MemNNs(Memory Neural Networks)

### 2018-04-04
- Japanese and Korean Voice Search [(link)](https://static.googleusercontent.com/media/research.google.com/ko//pubs/archive/37842.pdf)

This paper describes challenges and solutions for building voice search system as applied to Japanese and Korean, 
but I focused on only segmentation(word-piece model). Word-piece model learns word units from large amounts of text 
automatically and incrementally by running a greedy algorithm. (data-driven, language-independent technique)

How to find the automatically learned word inventory: 1. Initialize the word unit inventory with the basic Unicode characters
(e.g. 음절 in Korean, alphabet in English). 2. Build a language model on the training data using from 1. 3. Generate
a new word unit by combining two units out of the current word inventory. 4. goto 2 until reaching a certain threshold.
