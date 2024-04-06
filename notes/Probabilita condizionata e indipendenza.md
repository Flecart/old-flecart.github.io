---
layout: page
permalink: notes/probabilita-condizionata-e-indipendenza
tags: en
title: Probabilita condizionata e indipendenza
---

Ripasso Prox: 40
Ripasso: May 31, 2023
Ultima modifica: May 3, 2023 8:04 AM
Primo Abbozzo: February 28, 2023 12:24 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Probabilità condizionata e indipendente

## Condizionata

### Definizione 🟩

Andiamo a definire una probabilità di un evento $$A$$, condizionata a un evento non nullo $$B$$, come


$$
P(A|B) = \dfrac{P(A\cap B)}{P(B)}
$$


Questo è la cosa fondamentale per poter considerare cose come bayes perché in questo modo abbiamo una certa relazione fra causa ed effetto e anche il contrario! Cosa che ci piace molto molto molto.

### La definizione di sopra è un probabilità 🟩

<img src="/images/notes/Probabilità condizionata e indipendenza/Untitled.png" alt="Probabilità condizionata e indipendenza/Untitled">

**Dimostrazione** mia

inanzitutto vediamo che soddisfatta il fatto che  $$P(A) \in [0, 1]$$, poi possiamo notare che


$$
P(\Omega | B) = \dfrac{P(\Omega\cap B)}{P(B)} = P(B) / P(B) = 1
$$



$$
P(\bigcup A_n | B) = \dfrac{P(\bigcup A_i\cap B)}{P(B)} = \dfrac{P(\bigcup (A_i\cap B))}{P(B)} = \sum_{i = 1} ^\infty\dfrac{P(A_i\cap B)}{P(B)}
$$


Quindi ecco che è una probabilità su Omega!

L’ultima disuguaglianza vale perché sto facendo unione di insiemi  disgiunti. (che sono disgiunti per ipotesi.

### Regola della catena 🟩

<img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 1.png" alt="Probabilità condizionata e indipendenza/Untitled 1">

- Dimostrazione in libro

    <img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 2.png" alt="Probabilità condizionata e indipendenza/Untitled 2">


Questa è uno delle proprietà più importanti che abbiamo per la probabilità è molto interessante notare come basta una induzione così semplice per fare questo

### Formula di disintegrazione o delle probabilità totali 🟩

<img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 3.png" alt="Probabilità condizionata e indipendenza/Untitled 3">

<img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 4.png" alt="Probabilità condizionata e indipendenza/Untitled 4">

**Dimostrazione**

Questo non è tanto difficile da dimostrare, bisogna notare che


$$
B = \bigcup_i (B \cap A_i)
$$


il che è vero perché $$\forall i, j A_i \cap A_j = \empty, \bigcup A_i = \Omega$$ per ipotesi, e quindi sto facendo una unione disgiunta, si ha per $$\sigma-$$additività la prima tesi, mentre la seconda tesi è derivante dalla definizione di probabiltià condizionate

## Indipendenza d'eventi

### Introduzione

L’intuizione di maggior rilievo è il fatto che non ho nuove informazioni se è successo B ossia deve valere che $$P(A|B) = P(A)$$, oppure che $$P(B|A) = P(B)$$, dato che vale per entrambi, è una proprietà simmetrica.

ha quindi senso andare a definire che due eventi siano indipendenti se vale questa proprietà:


$$
P(A \cap B) = P(A)P(B)
$$


È molto importante notare che l'indipendenza di a due a due due eventi non implica l'indipendenza di 3! (guardare l'esempio sul libro)

- Esempio fatto in classe di questo

    Se ho un evento composto da due lanci un dado a 6 faccie, se considero gli eventi:

    1. Al primo lancio esce un numero dispari
    2. Al secondo un numero pari
    3. La somma dei due lanci è pari.

    Si può notare che insieme tutti non possono avvenire, ma se li prendo a due a due sono indipendenti, questo è molto curioso come fenomeno!


Infatti deve essere che valga la proprietà di sopra per **ogni singolo sottoinsieme**. È una cosa molto importante!

**Caso speciale**

Nel caso in cui $$P(A) = 0$$ , oppure vale l’altro, oppure basta che siano  $$P(A \cap B) = 0$$ ossia siano disgiunti allora secondo la definizione sono indipendenti, anche se logicamente dovrebbero essere dipendenti, dato che uno implica l'esclusione dell’altro.

### Th Indipendenza e complementari 🟨

<img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 5.png" alt="Probabilità condizionata e indipendenza/Untitled 5">

- Dimostrazione

    <img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 6.png" alt="Probabilità condizionata e indipendenza/Untitled 6">

    <img src="/images/notes/Probabilità condizionata e indipendenza/Untitled 7.png" alt="Probabilità condizionata e indipendenza/Untitled 7">

- Dubbio vecchio

    La dimostrazione è un po`strana, per quale motivo per (ii) → (i) è necessario utilizzare l'induzione? Perché voglio dimostrarlo per ogni modo in cui posso scegliere un sottoinsieme! È molto interessante come con il secondo riesco a dimostrare il tutto.

    **Risposta**:

    hai capito male la definizione di indipendenza, affinché sia indipendente, deve essere che lo siano tutti i sottoinsiemi di eventi! Quindi ciò rende la dimostrazioen molto più contorta.




# References