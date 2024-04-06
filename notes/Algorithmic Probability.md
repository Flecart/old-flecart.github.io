---
layout: page
permalink: notes/algorithmic-probability
tags: en
title: Algorithmic Probability
---

> _"Information theory must precede probability theory, and not be based on it. By the very essence of this discipline, the foundations of information theory have a finite combinatorial character."_  Kolmogorov, A. N. (1983). [Combinatorial foundations of information theory and the calculus of probabilities](http://rainbow.ldeo.columbia.edu/~alexeyk/Papers/Kolmogorov1983.pdf).  
_Russian mathematical surveys_, _38_ (4), 29-40.

> _"it is clear that elements requiring an extremely large number of words for their definition should be considered as having an extremely low probability."_ (Borel E., [1909](https://link.springer.com/content/pdf/10.1007/BF03019651.pdf) p. 272).


Questa sezione si distacca dalla probabilità classica che abbiamo fatto in questo corso, ma per vicinanza metto qui l'appunto.
### Prefix Complexity
#### Definizione

$$
K(s) = min_{p}\left\{ \lvert p \rvert : U_{pr}(p) = s \right\} 
$$

L'unica differenza con [Kolmogorov complexity](/notes/kolmogorov-complexity) è che qui usiamo una macchina di turing con prefix codes.
#### Intuizione
Una macchina che esegue programmi random può produrre una certa stringa?
Definiamo la probabilità come

$$
P(x) = \sum_{p:U(p)=x} 2^{-l(p)}
$$

Che è un modo per dire generare in modo random certi programmi.
Il valore di sopra è simile a

$$
P(x) \approx 2^{-K(x)}
$$


Per $$K$$ vedi [Kolmogorov complexity](/notes/kolmogorov-complexity).
TODO: cercare di capire perché limitarsi solamente alla versione più corta.
#### Prefix Machine
Da [Leonid Levin](http://old.math.nsc.ru/LBRT/g2/english/ssk/levin_e.html), risolve il problema di termine di interpretazione, perché prefix codes hanno valore sempre minore di 1 come descritto in [Entropy#Krafts Inequality](/notes/entropy#krafts-inequality). 
Se non si escludono, fanno qualcosa di brutto con quel valore di probabilità, perché la somma di tutti avrebbe superato $$1$$ e non avrebbe soddisfatto gli assiomi 
La proprietà principale è che non esistono due programmi per questa macchina tale per cui uno sia prefisso di altro.

#### Self delimiting codes
Con i prefix codes posso avere delle cose self-delimiting, perché so quando un codice finisce e posso interpretarlo per la proprietà dei prefissi.

#### Definition of prefix complexity

Praticamente per encodare un numero encodiamo la sua lunghezza binaria con un codice e poi concateniamo il numero stesso.
<img src="/images/notes/Algorithmic Probability-20240218091550603.webp" alt="Algorithmic Probability-20240218091550603">

Quindi il codice finale avrebbe lunghezza di 

$$
2\log \log(\lvert s \rvert ) + \lvert s \rvert 
$$

#### Relazione con complessità normale


$$
C(s) + O(1) \leq K(s) < C(s) + 2\log(C(s)) + O(1)
$$

La prima diseguaglianza sembra essere presa da [Kolmogorov complexity#Teorema dell'invarianza](/notes/kolmogorov-complexity#teorema-dell-invarianza), mentre la seconda dallo stesso teorema più dal fatto che stiamo usando una macchina di Turing con prefissi.


### Algorithmic probability
#### Definizione algorithmic probability

$$
\mathbb{P}(x) = \sum_{p:U(p)=x} 2^{-l(p)}
$$

TODO: sarebbe carino provare ad esplorare di più questo topic, perché mi sembra abbia belle connessioni con resto.
Poi un sacco di questo content è bloggabile.






# References