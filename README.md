# predict-answer-label-on-Ubuntu-Chat Channel
The answer bot, Ubotu, plays an important role in answering questions on Ubuntu Q&A channel. However, specific labels are required to trigger their answers. These labels are manually entered by human users when they see questions that are answerable by bots.
My project is to learn the features of a question and predict the answer labels, which then trigger the Ubotu to answer the question. The goal of this is to replace the human label with an automated algorithm

## An Example
Question: 
2007-02-13-ubuntu.txt:[01:41] <Ins|de> hi there, i've a little problem with sound, i cannot hear anything, i've unmuted all channels, all modules are loaded, but it stills completely mute, can anyone help me? thanks

Human User who enters the label:
2007-02-13-ubuntu.txt:[01:42] <IdleOne> !sound | Ins|de

Ubotu answers the question:
2007-02-13-ubuntu.txt:[01:42] <ubotu> Ins|de: If you're having problems with sound, first ensure ALSA is selected, by double clicking on the volume control, then File -> Change Device (ALSA Mixer). If that fails, see https://help.ubuntu.com/community/Sound - https://help.ubuntu.com/community/SoundTroubleshooting - http://alsa.opensrc.org/index.php?page=DmixPlugin - For playing audio files, see !Players and !MP3
  
In this example, My algorithm would predict "!sound" when seeing the question

### Prerequisites

Things to install
* numpy
* fasttext
* matplotlib

### Installing

* pip install numpy
* pip install fasttext
* pip install matplotlib

## Data Representation
* Built a dictionary of unique words from the full dataset
* Represent the sentences using vectors containing 0 and 1 (one hot encoding) with the unique word dictionary
* Represent the training, test, validation sets as sentence-label pairs eg.(("hi there, i've a little problem with sound, i cannot hear anything, i've unmuted all channels, all modules are loaded, but it stills completely mute, can anyone help me? thanks", "!sound"))
* Use the special representation “\__label__ label input” for fasttext eg.(\__label__!sound hi there, i've a little problem with sound, i cannot hear anything, i've unmuted all channels, all modules are loaded, but it stills completely mute, can anyone help me? thanks)
* hashtable of label to answers


## Model and Performance
Performance score measure: Each time the model predicts a label correctly, it gets 1 point. 
After going through all data, divide the total point with the number of data points.
The baseline score, which is the score of printing the most frequent label, is 0.08196721311475409

* Fasttext CNN
* score: 0.6338797814207651
* Perceptron
* score: 0.5747126436781609
* SVM
* score: 0.47701149425287354


## Authors
Shulin Pan

## Next Step
I will continue implementing RNN text classification and experiment with huggingface library. 

## Acknowledgments
This project was supervised by Dr. Jonathan Kummerfeld and Dr. Charles Welch from University of Michigan Language and Information Technology Lab
