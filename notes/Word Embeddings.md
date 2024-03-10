---
layout: page
permalink: notes/word-embeddings
tags: italian
title: Word Embeddings
---

### Word2Vec
Paper di riferimento: @mikolovEfficientEstimationWord2013.

[Video youtube intuitivo]([https://www.youtube.com/watch?v=viZrOnJclY0&ab_channel](https://www.youtube.com/watch?v=viZrOnJclY0&ab_channel)=StatQuestwithJoshStarmer)
[Blog pratico]([https://towardsdatascience.com/a-word2vec-implementation-using-numpy-and-python](https://towardsdatascience.com/a-word2vec-implementation-using-numpy-and-python)-d256cf0e5f28)

È stato uno dei primi approcci che provano a fare un **embedding semantico** del significato delle parole.
Semplicemente andare a fare [Tokenization](/notes/tokenization) per andare a encodare le parole non è sufficiente, perché questi non hanno nessun apporto semantico alle parole.

In questo caso vogliamo **rappresentare una parola tramite vettori**. Il vettore alla fine non sarà altro che il *layer lineare iniziale* per fare all'associazione. Poi questo viene utilizzato per fare una cosa simile a un autoencoder [Autoencoders](/notes/autoencoders).
La cosa da notare è che il layer iniziale è enorme, è **l'intero vocabolario.**
Già questi

Poi si utilizza la Crossentropy per fare backprop. 

#### Negative sampling
È un modo per velocizzare il training per word2vec, fare in contemporanea 600k non era feasible al tempo. Seleziona 2-20 parole nel vocabolario che non vogliamo andare a predire.
600k perché Word2Vec è solamente doppio layer lineare, con però 3kk parole di input e output.

Non so se lo ho capito bene ma credo faccia sampling di un certo numero di parole alla volta e aggiorna solamente i pesi interessati (quindi k target, e l'insieme dei pesi interessati, solamente quelli).
Non so perché si chiami negative sampling se è questa l'idea sotto.


#### Tentativo raw di codice non finito
```python
# [https://github.com/rahul1728jha/Word2Vec_Implementation/blob/master/Word_2_Vec.ipynb](https://github.com/rahul1728jha/Word2Vec_Implementation/blob/master/Word_2_Vec.ipynb)
import re
import numpy as np
from typing import Literal

stop_words = ['i', 'me', 'my', 'myself', 'we', 'our', 'ours', 'ourselves', 'you', "you're", "you've", "you'll", "you'd", 'your', 'yours', 'yourself', 'yourselves', 'he', 'him', 'his', 'himself', 'she', "she's", 'her', 'hers', 'herself', 'it', "it's", 'its', 'itself', 'they', 'them', 'their', 'theirs', 'themselves', 'what', 'which', 'who', 'whom', 'this', 'that', "that'll", 'these', 'those', 'am', 'is', 'are', 'was', 'were', 'be', 'been', 'being', 'have', 'has', 'had', 'having', 'do', 'does', 'did', 'doing', 'a', 'an', 'the', 'and', 'but', 'if', 'or', 'because', 'as', 'until', 'while', 'of', 'at', 'by', 'for', 'with', 'about', 'against', 'between', 'into', 'through', 'during', 'before', 'after', 'above', 'below', 'to', 'from', 'up', 'down', 'in', 'out', 'on', 'off', 'over', 'under', 'again', 'further', 'then', 'once', 'here', 'there', 'when', 'where', 'why', 'how', 'all', 'any', 'both', 'each', 'few', 'more', 'most', 'other', 'some', 'such', 'no', 'nor', 'not', 'only', 'own', 'same', 'so', 'than', 'too', 'very', 's', 't', 'can', 'will', 'just', 'don', "don't", 'should', "should've", 'now', 'd', 'll', 'm', 'o', 're', 've', 'y', 'ain', 'aren', "aren't", 'couldn', "couldn't", 'didn', "didn't", 'doesn', "doesn't", 'hadn', "hadn't", 'hasn', "has"]

def get_file_data(stop_word_removal: bool = False):
    file_contents = []
    with open('jef_archer.txt') as f:
        file_contents = f.read()
    text = []
    for val in file_contents.split('.'):
        sent = re.findall("[A-Za-z]+", val)
        line = ''
        for words in sent:
            
            if stop_word_removal: 
                if len(words) > 1 and words not in stop_words:
                    line = line + ' ' + words
            else:
                if len(words) > 1 :
                    line = line + ' ' + words
        text.append(line)
    return text

def generate_dictinoary_data(text: list[str]):
    word_to_index= dict()
    index_to_word = dict()
    corpus = []
    count = 0
    vocab_size = 0
    
    for row in text:
        for word in row.split():
            word = word.lower()
            corpus.append(word)
            if word_to_index.get(word) == None:
                word_to_index.update ( {word : count})
                index_to_word.update ( {count : word })
                count  += 1
    vocab_size = len(word_to_index)
    length_of_corpus = len(corpus)
    
    return word_to_index,index_to_word,corpus,vocab_size,length_of_corpus

def get_one_hot_vectors(target_word: str, context_words: list[str], vocab_size: int, word_to_index: dict[str, int]):
    
    #Create an array of size = vocab_size filled with zeros
    trgt_word_vector = np.zeros(vocab_size)
    
    #Get the index of the target_word according to the dictionary word_to_index. 
    #If target_word = best, the index according to the dictionary word_to_index is 0. 
    #So the one hot vector will be [1, 0, 0, 0, 0, 0, 0, 0, 0]
    index_of_word_dictionary = word_to_index.get(target_word) 
    
    #Set the index to 1
    trgt_word_vector[index_of_word_dictionary] = 1
    
    #Repeat same steps for context_words but in a loop
    ctxt_word_vector = np.zeros(vocab_size)
    
    
    for word in context_words:
        index_of_word_dictionary = word_to_index.get(word) 
        ctxt_word_vector[index_of_word_dictionary] = 1
        
    return trgt_word_vector,ctxt_word_vector

#Note : Below comments for trgt_word_index, ctxt_word_index are with the above sample text for understanding the code flow
def generate_training_data(corpus,window_size,vocab_size,word_to_index,length_of_corpus,sample=None):

    training_data =  []
    training_sample_words =  []
    for i,word in enumerate(corpus):

        index_target_word = i
        target_word = word
        context_words = []

        if i == 0:  
            context_words = [corpus[x] for x in range(i + 1 , window_size + 1)] 

        elif i == len(corpus)-1:
            context_words = [corpus[x] for x in range(length_of_corpus - 2 ,length_of_corpus -2 - window_size  , -1 )]
        else:
            before_target_word_index = index_target_word - 1
            for x in range(before_target_word_index, before_target_word_index - window_size , -1):
                if x >= 0:
                    context_words.append(corpus[x])
            after_target_word_index = index_target_word + 1
            for x in range(after_target_word_index, after_target_word_index + window_size):
                if x < len(corpus):
                    context_words.append(corpus[x])

        trgt_word_vector, ctxt_word_vector = get_one_hot_vectors(target_word,context_words,vocab_size,word_to_index)
        training_data.append([trgt_word_vector, ctxt_word_vector])   
        
        if sample is not None:
            training_sample_words.append([target_word, context_words])   
        
    return training_data, training_sample_words

def forward_prop(weight_inp_hidden, weight_hidden_output, target_word_vector):
    hidden_layer = np.dot(weight_inp_hidden.T, target_word_vector)
    u = np.dot(weight_hidden_output.T, hidden_layer)
    y_predicted = softmax(u)
    
    return y_predicted, hidden_layer, u
  
def softmax(x):
    e_x = np.exp(x - np.max(x))
    return e_x / e_x.sum(axis=0)

def calculate_error(y_pred,context_words):
    total_error = [None] * len(y_pred)
    index_of_1_in_context_words = {}
    
    for index in np.where(context_words == 1)[0]:
        index_of_1_in_context_words.update ( {index : 'yes'} )
        
    number_of_1_in_context_vector = len(index_of_1_in_context_words)
    
    for i,value in enumerate(y_pred):
        
        if index_of_1_in_context_words.get(i) != None:
            total_error[i]= (value-1) + ( (number_of_1_in_context_vector -1) * value)
        else:
            total_error[i]= (number_of_1_in_context_vector * value)
            
            
    return  np.array(total_error)

def backward_prop(weight_inp_hidden,weight_hidden_output,total_error, hidden_layer, target_word_vector,learning_rate):
    
    dl_weight_inp_hidden = np.outer(target_word_vector, np.dot(weight_hidden_output, total_error.T))
    dl_weight_hidden_output = np.outer(hidden_layer, total_error)
    
    # Update weights
    weight_inp_hidden = weight_inp_hidden - (learning_rate * dl_weight_inp_hidden)
    weight_hidden_output = weight_hidden_output - (learning_rate * dl_weight_hidden_output)
    
    return weight_inp_hidden,weight_hidden_output

def calculate_loss(u,ctx):
    sum_1 = 0
    for index in np.where(ctx==1)[0]:
        sum_1 = sum_1 + u[index]
    
    sum_1 = -sum_1
    sum_2 = len(np.where(ctx==1)[0]) * np.log(np.sum(np.exp(u)))
    
    total_loss = sum_1 + sum_2
    return total_loss

if __name__ == "__main__":
    # text = get_file_data(stop_word_removal='yes')
    text = ["Best way to success is to work hard and never give up"]
    word_to_index,index_to_word,corpus,vocab_size,length_of_corpus = generate_dictinoary_data(text)
    print('word_to_index:',word_to_index)
    print('index_to_word:',index_to_word)
    print('corpus:',corpus)
    print('vocab_size:',vocab_size)
    print('length_of_corpus:',length_of_corpus)
```


### GloVe

### ELMo

## Note di ripasso

| Data | Commenti |
| ---- | -------- |
|      |          |