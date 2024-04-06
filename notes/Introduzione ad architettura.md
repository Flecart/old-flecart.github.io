---
layout: page
permalink: notes/introduzione-ad-architettura
tags: italian
title: Introduzione ad architettura
---

Ripasso Prox: 40
Ripasso: January 8, 2022
Ultima modifica: October 27, 2022 12:15 PM
Primo Abbozzo: September 21, 2021 7:04 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Dubbi vecchi (se ti va rispovera)

    Quale è la differenza fra Microarchitettura e il livello assembly? Non vanno entrambi a fare istruzioni eseguite livello macchina? Dici assembly ha bisogno di essere tradotto?


# 1. Livelli di astrazione

### 1.1 Il principio di astrazione/implementazione

Astrazione per macchine livello n con linguaggi n.

## 1.2 I livelli principali di astrazione

- Livelli in breve

    <img src="/images/notes/image/universita/ex-notion/Introduzione ad architettura/Untitled.png" alt="image/universita/ex-notion/Introduzione ad architettura/Untitled">


### 1.2.1 Livello 0

Qua è utile indagare la

[Porte Logiche](/notes/porte-logiche) in cui si indagano in un modo molto alto il funzionamento di porte

È il livello fisico delle porte logiche e dell'ingegneria elettrica.

### 1.2.2 Livello 1

Link utili potrebbero essere la
[CPU e storia degli elaboratori](/notes/cpu-e-storia-degli-elaboratori)

[Circuiti Sequenziali](/notes/circuiti-sequenziali) Ossia la  [Memoria](/notes/memoria)

> la **microarchitettura** governa il flusso dei dati fra i vari componenti del livello logico digitale
>

Questo è il livello della micro-architettura, ossia come i componenti logici interagiscono fra di loro.

### 1.2.3 Livello 2

[Livello ISA](/notes/livello-isa)

Livello ISA, Instruction Set Architecture, che sono le sequenze di 0 e 1 che definiscono una istruzione

Fino a qua (+ anche parte del sistema operativo) è il lavoro del **system programmers** che si devono occupare di cose di questo livello di astrazione, in seguito i linguaggi sono spesso compilati e non interpretati (**application programmers**).

### 1.2.4 Livello 3-4

È il sistema operativo, il programma che organizza le risorse per il problema, la memoria virtuale etc.

Linguaggio assembly.

Si parla di livello ibrido perché spesso questo livello utilizza ancora le istruzioni ISA (Quindi assembly tradotto), con semmai in aggiunta alcuni programmi per l'esecuzione concorrenziale, gestione della memoria e simili.

Ecco che questi due livelli non si distinguono molto l'uno dall'altro, Il SO è fatto probabilmente in assembly o ISA (ma nessuno lo fa direttamente in codice macchian) in più aggiunge servizi tipici del sistema operativo.

### 1.2.5 Livello 5+

Sono i linguaggi utili alla risoluzione dei problemi, come Python, c++, Java, Js, Ts

## Livelli e macchine virtuali

### Traduzione e interpretazione

Spesso linguaggi a livelli superiori non sono direttamente interpretabili da un livello, basso, per questo motivo devono essere tradotte a un linguaggio comprensibile al livello inferiore.

### Macchina virtuale

Spasso invece di continuare a pensare come un continuum di traduzioni fra i livelli è opportuno pensare a un livello come una macchian virtuale a sé stante. Ossia **ogni livello ha una macchina che opera con un metodo a sé stante**, diverso da tutti gli altri livelli.

- Esempio di questa struttura

    <img src="/images/notes/Introduzione ad architettura/Untitled 1.png" alt="Introduzione ad architettura/Untitled 1">
gni livello ha una macchina che opera con un metodo a sé stante**, diverso da tutti gli altri livelli.

- Esempio di questa struttura

    <img src="/images/notes/image/universita/ex-notion/Introduzione ad architettura/Untitled 1.png" alt="image/universita/ex-notion/Introduzione ad architettura/Untitled 1">

# References