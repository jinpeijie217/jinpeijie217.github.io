---
title: API
date: 2019-07-29 16:55:18
tags:
---

**Flask**
- get text input and fixed model to predict
```
from flask import Flask,jsonify,request

import numpy as np
import flask
import io
import json
from flask import request

import os
import re
import gensim
from gensim.models import Word2Vec
import kashgari
from kashgari.embeddings import WordEmbeddings,CustomEmbedding
from kashgari.tasks.seq_labeling import BLSTMCRFModel
from kashgari.embeddings import BERTEmbedding

# initialize our Flask application and the Keras model
app = flask.Flask(__name__)

model = None

def load_model():
	global model
	my_embedding = BERTEmbedding("C:/Users/bpk1036/OneDrive - Varian Medical Systems/Desktop/crash_Jin/chinese_L-12_H-768_A-12", 200)
	model0 = BLSTMCRFModel(my_embedding)
	model = model0.load_model('C:/NLP_API/mymodel/model_diabetes')

@app.route("/predict", methods=["POST"])
def predict():
	text = request.get_data().decode('utf8')
	print(text)
	
	text = [i for i in text]

	preds = model.predict(text)

#	print(text)

	return jsonify({'result':preds})

if __name__ == '__main__':
	app.config['JSON_AS_ASCII'] = False
	load_model()
	app.run(debug = True, lazy_apps = True)
```

- how to deal with the error of tf model while deploying on flask
reference: https://justttry.github.io/justttry.github.io/not-an-element-of-Tensor-graph/
reference: https://github.com/fchollet/keras/issues/2397
1. graph = tf.get_default_graph()
2. global graph
   with graph.as_default():
	(.. do inference here...)


- how to deploy the models of tf online to predict
reference: http://www.mayexia.com/%E5%B7%A5%E7%A8%8B%E5%B7%A5%E5%85%B7/tensorflow%E6%A8%A1%E5%9E%8B%E4%BF%9D%E5%AD%98%E4%B8%8E%E8%B7%A8%E5%B9%B3%E5%8F%B0%E4%B8%8A%E7%BA%BF/

- how to allow other computers to use your API
app.run(host = '0.0.0.0',port = 5000, debug = 'True')