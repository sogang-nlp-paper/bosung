# 2018 Sep

### Accelerating Neural Transformer via an Average Attention Network [(link)](https://arxiv.org/pdf/1805.00631.pdf)
Biao et al., 2018

keywords: NMT, Transformer, Average, Attention, AAN(average attention network)

- problem: due to the auto-regressive architecture and self-attention in the decoder, the decoding procedure becomes slow.
- proposal: an average attention network as an alternative to the self-attention network in the decoder of the neural Transformer.
- conclusion: speed-ups in decoding with almost no loss in translation performance.
- Model:
average input vectors to j-th step -> feed-forward network -> gate layer