---
layout: page
permalink: notes/algebra-modulare
tags: italian
title: Algebra modulare
---

Ripasso Prox: 5
Ripasso: May 26, 2022
Ultima modifica: October 19, 2022 5:02 PM
Primo Abbozzo: May 3, 2022 9:26 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 7 Algebra modulare

## 7.1 Assunzioni

Andiamo ora ad assumere  l'esistenza e correttezza di alcune cose di base.

**Teorema fondamentale dell'algebra**

Ogni numero intero si fattorizza in modo unico.

**Algoritmo di divisione**

Se ho a, b negli interi, allora esistono resto e dividendo.

**mcd e divisibilità**

Se a | d e sono interi allora esiste esiste c tale per cui d = ca. (tutti interi senza restrizioni)

mcd fra interi a e b è il più grande intero che divide sia a sia b.

Osservazione: mcd(a, 0) = a

**Teorema di Bezout**

che dice che esistono r ed s tali che per ogni 2 interi a,b ho che ar + sb = gdc(a,b);

E da questo possiamo andare a fare algoritmo di euclide esteso.

## 7.2 Classi di resto modulo n

Si dicono che $$a \equiv b \mod n \iff n | a - b$$

SI indica con $$[a]_n = \{ b \in \Z :b \equiv a \mod n\} =$$  elementi la cui differenza con a è divisibile per n

E indichiamo con $$\Z_n$$ come l'insieme di tutte le classi di quivalenza ossia $$\{[[a]_n : a \in \Z\}$$ ossia **insieme quoziente**, [Relazioni fra insiemi]].

### 7.2.1 Dimostrazione classe di equivalenza

**Riflessività**

si ha che $$n | a- a \iff n | 0$$ che è vero

**Simmetrica**

se $$a \equiv b \iff b \equiv a$$ in quanto se $$a \equiv b \iff n | a - b \iff n | b - a \iff b \equiv a$$ (cioè basta moltiplicare per qualcosa di negativo, si ha lo stesso risultato

**Transitiva, mi sono rotto**

Allora sappiamo di avere una classe di equivalenza (una partizione su Z in pratica).

### 7.2.2 Prop equivalenza con resto  (!!!)

Sia $$a\in \Z$$ e r il suo resto di divisione per n, allora $$a \equiv r \mod n$$ ossia appartengono alla stessa classe di equivalenza

### 7.2.3 Prop costituzione dell'insieme quoziente (!!!)

Per la proposizione precedente posso trovare proprio come è costituito

$$Z_n = \{[0]_n, [1]_n...,[n-1]_n\}$$

- Dim

    dimostrare che $$\impliedby$$ ossia destra è contenuto in sinistra è ovvio per definizione di Zn, per dimostrare che $$\implies$$si utilizza la proposizione sopra:

    Sia $$[a]_n \in \Z_n$$ per proposizione sopra si ha che $$[a]_n = [r]_n \in \{[0]_n,...,[n - 1]_n\}$$

    Per concludere (se voglio dimostrare nel modo classico utilizzando classe di equivalenza) devo dimostrare che tutte le classi presenti in Zn sono effettivamente distinte.

    Prendo $$i,j \in [0...n-1]$$ wlog $$i > j$$ allora $$0 < i - j \leq i \leq n- 1$$ allora $$n \not | i-j,$$  quindi si ha che $$i \not\equiv j \mod n$$ e questo conclude che Zn ha n elementi


### 7.2.4 Somma e prodotto in questa classe

La definizione di classe modulo resto in questo modo è molto simile alla classica definizione di somma e prodotto (ma non per la divisione, non è sempre invertibile).

E si dimostrano anche

1. Commutatività
2. Associatività
3. Distributività (entrambe, destro e sinistra)
4. C'è il neutro per la somma

### 7.2.5 Prop. invertibilità di una classe (!!!)

Si dice che $$[a]_n \in \Z_n$$ è invertibile se esiste $$[b]_n \in \Z_n : [a][b] = [1]$$ (sottinteso indici)

Si dimostra che è invertibile se solo se è coprimo col modulo poi( perché con euclide esteso riesco a trovarmi l'inversa).

### 7.2.6 Prop. unica soluzione diofantea (!!)

È un corollario della precedente, praticamente dice che se  ax = b, e gcd(a, n) è 1 allora esiste una unica soluzione.

# 8 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
un corollario della precedente, praticamente dice che se  ax = b, e gcd(a, n) è 1 allora esiste una unica soluzione.