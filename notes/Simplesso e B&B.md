---
layout: page
permalink: notes/simplesso-e-b&b
tags: italian
title: Simplesso e B&B
---

Ripasso Prox: 3
Ripasso: December 28, 2022
Ultima modifica: December 27, 2022 5:07 PM
Primo Abbozzo: December 5, 2022 10:02 AM
Stato: 🌕🌕🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# Simplesso e branch n bound

## Algoritmo del simplesso

### Ricerca della direzione migliore

### Ricerca dello step

### Pseudocodice

- Slide

    B sono gli indici di partenza, poi questi vengono aggiornati

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled">

    In riga 5 vado a checkare se ho **direzioni di crescita possibili**, se è tutto positivo non ne ho.

    in riga 6, si sceglie il più piccol per **evitare loop**.


L'idea in generale va in questo modo

1. Cerco di trovare il duale e confrontarlo con la x attuale
    1. Se sono uguali, allora ho trovato l’ottimo ed esco
2. Altrimenti cerco una direzione di crescita che sia anche ammissibile
3. Continuo fino a trovare un vertice, se ho il vertice allora mi muovo lì e riapplico,
altrimenti è illimitata, se non esiste un vertice.

### Correttezza

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 1.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 2.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 3.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 4.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 4">


 **

**Invarianti (3)**

queste invarianti vengono mantenute per tutto il corso dell'algoritmo

**La scelta della direzione di crescita**

<img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 5.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 5">

NOTA: il vettore $$u_h$$ è un versore utilizzato per selezionare la direzione che ci interessa (quindi 0 in tutto e 1 nella parte che ci interessa!).

La parte in cui dobbiamo stare attenti nella scelta della direzione di crescità è restare nella zona delle soluzioni ammissibili.

### Complessità

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 6.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 6">


Fare una analisi in modo rigoroso non riusciamo a farlo, più o meno ora restiamo con l'intuizione che **al massimo ogni singolo vertice è visitato una volta** quindi teniamo il bound su questo.

si tratterebbe quindi di prendere fra tutti gli $$m$$ restrizioni possibili, dobbiamo andare a prendere $$n$$ elementi, con questo il numero di variabili.

quindi $$m \choose n$$.

Nella pratica è **molto veloce** poi ha un runtime nel costo medio polinomiale, ma per fare questa analisi abbiamo bisogno di altri strumenti, molto avanzati.

## Branch and bound

non si può applicare l'algoritmo del simplesso per vincoli interi, questo sembra quasi paradossale ma è così. il motivo è che il simplesso gira sui vertici delle rette, cosa che non può essere intera, e non abbiamo un modo banale per trovare la parte intera più vicina!.

### Intuizione

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 7.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 7">


Proviamo a **rilassare il problema** chiedendo che anche i vincoli non interi siano buoni. Spesso questa cosa non è buona, quindi utilizziamo una **partition** per andare a ritrovare una cosa intera.

In pratica, cerco la soluzione non intera utilizzando Simplesso o altri algoritmi che mi diano dei risultati boni. Poi se è intera ritorno, altrimenti aggiungo due vincoli interi, creandomi due sottoproblemi, e me li vado ad esplorare in questo modo…

### Pseudocodice

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 8.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 8">


Si basa sull’applicare in modo continuo un algoritmo per la risoluzione della programmazione lineare non intera, e cercare con una sorta di divide e conquer una soluzione che sia intera.

### Correttezza

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 9.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 9">


### Complessità

- Slide

    <img src="/images/notes/image/universita/ex-notion/Simplesso e B&B/Untitled 10.png" alt="image/universita/ex-notion/Simplesso e B&B/Untitled 10">


Esponenziale, bisogna andare ad utilizzare il simplesso come subroutine molte volte, anche se magari si può velocizzare di molto come subroutine, resta comunque almeno della complessità del simplesso.

# Registro ripassi

| 27/12 |  |
| --- | --- |
|  |  |
|  |  |
te volte, anche se magari si può velocizzare di molto come subroutine, resta comunque almeno della complessità del simplesso.

# Registro ripassi

| 27/12 |  |
| --- | --- |
|  |  |
|  |  |