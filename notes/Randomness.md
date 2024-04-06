---
layout: page
permalink: notes/randomness
tags: en
title: Randomness
---

### Introduzione alla Randomicità
Questo è principalmente basato su [(Li & Vitányi 2019)](http://link.springer.com/10.1007/978-3-030-11298-1) Capito 1.9
Sembra che la nozione di random sia alla fine una cosa molto profonda. Per esempio, un caso lampante che le definizioni non funzionano nel caso di numeri trascendenti è che catalogano i numeri di $$\pi$$ come se fossero casuali, mentre in realtà possono essere trovati mediante procedimenti precisi. È una distinzione filosoficamente molto interessante.

Alla fine sembra ci sia un link molto diretto con la crittografia, si può vedere [(Stinson 2005)](https://books.google.it/books/about/Cryptography.html?id=FAPLBQAAQBAJ).
#### Minimum description length come probabilità reale
Una altra osservazione è che gli assiomi della probabilità sviluppati da Kolmogorov, che puoi trovare in[Introduzione alla probabilita](/notes/introduzione-alla-probabilita), sono nella teoria molto belli, ma mancano un framework reale su cui possono essere applicati. Un possibile ipotesi è che il sistema sviluppato da [Kolmogorov complexity](/notes/kolmogorov-complexity) possa essere alla fine il nostro sistema buono per descrivere le cose randomiche, come programmi che generano la stringa voluta.

Von Mises all'inizio del secolo scorso fu uno dei primi che ha studiato questo problema, lui era un frequentista, quindi credeva nel [Central Limit Theorem and Law of Large Numbers](/notes/central-limit-theorem-and-law-of-large-numbers). Una nota interessante è che secondo lui le probabilità sono cose osservabili, come fenomeni fisici, come [Magnetismo](/notes/magnetismo). mentre nel corso fatto di [Poisson processes](/notes/poisson-processes) il prof. del MIT ha chiaramente detto come le probabilità a differenza di altri fenomeni, non sono osservabili da sole, ma hanno bisogno di altri eventi (misura sulla collezione, non sul singolo evento). Un po' questo fa la distinzione fra [Entropy](/notes/entropy) e [Kolmogorov complexity](/notes/kolmogorov-complexity), in cui una è su cose che hanno frequenza, l'altra definibile anche su singoli oggetti.

### Mises–Wald–Church randomness
Questo prende in considerazioni solo cose statistiche:
Una sequenza $$a_{1}, a_{2}, \dots$$ composta di 0 e 1 è definita **random** dal punto di vista di *collezione* (probabilmente avremo una altra definizione più tardi) se valgono le seguenti condizioni:
Sia $$f_{n}$$ il numero di $$1$$ nei suoi primi $$n$$ numeri, allora deve valere che 

$$
\lim_{ n \to \infty } \frac{f_{n}}{n} = p, 0\leq p\leq 1
$$

Ossia il numero di $$1$$ deve essere la nostra probabilità di interesse

E che valga la *place selection rule*, anche conosciuta come *law of
excluded gambling strategy*, ossia per qualunque sotto sequenza della nostra sequenza, valga l stesso il limite, e questo limite deve essere lo stesso valore di $$p$$.
La formalizzazione di questa regola è un po' strana, si vuole avere una funzione computabile parziale $$\phi: \left\{ 0, 1 \right\}^{n} \to \left\{ 0, 1 \right\}$$, allora seleziono l'indice $$n$$ se vale $$\phi(a_{1}a_{2}a_{3},\dots,a_{n-1}) = 1$$. Se ho questa proprietà prendo $$a_{n}$$ nella mia sequenza, poi vado a considerare la sottosequenza $$a_{n_{1}}, a_{n_{2}}, \dots$$ e questa vogliamo che converga ancora a $$p$$ questo dovrebbe essere una necessità abbastanza forte.

#### No analisi a posteriori
Una altra nota negativa è che questa definizione non si può verificare a posteriori, perché in nessun caso reale abbiamo un limite vero (realtà finita, non riusciamo ad andare all'infinito).

#### Random stocastico vs random regolare
Un controesempio classico a questa definizione è il numero $$0,123456789010203040506070809111213141516171819\dots$$  che dovrebbe soddisfare queste proprietà, ma chiaramente non è per niente random. Si chiama **Champernowne’s number**.
Kolmogorov giustifica questo dicendo questo:
> “In everyday language we call random those phenomena where we cannot ﬁnd
a regularity allowing us to predict precisely their results. Generally speaking,
there is no ground to believe that random phenomena should possess any deﬁ-
nite probability. Therefore, we should distinguish between randomness proper
(as absence of any regularity) and stochastic randomness (which is the sub-
ject of probability theory). There emerges the problem of ﬁnding reasons for
the applicability of the mathematical theory of probability to the real world.”
[Kolmogorov]


### Martin-Löf randomness


### Kolmogorov randomness


### Randomness tests
Vorremmo creare un formalismo che ci permetta di descrivere se una certa stringa è random o meno.
Utilizziamo l'idea da statistica dell'*elemento tipico* che definiamo come un *elemento appartenente alla maggiorità*. Per qualche motivo che non ho capito vuole definire in modo random la cosa che appartiene al confine.

Definiamo un insieme $$V = \mathcal{N} \times S$$, e poi una sequenza di $$V_{m} = \left\{ x : (m, x) \in V \right\}$$
tale per cui $$V_{m + 1} \subseteq V_{m}$$ allora puoi definire un livello di confidenza $$\varepsilon$$ entro il quale considerarlo random, solitamente questo lo mettiamo come valore a  $$2^{-m}$$ non so per quale motivo, probabilmente per il fatto che definisce una sorta di valore lunghezza. Dato un certo $$V_{m}$$ 

$$
\forall n \in \mathbb{N},\sum_{x} \left\{ P(x | l(x) = n) : x \in V_{m} \right\} \leq \varepsilon
$$

Si generalizza scegliendo degli insiemi $$V_{m}$$ su cui valutare, sul libro ci sono esempi 2.4.1, 2.4.2.
Se vale la cosa di sopra vuol dire che il test è superato a quel livello. Non so quanto possa essere utile questa def, ma sicuramente è qualcosa.
In pratic



# References

[1] Li & Vitányi [“An Introduction to Kolmogorov Complexity and Its Applications”](http://link.springer.com/10.1007/978-3-030-11298-1) Springer International Publishing 2019

[2] Stinson [“Cryptography: Theory and Practice, Third Edition”](https://books.google.it/books/about/Cryptography.html?id=FAPLBQAAQBAJ) CRC Press 2005