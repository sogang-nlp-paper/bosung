# 2018 May

### 2018-05-09
- Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates

Subword units are an effective way to alleviate the open vocabulary problems in NMT.

A common approach for dealing with the open vocabulary issue is to break up rare words into subword units: BPE(Byte-Pair-Encoding), WPM(Wordpiece Model)

BPE encodes a sentence into a unique subword sequence. However, a sentence can be represented in multiple subword sequences even with the same vocabulary.

At training time of NMT, multiple segmentation candidates will make the model robust to noise and segmentation errors, as they can indirectly help the model to learn the compositionally of words, e.g, “books” can be decomposed into “book” + “s”.

In this study, a new regularization method for open-vocabulary NMT, called subword regularization, which employs multiple subword segmentations to make the NMT model accurate and robust is proposed.

2 sub-contributions:
- simple NMT training algorithm to integrate multiple segmentation candidates. (Can be applied to any NMT system without changing the model structure
- subword segmentation algorithm based on a language model, which provides multiple segmentations with probabilities.