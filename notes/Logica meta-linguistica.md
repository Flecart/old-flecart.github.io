---
layout: page
permalink: notes/logica-meta-linguistica
tags: italian
title: Logica meta-linguistica
---

Ripasso Prox: 30
Ripasso: January 1, 2022
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: September 24, 2021 10:13 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Dubbi vecchi
    1. Sulle premesse di antinomi e paradossi.
    2. Capire cantor per l'ultimo paradosso

1. Se ti va approfondisci la prima teoria degli insiemi e la storia del dibattito matematico iniziale.
2. Funzioni non totali

# 1 Paradossi Metalinguistici

## 1.1 Antinomie e Paradossi

### 1.1.1 Antinomia

Definizione di antinomia è un ragionamento corretto da cui deriva una conclusione errata, probabilmente è **l'insieme o campo in cui stiamo operando ad essere errato** e bisogna cercare di ridefinirlo in modo più corretto, in quanto **le premesse erano accettabili**

### 1.1.2 Paradosso

Paradosso quando il ragionamento corretto va contro l'intuizione, come il paradosso dei gemelli in fisica e simili. **premesse erano accettabili**

**Falsi paradossi**: in cui c'è un errore del ragionamento da cui viene dedotto un ragionamento errato.

## 1.2 Linguaggio naturale

Da ora NL = Natural Language

### 1.2.1 Caratteristiche del NL

Il linguaggio naturale è il linguaggio comunemente utilizzato come italiano, inglese arabo e cinese etc. utilizzato nella maggior parte della vita quotidiana.

Questo linguaggio non è utile per i ragionamenti rigorosi come descrizione del calcolo o dimostrazioni in quanto questo linguaggio è:

- Fortemente dipendente dal contesto
- Ambigua grammatica: e.g. Il poliziotto ha ucciso il ladro con la pistola (pistola mezzo oppure compagnia?)

### 1.2.2 Paradossi in NL

Paradossi visti in classe:

- Io mento
- eterologico è eterologico.

Le cause individuate per i paradossi sono

1. Utilizzo meta-linguistico, ce si riferisce sul linguaggio stesso (Io mento).
    1. Linguaggio naturale potrebbe essere così ampio che può parlare di sé stesso, per esempio:
    contare numero di sillabe o parole, o mischiare il senso del linguaggio o simile, questo genera paradossi.
    2. Sarebbe difficile esprimere idee senza la negazione in poche parole.

    Per scoprire l'utilizzo meta linguistico si utilizza un teorema di invarianza delle denotazioni

2. Auto applicazione di meta-linguistico a se stesso (eterologico è eterologico).
    1. Cerco di usare qualcosa su sé stesso, anche se la definizione dell'aggettivo non dovrebbe essere utilizzate in questo modo, possiamo dire che perde di senso
3. L'utilizzo della negazione (x minore non definibile in meno di 1000 parole).
    1. L'utilizzo della negazione su sé stesso e anche la negazione di sé stesso crea antinomia (paradosso NL)

### 1.2.3 Ricerca di un linguaggio formale

La negazione è necessaria per fare i ragionamenti, non si può togliere.

Non si riesce a evitare di applicare una definizione su sé stessa, dopo che hai oggetto e soggetto puoi scegliere dove applicarlo, cioè è brutto evitare solamente l'applicazione a sé stesso, una volta creata la preposizione può essere usata senza questi piccoli vincoli.

I'uso metalinguistico invece si può evitare, e quindi bisogna abbandonare il linguaggio naturale e approdare in un linguaggio artificiale, il linguaggio rigoroso della matematica.

## 1.3 Linguaggio Matematico

### 1.3.1 Storia dell'insiemistica

Quando ancora la matematica non era ancora scienza diversa dalla informatica, i matematici si mettevano proprio a calcolare modi di calcolo,

Vennero studiate le basi e introdotte la teoria degli insiemi, da Cantor, una base per tutta la matematica attuale, ma questo viene messo in crisi dal paradosso di Russel, creando due filosofie matematiche, gli insiemisti e altri contrari.

Paradosso di Russel: $$X = \{ Y \,|\, Y \not\in Y \, \}$$ e si ha ancora un paradosso auto-refere

Dopo tutta questa diatriba, venne creato circa nel 1930 il significato di calcolare, credo e venne creato il campo dell'informatica.

### 1.3.2 Paradosso di Russel

<img src="/images/notes/image/universita/ex-notion/Logica meta-linguistica/Untitled.png" alt="image/universita/ex-notion/Logica meta-linguistica/Untitled">

**Analisi del paradosso**

Possiamo vedere che la teoria degli insiemi è possibile creare paradossi:

1. Presente l'uso della negazione
2. La negazione, la caratteristica usata è fatta in modo **autoreferenziale**
3. Gli insiemi possono contenere sé stessi, e quindi è possibile l'use meta-linguistico.

Quindi non può esistere un insieme che li contenga tutti come voleva sostenere Cantor.

<img src="/images/notes/image/universita/ex-notion/Logica meta-linguistica/Untitled 1.png" alt="image/universita/ex-notion/Logica meta-linguistica/Untitled 1">

**Soluzione trovata**

Su questa soluzione basa l'intera matematica e non si sa se ci sono altri paradossi dentro questo. Potrebbe essere errata anche questa.

1. Limitazioni sulla creazione di insiemi che abbiano proprietà comunque → **Assioma di comprensione** deve essere gettata.
2. **Assioma di separazione** ovvero gli elementi devono essere presi da un insieme esistente e una proprietà di questo insieme (quindi posso solamente restringere un insieme).
3. È definita come separata la collezione di tutti gli insiemi, per evitare il paradosso di autoreferenzialità, **prevenire l'uso meta-linguistico.**

## 1.4 Paradossi Informatici

### 1.4.1 Esistenza di paradossi

- La composizione di funzioni, cioè l'utilizzo in modo meta-linguistico delle informazioni informatiche è necessaria
    - Sia in linguaggi funzionali, imperativi, basta saltare, quindi si può modificare un programma ~~ Insieme che contiene insieme, molto simile questa cosa.
- La negazione delle affermazioni è necessaria
- Una funzione applicata su sé stessa è presente, possibilissima l'autoreferenzialità

Per questo motivo non si può evitare il paradosso nell'ambito dell'informatica.

### 1.4.2 Paradosso sulle funzioni non totali

Riguardare se sei in grado di definire il significato di

Espressività di un linguaggio

Convergenza e divergenza di una funzione

totalità di una funzione

**Totalità** significa che una funzione riesca a restituire un output in tempo finito.

$$f(g) = not\,(g(g))$$ è una funzione che può creare un paradosso, se analizzata si possono trovare tutti i tre ingredienti per la creazione di paradosso:

C'è la negazione, c'è l'uso meta-linguistico (composizione di funzione) e se al posto di $$g$$ ci metto $$f$$ c'è anche l'auto-referenzialità, creando un paradosso.

<aside>
💡 Le funzioni matematiche danno sempre risultato, invece le funzioni informatiche possono divergere.

</aside>

### 1.4.3 Paradosso sulla divergenza

Questo è il problema della fermata discusso in [Halting Theorem and Reducibility#Halting theorem](/notes/halting-theorem-and-reducibility#halting-theorem)
Nelle funzioni informatiche c'è una fase di calcolo ed elaborazione delle informazioni.
Nelle funzioni matematiche sono solamente una relazione fra insiemi (ossia calcolano un unico input).
Una funzione tale che $$f(g,x) = true \, iff \, g(x) \downarrow$$
Definisco una funzione: $$h(g) = \uparrow if \,f(g,g) \, else \downarrow$$

Questo porta alla conclusione che **non esiste un programma che decida se un altro diverga**.$$f(g) = \uparrow if \,f(g,g) \, else \downarrow$$

### 1.4.4 Paradosso sull'espressività di funzioni matematiche

Spiegata per filo e per segno per la diagonalizzazione di cantor [Relazioni fra insiemi#Diagonalizzazione di Cantor](/notes/relazioni-fra-insiemi#diagonalizzazione-di-cantor)

!<img src="/images/notes/image/universita/ex-notion/Logica meta-linguistica/Untitled 2.png" alt="image/universita/ex-notion/Logica meta-linguistica/Untitled 2">