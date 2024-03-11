---
layout: page
permalink: notes/model-of-analogies
tags: italian
title: Model of Analogies
---

> The human ability of making analogies proceeds in such a way as to keep complexity minimal.

Perché facciamo questo? Perché è la cosa più semplice da fare! Anche su Vapnik's dimensions è simile questa idea!

Occam razor, Epicuro, con Solomonoff che ha risolto problema dell'induzione che Hume pensava di fare con abitudini. Attualmente IQ tests provano a misurare la capacità di estendere questo.

### Analogia

Studiamo l'analogia come oggetto matematico perché sembra essere una capacità molto difficile da generalizzare e utilizzare nelle macchine.

#### Definizione di analogia
Scrivo $$A:B :: C:D$$ per dire che esiste una relazione $$\mathcal{R}$$ tale per cui valga $$R(A,B), R(C,D)$$
Questa relazione deve soddisfare certi assiomi come

#### Proprietà dell'analogia
**Identità**

$$
\mathcal{A}(A,B,A,B)
$$

**Simmetria**


$$
\mathcal{A}(A,B,C,D) \implies \mathcal{A}(C, D, A, B)
$$

**Permutazione centrale**


$$
\mathcal{A}(A,B,C,D) \implies \mathcal{A}(A,C,B,D)
$$


Sono tutte proprietà che intuivamente hanno senso quando si parla di analogia.

#### Equazione di analogia
Scriviamo 
$$
A:B::C:x
$$

L'obiettivo è trovare un $$x$$ nel dominio che soddisfa la relazione $$\mathcal{R}$$ scelta, che che sia più semplice possibile. Per la semplicità utilizziamo [Kolmogorov complexity](/notes/kolmogorov-complexity) quindi scegliamo

$$
x = argmin(K(A,B,C,x))
$$



### Minimum Description length principle
[https://truththeory.com/2018/05/07/string-theory-explained-what-is-the-true-nature-of-reality-video/](https://truththeory.com/2018/05/07/string-theory-explained-what-is-the-true-nature-of-reality-video/)

Principle used to choose models to describe phenomenons of the world in particular:


$$
M_{0} = argmin_{M}(K(M) + K(D|M))
$$

Che è in un certo senso un trade fra overfitting e undefitting classico, solo da un punto di vista di AIT.

> The best model is neither the simplest one nor the one that offers the best fit with the data, but the model that achieves the best compromise between simplicity and data fitting.


### Universal Induction
Solomonoff usa principle of Multiple explanations (Epicuro, tiene tutte le spiegazioni che sono buone per i dati).