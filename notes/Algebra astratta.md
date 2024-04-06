---
layout: page
permalink: notes/algebra-astratta
tags: italian
title: Algebra astratta
---

Ultima modifica: October 19, 2022 5:05 PM
Primo Abbozzo: February 2, 2022 4:31 PM
Studi Personali: No

Cerco di riassumere i concetti principali nei video di Benedict Gross presenti sul web (in particolare youtube)

# Argomento

# Spazi vettoriali

## Th: generatori di spazi - linearmente indipendenti

Dati due insiemi di vettori S e L, con S che spanna nello spazio V e L di vettori in V che siano tutte linearmente indimendenti, allora  $$|S| \geq |L|$$

**Idee principali**

Sono principalmente due le idee principali.

1. L appartiene a V e S spazia tutto questo spazio, quindi posso scrivere il vettore L come combinazione lineare con vettori di S.
2. Utilizzo 1 questo per arrivare a una contraddizione sull’indipendenza lineare di L quando S < L
    1. Infatti quando questo succede, riesco a trovare una riscrittura di L con S che mi rende L = 0
    2. Utilizzo anche il fatto che quando ho n equazioni e m incognite, se m > n posso trovare una soluzione non banale sempre.

### Cor: Tutte le basi di V hanno stessa dimensione

La dimensione sarebbe il numero di elementi. Non so esattamente come si dimostrare questo.

### Cor: Tutti i generatori hanno dimensione maggiore o uguale della base

Questa è una conseguenza banale del teorema.

Possia.

Una cosa che si tiene in conto, molto simile a questo corollario è un algoritmo che si usa per dimostrare che se ho un insieme di vettori linearmente dipendenti L che generava uno spazio V, posso togliere vettori finché non diventa una base.

### Cor: Un insieme linearmente indipendente L ha dimensione minore o uguale alla base

Questo si può dimostrare che un insieme linearmente indipendente L si può espandere per generare lo spazio V aggiungendo un vettore alla volta finché non ha dimensione della base, e se è una base per il corollario 1 deve essere della stessa dimensione.

## Th: rimpiazzamento di basi

<img src="/images/notes/image/universita/ex-notion/Algebra astratta/Untitled.png" alt="image/universita/ex-notion/Algebra astratta/Untitled">

## Th: bigezione fra matrici e trasformazioni lineari

Buona bigezione, ma non approfondisco quam non la ho studiata.

## Th: counting theorem

Sia f un automorfismo su un vettore

# Relazione con Geometria

Quando usiamo come campo i reali, questo ha una relazione intima con la geometria.

Si ha un gruppo normale con il gruppo ortogonale con il gruppo generale lineare.

Vogliamo mettere un pò di struttura sul campo dei reali in modo che sia utile per i nostri calcoli geometrici.

## Gruppo ortogonale

<img src="/images/notes/image/universita/ex-notion/Algebra astratta/Untitled 1.png" alt="image/universita/ex-notion/Algebra astratta/Untitled 1">

Con la coppia ordinata come il prodotto scalare. Bisognerebbe dimostrare (check) che effettivamente questo sia un gruppo, ma non sembra difficile, almeno quando lo fa Benedict Gross.

# Discrete subgroups

Isometria è una transformazione che mantiene la distanza di punti. Si può dimostrare che è una composizione fra trasformazione ortogonale (rotazione) e translazione).

Discreto di solito significa che un sottogruppo finito di G, non contiene rotazioni o translazioni arbitrariamente piccole (esiste un minimo di rotazione o translazione).

Possono esistere insieme infiniti!

**Possibili sottogruppi:**

Gruppi di translazione.  → additive part.

Gruppi di rotazione → point stabilizer part, and linear operation

Gruppi di composizione fra i due, che andiamo a chiamare Reticoli (lattices).

### Lemma 1 Intersezione di uno sottospazio di R con L sottogruppo discreto contiene finiti punti di L

Se fosse infinito allora possiamo trovare una sottosequenza infinita, per qualcosa di simile a Bolzano Weierstrass (circa compattezza) posso trovare una serie di punti che converge a qualcosa, faccio translazione e allora dimostro che mi posso avvicinare quanto mi pare a 0, cosa che non può essere nel discreto.

Quindi ho un insieme finito.

### Classificazione punti possibili

Ogni punto nel gruppo, la distanza a due a due è maggiore o uguale a epsilon minore che c’è. (gruppo additivo di translazione). Altrimenti si avrebbe una contraddizione, c’è una distranza minima fra due punti ok?

L è diverso da 0, allora è in una riga, o reticolo. (possiamo estendere questo argomento a più dimensioni, ora ragioniamo su 2)

1. Se è sulla **riga**, dato che è un insieme discreto posso trovare il vettore più vicino all’origine (che è per forza nell’origine) la distanza è maggiore uguale a epsilon. Allora tutti i punti devono essere multipli di questo.
    1. L’argomento è simile all’algoritmo di euclide. (dici che c’è un resto minore di b e questo deve essere nell’insieme, ma questo non può essere  perché abbiamo preso già b come minimo quindi r = 0).
2. Se non è sulla riga allora **contiene una base** (linearmente indipendenti, altrimenti si ha una riga, poi in R2 basta che siano indipendenti per spannare l’intero spazio, quindi due vettori a caso ok?).
    1. Siano a, b vettori della base, e b il vettore di modulo minore nella linea bR, uguale per a.
    Vogliamo dire che questi siano i nostri generatori dello spazio.
    2. Consideriamo il parallelogramma formato da questi vettori. Questo parallelogramma contiene un insieme finito di punti di L per Lemma 1.
    3. Applichiamo questo algoritmo: rimpiazziamo b di sopra per il punto b’ nel parallelogramma che sia più vicino ad a rispetto a b. allora ho un parallelogramma più piccolo. Continuiamo finché non ci siano più punti (basterebbe anche applicarlo una sola volta prendendo subito il minimo lol).
    4. Abbiamo trovato il parallelogramma minimo e claimmiamo che L = Za + Zb, ovvero mettiamo parallelogrammini in giro per l’intero spazio così 🙂.
    5. Applichiamo l’argomento euclideo anche qui e concludiamo ciò.

### L’immagine di Gamma  in O(2) preserva L (lattice)

<img src="/images/notes/image/universita/ex-notion/Algebra astratta/Untitled 2.png" alt="image/universita/ex-notion/Algebra astratta/Untitled 2">

Questo pone delle grandi restrizioni sul sottogruppo discreto.

L = {0} allora ho il gruppo ciclico o dihedrale.

Altrimenti Gamma può essere gruppi $$L = C_n or D_{2n}, n = \{1,2,3,4,6\}$$ e quindi sta restringendo molte cose.

Dear Dr __.

I’m writing this letter to ask the recovery of some of my files on the codespace that got deleted without any forewarning.

I’m a student at first year of Computer Science in Bologna. I was amazed by the quality of your lessons and I astonished by the power of the codespaces. I began to take notes with it. Every note of the first semester was on this codespace.

I began to write programs on it and it was so fast! Such a good infrastructure! I began also to write some of my own hobby projects on it. It was fascinating.

But, suddenly, everything got deleted. I lost every note. I lost every program. I didn’t expect this would happen and i didn’t make a backup. I lost everything. i’m downhearted from this event.

So i’m writing this letter to ask you if it’s possible to recover my files, the files i wrote in a semester of work.

Best Filippo .
ything. i’m downhearted from this event.

So i’m writing this letter to ask you if it’s possible to recover my files, the files i wrote in a semester of work.

Best Filippo .

# References