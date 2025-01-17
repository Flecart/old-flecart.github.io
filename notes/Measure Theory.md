---
layout: page
permalink: notes/measure-theory
tags: en
title: Measure Theory
---

Ultima modifica: September 18, 2022 9:43 AM
Primo Abbozzo: September 16, 2022 9:52 AM
Studi Personali: Yes

# Elementi di ripasso

# Measure Theory

## Introduzione

### Requirements of the measure function

<img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled.png" alt="image/universita/ex-notion/Measure Theory/Untitled">

Vorremmo cercare di **estendere il concetto di misurabilità** a gruppi molto più ampi di un singolo intervallo, vorrei creare una funzione che sia in grado di misurare degli insiemi. *su vedrà che sono impossibili).

### Impossibilità di questi requirements (assurdo)

<img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 1.png" alt="image/universita/ex-notion/Measure Theory/Untitled 1">

**Costruzione dell’insieme di interesse**

Consideriamo la classe di equivalenza definita come in immagine, mi costruisco (credo si chiami cosets) $$\Lambda$$ in quel modo, prendendo le classi di equivalenza, posso dire che questo lambda non è numerabile, perché se lo fosse ogni elemento di R sarebbe rappresentabile con lambda e un pezzo di X (ad esempio .

Allora mi costruisco $$\Omega$$ definito con assioma della scelta prendendo un singolo elemento in ogni classe di equivalenza. È chiaro che questo insieme così creato sia innumerabile.

Inoltre lo creo in modo che $$\Omega \subseteq (0, 1)$$, credo sia abbastanza intuitivo vedere che  c’è sempre un elemento compreso, quindi basta translare.

Ora vado a utilizzare la regola 2, ossia **invarianza per traslazione**.

$$\forall p, q \in \mathbb{Q}\, (\Omega + p) \cap (\Omega + q) = \empty \iff p \neq q$$

Supponiamo che l’intersezione non sia vuota, allora $$\exists x : x = \alpha + p = \beta + q$$, ossia ho che $$\alpha - \beta = q - p \implies \alpha \equiv \beta \implies \alpha = \beta \implies p = q$$  l’uguaglianza dalla relazione di equivalenza deriva dal fatto che appartengono alla stessa classe di equivalenza, ma per costruzione ne ho presa solo una, quindi sono uguali. Quindi se l’intersezione non è vuota ho che p e q sono uguali. se sono uguali, invece, è chiaro che la loro intersezione è l’insieme stesso, quindi non è vuota.

**Upper bound**

Ora che abbiamo questa invarianza, sarebbe utile per cercare di utilizzare 3 e farci dei bounds, e poi dimostrare l’assurdo con questi bounds, allora considero l’insieme $$\bigcup_{-1<p<1, p \in \mathbb{Q}}(\Omega + p)$$, allora questa è una unione infinita numerabile di valori diversi fra di loro, stiamo parlando di elementi disgiunti uno a uno, inoltre, dato che p è compreso fra quei valori e Omega è compreso fra 0 e 1, si ha che tutto è contenuto nell’intervallo $$(-1, 2)$$, e si sa che $$\lambda((-1, 2)) = 3$$ per definizione, quindi poiché $$\forall E,F:E \subseteq F \implies \lambda(E) \leq \lambda(F)$$ (dimostrazione facile, basta scomporre F tramite unione disgiunta di E e il complementare di E rispetto F) si ha che


$$
3 \geq \lambda(\bigcup_{-1<p<1, p \in \mathbb{Q}}(\Omega + p)) = \lambda(\bigcup_{-1<p<1, p \in \mathbb{Q}} \Omega) = \sum_{-1<p<1} \Omega \implies \sum_{-1<p<1} \Omega  =0
$$


L’ultima uguaglianza è valida perché altrimenti, se la somma di un singolo set fosse diversa da zero, avrei che è una somma di infiniti elementi, quindi non è boundata da 3, non può che essere 0.

**Lower bound**

Ora per la seconda parte della nostra dimostrazione, vorrei affermare che $$(0, 1) \subseteq \bigcup_{-1<p<1, p \in \mathbb{Q}}(\Omega + p)$$. Chiaramente se riesco a dimostrare questa cosa, per lemma precedente ho che $$1 \leq \sum_{-1<p<1} \Omega$$  , che abbiamo detto essere 0, quindi ci sarebbe l’assurdo.

Sia $$x \in (0, 1)$$, allora ho che $$\exist\alpha \in \Omega : x \equiv \alpha$$ questo per costruzione di Omega. allora è vero che $$\exists q : x - \alpha = q$$ e deve essere che $$q \in (-1,1)$$ perché $$x, \alpha \in (0, 1)$$, ma allora $$x = \alpha + q \implies x \in \bigcup_{-1<p<1, p \in \mathbb{Q}}(\Omega + p)$$ e ciò finisce la dimostrazione.

## Classes of subsets

### Semialgebra, algebra e sigma algebra defs

- Semialgebra

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 2.png" alt="image/universita/ex-notion/Measure Theory/Untitled 2">

- Algebra

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 3.png" alt="image/universita/ex-notion/Measure Theory/Untitled 3">


Si può notare che $$algebra \implies semi-algebra$$ e si possono usare semi-algebra per generare algebra.

- Sigma-algebra

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 4.png" alt="image/universita/ex-notion/Measure Theory/Untitled 4">


NOTA: intersezione di un tante algebra derivanti da uno stesso insieme è sempre una algebra.

NOTA2: la stessa cosa funziona per le sigma-algebra.

### Algebra generated by a class of sets

- Requirements of generation

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 5.png" alt="image/universita/ex-notion/Measure Theory/Untitled 5">


Quindi quella generata, è l’algebra più piccola che contiene quell’elemento. Questo funziona anche per le sigma-algebra.

### Caratterizzazione delle algebre generate da semi-algebre

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 6.png" alt="image/universita/ex-notion/Measure Theory/Untitled 6">

- Proof ←

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 7.png" alt="image/universita/ex-notion/Measure Theory/Untitled 7">

- Proof →

    TODO: scrivolo te, non è banale, un buon esercizio.

    L’idea principale è la creazione di un algebra, costituito da tutti i modi in cui puoi unire uncountable elementi, e dire che questo insieme qui è un algebra, contiene l’insieme di partenza, e che Q(insieme di partenza) è contenuto in questa, dimostrando ciò finisci, perché sai che $$A \in Q(c) \subseteq \mathcal{B}$$


### Additivity function

- Definition

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 8.png" alt="image/universita/ex-notion/Measure Theory/Untitled 8">

    additivity

    la condizione 1 è importantissima per non avere risultati assurdi per certe cose.. (sarebbe sempre somma finita).

    Si può notare che un insieme algebra è l’insieme naturale di partenza perché soddisfa la chiusura per unione

    NOTA: se $$E \subseteq F$$, se è infinito la funzione allora è infinita anche F, altrimenti F è maggiore di E. (lo si può dire anche per l’infinito) in particolare so che $$\lambda(F) = \lambda(E) + \lambda(F - E)$$

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 9.png" alt="image/universita/ex-notion/Measure Theory/Untitled 9">

    Sigma-additivity

- Examples

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 10.png" alt="image/universita/ex-notion/Measure Theory/Untitled 10">

    example of additive function

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 11.png" alt="image/universita/ex-notion/Measure Theory/Untitled 11">

    Example of additive ,but not sigma-additive function

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 12.png" alt="image/universita/ex-notion/Measure Theory/Untitled 12">

    Why it isn’t sigma additive


## Continuous measures

### def C from below and above

- Definition

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 13.png" alt="image/universita/ex-notion/Measure Theory/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 14.png" alt="image/universita/ex-notion/Measure Theory/Untitled 14">

    Why the measure should be finite, in some cases, En = inf, and remains inf, never converging to 0.


### Lemma - c-measures and additivity

<img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 15.png" alt="image/universita/ex-notion/Measure Theory/Untitled 15">

- Proof of 1 (from below)

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 16.png" alt="image/universita/ex-notion/Measure Theory/Untitled 16">

- Proof of 1 (from above)

     Provo a ricondurmi al caso precedente, costruendo una serie di insiemi crescente. (a sottrazione)

    Poi dovrebbe essere facile concludere aprendo il limite e aprendo la costruzone.

    (Però si deve fare attenzione a qualche dettaglio sulla finitezza nel passaggio finale).

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 17.png" alt="image/universita/ex-notion/Measure Theory/Untitled 17">

- Proof of 2

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 18.png" alt="image/universita/ex-notion/Measure Theory/Untitled 18">

- Proof of 3

    <img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 19.png" alt="image/universita/ex-notion/Measure Theory/Untitled 19">


- Example of why finiteness is needed

    !<img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 20.png" alt="image/universita/ex-notion/Measure Theory/Untitled 20">


### Extension of additive measure from semi-algebra to algebra

!<img src="/images/notes/image/universita/ex-notion/Measure Theory/Untitled 21.png" alt="image/universita/ex-notion/Measure Theory/Untitled 21">



# References