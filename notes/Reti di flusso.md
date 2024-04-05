---
layout: page
permalink: notes/reti-di-flusso
tags: en
title: Reti di flusso
---

Ripasso Prox: 23
Ripasso: January 3, 2023
Ultima modifica: December 25, 2022 10:21 AM
Primo Abbozzo: October 21, 2022 10:04 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Reti di flusso

Questi problemi sono una **sottoclasse della programamzione lineare** con variabili reali. (Alcuni riescono a riconoscere se un problema è in questa forma, e lo risolvono in modo istantaneo se questo succede).

Un problema dei router è un classico problema di flusso, che si risolvono con questi algoritmi polinomiali

## Note introduttive

### Rete, terminologia 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled.png" alt="image/universita/ex-notion/Reti di flusso/Untitled">


Lo sai [Grafi](/notes/grafi). ma andiamo a ripeterlo

- Grafo def
- Def arco e il loro peso (**discreto o continuo**)
- Nodi

**Cose nuove:**

**Sbilanciamento**, mi da informazione riguardo se il nodo vuole ricevere o dare fuori, quindi il fatto che sia negativo   positivo può essere buona roba.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 1.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 1">


Importante sapere cosa sono **nodo di input, output e trasferimento** e quando un nodo si può chiare in questo modo.

Oltre a ciò possiamo definire **capacità inferiore e superiore** degli archi, e definire unconcetto di **ammissibilità** di un trasferimento di un arco quando la quantità che ci passa rispetta queste condizioni.

### Vincoli di un problema di flusso (3) 🟨+

1. **Domanda e offerta globale**
2. **Conservazione del flusso** sol nodo locale
3. **Amissimiblità del flusso**
- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 2.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 2">


Il perché si utilizzano grafi è perché sono **espressivi** per questo genere di problemi, ossia sono molto utili per modellizzare questo. E hanno una complessità gestibile perché sono stati molto studiati ed **esistono algoritmi efficienti per questa**(credo)

### Normalizzazione della capacità inferiore (3) 🟩-

Si tratta in questa parte di trasformare il problema in un altro problema con le capacità inferiori nulle, basta considerare questa cosa nel calcolo della funzione obiettivo e rimodulare i valori degli archi (per capacità superiore).

Le 3 cose per normalizzare

1. Togliere l a capacità superiore
2. Aggiungere l a b (così flusso si conserva
3. Considerare il costo di questo flusso

Cioè semplifico mettendo quanto deve passare per la capacità inferiore come flusso proveniente dall'esterno!

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 3.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 3">


### Modelizzazione del flusso di costo minimo (!!!) (3) 🟨-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 4.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 4">


Come si può notare la condizione è molto facile da scrivere.

1. Minimizzare il costo $$cx$$, con x il vettore dei flussi, c il vettore dei costi
2. Condizione di massimo flusso $$\forall i, 0\leq x_i \leq u_i$$, con u il vettore dei massimi
3. E tutte le condizioni di bilanciamento $$Ex = b$$ con E la matrice (probabilmente sparsa) che mi calcola l’incidenza (0, 1, -1 per dire esiste, entrata o uscita), che devono essere uguali a b.

**Condizione dei pozzi** 🟩

Spesso è molto buono idealizzare con un solo pozzo di entrata e un solo pozzo di uscita. Al fine di avere questo risultato si creano due pozzi aggiuntivi , uno che prende tutte le entrate e una che prende tutte le uscite

- Slide costruzione dei pozzi e sorgenti

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 5.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 5">


**Condizione limiti di nodo🟨—**

Per modellizzare cose come i router, che sono sì dei nodi, ma hanno dei limiti per trasmettere e ricevere creiamo un nodo fittizio che sia in grado di rappresentare questo genere di occazioni

- slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 6.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 6">


## Problema del flusso massimo

### Caratteristiche flusso max (3) 🟩

- Slide definizione del problema

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 7.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 8.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 9.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 9">


Da notare che questo problema può essere visto come **caso particolare di MCF** in cui

1. Costi sono nulli
2. Sbilanciamenti sono nulli
3. Presenza di arco fittizio con capacità infinita da target a source

## Tagli

### Definizione 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 10.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 10">


In pratica è una **partizione** dei nodi di una rete.

Un **s-t taglio**è un taglio in cui s e t stanno in partizioni differenti (dato che sono due le partizioni direi che stanno nelle due partizioni corrispondenti).

Andiamo ora a **caratterizzare gli archi**.

**A+** attraversa da s a t

**A-** attraversa da t a s.

- Esempio di Taglio

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 11.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 11">

    I rossi sono A+, i verdi sono A-

- Esempio del prof più contorto

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 12.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 12">


### Proprietà !! (2) 🟩

<img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 13.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 13">

Ossia il **flusso è uguale a ciò che attraversa il taglio**, e tutto questo è sempre minore alla capacità del taglio!

- Dimostrazione

    Per 1 in pratica prende la differenza iniziale e riscrive i nodi di trasferimento (quindi input - output = 0) in altro modo per averlo nella forma che ci piace).
    Gli archi interni si cancellano fra di loro, gli archi esterni in Nt non vengono proprio contati, quindi possiamo andare a considerare solamente gli archi della frontiera quindi andiamo a finire in questo modo.

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 14.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 14">

- Dimo Slides

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 15.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 15">


### Flusso e capacità del taglio 🟩

Le proprietà dei tagli spiegati in precedenza sono dei punti fondamentali per l’analisi di questo problema di flusso!.

> **Il valore di un flusso ammissibile è sempre minore o uguale della capacità di qualunque taglio**.
>

Andremo a cercare un caso in cui **il flusso = capacità**. In quanto trovato questo taglio, questo è un flusso massimo! Per il lemma precedente non può crescere ancora.

## Ford Fulkerson

Andremo in questa parte ad introdurre alcuni concetti molto utili che ci porteranno alla definizione dell’algoritmo di Ford Fulkelson.

### Grafi residui 🟩

Utile per dirmi se possono ancora migliorare o meno in un arco.

Quindi ci dà un concetto di **flusso rimanente** per un arco (termine mio questo) utilizzato per decidere se possiamo utilizzarlo o meno per migliorare qualcosa.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 16.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 16">


### Cammini aumentanti 🟩

Chiachiamo in questo modo i cammini nel grafo dei residui. Lo chiamiamo in questo modo perché ci permette di avere più flusso da s a t. In particolare lo utilizzo in questo modo

1. Se è un arco discorde diminuisco il valore del flusso.
2. Se è un arco concorde aumento il flusso.

Il valore di aumento o diminuzione è il minimo del residuo fra tutti gli archi, questa cosa la chiamiamo **capacità** del cammino aumentante.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 17.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 17">


### L’algoritmo 🟩

L’algoritmo si traduce nel

1. Setta flusso iniziale a 0
2. Prendi un cammino aumentante a caso, se esiste aggiungi al flusso il valore di cui è aumentato, altrimenti ritorna il flusso.
3. Continua finché non esci.
- Slide

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 18.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 18">


### Correttezza 🟨

Per dimostrare la correttezza è spesso molto bello trovare l’invariante, in questo caso è il seguente lemma

> Se x è un flusso ammissibile, allora è ammissibile anche il flusso modificato con una iterazione dell’algoritmo.
Se ho il flusso massimo, allora non posso trovare cammini aumentanti o flussi altri.
>
- Slide lemmi su flusso massimo e ammissibilità, con cammini aumentanti

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 19.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 19">


- Lemma fondamentale per correttezza, esistenza di taglio v

    NOTA: raggiungibili con un **cammino aumentante!**

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 20.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 20">

- Intera dimostrazione insieme

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 21.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 21">


### Complessità 🟨+

Possiamo dire che ha fine solo se ha **capacità intere**, altrimenti potrebbe essere che non termini mai. Il prof dice che questo algo dà troppa libertà per cui la complessità non è sotto controllo.

- Teorema e dimostrazione complessità casi interi

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 22.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 22">


Ma questa è una complessità **pseudopolinomiale** nel senso che è polinomiale solo se non si utilizza la compressione logaritmica nella rappresentazione degli interi (quindi polinomiale nel tempo, ma non nella rappresentazione in memoria).

Ma comunque il termine U ci è abbastanza brutto.

### Max Flow Min Cut (!) 🟩

Se riusciamo a dimostrare che il massimo flusso è ≥ di un taglio allora mettendo insieme al lemma sul upper bound del massimo flusso ho finito.

Utilizziamo il risultato nella dimostrazione di FF, assumento che abbiamo un flusso massimo, quindi non ci sono cammini aumentanti, allora abbiamo un taglio di capacità v, per cui ho finito.

- Enunciato e dimo

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 23.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 23">


## Edmonds Karp

### Introduzione 🟩

Questo algoritmo non è altro che una implementazione di Ford_fulkerson. Quindi **sappiamo già che sia corretta**. Utilizza una bfs per trovare il cammino aumentante migliore.

Utilizzando la bfs, quindi scegliemo sempre il percorso più corto questa è una delle proprietà di maggior rilievo per EK.

### Lemma distanze di EK (non chiede dim) 🟨—

Questo è un lemma che caratterizza fortemente EK, perché è una conseguenza della sua ricerca in BFS che trova gli archi critici più corti prima di quelli più lunghi.

È anche fondamentale per fare il calcolo della complessità dell'algoritmo!

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 24.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 24">

- Dimostrazione (non fatta in classe) preso dal cormen

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 25.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 25">

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 26.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 26">


### Complessità (!!) 🟨+

Il lemma di sopra ci permette di togliere il termine sulla capacità degli archi.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 27.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 27">


Il motivo è che per il lemma precedente ogni arco può essere considerato al più |N| volte, con N il numero dei nodi. Quindi Applico BFS, per ogni arco, al più N volte, costo $$O(NM^2)$$

- Hint dimostrazione

    Andiamo a considerare gli archi che vengono saturati durante il percorso di un cammino aumentante (questo esiste sempre perché il cammino aumentante è costruito sul minimo del percorso.

    Vogliamo dire che ogni arco può essere al massimo considerato critico N volte, per cui al massimo ho NA.

    Dopo aver fatto questa osservazione, bisogna andare a fare un ragionamento sulla distanza, che continua a crescere per ogni iterazione, e lo può fare per al massimo il numero di nodi, prima di diventare staccato.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 28.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 28">

    <img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 29.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 29">


## Goldberg-Tarjan

- Slide algoritmo

    !<img src="/images/notes/image/universita/ex-notion/Reti di flusso/Untitled 30.png" alt="image/universita/ex-notion/Reti di flusso/Untitled 30">