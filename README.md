# Lip-Reader
An attempt at creating an end-to-end deep learning model that can read lips, generalized to data outside the dataset used, using tensorflow.

The approach used involved feeding an entire video of at most 96 frames centered around a speaker's mouth as input, and from it, extracting the the right sequence of phonemes uttered by the speaker. The model is trained to recognize 34 out of the 44 phonemes used in the english language. The approach of recognizing phonemes as opposed to words is used to eliminate the errors that may arise from doing the former, such as; differences in accents, grammatical errors while speaking, etc. The model's ability to recognize phonemes could be generalized to recognizing full words. This can be done by mapping groups of phonemes to syllables, and perhaps groups of syllables to words.

The dataset used is the Lombard Grid (https://spandh.dcs.shef.ac.uk//avlombard/), consisting of 5400 videos of 54 speakers speaking sentences. Each utterance of phonemes is timestamped, allowing for easy data collection. The vocabulaty of the dataset is very limited, but it encompasses approximately 77% of the phonemes in the english language, which if learned, hypothetically gives the model a much larger vocabulary.

Some limitations of the model are also limitations placed on humans while lip reading, for example, there exist some phonemes that cannot be distinguished from each other from just visual input, such as:
  - 'p' and 'b'
  - 'ch' and 'sh'\n

There exist some innate limitations on the model that do not apply to humans while lip reading, such as an awareness of context, or body language.

The architecture of the model follows that of LipNet (https://github.com/nicknochnack/LipNet) closely, with some very distinct differences:
- The neural network is smaller, with fewer parameters to allow for faster training times.
- The output / vocabulary is phonemes rather than the english alphabet as in LipNet, for aforementioned reasons.
- The input videos are shuffled in order to generalize better.
- The dataset used by LipNet is the Grid Corpus, which consists of videos similar to that of the Lombard Grid.\n

Attempts made to generalize the model:
- 2 Dropout layers that exclude 50% of previous neuronal outputs.
- The input videos begin and end at randomly selected times. This was done to eliminate the idea that there is an order to the uttered phonemes, which could arise from the limited vocabulary of the dataset.

More work is to be done, but the primary goal is to train the model to recognize sounds / phonemes rather than words or alphabet.
