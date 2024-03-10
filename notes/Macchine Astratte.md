---
layout: page
permalink: notes/macchine-astratte
tags: italian
title: Macchine Astratte
---

Ripasso Prox: 80
Ripasso: June 3, 2023
Ultima modifica: June 4, 2023 3:20 PM
Primo Abbozzo: September 23, 2022 1:08 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled">

- Interpreti

    Quali sono i passi principali del ciclo FDE e cosa fa l’interprete (ciclo FDE)

- Implementazione linguaggio via microprogrammazione o software
- Realizzazione dell’interprete e del compilatore 🟥

# Macchine Astratte

### Definizione ed esempi per macchine astratte 🟩

> Una macchina astratta è un qualunque insieme di algoritmi e strutture di dati che permettono di memorizzare ed eseguire il linguaggio $$L$$, quindi una macchina astratta esiste per esguire **il proprio linguaggio** (inteso come insieme finito di istruzioni primitive che riesce ad  comprendere e eseguire).
>

Si può proprio dire che *esiste una simbiosi* fra macchina e linguaggio. Si potrebbe dire che la macchina fisica è soltanto una implementazione FISICA di un linguaggio, ossia una macchina che capisce ed esegue quel linguaggio e che sia solamente un caso particolare della macchina astratta.

Questa macchina astratta è costituita da **una memoria e un interprete**.

Come si potrebbe intuire una singola macchina ha un singolo linguaggio ma un linguaggio può avere *infinite* macchine che differiscono per strutture di dati utilizzate nell’implementazione!

- Macchina di von Neumann (esempio)

    Una delle prime macchine astratte, in questo caso molto semplice, con un unico bus centrale, e tante cose di mezzo.


### Linguaggio macchina

> Una **macchina fisica** è la realizzazione “a fili” di un particolare algoritmo che,
sfruttando alcune strutture dati, è capace di “eseguire” programmi scritti in
un certo linguaggio, detto il **linguaggio macchina**
>

In pratica è una implementazione ad hardware, come si vedrà dopo.

Possiamo dire che il linguaggio di una certa macchina astratta è il linguaggio compreso da quella macchina!

## Interpreti e compilatori

### Interprete 🟩

<img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 1.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 1">

L’interprete per un linguaggio **mantiene la SEMANTICA!**

- Esempio di interprete per macchina fisica

    ciclo FDE, vedi 3.1.3 Central Control Unit , è l’**interprete** della macchina hardware, ossia

    1. Decodifica l’istruzione che deve andare ad eseguire
    2. Esegue quanto deve eseguire (in questo caso recupera gli operandi, esegue e stora).

    In generale possiamo astrarre questo ciclo FDE fisico utilizzando questi passaggi un poco più astratti

1. Elaborazione dei dati primitivi (primitivi = che riesce a rappresentare direttamente in memoria) (es ALU che elabora bits, dato primitivo della macchina fisica)
2. Controllo sequenza delle operazioni (es. salti, sposta PC in macchina fisica, chiamate di funzione)
3. Controllo trasferimento di dati (es copia, move, copia bits fra registri (nella macchina fisica registri come MDR e MAR).
4. Gestione della memoria (es pointers, allocazione, ma anche cache fra CPU e simili, rilocazione degli indirizzi e bla bla bla)

- Esempio MA dell’hardware

    Ha un set istruzioni RISC o CISC eseguibili direttamente dalla parte elettronica

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 2.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 2">


Una osservazione principale da cui deriva dal concetto di macchina astratta è il concetto di gerarchizzazione fra le macchine astratte. Un primo esempio è la microprogrammazione

- Slide interpretativa pura

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 3.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 3">


### Compilatore 🟩

<img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 4.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 4">

- Slide compilativa pura

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 5.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 5">


### Vantaggi e svantaggi Inteprete-compilatore 🟩-

**Vantaggi interpretazione**

- Implementazione: Di facile realizzazione rispetto-compilatore
- Memoria: risparmio in quanto non ho un nuovo programma da memorizzare
- Flessibilità: facile cambiare comportamento in esecuzione (eg. per debugging) (mentre compilatore perde anche dati di debug, come la struttura dell’informazione)

**Svantaggi interpretazione**

- Lentezza, dato che legge ed esegue insieme
- In breve

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 6.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 6">


### Implementazione Compilativa-interpretativa 🟩

- Se l'interprete della macchina intermedia è sostanzialmente diverso dall'in-
terprete di $$Mo_{Lo}$$, diremo che siamo in presenza di un'implementazione di
tipo interpretativo.
- Se l'interprete della macchina intermedia è sostanzialmente uguale all' in-
terprete di $$Mo_{Lo}$$ (di cui estende alcune funzionalità), diremo che siamo in
presenza di un'implementazione di tipo compilativo.

In generale non si utilizza mai una implementazione di tipo interpretativo pura o pura compilativa.

### Nella realtà 🟩

Non vengono mai utilizzate soluzioni compilative o interpretative pure, ma si utilizzano sempre cose miste (ad esempio per chiamate input e output si utilizzano chiamate a sistema operativo, che sono solitamente interpretate).

La compilazione di solito si utilizza per linguaggi molto simili (è questa la difficoltà maggiore per la costruzione di un compilatore), e ci sono alcuni passi che sono *simulati* (quindi non compilativa pura).

Mentre l'interpretazione è molto più facile da scrivere (perché di solito ho subito molte funzionalità del linguaggio attuale), e capita spesso che il codice iniziale venga compilato in un linguaggio intermedio che sia interpretabile.

Nel pratico esistono linguaggi più interpretati che compilati e anche il contrario, oppure entrambi (esempio pascal).

- Schema di compilazione intermedia classico

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 7.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 7">


A seconda di quanto il linguaggio della macchina intermedia si avvicini al linguaggio sorgente o macchina possiamo definire le sfumature di linguaggio interpretato o compilato. vedi 20pg libro. (1.2.3)

### Implementazione via Kernel 🟨-

Facciamo solamente degli accenni a come si fa a creare compilatori o interpretatori

Si implementa un linguaggio intermedio, il cui compilatore o interprete è molto facile da fare $$H$$.

Poi si costruiranno compilatori o interpreti che avranno come target questo linguaggio, quindi questo linguaggio sembra un linguaggio intermedio quasi.

- Slides

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 8.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 9.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 9">


### Boostrapping 🟨+

<img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 10.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 10">

<img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 11.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 11">

## Implementazione delle macchine astratte

Esistono 3 modi principali per realizzare l’implementazione di una macchina astratta:

1. Implementazione tramite Hardware
2. Emulazione tramite micro-programmazione  (firmware)
3. Interpretazione tramite Software

### Hardware 🟩

L'implementazione hardware è spesso

- poco flessibile, dato che capisce solamente questo linguaggio.
- Molto veloce, dato che esegue a livello hardware le sue istruzioni.

- Nota influenza linguaggio astratto in linguaggio hardware

    Ciò non toglie che vi siano molti casi in cui la struttura della macchina astratta
    di un linguaggio di alto livello ha influenzato la realizzazìone di un•architettura
    hardware, non nel senso di una diretta realizzazione in hardware della macchina
    astratta, ma nella scelta di operazioni primitive e strutture dati che permettessero
    una più semplice e efficiente realizzazione dell'interprete del linguaggio di alto
    livello. Questo è il caso, ad esempio, dell'architettura del B5500, un computer
    degli anni '60, influenzata dalla struttura del linguaggio *ALGOL*.


### Microprogrammazione 🟩-

Può essere (soprattutto nelle macchine NON-risc) in cui alcune istruzioni non sono esattamente eseguibili dall’hardware, ma l’interprete decodifica l’istruzione in più istruzioni al livello inferiore, ora queste istruzioni sono eseguibili.

L’interprete del linguaggio di questo livello è solitamente scritto in un linguaggio di livello inferiore.
Di solito la microprogrammazione è fatta a **livello firmware**. Questa microprogrammazione è spesso depositata in una zona di memoria adibita alla **sola lettura** (ROM).

Ciò permette una flessibilità maggiore rispetto all’implementazione a livello hardware, e tiene una velocità maggiore rispetto all’implementazione tramite software (però resta sempre un linguaggio a basso livello vicino alla macchina).

- Motivo storico della microprogrammazione

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 12.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 12">


### Macchina ospite - software 🟩

È possibile implementare tramite software una macchina astratta su una **macchina ospite.** Ossia una macchina che appunto ospita una macchina astratta con un proprio linguaggio. Solitamente questa macchina con questo linguaggio compila in un linguaggio della macchina ospite, in modo che sia eseguibile. Ecco che da qui si può vedere una gerarchizzazione.

macchina con Linguaggio di alto livello → macchina di altro livello → … → macchina fisica che esegue.

- Moltissima flessibilità
- Velocità leggermente minore
- Livello di interpretazione/traduzione in più
- Esempio di astrazione solita

    <img src="/images/notes/image/universita/ex-notion/Macchine Astratte/Untitled 13.png" alt="image/universita/ex-notion/Macchine Astratte/Untitled 13">


# Registro ripassi

| 30/09/2022 | Ok direi, da ripassare ancora un po’ bootstrapping e fare meglio i metodi 3 di implementazione di un linguaggio |
| --- | --- |
| 28/10/2022 | Tutto apposto direi |
| 14/11/2022 | Apposto, anche bootstrap è simili sono apposto, bisogna solo avere discorso preparato per ogni argomento. |
| 07/12/2022 |  Maggior parte delle cose riesci a dirle. |
| 21/12/2022 | Ok |
| 03/02/2023 | Dai è Ok, non ci sono stato molto |
| 03/04/2023 | Ok |
| 04/06/2023 | Siamo ancora Ok, dovrò probabilmente ripassarlo per benissimo per l’l esame che è vicino, ma credo che ci siamo. |
23 | Dai è Ok, non ci sono stato molto |
| 03/04/2023 | Ok |
| 04/06/2023 | Siamo ancora Ok, dovrò probabilmente ripassarlo per benissimo per l’l esame che è vicino, ma credo che ci siamo. |