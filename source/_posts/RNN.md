---
title: RNN
date: 2019-07-16 18:19:38
tags:
---

1. RNN use the hidden state to store the previous memory
2. RNN using stochastic sampling and neighbouring sampling are a little different
3. for parameters explostion, we could use clip gradient with a threshold to control parameters
4. perplexity : the expotentiation of crossentropy loss
	- the best: perp = 1 , the worst : perp = infinite , the baseline: perp < the number of classification
5. models:
**GRU: Gated Recurrent Unit**
- reset gate(decide whether to discard the previous hidden state) + update gate(decide whether to update the current hidden state)
- reset gate is good for short-term dependency, update gate is good for long-term dependency

**LSTM: long short-term memory**
- input gate + forget gate + output gate + memory cell
- good to avoid gradient vanishing, because the update is addition which could restore the long-term memory

6. deep recurrent NN consists of more hidden layers. In addtion, hidden units (or hidden_size) is hyper parameter as well
7. both direction of RNN is useful for the sequence data which depend both on forehead and backhead info


