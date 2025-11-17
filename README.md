Autocorrector Feature Using NLP in Python
Project Description
This project is an autocorrection generator built with Python, using principles of Machine Learning and Natural Language Processing (NLP). Given a (potentially misspelled) input word, the program suggests the most likely correct spellings, ranked by probability.

This implementation is based on statistical NLP techniques. It uses a large text corpus to build a vocabulary and calculate the probability of each word's occurrence. It then generates a set of candidate words (potential corrections) based on "edit distance" and selects the most probable word from that set as the best suggestion.

How It Works
The autocorrect model works by following these core implementation steps:


Load and Process the Dataset: The system first reads a large text file (corpus) to build its vocabulary. In this project, the corpus used is final.txt, which contains the text of "The Adventures of Sherlock Holmes".


Compute Word Frequencies: It processes the text to create a word frequency dictionary, counting the occurrences of each word. This is handled by the counting_words() function.

Calculate Word Probabilities: From the word counts, the model calculates the probability (P) of each word appearing in the text. This is calculated as: P(word) = Frequency(word) / Total number of words in corpus This step is handled by the prob_cal() function.

Generate Possible Corrections: When a user inputs a word, the system generates a set of "candidate" words that are a small "edit distance" away. An edit is a single change, and this model generates all possible words that are one or two edits away from the original input. These edits are implemented through the following functions:

DeleteLetter(): Removes one letter from the word (e.g., 'bannana' -> 'banana').


Switch_(): Swaps two adjacent letters (e.g., 'bannaa' -> 'banana').

Replace_(): Replaces one letter with another (e.g., 'bznana' -> 'banana').

insert_(): Adds a new letter (e.g., 'banaa' -> 'banana').

LemmWord(): Finds the root (lemma) of the word using NLTK.

Find the Best Corrections: The list of candidate words is filtered to find those that actually exist in the vocabulary. The system then uses the get_corrections() function to rank these valid candidates based on their probability (frequency). The word with the highest probability is considered the most likely correct spelling and is returned as the best suggestion.

Technologies Used
Python 3

Jupyter Notebook


NLTK (Natural Language Toolkit): Used for text processing and lemmatization.

re (Regex): Used for cleaning and tokenizing the text.

pattern: A Python library used for various NLP tasks.

Dataset
The model's vocabulary and word probabilities are built from the final.txt corpus file, which contains the complete text of Sir Arthur Conan Doyle's "The Adventures of Sherlock Holmes."

This dataset was originally sourced from Kaggle: https://www.kaggle.com/datasets/subho117/autocorrector-feature-using-nlp-in-python

How to Use
Ensure you have the required libraries installed:

Bash

pip install nltk pattern
Run the Autocorrector Feature Using NLP In Python.ipynb notebook.

The final cell in the notebook will prompt you for input.

Enter any word (misspelled or correct) to see the top 3 correction suggestions.

Python

# Example from the notebook:
# Input
my_word = input("Enter any word:")

# Counting word function
word_count = counting_words(main_set)

# Calculating probability
probs = prob_cal(word_count)

# only storing correct words
tmp_corrections = get_corrections(my_word, probs, main_set, 2)
for i, word_prob in enumerate(tmp_corrections):
    if(i < 3):
        print(word_prob[0])
    else:
        break

Project By: Rohan Pimparkar
