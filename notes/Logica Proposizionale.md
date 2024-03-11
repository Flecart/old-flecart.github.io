---
layout: page
permalink: notes/logica-proposizionale
tags: italian
title: Logica Proposizionale
---

Ripasso Prox: 20
Ripasso: December 14, 2021
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: November 5, 2021 9:19 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - La funzione semantica vs funzione di interpretazione
    - definizione di conseguenza logica ed equivalenza logica
- Le 3 caratteristiche della deduzione naturale
- Perché un sistema deduttivo è sintattico?

# 6 Logica proposizionale

Con la logica proposizionale studiamo le denotazioni che hanno un valore di verità, ovvero deve essere una sentenza assertiva. Studio solamente le connotazioni che hanno una capacità denotativa, in quanto è solo quello ch emi importa.

## 6.1 La sintassi

Vengono qui definite le produzioni che valgono in ogni singolo mondo.


$$
F ::= \top|\bot|A|B|...|\not F| F \wedge F| F \vee F| F \implies F
$$


Questa è la BNF della nostra sintassi.

Le lettere sono asserzioni, sono sentenze dichiarative a cui posso dare un valore

**Connotazioni atomiche**
Sono solamente ABCD e le singole lettere che rappresentano le proposizioni.

### 6.1.1 Formalizzazione

Ovvero il tentativo di esprimere asserzioni attraverso la sintassi della logica proposizionale.
Quindi dare un valore logico a frasi come oggi piove, marco è bello, marco è brutto  e simili.
Quest è importante perché è probabile che all'esame ci sia un esercizio di formalizzazione

### 6.1.2 Note per attenzione

Fare attenzione ai sinonimi e contrari, che devono avere la stessa lettera, non è ovvio.

Una altra cosa su cui fare attenzione sono le connotazioni ovvero modi diversi per dire la stessa denotazione come:

$$A \implies B$$ è la denotazione delle connotazioni : A è condizione sufficiente di B, B è condizione necessaria di A e altro.

## 6.2 La semantica

> La semantica classica associa il **valore di verità** per ogni connotazione del linguaggio. Allora si dice che stiamo utilizzando la **logica proposizionale classica**
>
Noi parliamo tutti i giorni con una semantica naturale, principale o intesa sono tutti dei sinonimi
Devo partire da alcune premesse filosofiche che mi portano alla logica classica.

$$filosofia \implies logica \implies matematica$$

**Nota di wiki**
La semantica studia il significato delle parole, quindi ci dice cosa deve significare una connotazione, e possono essere molto diverse: molte semantiche per una stessa sintassi.

- Esempio semantica (interpretazione) in prog
    Semantica che interpreta la sintassi in termini di tempo:
    Interpreto i miei costrutti come il tempo che impiega ad eseguire (molto utile per avere una complessità computazionale (es. if, vado a guardare guardia).
    Semantica che interpreta la sintassi in termini di memoria occupata.


### 6.2.1 Dominio di interpretazione, f semantica

Dominio di interpretazione sono connotazioni (definite tramite BNF)

Dipende dai mondi in [Verita, Teorie, modelli, connotazione, denotazione](/notes/verita,-teorie,-modelli,-connotazione,-denotazione), ossia si può interpretare la connotazione in modi diversi a seconda della denotazione in quello specifico mondo

Si potrebbe dire che ogni mondo possieda una **funzione semantica** che parte da un dominio di interpretazione e denota queste connotazioni con oggetti precisi in un mondo.

### 6.2.2 Enunciati della logica classica

TODO: fai una parte a sé per questo

Questa logica parla della verità.

**Manicheo** (visioni estreme)

Sulla falsità e verità

- Ogni enunciato è vero o falso (esistono gradi di verità, secondo alcuni, dibattibile ~Fuzziness)
- Ogni enunciato non può essere vero o falso allo stesso momento

**Platoniche**
- Staticità il valore di verità non muta nel tempo, immutabile.
    - No libero arbitrio o possibilità di cambiare il proprio futuro (se è una verità...) ah i trip mentali.
- Determinatezza il valore di verità è sempre determinato (simile al primo aristoteo?)
    - Tutto il futuro è predicibile e non si può fare niente (ma mancano le conoscenze).

Utilizzando queste due caratteristiche del valore di verità possiamo già fare delle inferenze:

**Differenza fra verità e conoscenza**
La conoscenza non possiede il senso di staticità e determinatezza (può cambiare nel tempo (cresce), e non è sempre quella) mentre la verità lo è

**Differenza fra verità e risorse**
La verità è statica (si può utilizzare quante volte si vuole), mentre le risorse vengono consumate (esempio cibo, se lo mangio scompare,o almeno non è più nella forma attuale).

**Critiche della logica intuizionista**
Esistono dei mondi non determinati che si possono determinare a seconda dei mondi, non posso avere una verità statica immutabile.

Non vale per la conoscenza e mondi non-deterministici

### 6.2.3 Booleani e funzione di interpretazione classica

Scegliemo di indicare i booloani come
1 → Vero 0 → Falso
Per tre motivi principali:
1. Posso utilizzare le regole dell'algebra in quanto sono dei numeri e possiedono quelle proprietà
2. Non vanno in confuzione con top e bottom per il loro essere dei numeri (altrimenti avrei dovuto distinguere il vero e il falso a livello sintattivo, a livello denotativo e poi latro)
3. Si può facilmente trovare un intervallo di verità.

**Interpretazione**
Si può definire (funzione di) interpretazione (classica) di un mondo, possibile solamente grazie all'esistenza di cui sopra dei boleani, che associa a ogni sentenza del mondo un valore di verità.

Allora dato che è una funzione, possiamo notare che possiede i valori di:

1. Staticità, in quanto le funzioni sono solamente quelle e non cambiano
2. Determinatezza per le proprietà delle funzioni, ossia per ogni sentenza del mondo posso associare un valore di verità.

### 6.2.4 funzione semantica per la logica classica

Questo è definito tramite BNF e fissa il linguaggio della logica in un mondo preciso.

NOTA: distingui bene la differenza fra valore semantico e interpretazione in un mondo.

<img src="/images/notes/image/universita/ex-notion/Logica Proposizionale/Untitled.png" alt="image/universita/ex-notion/Logica Proposizionale/Untitled">

### 6.2.5 Tabella di verità

Le tabelle di verità hanno senso solamente nell'ambito della logica classica, in quanto può **solamente rappresentare una logica finita**,, quindi la classica non la intuizionistica.

Le tabelle di verità sono le stesse viste in [Porte Logiche](/notes/porte-logiche)  (con una nota particolare sulla implicazione materiale, molto diversa dalla normale relazione di causalità utilizzata tutti i giorni

**Semantica Tarskiana**

È una logica che utilizzano i matematici (molto lapalissiana, inutile dal punto di vista di nuove informazioni che la definizione riesce a dare) (Coen critica anche che questo è perché i matematici se ne fregano della logica, di quello che sta sotto la matematica).

Praticamente utilizza il linguaggio naturale per descrivere la funzione semantica descritta qui sopra, cosa che funziona solamente con la logica classica, e appena si esce da questo reame non ha più senso. Utilizza **troppe nozioni meta-linguistiche**, tanto che potrebbe dire che meta-linquistica e linguistica siano quasi la stessa cosa

## 6.3 Conseguenza logica (formale)

Questa è la definizione formale di conseguenza logica


$$
\Gamma \Vdash F \iff \forall v, (\forall G \in \Gamma, [G](/notes/g)^v = 1) \implies [F](/notes/f)^v = 1
$$


NOTA 1 questa definizione non è computabile, non è direttamente studiabile in ambito informatico, allora c'è bisogno della creazione di un [#6.4 Sistemi deduttivi](#6.4-sistemi-deduttivi). (In questa definizione stiamo parlando di infiniti (di mondi v e assiomi G, che chiaramente non è computabile quindi non è possibile prendere decisioni in questo ambito).

NOTA 2 Intelligenza artificiale forte, che possa sapere tutto, è ucciso da questa osservazione, in quanto la computazione non può arrivare a sapere tutto. (quindi non può essere un programma... mmmm).

### 6.3.1 **Equivalenza logica**

ovvero la semantica per ogni modello v di una teoria è uguale, quindi possiamo dire che valgono per gli stessi mondi. $$G \equiv F \iff \forall v, [F](/notes/f)^v = [G](/notes/g)^v$$

## 6.4 Sistemi deduttivi

### 6.4.1 Intro

Esistono sistemi deduttivi diversi, quella che vediamo noi è la deduzione naturale.

Possono variare per

- Sintassi diverse
- Esigenze diverse

**Cosa è un sistema deduttivo**

Il sistema deduttivo è una nozione sintattica **che contiene in sé una prova (dimostrazione) di una proposizione. (sintattico perché parla di connotazioni, non di denotazione esatta di quello presente sotto).

Deve quindi utilizzare regole precise per le prove. Ci sono molti modi per fare regole, la più naturale è la deduzione naturale.

### 6.4.2 Deduzione (3)

$$\Gamma \vdash F$$, si legge da $$\Gamma$$ deduco $$F$$, ed è una nuova nozione sintattica (prova esplicita tale per cui la sintassi vada, quasi algoritmico). Poi si potrà dire che ogni dimostrazione deve essere una conseguenza logica e il contrario. Dimostrazione è un dato!

- Deve esserci una **prova esplicita**

    È possibile scrivere una dimostrazione in una qualche sintassi, questo è il significato di deduzione.

    Se è sintatizzabile (si può scrivere con una sintassi) **si può trasmettere** ecco che si cerca una sintassi per le dimostrazioni.

- Deve essere **corretta**, ossia $$\Gamma \vdash F \implies \Gamma \Vdash F$$

    Devo definire il motivo per cui le regole di dimostrazione siano giuste (Le varie regole di introduzione e eliminazione. non vale per le logiche espressive ma solo per la classica!
    Questa nozione è dimostrata in quando parliamo di connettivi, anche se utilizza solamente il concetto di induzione strutturale per dimostrarla...

- **Completezza** (non per logiche espressive (?)) **$$\forall \Gamma, F, \Gamma \Vdash F \implies \Gamma \vdash F$$** vale per logiche semplici, ma esistono dimostrazioni logiche che non saremo mai in grado di dimostrare, in modo simile alla non implementabilità di funzioni matematiche, utilizzando paradossi.

Questa dimostrazione esiste ma è molto complessa, lo ha saltato di striscio il prof.

### 6.4.3 La deduzione naturale

Studieremo la deduzione naturale in [Deduzione naturale](/notes/deduzione-naturale)

## 6.6 Definizioni

### 6.6.1 Tautologia

$$\Vdash F$$, quando è è conseguenza logica per tutto. Quindi è anche una **verità assoluta** perché non dipende da mondo in esame. (la tabella logica in esame possiede solamente delgi uno).

**Not-tautologia** ricorda che il contrario del per ogni è l'esiste il not!, quindi basta un mondo in cui questa proposizione sia falsa.

### 6.6.2 Soddisfacibilità e non

**Soddisfacibilità**

Si utilizza lo stesso simbolo $$\exists v,v \Vdash F \iff \llbracket F \rrbracket ^v = 1$$ tale che v sia un mondo

**Insoddisfacibilità**

Quando non esiste nessun mondo, quindi per ogni mondo nno vale la cosa sopra.

(Più o meno questa proprietà è

**Taotologicità (teorema)**

Si può dimostrare da sopra che una formula è tautologica se per ogni mondo vale che la funzione semantica per input quella proprietà si ha 1

Nota: tautologica implica soddisfacibile, quindi devi fare attenzione!

### 6.6.3 Conseguenza logica per mondi diversi

Ricondursi al concetto di variabile presente in [Connettivi Logici, correttezza, variabili](/notes/connettivi-logici,-correttezza,-variabili)

- Ragionamento
    <img src="/images/notes/image/universita/ex-notion/Logica Proposizionale/Untitled 1.png" alt="image/universita/ex-notion/Logica Proposizionale/Untitled 1">

Con questo per trovare una conseguenza logica mi posso ridurre a leggere le tabelle di verità.

**Drawback**
Le righe totali sono $$2 ^n$$  per le $$n$$ variabili totali, m  per numeri grossi
Non mi dice il perché sia una conseguenza logica.
Quindi sappiamo che esiste ma non si fa mai.

## 6.7 Deduzione semantica

### 6.7.1 Teorema di DS

Questo teorema è molto importante per dare il senso all'implicazione materiale.

$$
\Gamma \Vdash F \implies G \iff \Gamma, F \Vdash G
$$


- Dim Destra
    <img src="/images/notes/image/universita/ex-notion/Logica Proposizionale/Untitled 2.png" alt="image/universita/ex-notion/Logica Proposizionale/Untitled 2">

- Dim Sinistra
    <img src="/images/notes/image/universita/ex-notion/Logica Proposizionale/Untitled 3.png" alt="image/universita/ex-notion/Logica Proposizionale/Untitled 3">

    Nota: dopo aver supposto che  $$v \Vdash \Gamma$$, sto utilizzando l'eliminazione dell'or $$F \vee \neg F$$ per finire la dimostrazione (questa è una tautologia).


### 6.7.2 Corollario DS

<img src="/images/notes/image/universita/ex-notion/Logica Proposizionale/Untitled 4.png" alt="image/universita/ex-notion/Logica Proposizionale/Untitled 4">
La conclusione dovrebbe essere quasi banale grazie al teorema sopra. (Questo mi diche che sono quasi **infinite le tautologie**!) Possiamo trovare cose vere in ogni mondi.

### 6.7.3 Teoremini
$$\Vdash F \iff \neg F$$ insoddisfacibile
$$\Gamma$$ Insoddisfacibile sse $$\Gamma\Vdash \bot$$ e è soddisfacibile nel caso in cui non è conseguenza logica
$$\Gamma \Vdash F \iff \Gamma,\neg F$$, insoddisfacibili.,Gamma finito
$$\neg F \equiv F \implies \bot$$
ash \bot$$ e è soddisfacibile nel caso in cui non è conseguenza logica
$$\Gamma \Vdash F \iff \Gamma,\neg F$$, insoddisfacibili.,Gamma finito
$$\neg F \equiv F \implies \bot$