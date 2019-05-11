# Keras NMT

## Introduction
Neural Machine Translation(NMT) is a relatively new approach towards the translation of text between languages. More specifically, the seq2seq models have been employed in many fields of research but NMT was one of the very strong applications of the model. It is superior to the older models as older models broke up problems into larger word phrases. NMT models work by creating an encoder for the input sentence, reads through the whole sentence, and decodes what it thinks the sentence is about. In other words, the model thinks about the sentence you want translated, then decides which one best sounds like whatever language you want to translate into.

The model here is an attempt at replicating the work that Google has published in the fields of NMT. In the Google Neural Machine Translation(GNMT) paper published in , they employ numerous methods to improve upon their models to better handle unseen words, speed, and other features to become the world leaders in machine translation. In addition to their baseline model, they also developed a method in order to allow their GNMT to perform zero shot translation which essentially allows the network to learn associations between word phrases and to find translations that it has not explictly learned.

This repository is an attempt to implement a NMT model using a wordpiece model and the additional features needed to create a zero shot translation model.


## Architecture

### Datasets
The datasets used in this experiment are the Spanish-English and French-English sentence pairs from [manythings.org](manythings.org). The links to download the datasets are the following:  

[Spanish-English](http://www.manythings.org/anki/spa-eng.zip)
[French-English](http://www.manythings.org/anki/fra-eng.zip)

### Training Parameters


### Results


## References
[Google's Neural Machine Translation System: Bridging the Gap between Human and Machine Translation](https://arxiv.org/abs/1609.08144)
[Google's Multilingual Neural Machine Translation System: Enabling Zero-Shot Translation](https://arxiv.org/abs/1611.04558)