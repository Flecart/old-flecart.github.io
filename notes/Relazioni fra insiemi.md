---
layout: page
permalink: notes/relazioni-fra-insiemi
tags: en
title: Relazioni fra insiemi
---

Ripasso Prox: 40
Ripasso: December 24, 2021
Ultima modifica: September 30, 2022 3:18 PM
Primo Abbozzo: October 6, 2021 11:03 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Classe di equivalenza
    - Dimostrazione della proprietà fondamentale della coppia ordinata di Kuratowsky
    - Costruzione di R.
    - Definizione di spazio di funzioni
- 21/11 ho ripassato, prodotto cartesiano, funzioni, spazi, classi equiv, insiemi quoziente, dovrei ancora ripassare la dimostrazione di suriettiva e iniettiva presenti in laboratorio
Anche definizione e dimostrazione di Cantor, insiemi infiniti, costruzione di R, Z, N.

# 3 Relazioni fra insiemi

## 3.1 Coppia ordinata

### 3.1.1 Definizione di Kuratowsky

Una coppia ordinata è definita dall'insieme


$$
\langle X, Y \rangle = \{X, \{X, Y\}\}
$$


È quindi chiaro che due coppie ordinate sono uguali fra di loro nel caso in cui gli elementi sono uguali ma anche la loro posizione sono uguali

- Teorema caratterizzazione delle coppie

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled">


### 3.1.2 Definizione di Wiener


$$
(X,Y) := \{\{\{X\}, \empty\}, \{\{Y\}\}\}
$$


### 3.1.3 Definizione di Hausdorff


$$
(X,Y) := \{\{X, 1\}, \{X,2\}\}
$$


### 3.1.4 Proprietà fondamentale coppie ordinate

Due coppie ordinate si dicono uguali se e solo se il primo elemento dei due sono uguali e la stessa cosa per il secondo

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 1.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 1">

- DImostrazione di wiki, difficile

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 2.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 2">


## 3.2 Prodotto cartesiano

### 3.2.1 Definizione del prodotto


$$
\forall A, \forall B, \exists C,\forall Z (Z \in C \iff \exists a, \exists b(a \in A \, \wedge \, b \in B \, \wedge \, Z \in \langle a, b\rangle))
$$


Utilizzando un linguaggio naturale, stiamo prendendo tutti gli elementi da due insiemi e stiamo prendendo una coppia ordinata: *prendiamo tutte le coppie ordinate possibili*.

questo si indica con $$A  \times B$$

### 3.2.2 Relazione e con il Vuoto

> Una relazione è una **qualunque sottoinsieme** di $$A \times B$$
>

Questa cosa si scrive come $$a\mathcal{R}b \iff \langle a,b \rangle \in \mathcal{R}$$

**Teorema relazioni da e verso insiemi vuoti.**

Se  $$\mathcal{R} \subseteq A \times \empty \text{ or } \empty \times A \text{ allora } \mathcal{R} = \empty$$ questo si dimostra che il prodotto cartesiano con un insieme vuoto è sempre vuoto, quindi l'unica relazione esistente è il vuoto.

## 3.3 Funzione

Per ogni elemento di un elemento dominio, si ha solo una unica immagine in un insieme d'arrvo immagine, si scrive $$X f Y$$:


$$
\forall X(X \in A \implies \exists! Y, X f Y)
$$


L'abuso di notazione tipico dei matematici è una falsità perché sembra che la funzione calcoli Y, inverità non calcola niente, ma solamente è una relazione. Ecco l'abuso di notazione.

### 3.3.1 Spazio di funzioni

$$\forall A, \forall B, \exists C, \forall f (f \in C \iff \text{ f è una funzione dal dominio A e codominio B} \text{ e si ha che C = } B^A)$$

### 3.3.2 **Funzioni da e verso insieme vuoti**

Se è il codominio vuoto, allora non esistono funzioni possibili perché non esistono relazioni possibili, non ho nessun elemento da collegare agli elementi del dominio.

$$\empty^A = \empty$$

Se il dominio è vuoto, allora esiste la funzione vuota, che non fa nulla, perché tanto non ho nessun X appartenente a A da loopare, non faccio niente quindi creo l'insieme che non ha nulla.

$$B^\empty = \{\empty\}$$

Se sia codominio che dominio sono vuoti allora devo prima loopare nel dominio, che è vuoto, quindi già l'insieme vuoto ho creato.

## 3.4 Relazioni RST

### 3.4.1 Proprietà delle relazioni

- Riflessiva se $$\forall X, X\mathcal{R}X$$
- SImmetrica $$\forall X, \forall Y X\mathcal{R}Y \implies Y\mathcal{R}X$$
- Transitiva $$\forall X,Y,Z (X\mathcal{R}Y \wedge Y\mathcal{R}Z\implies X\mathcal{R}Z)$$
- Proprietà

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 3.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 3">

- Esempi

    = Vale tutti e tre

    < Transitiva non simmetrica e non riflessiva

    ≤ transitiva e riflessiva ma non simmetrica

    ≠ è simmetrica e bbasta


### 3.4.2 Ordinamento stretto

Una funzione che sia transitiva e non riflesssiva, per esempio il < o  il >

### 3.4.3 Ordinamento lasco

Una funzione che sia transitiva e riflessiva per esempio ≤ o il ≥

In più si può dire che sia antisimmetrica, cioè che se vale $$x\mathcal{R}y \wedge y\mathcal{R}x \implies x = y$$

Un altro buon esempio è la relazione di divisione.

### 3.4.4 Equivalenza

Se ha tutte e tre le proprietà si può dire che sia una relazione di equivalenza.

 Questa relazione è **utile per confrontare oggetti** perché è come dire che sono la stessa cosa due elementi quando soddisfano una relazione di equivalenza.

Dire che sono uguali è stato un qualcosa di cui la matematica si è interessata storicamente, dire uguale è diverso da dire che sono equivalenti.

### Esercizio

- Difficile

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 4.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 4">

    Soluzione

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 5.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 5">

- Misc

    <img src="/images/notes/image/universita/ex-notion/Relazioni fra insiemi/Untitled 6.png" alt="image/universita/ex-notion/Relazioni fra insiemi/Untitled 6">


## 3.5 Classi

$$\equiv\subseteq A \times A \text{ è una relazione di equivalenza, allora la classe di equivalenza di } x\in A \text{ rispetto a } \equiv \text{ è definito come }[x]_\equiv =^{def} \{ y \in A | y \equiv x\}$$

### 3.5.1 Relazioni fra classi di equivalenza

Fra tutte le classi di equivalenza di ha che ho le due classi sono equivalenti fra di loro, oppure sono diverse (disgiunte) fra di loro.

**Abbozzo di dim**

Preso classe equivalente X, Y,allora per la transività Z è transitivo sia a Z X sia a Y, e poi si può utilizzare, usiamo l'assioma di estensionalità per dimostrare che le due classi sono uguali.

Poi cerco l'intersezione, se nell'intersezione di due classi di equivalenza trovo un Z, ho che queste due classi sono identitiche, e se sono identiche so che ci sono Z e simili.

### 3.5.2 Insieme quoziente

L'insieme quoziente **contiene tutti gli elementi** (classi di equivalenza) possibili (disgiunti per la classe di equivalenza).

è definita come, fatto con l'assioma di rimpiazzamento (posso creare un insieme se possiedo una funzione)


$$
U_{/\equiv} := \{[x]_\equiv \,|\, x \in U \}
$$


**Utilità**

Questi insiemi sono utili per costruire ancora, scegliere qualche proprietà a seconda del bisogno.

### 3.5.3 Costruzione di $$\Z$$

Partendo dall'insieme del prodotto cartesiano $$\N \times \N$$ definiamo ogni coppia $$\langle a, b\rangle$$ come $$a - b$$. Allora possiamo definire una classe di equivalenza per il risultato di una sottrazione...

Preso l'insieme quoziente di tutte queste classi di equivalenza si può creare $$\Z$$ e lo possiamo indicare con numeri come al solito.

Quindi invece di indicare un numero in Zeta come una classe di equivalenza, indico normalmente con + -.

### 3.5.4 Costruzione di $$\mathbb{Q}$$

Uguale a Z solo che invece della sottrazione creo la somma

Esistenza funzione bigettiva N → Q

## 3.6 Cardinalità di un insieme

### 3.6.1 Intuizione dalle funzioni

Si può creare una prima intuizione dal concetto di iniettività, suriettività e bigezione di funzioni fra due insiemi sul concetto di cardinalità

**Iniettività**

Se il codominio fosse più piccolo del dominio, per il principio dei cassetti deve esserci una relazione che punta allo stesso elemento nel codominio, per cui la cardinalità del codominio deve essere più grande

**Suriettività**

Se il dominio fosse più piccolo del cominio, non avrei abbastanza frecce per raggiungere tutti gli elementi del codominio, quindi sarebbe impossibile una funzione suriettiva.

**Bigettività**

Se per iniettività e suriettività i due insiemi devono essere uguali per cardinalità

### 3.6.2 Definizione di cardinalità

Due elementi hanno la stessa cardinalità **sse esiste una bigezione fra i due**, e quindi possono definire una classe di equivalenza indicata

$$U_{/\equiv}$$ e posso poi definire anche una classe quoziente delle relazioni di equivalenza.

### 3.6.3 Definizione con insiemi

È possibile, con un lunghissimo lavoro, costruire questa classe attraverso solamente gli insiemi questa classe, invece di utilizzare le classi di equivalenza.

In altre parole si può dimostrare che è abbastanza piccola la classe dei numeri cardinali

**Critica al matematico**

Il matematico indica con lo stesso numero un numero cardinale e il numero naturale, ma per definizione di numero cardinale e numero naturale sono diverse, il primo è una classe di quivalenza ddell'insieme {1,2,3} (che contiene in sé tutti gli insiemi di 3 elementi, fra qui anche il numero naturale 3, mentre per definizione del numero natuale 3 è {0,1,2}

### 3.6.4 Abuso di notazione e aleph

Si indica la classe di equivalenza per la classe di equivalenza $$[x]_{/\equiv}$$ come $$|x|$$

In particolare per indicare la cardinalità dei numeri naturali è $$\aleph_0$$

### 3.6.5 Insiemi infiniti

Fra questi definiamo anche **l'insieme finito** che praticamente è definito come la negazione dell'insieme finito.

## 3.7 Albergo di Hilbert

Hilbert è stato uno dei matematici più famosi a fine secolo scorso e creò i problemi del millennio per lo sviluppo della matematica attuale.

### 3.7.1 Albergo finito e infinito

Se è finito allora non si può accomodare in nessun modo.

Ma se invece è infinito? Una soluzione potrebbe essere che ogni cliente si muova nella stanza col numero seguente e si potrebbe trovare di nuovo altro spazio.

### 3.7.2 Definizione di infinito

> **Infinito** è quando in bigezione con un suo sottoinsieme proprio, ma non è sé stesso.
In simboli: $$A \subset B \wedge \exists f: B f A$$ e f sia bigettiva.
>

qui infatti esiste un **paradosso**, in quanto essendo essendo un sottoinsieme allora si può dire che sia più piccolo, ma con l'intuizione dell'infinito possiamo dire che hanno la stessa cardinalità, hanno la stessa grandezza.

### 3.7.3 Ordinamento sugli infiniti <, ≤

**≤ Ordinamento lasco**

Esiste una classe di equivalenza di ordinamento lasco sse dati due insiemi A, B si ha |A| ≤ |B| se esiste una iniezione fra |A| o |B|

**< Ordinamento stretto**

È simile al precedente, ma devo togliere l'uguale quindi dico che non esiste una bigezione.

## Diagonalizzazione di Cantor

### Dimostrazione diagonalizzazione di Cantor

Teorema $$|T| < | 2^T|$$

Dimostrare per assurdo che non esiste una funzione bigettiva da T a $$2^T$$ e poi dimostrare che esiste una funzione iniettiva da T a $$2^T$$.

La funzione iniettiva è semplice perché basta mappare ogni T al suo singoletto equivalente in $$2^T$$

In seguito dimostriamo per **assurdo che** non esiste una funzione bigettiva.

Supponiamo una funzione bigettiva, al fine di creare l'assurdo abbiamo bisogno dei tre elementi presentati in [Logica meta-linguistica](/notes/logica-meta-linguistica). Quindi meta linguistica, riflessione e negazione.

Definiamo quindi un insieme $$A = \{x \in T| x \not\in  g(x) \}$$ data la funzione $$g(x)$$  bigettiva.

(Possiamo definire x che appartiene all'insieme imamgine perché l'insieme di arrivo sono degli insiemi, in quanto è l'insieme delle parti).

Ma allora data l'iniettività della funzione $$g(y) \in 2^T$$ esiste un $$y \in T$$, ma allora $$y \in g(x) \iff y \not\in g(x)$$ e quindi porta all'assurdo.

#### Dimostrazione con tabella
Questa è quella usata in [R e Intervalli#Innumerabilità di R](/notes/r-e-intervalli#innumerabilità-di-r).

Supponiamo che l'intervallo $$[0, 1[$$ sia numerabile, ossia esiste una funzione $$f: \mathbb{N} \to [0, 1[$$ che sia bigettiva.
Scriviamo tutti i numeri possibili in forma binaria

Avremo una tabella simile: che ci dice che 

| Natural | Real number      |
| ------- | ---------------- |
| 1       | 0,00001010101... |
| 2       | 0,100101011010   |
E continua all'infinito (poi sopra sarebbe bello avere anche uno 0), allora posso creare un nuovo numero che per costruzione non è mappato da nessun naturale (flippo i numeri sulla diagonale). Quindi non è suriettiva, e la costruzione porta ad un assurdo.

### 3.8.2 Sintesi Dim

Data la dimostrazione abbastanza complicata (per me boh) provo a rilistare i passaggi principali utili per questa dimostrazione.

1. Utilizzare l'assurdo per dimostrare l'inesistenza di una funzione bigettiva
2. Utilizzare la suriettività della funzione bigettiva per creare un insieme che possa dare un assurdo.
    1. Allora $$g(y) = A$$ definito con quella proprietà per assurdo, questa deve esistere per suriettività
3. Devo creare un y appartenente a $$T$$ l'insieme iniziale perché così comincio a creare qualcosa
4. Dico assurdo perché entrambi i casi, che $$y \in A, y\not\in A$$ creano assurdo perché implicano tra di loro.

### 3.8.3 |T| < |T^T|

Questo è un corollario della diagonalizzazione di Cantor, che utilizza una semplice disuguaglianza di una funzione caratteristica.

L'unica cosa nuova è $$\mathbb{B}^T \leq |T^T|$$ questo è vero perché le funzioni che restituiscono un booleano, sono un sottoinsieme delle funzioni che restituiscono T, quindi iniezione è semplice da trovare e si dimostra.

### 3.8.4 Funzione caratteristica

Data un'insieme booleano, prendiamo un insieme che restituisce vero se l'elemento appartiene, falso se non lo fa.

$$\mathbb{B}$$ è un insieme con due elementi indicati con 1, 0.

$$\chi_c \in \mathbb{B} ^A$$, posso dire che esiste una bigezione fra questo e l'insieme delle parti di A.

AAAAAA, ovvio, per ogni sottoinsieme C, esiste una unica funzione che mi dice se questi elementi appartengono o meno ad A!

### 3.8.5 Impossibilità eguaglianza in matematica

Questo teorema ci dice che non si può creare totalmente una funzione implementata che sia precisa come una funzione matematica.

> Data una funzione che va da un insieme grande da un insieme grande, è possibile che non possa essere implementata
>
- Curiosità

    Per il matematico, data una qualunque funzione, la probabilità che sia implementabile, è molto vicina a Zero


## 3.9 Costruzione di \R

Immaginando un numero reale, si ha che un $$n\in\R$$ in può rappresentare come una parte intera e una sequenza infinita di numeri dopo (di cui possiamo solo approssimare).

### 3.9.1 Cardinalità dei reali superiore di Aleph 0

Per semplicità, prendiamo la rappresentazione in base due di questo numero, allora questo $$\in B^\N$$

(Questo si può vedere senza molti problemi, quanto la sequenza è infinita, prendo per ogni posizione dopo la virgola arriva a un numero Booleano)

Es.  0,111100001111...

N    0  0123456789....

Ma se queste funzioni appartengono a questo spazio di funzioni, si può finire dicendo che è $$|B^\N| > |N|$$

### 3.9.2 Esempio sulla densità di R

I numeri hanno possibilmente infinite cifre dopo la virgola, ma è possibile tenerli solamente per $$\dfrac{1}{10^n}$$ con n il numero di cifre dopo la virgola (e ci stanno un sacco di numeri).

Questa successione tende chiaramente a 0. Quindi le probabilità sono quasi nulle.

## Esercizi

- Sulle classi di equivalenza

    Dimostrare che l' insieme A appartiene all' insieme unione per una qualunque classe di equivalenza in A

- Suriettivita o iniettivita di una funzione

    Dimostrare che se f o g sono suriettive o iniettive, allora la funzione composizione fra le due sono anche sse suriettive o iniettive.
vita o iniettivita di una funzione

    Dimostrare che se f o g sono suriettive o iniettive, allora la funzione composizione fra le due sono anche sse suriettive o iniettive.