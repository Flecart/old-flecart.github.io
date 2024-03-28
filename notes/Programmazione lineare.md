---
layout: page
permalink: notes/programmazione-lineare
tags: italian
title: Programmazione lineare
---

Ripasso Prox: 6
Ripasso: December 31, 2022
Ultima modifica: December 27, 2022 10:37 AM
Primo Abbozzo: November 25, 2022 8:55 AM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Programmazione lineare

Vogliamo cercare di restare nel nostro spazio delle soluzioni ammissibili, senza dover stare ad esplorare tutto, vogliamo andare a concentrarci su una parte specifica di essa. Vogliamo utilizzare una struttura fondamentale per i problemi di programmazione lineare, che è quello con cui vogliamo andare a fare. Il fatto è che spostandoci leggermente da un punto tra le soluzioni, possiamo gestire in modo molto semplice il modo con cui si sposta la retta dei valori.

Questo è **possiamo ridurci a considerare i vertici** del poliedro che si costruisce, quindi andiamo in questa prima parte a definire alcune nozioni matematiche utili a mettere in gioco questa intuizione

## Nozioni preliminari

### Vocabolario di base

#### Iperpiano
L'insieme delle soluzioni di equazioni in


$$
\left\{ x \in \mathbb{R}^{n} \mid a^{T}x = b, a \neq 0 \right\} 
$$

E si può dimostrare che questo è un insieme affine, quindi è una linea. Questi piani sono anche convessi perché prendiamo tutti i punti 🤠.

#### Semispazio

$$
\left\{ x \in \mathbb{R}^{n} \mid a^{T}x \geq b, a \neq 0 \right\} 
$$


Lo spazio è diviso fra zone in cui è maggiore e altre in cui è minore.
Questi **non sono affini** ma sono solo convessi (perché limitati in certe zone)

#### Palla euclidea


$$
B(x_{c}, r) = \left\{ x \mid \lvert x - x_{c} \rvert _{2} \leq r \right\}  = \left\{ x _{c} + ru \mid \lvert u \rvert _{2} \leq 1 \right\} 
$$

Dove $$r$$ è chiamato raggio.

#### Ellissoide
È un insieme formato in questo modo

$$
\left\{ x \mid (x - x_{c})^{T} P^{-1} (x - x_{c}) \leq 1 \right\} 
$$

Quindi è una **forma quadratica** quelle saltate in algebra.
Nella pratica è una palla, un po' allungata in certe direzioni descritte da $$P$$, che è una matrice **simmetrica definita positiva**. ossia nell'insieme $$S_{++}$$
Si scrive anche a volte come

$$
\left\{ x_{c} + Au \mid \lvert u \rvert _{2} \leq 1 \right\} 
$$

#### Poliedro
È una intersezione di un numero finito di $$m$$ semispazi come definiti di sopra inoltre non vogliamo che da nessuna parte si estenda all'infinito, quindi vogliamo che valga

$$
\left\{ x \mid Ax \leq b \right\}
$$

Per qualche valore di $$A$$ e $$b$$.

<img src="/images/notes/Programmazione lineare-20240327205441381.webp" alt="Programmazione lineare-20240327205441381">


Un **poliedro** è una qualunque intersezione di semispazi (anche vuota, ma non è molto interessante un poliedro vuoto), ed è un insieme sempre convesso perché l’intersezione di cose convesse è ancora convesso.

L’amico del poliedro che deve essere per forza finito è il **politopo.** (che è la versione non bounded, ma alcuni autori utilizzano una definizione opposta, ma comunque non è molto importante).)

### Facce 🟨
<img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 1.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 1">


**Formalmente:**

Preso un poliedro, andiamo a definire una sua faccia, un insieme di punti che soddisfano queste caratteristiche:

1. Giace direttamente su una o più condizioni
2. Giace dentro il poliedro (quindi ogni punto della faccia è un punto del poliedro anche!)

Che matematicamente si possono andare a caratterizzare in questo modo: sia $$I$$ l’insieme degli indici delle condizioni della matrice del poliedro che andiamo a prendere, e $$\bar{I}$$  il suo complementare, allora


$$
P_I = \{x: A_Ix=b_I \wedge A_{\bar{I}}x \leq b_{\bar{I}} \}
$$


**Intuitivamente**
L'intuizione per questa parte è prendere un sottoinsieme che ci piace riguardante la nostra matrice, quella cosa corrisponderà a una faccia del nostro poliedro.

nozioni sulla **dimensione della matrice finale** è molto buona, ci può dare un concetto di dimensione della faccia che andiamo a prendere. Per fare un esempio, se riusciamo ad avere una faccia di dimensione n, è un singolo punto, quindi è un vertice!

in generale, come dicono le dispense vale la relazione sul fatto che

> E` possibile verificare che una faccia determinata da una
matrice AI di rango k ha dimensione n − k o inferiore, pagina 8 dispense 3.
>

### Spigoli e vertici e soluzioni base 🟩

Una sottomatrice di dimensione n, è un vertice!.

Una sottomatrice di dimensione n - 1 è uno spigolo!.

Questo sarà il nostro **spazio di ricerca** quelli sui vertifici!

**Soluzione di base**

Parlano dei vertici e lo fanno attraverso il concetto di invertibilità. Una soluzione di base non è detto che faccia parte del poliedro che stiamo andando a considerare! Vogliamo andare a considerare delle **basi ammissibili** ossia che sono anche all'interno del poliedro (un esempio ez. è il vertice).

**Matrice di base, ammissibilità o non della base.**

### Vincoli attivi 🟨+

I vincoli attivi sono vincoli del nostro problema che vengono soddisfatte come uguaglianze. Questa è una cosa di interesse, per ragioni che mi sono ancora oscure.

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 2.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 2">


Di importanza però è la notazione

$$
I(x) = \{ i |  A_ix = b_i\}
$$


Questa notazione più o meno ci dice quante righe della matrice sto andando poi a contare

## Cose convesse
Trattate un po' meglio in [Analisi di Convessità](/notes/analisi-di-convessità).

### Inviluppi convessi 🟩

Queste cose ci sono molto utili, vanno simili al concetto di [Base e dimensione](/notes/base-e-dimensione), cercare di riassumere un insieme di punti illimitato con alcuni punti cardine limitati. In questo caso considero l'insieme , $$X = \{x_1, ..., x_n\}$$


$$
conv(X) = \{ \sum _{i = 0} \lambda_ix_i | \sum_{i = 0} \lambda_i = 1 \land \lambda_i \geq 0\}
$$


Questo insieme ci è sufficiente per avere un **politopo**, per il caso infinito dovremmo andare sui coni.

Per ora basta avere un intuizione per questo. Riusciamo a costruire in questo modo tutti i spigoli che uniscono i nostri punti di vertice, e partendo da questi possiamo andare a costruire l’intero politopo, ma la dimostrazione formale non la andiamo a dare.

### Coni convessi 
See [Analisi di Convessità#Convex Cone](/notes/analisi-di-convessità#convex-cone).
    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 3.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 3">


Il concetto di cono convesso ci aiuta a costruire il caso infinito, considerando alcune operazioni di prolungamento e somma

$$x,y \in C, \lambda, \beta \in \mathbb{R} \implies \lambda x + \beta y \in C$$

Possiamo provare a generalizzare questo concetto utilizzando la somma fra tutti i possibili

$$V = \{ v_1, ... v_n\}$$


$$
cono(V) = \{ \sum _{i = 1} \lambda_i v_i | \lambda_i \in \mathbb{R} ^+\}
$$


### Teorema di Motzkin o di decomposizione (!) 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 4.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 4">


Questo è un teorema molto importante perché **teorema caratterizzante dei poliedri**!

**Intuizione**

Più o meno questo teorema ci dice che tutti i poliedri possono essere ridotti a un insieme di punti di partenza, che quasi vanno a formare una base (nel caso del politopo sono solamente questi punti di base, il cono che andiamo a considerare è vuoto!) e poi poter estenderli in una direzione utilizzando il cono!

**Differenza dimensione motzkin e vincoli**

L’utilizzo più importante di questo teorema è che possiamo caratterizzare i poliedri in modo molto più semplice, differentemente a quanto fatto con i vincoli lineari, perché quelli hanno un’esplosione esponenziale per quanto riguarda il numero di vertici. (nota importnate è che i vertici non si calcolano in modo molto veloce fra i vertici e i vincoli lineari!).

**Vertici → exp**

**Vincoli → lin**.

Questa differenza di crescita non ci piace proprio! Non ci piace andare a cercare il numero di vertici se questi vertici crescono in modo esponenziale!

### Th esistenza dell’ottimo finito (!!) 🟨++

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 5.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 5">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 6.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 7.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 7">


Questo teorema lega in modo molto forte la parte di **cono convesso** con la soluzione del nostro problema lineare!

ossia possiamo avere soluzione solo se il cono non si espande verso l'infinito positivo, se succede, la soluzione ottimale è infinito, altrimenti possiamo andare a scartare il contributo negativo del cono, e tenerci solamente il contributo dato dalla inviluppo convesso.

## Teoria della dualità

È una branca dell'algebra lineare che ci permette di semplificare tutti i concetti.

### Intro dualità🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 8.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 8">

- Si fa una sorta di trasposta alla matrice di A.
- y è pari al numero di righe di A

La trasformazione al duale è molto facile, ed è abbastanza intuitiva una volta che capiamo che vogliamo andare a fare l’upper bound.

### Dualità asimmetrica 🟥+

### Teorema debole di dualità 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 9.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 9">


Qui c'è una cosa simile a quanto fatto in MCMF, il cui massimo di x è boundato dal minimo del suo duale, in [Tarjan e MCMF](/notes/tarjan-e-mcmf).

### Corollari di dualità (2) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 10.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 10">

1. il fatto che ci sia un bound a x, implica che se x è illimitato, non posso avere il bound!
2. Abbiamo una condizione di ottimalità delle soluzioni trovate!

### Def Direzioni ammissibili

Vogliamo trovare un modo per muoverci e trovare ancora una direzione ottimale!

**Def:**

un vettore $$\varepsilon \in \R ^n$$ è una **direzione ammissibile** se esiste  $$\bar{\lambda}  > 0$$ tale che  $$x(\lambda) = x +  \lambda \varepsilon$$, per ogni $$\lambda \in 0...\bar{\lambda}$$

**Intuizione**

Ossia se possiamo spostarci di almeno un pò verso la direzione che vogliamo!

### Def direzione di crescita

Possiamo considerare una **direzione di crescita**


$$**\lambda  \iff cx(\lambda)  = c \bar{x} + \lambda c\varepsilon > c \bar{x} \iff c\varepsilon > 0**$$

La cosa interessante è che una direzione di crescita cresce **indipendentemente dal punto**, questo è una proprietà molto forte della programmazione lineare!

Questi due concetti sono molto utili perché una volta che abbiamo una **direzione ammissibile e di crescita** allora si può verificare che si può migliorare ancora la soluzione di x.

### Suff e nec per direzione ammissibile

- Slide

    <img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 11.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 11">


L'idea principale per questa dimostrazione è sui vincoli attivi, differenziare se una riga è un vincolo attivo o meno. Se lo è allora voglio che sia minore, altrimeni basta scegliere un intorno sufficientemente piccolo perché il vincolo è stretto.

Da notare che se non è un vincolo attivo allora ho una disuguaglianza stretta allora posso andare ad utilizzare cose di analisi

### Ottimalità del punto

> Dato un punto $$x$$ ammissibile, questo punto è ottimo sse non ci sono direzioni di crescita ammisibile
>

**Intuizione sulla dimo**

→ se è già ottimo allora se esistessa una direzione di crescita, si potrebbe far crescere ancora il nostro punto di ottimo, violando l’ipotesi di ottimalità

←Se non ho direzioni di crescita, supponendo per assurdo che non sia ottimo abbiamo allora possiamo trovare una direzione di crescita ammissibile, creando un assurdo, questa direzione la andiamo a trovare prendendo un punto ottimo e creando il vettore da questo punto a quello nostro iniziale.

- Dimostrazione dispense

    !<img src="/images/notes/image/universita/ex-notion/Programmazione lineare/Untitled 12.png" alt="image/universita/ex-notion/Programmazione lineare/Untitled 12">