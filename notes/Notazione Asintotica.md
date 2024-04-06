---
layout: page
permalink: notes/notazione-asintotica
tags: en
title: Notazione Asintotica
---

Ripasso Prox: 31
Ripasso: May 28, 2022
Ultima modifica: April 28, 2022 5:07 PM
Primo Abbozzo: February 24, 2022 9:19 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Notazione asintotica

## Introduzione alla notazione asintotica

Cercare di definire il tempo impiegato da una funzione per essere eseguita **in termini di DIMENSIONE dell'input**. **(il numero di bit a livello basso basso)

Ma abbiamo il problema di misura, in quanto dobbiamo considerare delle variabili che siano indipendenti rispetto alla macchina.

### Caratteristiche della notazione

Vogliamo considerare una notazione asintotica (che guarda quanto fa il comportamento verso l'infinito)

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled">

### Funzione di costo

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled 1.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled 1">

## Modelli asintotici
Abbiamo trattato di o-piccolo e ogrande in [Analisi](/notes/hopital,-taylor,-peano#o-piccolo-di-funzione).****

### O-grande

Prendiamo due funzioni $$f, g : \mathbb{N} \to \mathbb{R}^{+}$$ allora definiamo $$f(x) = O(g(x))$$ se esiste un $$n_{0} \in \mathbb{N}$$  e un $$c$$ tale che per cui per ogni $$n > n_{0}$$ si ha che 

$$
f(n) \leq c g(n)
$$

Ossia: la funzione è **upper-bounded** per numeri molto grandi.
Quando vale la versione stretta si può dire che è anche o-piccolo.

Note interessanti che notazioni come

$$
n^{c}, 2^{O(\log n)}, n^{O(1)}
$$

Sono **equivalenti**.
### o-piccolo
Usiamo la definizione trattata in Analisi:
<img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 13.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 13">

### Theta

### Omega-grande

### omega-piccolo

## Costo e Complessità computazionale

### Definizioni

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled 2.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled 2">

## Analisi ammortizzata

### Introduzione

Questa è una tecnica che trova il **costo medio** di un algoritmo. La differenza con il calcolo del costo medio classico è che questo calcolo mi trova il costo medio per una *sequenza di operazioni* mentre il classico mi trova il costo medio per una singola operazione

### Casi di utilizzo

Di solito è utile utilizzare questo metodo di analisi in queste condizioni

1. Caso pessimo non frequente (quindi per dire che nella media un algoritmo è molto più efficiente)
2. Semplificare l'analisi del caso medio

### Aggregazione

Vogliamo cercare un limite superiore su n operazioni, poi dividere il tutto per n.

Questo è più utile quando il costo **totale è conosciuto**

### Accantonamenti

Questo è basato sulla contabilità, ho un certo credito iniziale, posso utilizzare tutto, ma non posso mai andare in negativo.

Questo è utile quando **ci sono diverse operazioni**.

Un esempio di analisi ammortizzata utilizzando gli accantonamenti è la doubling and halving in cui 3 monete per ogni operazione di inserimento bastano poi per ricopiare ed espandere o diminuire il tutto a piacere (quindi 3n , si ha un costo costante).
menti è la doubling and halving in cui 3 monete per ogni operazione di inserimento bastano poi per ricopiare ed espandere o diminuire il tutto a piacere (quindi 3n , si ha un costo costante).

# Registro Ripassi

|            |                                   |
| ---------- | --------------------------------- |
| 14/03/2024 | Ripassato per [Time Complexity](/notes/time-complexity) |

# References