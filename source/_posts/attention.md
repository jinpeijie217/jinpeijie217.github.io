---
title: attention
date: 2019-09-04 18:39:53
tags:
---

#layer of attention

1. Attention(Q,K,V) = softmax(QKT/dk*1/2)V
2. multiply(n*dk, dk*m, m*dv) = n*dv
3. query, key, value and key-value.
4. multi-head attention is the result of several attentions by duplicating the same thing
5. self-attention: Attention(X,X,X),Q=K=V, X is the sequence of input
6. position embedding: this is necessary for the only attention structure
- PE2i(p) = sin(p/100002i/dpos), PE2i+1(p) = cos(p/100002i/dpos) special definition of position embedding
- two ways to combine the word embedding and position embedding, addition or concatenation
 
#code
reference: https://github.com/bojone/attention/blob/master/attention_keras.py

#example
```
from __future__ import print_function
from keras.preprocessing import sequence
from keras.datasets import imdb
from attention_keras import *

max_features = 20000
maxlen = 80
batch_size = 32

print('Loading data...')
(x_train, y_train), (x_test, y_test) = imdb.load_data(num_words=max_features)
print(len(x_train), 'train sequences')
print(len(x_test), 'test sequences')

print('Pad sequences (samples x time)')
x_train = sequence.pad_sequences(x_train, maxlen=maxlen)
x_test = sequence.pad_sequences(x_test, maxlen=maxlen)
print('x_train shape:', x_train.shape)
print('x_test shape:', x_test.shape)

from keras.models import Model
from keras.layers import *

S_inputs = Input(shape=(None,), dtype='int32')
embeddings = Embedding(max_features, 128)(S_inputs)
# embeddings = Position_Embedding()(embeddings) # ??Position_Embedding????????
O_seq = Attention(8,16)([embeddings,embeddings,embeddings])
O_seq = GlobalAveragePooling1D()(O_seq)
O_seq = Dropout(0.5)(O_seq)
outputs = Dense(1, activation='sigmoid')(O_seq)

model = Model(inputs=S_inputs, outputs=outputs)
# try using different optimizers and different optimizer configs
model.compile(loss='binary_crossentropy',
              optimizer='adam',
              metrics=['accuracy'])

print('Train...')
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=5,
          validation_data=(x_test, y_test))

```


- 

---

`code`

```code snippet ```

1. 
2. 