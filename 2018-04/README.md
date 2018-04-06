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

### 2018-04-07
- Bi-Directional Attention Flow for Machine Comprehension [(link)](https://arxiv.org/pdf/1611.01603.pdf)

This paper introduces the Bi-Directional Attention Flow (BIDAF) network, a multi-stage hierarchical process that
represents the context at different levels of granularity and uses bi-directional attention flow mechanism to
obtain a query-aware context representation without early summarization. (let the attention vectors flow into
the modeling(RNN) layer.)

Model

1. Character Embedding Layer; maps each word to a vector space using character-level CNNs.
2. Word Embedding Layer; maps each word to a vector space using a pre-trained word embedding model.
3. Contextual Embedding Layer; utilize contextual cues from surrounding words to refine the embedding of the words.
These first 3 layers are applied to both the query and context.
4. Attention Flow Layer; is responsible for linking and fusing information from the context and the query words. 
Unlike previously popular attention mechanisms, the attention flow layer is not used to summarize the query and
context into single feature vectors. Instead, the attention vector at each time step, along with the embeddings
from previous layers, are allowed to flow through to the subsequent modeling layer. -> reduce loss by summarization.
    - Query2Context
    - Context2Query
5. Modeling Layer; 2 bi-directional LSTM, input: context words conditioned on the query. 
6. Output Layer.

Related Work

Previous works in end-to-end machine comprehension use attention mechanisms in three distinct ways.
1. Use dynamic attention mechanism, in which the attention weights are updated dynamically given the query and the context
as well as the previous attention.
2. Compute the attention weights once, which are fed into an output layer for final prediction. In contrast to these model,
proposed BIDAF does not summarize the two modalities in the attention layer and instead lets the attention vectors flow
into the modeling (RNN) layer.
3. Repeat computing a attention vector between the query and the context through multiple layers, typically referred
to as multi-hop.