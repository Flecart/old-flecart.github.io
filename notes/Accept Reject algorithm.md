---
layout: page
permalink: notes/accept-reject-algorithm
tags: en
title: Accept Reject algorithm
---

#### Some useful links
Main results: [https://jblevins.org/notes/accept-reject](https://jblevins.org/notes/accept-reject)

Intuition: [https://en.wikipedia.org/wiki/Rejection_sampling](https://en.wikipedia.org/wiki/Rejection_sampling)

La cosa è che faccio sampling fra due distribuzioni diverse e devo settare anche un parametro (e a seconda di certe cose diventa molto lento).

#### Introduzione al metodo
Vorrei utilizzare una funzione $$g$$ per generarne una altra, questo è il fulcro del concetto.
L'idea principale è:
1. Conosco la funzione densità della funzione $$f$$ che voglio andare a generare
2. Riesco a generare seguendo una funzione semplice, la chiamo $$g$$, **candidate density**. (che è la densità che utilizzo per calcolare il target che non conosco molto bene).

Ma devono esserci due cose:
1. Due densità devono avere lo stesso supporto
2. La funzione $$\frac{f}{g}$$ deve essere limitata superiormente. (perché è come l'esempio del lago in cui lancio cose dentro per approssimarne il valore).
Allora sia $$M$$ il limite superiore, un buon modo per fare sampling sarà allora 

$$
U \leq \frac{1}{M} \frac{f(Y)}{g(Y)}
$$

Ossia
1. genero $$Y$$ usando g, e genero $$U$$ in modo uniforme normale
2. Guardo se viene soddisfatta la funzione di sopra
3. Se sì prendo, altrimenti rifiuto e continuo così.

#### Dimostrazione
<img src="/images/notes/Inverse Transform-1700141332706.jpeg" alt="Inverse Transform-1700141332706">

#### Probability of accepting
dato una certa $$M$$ allora ho probabilità $$\frac{1}{M}$$ di accettare un sample generato in questo modo, vedere dimostrazione su [wikipedia]([https://en.wikipedia.org/wiki/Rejection_sampling](https://en.wikipedia.org/wiki/Rejection_sampling)#Theory). 
Ma qui diamo una altro valore:


$$
\mathbb{P}\left( U \leq \frac{f(Y)}{Mg(Y)} \right) \
= \int_{-\infty}^{+\infty} \int _{-\infty}^{f(Y)/f(X)M} 1 \, du g(y) \, dy
$$

Dove abbiamo utilizzato la marginalizzazione sulla distribuzione $$Y$$, quello si semplifica con:

$$
= \int_{-\infty}^{+\infty} \frac{1}{M} \frac{f(y)}{g(y)} g(y) \, dy = \frac{1}{M}
$$

E si ha la soluzione.
#### Average waiting time (!)
il valore corretto è $$c^{-1}$$ dove

$$
c = \sup_{x} \frac{f(x)}{g(x)}
$$

Ad intuito questo sarebbe il valore di $$M$$ migliore, perché è quello con probabilità migliore per fare sampling, ma non so bene perché si potrebbe considerare come un concetto di tempo.
#### With Unnormalized density

ossia tale per cui l'integrale su tutto il supporto non è 1, ma un valore $$k$$, si può dire che questo algoritmo funziona lo stesso.
Il motivo che è stato dato è che questa costante si può tirare fuori e messa dentro $$M$$ e quindi sarebbe come il dato precedente.

consideriamo $$\tilde{f}$$ e $$\tilde{g}$$ tale che entrambi non siano normalizzati, magari con costanti diversi, e supponiamo che anche questi siano limitati su $$\tilde{M}$$.

Si può vedere che anche in questo caso la probabilità di acceptation è uguale a una costante.
di valore

$$
\frac{i}{\tilde{M} \cdot k}
$$

Dove $$k = \int _{-\infty}^{+\infty} f(x) \, dx$$ dato che non è normalizzato.

# References