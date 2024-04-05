---
layout: page
permalink: notes/teoria-assiomatica-degli-insiemi
tags: en
title: Teoria assiomatica degli insiemi
---

Ripasso Prox: 60
Ripasso: January 5, 2022
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: September 29, 2021 9:42 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi Dubbi
    - Assioma di rimpiazzamento e regolarità, capirli meglio

# 2 Teoria degli insiemi

## 2.1 Elementi di base

### 2.1.1 Definizione e caratteristiche

1. Tutto è un insieme (su questo *si basa la maggior parte della matematica*)
2. Efficace nella descrizione degli oggetti (infiniti è ez), ma **non è efficiente** nel calcolo in quanto non dà nessun indizio sul'implementazione in memoria o sul modo per calcolarlo, c'è solo una associazione

Si può concludere che per l'informatico non serve a molto questa teoria, ma è la base per la matematica.

### 2.1.2 Teoria Naif

È la teoria disposta a paradossi (Russel) che afferma che gli insiemi si possono formare liberamente → **Assioma di comprensione**.

Abbiamo già analizzato in [Logica meta-linguistica](/notes/logica-meta-linguistica) che questo paradosso è distruttivo,

in particolare guardare [qui](/notes/qui)

**Operazioni di base**

- l'appartenenza
- Creazione di sottoinsiemi

### 2.1.3 Diagrammi di Venn

Il diagramma di Venn permette la rappresentazione di insiemi finiti

L'unica cosa di ricordare, è che **non permette nesting di insiemi**.

## 2.2 Zermelo-Frank Set Theory

Questa è una possibile teoria assiomatica degli insiemi.

**Enti primitivi**

Sono enti di cui non esiste la definizione (perché serve un punto di partenza).

In particolare sono enti primitivi

1. Appartenenza
2. Uguaglianza
    1. Nella slide c'è scritto che non vengono definiti, ma poi l'assioma di estensionalità lo definisce, invece estensionalità definisce solo una relazione
3. Insieme

Andiamo ora a definire assiomi, cose ovvie di questa teoria che sia utile per dimostrare altre proprietà

### 2.2.1 Assioma di Estensionalità e sottoinsiemi

<img src="/images/notes/image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled.png" alt="image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled">

Questo assioma definisce l'uguaglianza fra gli insiemi.

Per ogni X e Y, i due insiemi sono uguali sse hanno gli stessi elementi (un Z che sta sia in X sia in Y, possiamo dire che Z è un elemento temporaneo utile per la stesura)

**Sottoinsieme**

Definizione = `#define` in c++ ossia una sostituzione, una abbreviazione.

Uguale a sopra, ma invece di SSE, utilizziamo un SE.

Se Z appartiene a X allora appartiene a Y.

**Cosa è**

Relazione fra l'ente primitivo uguaglianza con l'appartenenza, ma non è definito come appartenenza, ente primitivo è dato come gli pare.

### 2.2.2 Assioma di separazione

L'assioma di separazione è lo strumento utile che hai visto durante la risoluzione del paradosso di Russel.

Quindi definiamo un insieme Y a seconda di una caratteristica di X. Usiamo sempre un insieme temporaneo Z per definirlo.

Quindi scriviamo $$Y=\{Z\in X | P(X) \}$$ ossia esiste un Y definito per elementi Z tale che questo Z appartenga a X e soddisfa una proprietà P(Z). *Questo è un abuso di notazione, che però dà il senso, dovresti scrivere sempre in altro modo.*


$$
\forall X,\exist Y, \forall Z, (Z \in Y \iff Z \in X \wedge Z \in P(X))
$$


Esempio, L'insieme degli studenti biondi è definito per gli studenti biondi che siano studenti (X) e che abbiano la proprietà di essere biondi P(Z).

### 2.2.3 Assioma dell'insieme vuoto e definizione

Questo assioma definisce l'insieme vuoto e definisce alcune caratteristiche

**L'insieme vuoto non ha elementi**

$$\exist X, \forall Z, Z \not\in X$$ Ma è ridondante perché è sufficiente definirlo con l'assioma di separazione in questo modo:

Sto ottenendo l'insieme vuoto svuotandolo da un insieme che esiste già, in questo modo:


$$
\empty \coloneqq \{X \in Y| false\}
$$


### 2.2.4 Definizione di intersezione infinita

L'intersezione si può definire come l'insieme tale che sia contenuto sia in X sia in Y, quindi utilizzando assioma di separazione di può fare.

**Teorema di appartenenza a un insieme intersezione**

Si può dimostrare subito partendo dall'assioma di separazione, intendi A come insieme da cui prendi e P(Z) come appartenza a B.

**Estensione a intersezioni infinite**

Basta prendere l'intersezione binaria e utilizzare l'insieme di ritorno per altri, in modo ricorsivo se potrebbe aiutare.

Questo però non funziona per **l'intersezione infinita** ecco che c'è il bisogno di definire l'intersezione meglio.

**Definizione di intersezione**

F è l'insieme tdi tutti gli insiemi da intersecare, se F vuoto lo definisco come vuoto, altrimenti utilizzo un insieme A e interseco sempre per ogni insieme Y!.


$$
A\in F,\{X \in A\,|\,\forall Y :Y \in F \implies X \in Y\}
$$


$$\bigcap F =$$  intersezione dell'insieme Insieme di tutti gli elementi da intersecare

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled 1.png" alt="image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled 1">


### 2.2.5 Assioma di unione

L'assioma dell'unione definisce l'unione fra insiemi infiniti e la notazione è molto simile per l'insieme intersezione

$$\bigcup F$$ definito in modo simile


$$
\exists A \, \forall X, \{X \in A\iff\,\exists Y: Y \in F \wedge X \in Y \}
$$


E da questo si può dimostrare il teorema dell'unione binaria che è la definizione di unione classica che abbiamo.

### 2.2.6 Assioma del singoletto

Se c'è solo un elemento in un insieme allora questo si dice singoletto


$$
\forall X,\exists Y, \forall Z \{Z \in Y \iff Z = X \}
$$


Si può utilizzare insieme all'unione per relazionarsi all'ente primitivo dell'appartenenza.

**NOTA:**

l'assioma del singoletto a volte è ridondante perché si potrebbe definire in altro modo, in particolare attraverso l'assioma di rimpiazzamento

**INSIEME A UNIONE**

Possiamo utilizzare un abuso di notazione di questo genere:


$$
I = \{ A_0,A_1 ... A_n\} := \{A_0\} \cup \{A_1\} \cup ... \cup \{A_n\}
$$


Definendo ogni insieme con più elementi tramite l'unione dei singoletti dei suoi elementi.

### 2.2.7 Definizione dei numeri naturali e caratteristiche

Definiamo ogni codifica del numero naturale partendo da $$\empty = 0$$ e definendo in modo ricorsivo

$$[N + 1](/notes/n-+-1) =  [N](/notes/n) \bigcup \{[N](/notes/n)\}$$

Usiamo la notazione $$[\,\,](/notes/\,\,)$$ per le definizioni, una relazione, una implementazione di un concetto astratto

### 2.2.8 Assioma dell'infinito

Questo assioma permette la creazione di un insieme infinito da cui poi si possono **creare i numeri, in finiti**, unito all'assioma potenza si possono creare infiniti ancora più grandi, dato che possiede all'interno tutte le codifiche dei numeri naturali, qualcosa di *metamatematico*. Alcuni matematici pensano che sia una classe.


$$
\exists Y(\empty \in Y, \forall N(N\in Y \implies N \cup\{N\} \in Y))
$$


Definisce in modo univoco ogni elemento di N, partendo dagli insiemi, esiste una biunivicità fra elementi di questo insieme e elementi dei numeri naturali.

**Abusi di notazione**

L'insieme infinito così definito si indica con $$\mathit{N}$$

### 2.2.9 Assioma dell'insieme potenza

Questo insieme è utile per **espandere l'infinito** ossia creare degli insiemi ancora più grandi.

È il primo tra gli assiomi per ora esistenti che può avere qualcosa di controverso.


$$
\forall X, \exists Y, \forall Z (Z \in Y \implies Z\subseteq X)
$$


Ossia l'insieme Y contiene tutti gli insiemi di X.

**Abusi di notazione**

Possiede due abusi di notazione possibili: come

$$2^{\{1,2\}}  \,\text{or} \,P(x)$$

### 2.2.10 Assioma di regolarità o fondazione


$$
\forall A (A \neq \empty \implies \exists B(B \in A \,\wedge \not\exists C(C \in A \wedge C \in B)))
$$


> Ogni insieme non vuoto ha un elemento dal quale è disgiunto.
>

Fra le conseguenze: **nessun insieme contiene (ricorsivamente) se stesso** e ha quindi senso cercare di misurare la taglia (chiamata cardinalità) di un insieme.

Si chiama di fondazione perché **evita la ricorsione infinita** permettendo, quindi, una fine. Sarà in seguito su questa fine che si baserà il concetto di cardinalità di un insieme.

Ossia l'insieme A deve possedere per questo assioma un elemento per cui l'intersezione sia vuota).

### 2.2.11 Assioma di rimpiazzamento

Questo è un assioma dibattuto, in pratica mi dice che posso costruire un altro insieme a partire da un insieme e una funzione.

<img src="/images/notes/image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled 2.png" alt="image/universita/ex-notion/Teoria assiomatica degli insiemi/Untitled 2">

> Intuitivamente: l’immagine di un insieme rispetto a una formula
che descrive una funzione è ancora un insieme.
>

Intuitivamente: se A è un insieme, quindi è abbastanza piccolo, e a ogni elemento ne associo un altro, in una relazione molti-a-uno, quello che ottengo come immagine è ancora piccolo.

- Intuizione

    Data una funzione che associa elementi fra due insiemi, allora questo assioma stabilisce che l'insieme d'arrivo, l'immagine, esiste come insieme (cioè è un insieme ben definito


Questo assioma è **necessario per gli infiniti** e gestire queste cose, per le cose finite non serve.`

## 2.3 Regole di dimostrazione

Queste regole sono presentate con maggiore rigore in [Deduzione naturale](/notes/deduzione-naturale)

### 2.3.1 Regole di introduzione e eliminazione

Eliminazione mi serve per restringere sull'ipotesi, un risultato intermedio per avere qualcosa che voglio.

Questa eliminazione può essere utilizzata con $$\forall X. P(X) ||\implies$$

Introduzione

$$\subseteq$$

### 2.3.2 Abbreviazioni

sia x tale che P(X) significa che prendo ogni x tale che valga quello. Probabilmente per dimostrare un certo risultato Q(X).

Di solito si fa una lunga catena di relazioni da ipotesi che finiscono con un quindi per asserire la tesi.

### 2.3.3 Esempi di dimostrazione

Riflessività di $$\subseteq$$, Asimmetria di $$\subseteq$$, transività di $$\subseteq$$

### 2.3.4 Dimostrazione per assurdo

Si utilizzano le ipotesi per dimostrare una contraddizione, per cui l'ipotesi è falsa.

Posso concludere qualunque cosa dopo la dimostrazione per assurdo **ex-falso quodlibet** abbiamo solamente dimostrato che le ipotesi sono false (quindi se le ipotesi sono binarie, è vero l'opposto).

Significa che una volta giunto ad un assurdo posso dire qualunque cosa, in particolare quello che mi serviva, terminando la dimostrazione.

L'assurdo si ha quando si ha una antinomia, un pò come un paradosso in cui si conclude P e Not P.

**NON P**

si può definire non P come P $$\implies$$Assurdo

Poniamo che $$P = \text{true} \,$$ allora  $$\bar P \implies \text{absurd}$$ passando da qualche ragionamento, cosa che chiaramente è contro la tesi.

**Dimostrazione di ex-falso quodlibet**

IP: $$P, \bar{P}$$

HP: $$B$$

essendo vera P, è vera l'unione $$P \cup B$$ partendo da questa ipotesi, e unendola con l'ipotesi  $$\bar{P}$$ si sa che $$P$$  è falso allora $$B$$ deve essere vera affinché  $$P \cup B$$  sia vera. Ecco che da un assurdo si ha qualunque cosa.

## 2.4 Relazioni fra insiemi

Vedere la pagina di appunti sulle relazioni fra insiemi (classi di equivalenza e simili, con anche le funzioni!) [Relazioni fra insiemi](/notes/relazioni-fra-insiemi)

## **Valutazione:**

Non fare detour

Utilizza la logica debole invece di forte, cioè utilizzare solamente assiomi consociuti o teoremi dimostrati con gli assiomi e **non utilizzando l'intuizione. `**
:**

Non fare detour

Utilizza la logica debole invece di forte, cioè utilizzare solamente assiomi consociuti o teoremi dimostrati con gli assiomi e **non utilizzando l'intuizione. `**