---
layout: page
permalink: notes/grammatiche-regolari
tags: italian
title: Grammatiche Regolari
---

Ripasso Prox: 60
Ripasso: June 1, 2023
Ultima modifica: June 1, 2023 12:46 PM
Primo Abbozzo: October 21, 2022 1:09 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Domande chieste

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled">


# Grammatiche regolari

## Introduzione

### Definizione grammatica regolare 🟩

- Definizione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 1.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 1">


In pratica posso avere solamente come terminali a, oppure un suffisso a su un non terminale.

Queste grammatiche sono interessanti perché è molto facile costruire un automa che sia in grado di riconoscere questo linguaggio.

Seguendo una definizione più *lasca* possono anche accettare dei nonterminali **epsilon**

### Espressione regolare a NFA 🟩

Questa sezione è anche presente in [Automi e Regexp](/notes/automi-e-regexp), però è riportata qui così c’è l’insieme di tutte le cose in un unico posto.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 2.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 2">

- Dimostrazione

    Mi creo un automa che riconosce in modo ricorsivo (per tutte le produzioni della grammatica delle regexp

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 3.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 4.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 4">

    Guarda lezione 7


### Da grammatica regolare a NFA (!) 🟩

<img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 5.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 5">

In modo simile a quanto si fa per la dimostrazione per espressioni regolari rappresentabili come NFA anche questa è così

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 6.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 6">


### Da DFA a grammatica regolare (chiede) 🟩

<img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 7.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 7">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 8.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 9.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 9">


### Grammatica regolare a linguaggio regolare 🟩

<img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 10.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 10">

- Dimostrazione molto informale

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 11.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 11">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 12.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 13.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 13">


Praticamente l'idea principale è fare rimpiazzamenti ricorsivi finché non lo ho in una forma bella.

- Riassunto tutte le equivalenze NFA, DFA, grammatiche ed espressioni.

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 14.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 14">


### Riassunto delle equivalenze 🟩-

C’è una precisa domanda che chiede di discutere in modo generale le equivalenze, quindi metto anche questo doc.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 15.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 15">


## Costruzione dello scanner

### Introduzione 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 16.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 16">


Per fare questa cosa rientra il problema di **creazione della DFA** da NFA **più piccola possibile!**.

Non so come si faccia, ma almeno ora sai che esiste questo problema.

Ad intuito possiamo andare ad affermare che un automa è **minimo quando non ci sono due stati equivalenti** ossia, sempre ad intuito, non li possono compattare in uno, quindi non ho ridondanza di stati.

- Esempio di minimizzazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 17.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 17">


### Equivalenza ed indistiguibilità (di stati) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 18.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 18">


Ossia se due stati sono in grado di riconoscere esattamente lo stesso linguaggio, sono equivalenti. Ma ogni stringa del linguaggio è una cosa difficile da gestire, per questo motivo provo a dimostrare che non siano equivalenti, ossia lo stato di accettazione per una stessa stringa sia diversa partendo dalla stringa vuota

- Slide strategia

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 19.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 19">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 20.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 20">


Provo a togliere tutti

### Famiglia di relazioni (5) 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 21.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 21">


In pratica sto andando a guardare se lo stato finale è lo stesso o meno, partendo dalla stringa nulla, poi andando avanti a costruire altre, e continuando a togliere se lo stato finale ora è diverso.

Questa è una **relazione di equivalenza**.

- Proprietà

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 22.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 22">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 23.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 24.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 24">


### Dimo proprietà 4, se non cambia ho finito 🟨

Ossia se non tolgo più coppie in un passo, allora il mio algoritmo dovrà essere finito.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 25.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 25">

- Esempio di applicazione dell’algoritmo di minimizzazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 26.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 26">


## Minimizzazione

In questa parte andremo a trattare definizioni e algoritmi utili a minimizzare un automa DFA (nel senso di meno stati possibili).

### Algoritmo degli stati equivalenti 🟩

- Algos

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 27.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 27">


Praticamente vado a marcare per tutte le cose possibili (partendo dalla relazione 0). Vado a marcare se non appartengono alla stessa relazione di equivalenza (ossia sono diversi). E se i percorsi più lunghi finiscono su altre celle già occupate, allora marco anche questo, con un segno diverso, per dire che non sono equivalenti per un certo percorso più lungo.

### Dimostrazione correttezza algoritmo 🟨+

- Enunciato di terminazione e correttezza dell’algoritmo

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 28.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 28">

- Dimostrazione di sopra

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 29.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 29">


**Terminazione** è dipendente dalla proprietà 4 a 5, cioè che se non cambia a un passo, allora non cambia a nessun passo, e la 5 che mi dice che ad ogni passo ne marco almeno uno (e questi sono numeri finiti).

**Distinguibilità** se la casella marcata allora esiste un percorso che termina in modo diverso da uno rispetto all'altro, in altro termine esiste una stringa che è riconosciuta da uno ma non è riconosciuta da un altro! (ma se lo ho marcato in questo modo allora è ovvio che succeda questo!).

### Automa minimo (4) 🟩

Questa definizione tratta le caratteristiche formali di un automa minimo costruito da un DFA valido.

(minimizzare gli stati, la funzione di transizione e gli stati accettati).

In pratica nello stesso stato dell’automa minimo ci metto tutti gli stati equivalenti ad essa, in questo senso di minimo!

- Definizione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 30.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 30">


Probabilmente in questo passo intendevo sono 3 le cose nuove differenti

1. Stati possibili devono essere gli equivalenti fra tutti.
2. Transizioni è ora fatto su stati equivalenti
3. Stato iniziale è la classe di equivalenza sullo stato iniziale
4. Gli stati accettati sono le classi si equivalenza sugli stati finali..
5. Alfabeto è lo stesso.

### Equivalenza automa minimo e originale (non chiede) 🟨—

- Slide linguaggio riconosciuto è lo stesso, ed è anche il minimo

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 31.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 31">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 32.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 32">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 33.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 33">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 34.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 34">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 35.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 35">


In pratica per dimostrare il minimo suppongo che esista un automa con ancora meno stati, questi due (il minimo nuovo e il minimo costruito) devono riuscire a riconoscere esattamente le stesse cose, ma essendo questo con ancora meno, deve essere che il minimo costruito abbia due stati equivalenti, cosa che non può succedere col nostro algoritmo

## Lex/Flex  e Yacc

Questi sono **analizzatori lessicali** che prendono in input un file di definizioni regolari e restituisce un programma in C che riesca a riconoscere questi automi

- Diagramma semplificativo di quanto fa

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 36.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 36">

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 37.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 37">


### Struttura di file Lex (3) 🟩

- Slide riassunto

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 38.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 38">


**Dichiarazioni**

Praticamente in sta parte ci sono le definizioni regolari che abbiamo discusso più sopra nello stesso documento che ci rende la scrittura di espressioni regolari molto più semplice

**Regole**

Qui definisci tutte le espressioni regolari che ti servono. Definite in schema di

Pattern → azione

Ossia se un pattern è riconosciuto, esegui una azione.

**Funzioni ausiliarie**

Nel caso in cui le azione sono tropp complesse una serie di funzioni ausiliare possono essere molto utili

### Funzionamento di Lex (4) 🟨+

In questa parte descriviamo brevemente le regole che il lex utilizza per decidere cosa fare.

1. Matcha seguendo le regole
    1. A parità di matching diversa, sceglie quello il matching più lungo
    2. A parità di lunghezza di matching, sceglie quello listato prima
2. Se non matcha, viene dato in output la stringa inalterata
3. Esistono funzioni per gestire i match, la stringa matchata, la lunghezza della stringa matchata (yytext e yylenght)
4. Esistono funzioni per matchare di più o di meno, come yymore e yyless.

### Yacc  🟩

A differenza di Lex, Yacc si occupa di generare la sintassi.

Questo è un analizzatore sintattico, quindi sarà trattato nel dettaglio in un capitolo successivo. Per ora basta capire che i processi di scanning e parsing sono eseguiti più o meno in parallelo, è il parser che chiede ogni volta il token, evitando di avere in memoria rappresentazioni differenti della stessa cosa.

yylval sono variabili comuni che permettono di scambiare informazioni.

yylex() è cchiamato da yacc nel momento di richiesta di lessemi

### Pumping Lemma (!!!) 🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 39.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 39">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 40.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 40">

- Negazione del pumping lemma

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 41.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 41">


- Alcuni esercizi da fare

    [pumpingLemmaExerALRsol.pdf](Grammatiche%20Regolari%200d18e43cabe747d39556632c186bede6/pumpingLemmaExerALRsol.pdf)


### Proprietà dei linguaggi regolari  (5) 🟩

1. unione
2. concatenazione
3. stella di Kleene
4. Complemento
5. Intersezione
- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Grammatiche Regolari/Untitled 42.png" alt="image/universita/ex-notion/Grammatiche Regolari/Untitled 42">


# Registro ripassi

| 22/10/22 | Principalemente da fare meglio i teoremi sulla distinguisibilità. |
| --- | --- |
| 01/11/22 |  Da fare npo meglio il pumping lemma. E le cose per la minimizzazione. |
| 12/11/22 | Da fare un sacco di cose meglio!. Pumping lemma utilizzo e dimostrazione, le proprietà dei linguaggi regolari, fare una applicazione della minimizzazione, ricordarsi meglio le 5 propreità che stanno molto così così. Scrivere proprio le dimostrazioni da DFA a espressioni a grammatiche etc (quelle iniziali) |
| 22/11/22 | Non mi ricordavo che da Grammatica regolare a NFA lo stato finale era il carattere vuoto, né dimostrazione del complemento per linguaggi regolari.
Non riuscivo a descrivere bene il mini algoritmo del lex. |
| 11/12/22 | Ok. |
| 21/12/22 | Ok post esame. |
| 01/02/23 | Lo ho fatto troppe volte forse, maggiormente sì credo di riuscire a creare un discorso per ogni domanda. |
| 31/03/23 | Non mi sembra di aver trovato nessun problema in particolare. |

| 01/02/23 | Lo ho fatto troppe volte forse, maggiormente sì credo di riuscire a creare un discorso per ogni domanda. |
| 31/03/23 | Non mi sembra di aver trovato nessun problema in particolare. |