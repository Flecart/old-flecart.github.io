---
layout: page
permalink: notes/object-orientation
tags: italian
title: Object orientation
---

Ripasso Prox: 10
Ripasso: May 29, 2023
Ultima modifica: May 19, 2023 10:33 AM
Primo Abbozzo: May 8, 2023 9:20 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Object orientation

## il tipo di dato astratto

### Introduzione

Per questi tipi di dato non ci interessa di sapere cosa ci sia sotto (storato come bit? storato come sabbia boh), ci interessa solamente che abbia quei metodi, che possiamo in un certo senso identificare come la sua capsula, **opaca** in questo caso.

Quando si può andare a modificare solamente attraverso questo metodo potrei dire che sia **safe** collegato alla [Algebra dei tipi](/notes/algebra-dei-tipi), nel senso che vengono soddisfatte sempre le proprietà del tipo.

### Costituenti del ADT (4) (abstract data structure) 🟨

- Slide ADT

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled.png" alt="image/universita/ex-notion/Object orientation/Untitled">


Ci sono principalmente 4 elementi:

1. Il nome del tipo di dato astratto
2. Il dato concreto che sta sotto (ad esempio intero
3. Operazioni di creazione ed accesso (che in un certo senso sono simili ai meccanismi di [Architettura software dell’OS](/notes/architettura-software-dell’os))
4. **confine di astrazione** che sono come le interfaccie, o politiche? In pratica credo siano equivlaenti alle cose pubbliche di questa, mentre il punto 3 racchiude anche quelle private.

### Information hiding 🟩

- Slide information hiding

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 1.png" alt="image/universita/ex-notion/Object orientation/Untitled 1">


Il fatto che vogliamo cercare di andare ad operare e prendere da questo tipo di dato astratto solamente attraverso delle interfacce. Per questo motivo si può dire che stiamo nascondendo cosa c'è dentro a quella classe.

Sotto questo punto di vista, si dice spesso che la classe è come **contratto con la superficie**, perché va a soddisfare certe proprietà con chi la utilizza.

Il fatto che l'implementazione effettiva viene nascosta, aiuta alla **modularità**. Non posso fare assunzioni sull’implementazione effettiva, mi basta che le proprietà dell’interfaccia siano rispettate.

Un altro aspetto è che è facile organizzare progetto in moduli a seconda di cosa stiamo rappresentando (prova a tenerti in mente la classica organizzazione in un file per una classe che si fa spesso in java).

### Indipendenza della rappresentanza 🟩

Andiamo ora ad introdurre il concetto di indipendenza della rappresentanza (ossia il fatto che non ci interessa questo tipo di dato astratto da quale tipo concreto è rappresentato), un fatto che la caratteristica dell’information hiding ci ha permesso di avere:

- Slide indipendenza

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 2.png" alt="image/universita/ex-notion/Object orientation/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 3.png" alt="image/universita/ex-notion/Object orientation/Untitled 3">


> implementazioni corrette (ben tipate) dello stesso ADT sono osservabilmente indistinguibili dai
consumatori dell’ADT.
>

### Tipi esistenziali 🟩

Questi sono quasi l'opposto dei tipi di polimorfismo universale parametrico in [Polimorfismo](/notes/polimorfismo), praticamente è un exist invece che un forall, che carina questa relazione.

Si potrebbe vedere come **la rappresentazione di ADT attraverso teoria dei tipi**.

- Slide tipi esistenziali

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 4.png" alt="image/universita/ex-notion/Object orientation/Untitled 4">


Quando vado a definire un tipo che soddisfa quella caratteristiche non starei facendo altro che risolvendo il tipo esistenziale da un punto di vista di teoria dei tipi.

- Esempio risoluzione di tipi esistenziali

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 5.png" alt="image/universita/ex-notion/Object orientation/Untitled 5">


### Oggetti esistenziali 🟩

- Slide problema tipi  esistenziali

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 6.png" alt="image/universita/ex-notion/Object orientation/Untitled 6">

- Slide oggetti esistenziali

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 7.png" alt="image/universita/ex-notion/Object orientation/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 8.png" alt="image/universita/ex-notion/Object orientation/Untitled 8">


Gli oggetti esistenziali mantengono l'astrazione del tipo esistenziale, a differenza delle ADT che vanno ad eliminare l’esiste e quindi diventano inoperabili fra di loro, tenendo l’astrazione possiamo andare a **cooperare fra istanziazioni diverse** di questo oggetto esistenziale. (si porta avanti l'interfaccia senza andarlo a risolvere come per ADT)

Una altra differenza è che oggetti fanno una differenza fra stati e metodi, mentre il tipo di dato astratto tiene solamente operazioni e il tipo sotto di esso.

- Slide confronto oggetti esistenziali con abstract data types

    <img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 9.png" alt="image/universita/ex-notion/Object orientation/Untitled 9">


In breve ADT sono aperti, mentre oggetti sono chiusi e quest'ultimo fatto permette di utilizzare tipi con istanziazione anche diversa fra di loro.

> una differenza rilevante degli oggetti rispetto agli ADT è che, poiché
ogni oggetto ha la propria rappresentazione interna e implementa le proprie
operazioni, un programma può liberamente mescolare implementazioni
diverse dello stesso tipo di oggetto (esistenziale).
>

## Classi e oggetti

### Def oggetto 🟩

> Oggetto: una **capsula** che contiene sia **dati** che **operazioni** per manipolarli e che fornisce **un'interfaccia**
al mondo esterno attraverso la quale è possibile accedervi.
>

Le operazioni sono anche chiamate **metodi**. mentre i dati sono chiamati **campi**  dell'oggetto.

### Def classe 🟩

> Una classe è un **modello** per un insieme di oggetti: stabilisce quali sono i loro **dati** (quanti, di che tipo, con quale visibilità) e fissa il **nome**, la **segnatura**, la **visibilità** e **l'implementazione** dei suoi metodi
>

In modo più intuitivo potremmo andare a dire:

> classe:
Specifica un canovaccio o un **modello di implementazione di**
riferimento che contiene le variabili e i metodi comuni alla stessa classe (da
cui il nome) di oggetti.
>

### Implementazione delle classi (2)🟩

La definizione dei metodi della classe è **unica**, sono solamente i campi di dati che sono diversi per ogni istanziazione. Come fanno ogni istanziazione ad accedere al metodo corretto allora? Puntatore all'unica istanziazione! L'immagine sotto può chiarificare questo concetto:

<img src="/images/notes/image/universita/ex-notion/Object orientation/Untitled 10.png" alt="image/universita/ex-notion/Object orientation/Untitled 10">

dall’altra parte quando dall'implementazione mi vado a riferire a this, questo deve derefernziarwsi sulla corretta istanziazione dell’oggetto!

Lo storage, come al solito, può essere sia a stack sia sulla heap, a seconda dell’implementazione del linguaggio.

Principalmente credo che le osservazioni principali siano due:

1. Dereferenziare correttamente il this
2. Sapere accedere alle funzioni definite nella classe

### Prototipi e confronto con classi 🟨

Questi sono un pattern che piace tanto a [Javascript](/notes/javascript).

si basa sulla possibilità che gli oggetti deleghino parti della loro implementazione ad altri oggetti.

Creazione ora si può fare in due modi, uno il classico è new, l'altro è **ex-nihilo** andando a definire passo passo tutto (in modo direi estensionale, andando a ricollegarmi con [Teoria dei Tipi](/notes/teoria-dei-tipi))

la differenza principale dei prototipi con le classi è la **flessibilità vs sicurezza** dato che in js i prototipi possono essere assegnati a runtime, quindi potrebbero anche cambiare (sicuramente cattiva pratica, credo si chiami anche monkey typing).

Nelle classi non possiamo andare a cambiare l'implementazione una volta dichiarata.

Si una possibilità di fare una **delegazione** ossia il metodo è implementato in modo dinamico e vado a cercare il primo prototipo per quell'oggetto. È molto flessibile, perché utilizza **duck-typing,**  molto facile cambiare le cose, solo che dal punto di vista della correttezza e sicurezza è un pò più difficile.

# Registro ripassi

| 11/05/23 | Non mi ricordavo gli ingredienti per il abstract data structure (4) |
| --- | --- |
|  |  |
|  |  |
 vista della correttezza e sicurezza è un pò più difficile.

# Registro ripassi

| 11/05/23 | Non mi ricordavo gli ingredienti per il abstract data structure (4) |
| --- | --- |
|  |  |
|  |  |