# Character-Level English-to-Hindi Neural Machine Translation (NMT)

## 🔧 Project Title

### 🔥Character-Level English-to-Hindi Neural Machine Translation (NMT)

## 📘 README

## 📌 Overview

  This project implements a character-level sequence-to-sequence neural machine translation (NMT) model that translates English sentences to Hindi using a Long Short-Term Memory (LSTM)-based encoder-decoder architecture. The model is trained on the TED portion of the Hindi-English Truncated Corpus.

## 📂 Dataset

#### Source:
  Hindi-English Truncated Corpus (/kaggle/input/hindi-english-truncated-corpus)

#### Filtering: 
  Only TED source sentences were selected.

#### Size: 
  25,000 parallel sentence pairs sampled randomly.

#### Preprocessing:

  Lowercasing

  Removing punctuation, digits, and English characters from Hindi text

  Stripping whitespaces

  Special start (%) and end ($) tokens added for decoder input

## 🧼 Preprocessing Steps

  Cleaned English and Hindi sentences using regular expressions

  Removed stopwords for word cloud visualization

  Tokenized character sets from both source (English) and target (Hindi) sentences

  One-hot encoded input and output sequences at character level

## 📈 Data Vectorization

  Defined vocabularies for input and target characters

  One-hot encoding used for encoder_input_data, decoder_input_data, and decoder_target_data

#### Shape:

  encoder_input_data: (25000, max_input_len, num_input_chars)

  decoder_input_data: (25000, max_output_len, num_output_chars)

  decoder_target_data: same as decoder_input_data, shifted by one timestep

## 🧠 Model Architecture

### Encoder

  LSTM with latent dimension = 256

  Returns final hidden (state_h) and cell (state_c) states

### Decoder

  LSTM initialized with encoder’s final states

  Fully-connected Dense layer with softmax activation

  Teacher forcing used during training

### Training

  Optimizer: RMSprop

  Loss: Categorical Crossentropy

  Epochs: 50

  Batch Size: 128

  Validation Split: 20%

  Checkpointing enabled to save weights ("/kaggle/working/training_1/cp.weights.h5")

## 🧪 Inference Setup

  Separate inference models for encoder and decoder

  Decoder loop generates Hindi characters one by one

  Stops on encountering the $ end token or reaching max length

## 🔁 Example Translation

  Looped over 100 test samples and printed:

  Input sentence

  Decoded (translated) Hindi sentence

## ✅ Key Technologies Used

  TensorFlow / Keras

  NumPy, Pandas, Matplotlib

  NLTK for preprocessing and stopword removal

  WordCloud for EDA

  Regular Expressions for text cleaning

