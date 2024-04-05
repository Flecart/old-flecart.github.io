---
layout: page
permalink: notes/tarjan-e-mcmf
tags: en
title: Tarjan e MCMF
---

Ripasso Prox: 12
Ripasso: January 5, 2023
Ultima modifica: December 27, 2022 4:55 PM
Primo Abbozzo: November 14, 2022 9:19 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Algo di grafi

Questa sezione la tengo separata rispetto agli altri per favorire lo studio, così questa roba nuova la ripasso più spesso, in seguito si può accorpare.

## Goldberg Tarjan/Push-relabel

Questo algoritmo è importante perché introduce ragionamenti sul **minimo locale** che possa alla fine essere ricomposto come soluzione globale.

[Questa lezione youtube](https://www.youtube.com/watch?v=0hI89H39USg) lo spiega da Dio

### Preflusso 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled">


La parte nuova di questa cosa è che i vincoli di bilanciamento possono diventare una disuguaglianza. (cioè quello che arriva è di più rispetto quanto va fuori.

Andiamo inoltre a definire un concetto di **attività** del nodo, ossia il fatto o meno che abbia un eccesso di flusso in entrata (e che quindi io abbia cose da mandare fuori ancora).

### Push forward e backward 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 1.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 1">


Vogliamo utilizzare un algoritmo locale che sposti il flusso in avanti oppure all’indietro, questi sono gli unici modi per spostare flussi in giro.

### Pseudocodice 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 2.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 2">


Si noti che è presente un **sistema di etichettatura** utilizzato per tenere sotto controllo il costo

**NOTA ERRORE:** Devono tornare a 5 invece che a 6

### L’etichettatura 🟩-

L’etichettatura per questo algoritmo è fondamentale. Lo utilizziamo principalmente per evitare che ci siano push che poi vadano a ciclo, cosa molto brutta dato che non finirebbe mai l’algoritmo.

Si fa una etichettatura iniziale in questo modo:

1. Sparo al massimo tutti gli archi che partono da S.
2. Metto N l’altezza di S, e 0 tutto il resto.

In questo modo vengono **soddisfatte queste** INVARIANTI:

1. il Label per S è sempre N
2. il label per L è sempre 0
3. Esiste un arco nel grafo residuo fra v, w solo se $$h(v) \leq h(w) + 1$$

Noi vorremmo pushare solamente se ho una relazione del tipo $$h(v) = h(w) + 1$$, ossia esattamente più alto di 1.

### Analisi del costo 🟩+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 3.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 3">


Sul perché  sia vero non lo presenta, bisogna fare un approfondimento a riguardo.

Se si sceglie il nodo di altezza massima si avrà alla fine un costo di $$O(N^3)$$.

## Flusso di costo minimo

algoritmi simili a ford fulkelson non sono molto buoni per trovare la migliore soluzione per questo, vorremmo andare a cercare il pseudoflusso del costo minimo!

### Pseudoflusso 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 4.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 4">


Intuitivamente sto prendendo qualunque flusso che soddisfi i vincoli di capacità, ma che non è sufficiente per soddisfare i vincoli di bilanciamento sui nodi.

### **Nodi di eccesso e difetto e sbilanciamento compressivo** 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 5.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 5">


Con la nozione di pseudoflusso è utile fare questa differenza.

$$O_x$$ i nodi con **eccesso di flusso** quindi $$e$$ positivo, ciò che entra è di più

$$D_x$$ il contrario. ciò che esce è di più.

Questi sono molto importanti, perché vorremmo far partire ed arrivare flusso dai nodi O ai nodi D, in modo da renderli bilanciati. E poi vorremmo avere il **percorso di costo minimo**.

### Cammini aumentanti 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 6.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 6">


In sta parte viene esteso il concetto di cammino aumentante introdotto in precedenza per introdurre il costo di un cammino aumentante.

Una cosa in più è che si può partizionare l’insieme degli archi nel cammino. Questa cosa sarà utile per calcolare il costo

### Costo dei cammini aumentanti 🟩

- Slide calcolo costo cammino aumentante

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 7.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 7">


Questo è un concetto nuovo rispetto a quello passato perché prima non si faceva caso ai costi, invece ora sì.

### Th struttura equivalenza dei pseudoflussi (!!) 🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 8.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 8">

- Nota, inizio e fine dei cammini

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 9.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 9">


È un teorema molto forte, dati due pseudoflussi qualunque, possiamo legare questi due con un numero di cammini aumentanti!

La dimostrazione non si fa 😀.

- Dimostrazione in dispensa

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 10.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 10">

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 11.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 11">


### Th struttura del pseudoflusso minimo (!) 🟩-

- Enunciato e dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 12.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 12">

- Hint per ←

    Consideriamo il nostro pseudoflusso, per ipotesi non è minimale, allora esiste un altro pseudoflusso di costo minore con gli stessi vettori di sbilanciamento, allora per il teorema precedente può essere applicato, posso trasformare uno nell’altro.

    La parte difficile da qui è trovare il ciclo con costo negativo. Per sapere questo bisogna fare un pò meglio il teorema precedente, infatti si può dire che tutti i percorsi sono dei cicli!


Quindi il pseudoflusso di costo minimo è strettamente legato all'esistenza di cicli aumentanti di costo negativo!. Quindi vogliamo andare a togliere questi cicli, se riesco a togliergli tutti allora possono trovare il pseudoflusso minimale.

**NOTA:** si ricordi che gli pseudoflussi si possono confrontare fra di solo solo se hanno gli stessi sbilanciamenti!.

### Th pseudoflusso minimo con aggiornamenti (!!!) 🟩

- Enunciato e dimo

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 13.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 13">

- hint a dimostrazione

    Dobbiamo prendere il cammino aumentante di costo minimo e poi anche il flusso di costo minimo! Questi due sono gli ingredienti fondamentali per questo teorema qui.

    E sì tal cred, sta roba è nell'enunciato

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 14.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 14">

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 15.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 15">


Come mai quella relazione riguardo i theta? Perché altrimenti avrei che lo sbilanciamento fra start-finish sarebbe diverso.

Questo è il teorema principale che ci garantisce l’invariante! Riusciamo a mantenere lo pseudoflusso di costo minimo in seguito alle operazioni di update con i cammini aumentanti!

Quindi si può costruire un algoritmo che utilizza questa proprietà

1. Trova un pseudoflusso minimo fra tutti quelli con lo stesso vettore di sbilanciamento
2. Aggirona finché c'è cammino aumentante
3. Quando non posso più aggiornare ho finito, ho il pseudoflusso di costo minimo, e di flusso massimo.

## Algoritmo cammini minimi successivi

### Pseudocodice algo 🟩—

<img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 16.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 16">

Per avere uno pseudoflusso minimale basta non avere cicli di costo negativo, vedremo fra poco come far ciò.

Da notare che ora l’aggiornamento tengo conto anche del minimo fra inizio e arrivo! Ricordo che il mio obiettivo è risolvere gli sbilanciamenti

### Correttezza e terminazione 🟩—

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 17.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 17">


Quindi se termina allora è corretto per i teoremi precedenti. Riguardo la terminazione riesco a fare ragionamenti sulla capacità del flusso, che posso dire che è sempre intero, e diminuisci almeno di uno, quindi se andiamo a fare un bound sullo sbilanciamento iniziale riusciamo a fare una stima sul numero di iterazioni necessarie per finire.

### Complessità 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 18.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 18">


Questo dipende fortemente dipende dallo sbilanciamento iniziale e dal tempo per trovare il cammino minimo (eg. bellman ford).

## Algoritmo eliminazione cicli negativi

Questo è un altro algoritmo utilizzato per trovare il flusso minore, l'obiettivo è trovare un qualunque flusso ammissibile, e poi togliere tutti i cicli negativi che trovo, in questo modo so per teorema precedente che il flusso che ho trovato è il minore possibile.

Se non sbaglio questo algoritmo è acnhe chiamato **algoritmo del ciclo di klein** e ha complessità pseudopolinomiale di $$O(m^2nCU)$$ dove C è la capacità massima e U il costo massimo. Il ragionamento per questa complessità è che mi costa mn per  Bellman ford per trovare il ciclo, e lo faccio diminuendo al massimo mCU volte (che è il lower bound per il costo minimo).

### Costruzione flusso ammissibile 🟩

Vogliamo costruire un qualunque flusso ammissibile, e vogliamo cambiarlo in modo che essa abbia anche il costo minimo.

1. **Risolvere il problema di maximum flux**, in questo modo ho un flusso ammissibile di flusso massimo
2. Poi vado a cercare i cicli negativi, questi non cambiano nessun bilanciamento, e abbassano solamente il costo. So che il minimo costo sarà quello che non avrà cicli di costo negativo.

In questo modo Ho trovato la migliore soluzione.

### Pseudocodice 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 19.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 19">


### Analisi del costo e correttezza 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Tarjan e MCMF/Untitled 20.png" alt="image/universita/ex-notion/Tarjan e MCMF/Untitled 20">


il bound per il numero di iterazioni è molto banale, in pratica vado a considerare il massimo costo possibile, so che almeno diminuisce di 1 ad ogni iterazione, più un costo di bellman ford per trovare i cicli. costo:


$$
O(NA) \cdot O(Auc) = O(NA^2uc)
$$