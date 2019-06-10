# Keras NMT

## Introduction
Neural Machine Translation(NMT) is a relatively new approach towards the translation of text between languages. More specifically, the seq2seq models have been employed in many fields of research but NMT was one of the very strong applications of the model. It is superior to the older models as older models broke up problems into larger word phrases. NMT models work by creating an encoder for the input sentence, reads through the whole sentence, and decodes what it thinks the sentence is about. In other words, the model thinks about the sentence you want translated, then decides which one best sounds like whatever language you want to translate into.

The model here is an attempt at replicating the work that Google has published in the fields of NMT. In the Google Neural Machine Translation(GNMT) paper, the authors employ numerous methods to improve upon their models such as using a word piece model to better handle unseen words. In addition to their baseline model, they also developed a method in order to allow their GNMT to perform zero shot translation which essentially allows the network to learn associations between word phrases and to find translations that it has not explictly learned.

This repository is an attempt to implement a NMT model using a wordpiece model and the additional features needed to create a simplified zero shot translation model.


## Architecture

### Datasets
The datasets used in this experiment are the Spanish-English and French-English sentence pairs from [manythings.org](manythings.org). The links to download the datasets are the following:  

[Spanish-English](http://www.manythings.org/anki/spa-eng.zip)
[French-English](http://www.manythings.org/anki/fra-eng.zip)

### Training Parameters
These notebooks were trained on Google Colab to take advantage of their GPUs. A lot of the parameters used are not ideal in order to be able to train something within 8 hours of the notebook resetting.  

The data of all samples were first converted into wordpiece model of 750 vocabulary pieces with their prefix langauge target and end of sentence token. The number of input samples varied depending on the notebook and architecture of the model but the datasets were downsampled to the same number of input samples. Test set data was generated from the training data using a split of 0.2. Similar to the papers, the batch size was 128 and the 512 tensors per layer were used. Adam was used with a learning rate of 1E-4. For models 1 and 2, the model used was a bidirectional LSTM followed by a 4 layer deep LSTM encoder, followed by a repeat vector, followed by a 4 layer deep LSTM decoder and softmax output. Dropout was used in every layer at a level of 0.2. Model3 was much simplified with a bidirectional LSTM encoder followed by repeat vector followed by a LSTM decoder and softmax. 

### Results
Model3 performs the best. Model3 was trained longer, had a good amount of input data, and was a much more simplified model overall. Model1 and Model2 was only trained on 10 epochs and potentially exhibiting the vanishing gradient problem because of it's deeper architecture which was mentioned in the papers. Model1 and Model2 both output gibberish but was at least able to handle random inputs compared to other models like the word vector models. Model3 on the other hand, is capable of some level of zero shot learning. The output is still not fluent but it is capable of some zero shot learning seeming returning some French or maybe English for instance Spanish to French from a model training against Spanish to English and English to French.

## References
[Google's Neural Machine Translation System: Bridging the Gap between Human and Machine Translation](https://arxiv.org/abs/1609.08144)
[Google's Multilingual Neural Machine Translation System: Enabling Zero-Shot Translation](https://arxiv.org/abs/1611.04558)