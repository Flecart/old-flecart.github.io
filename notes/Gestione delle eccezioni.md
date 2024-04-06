---
layout: page
permalink: notes/gestione-delle-eccezioni
tags: en
title: Gestione delle eccezioni
---

Ripasso Prox: 17
Ripasso: May 27, 2023
Ultima modifica: May 16, 2023 9:53 AM
Primo Abbozzo: March 27, 2023 10:58 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Gestione delle eccezioni

## Introduzione

### Metodi alternativi di gestione degli errori (3) 🟩

A volte le computazioni falliscono. Potremmo gestirle con i result come accennato in [Polimorfismo](/notes/polimorfismo), però diventa molto macchinoso fare tutte le funzioni che debbano inoltrare solamente delle results. bisogna trovare un modo più naturale. Ecco che arriva una gestione delle eccezioni direttamente nel linguaggio. Si tratta un sistema di comunicazione degli errori.

**ALTRI METODI**

- Results, stile monadico, vedi sopra.
- definire dei valori eccezionali (questo si va spesso in C)
- Il chiamato dice al chiamante una cosa da chiamare quando fallisce. Diciamo **inversione del controllo** perché in questo caso è il chiamato che dice cosa fare. Ma rende il codice poco composizionale, quindi difficile da seguire.
(Questa è la soluzione molto più simile alla gestione effettiva degli errori). Ma nelle eccezioni vere non è il chiamato che ritorn al'indirizzo da eseguire ma è il runtime che decide cosa andare ad eseguire. Questa cosa non interrompe il flusso del calcolo

Con le eccezioni vogliamo **trasferire il controllo a un gestore delle eccezioni** questo gestore solitamente si trova sulla stack (va a risalire tutta la stack di chiamata fino a raggiungere questo gestore).

### Definizioni di eccezioni 🟩

Una eccezione è un modo per poter interrompere la computazione attuale (descrizione di stati invalidi della computazione), in vista di errori semantici come la divisione per zero. Sono proprio dei **nomi** (!!!), ossia catturati nominalmente duratne la gestione degli errori.

Alcuni stemp importanti sono la

1. Definizione di errori gestibili, e sollevamento, o raising di questi errori
2. Politiche di gestione degli errori. (come viene trasmesso e il codiche che viene chiamato)
3. Meccanismi di sollevamento di errori

### Caratteristiche delle eccezioni 🟩

- **Nomi**, le eccezioni hanno nomi e rappresentano quale errore semantico di operazioni, hanno una sintassi precisa
- **Valori**, possono contenere certi valori che comunichino qualcosa sul’errore.

**COSTRUTTI DELLE ECCEZIONI**

Sono solitamente due

1. Un modo per marcare la porzione di codice protetta
2. Un gestore delle eccezioni, che esegue nel caso sia stato sollevato all'interno di tutto il codice protetto una eccezione non gestita.

### Eccezioni e sottotipaggio 🟩-

Possiamo utilizzare la machinery di [Polimorfismo](/notes/polimorfismo) anche in questa fase! Possiamo catturare eccezioni e tutti i sottotipi di una certa eccezione.

È anche considerata una bad practice, perché vorresti catturare una eccezione specifica (più facile da capirne la causa diciamo)

[https://stackoverflow.com/questions/2416316/why-is-the-catchexception-almost-always-a-bad-idea](https://stackoverflow.com/questions/2416316/why-is-the-catchexception-almost-always-a-bad-idea)

[https://stackoverflow.com/questions/6083248/is-it-a-bad-practice-to-catch-throwable](https://stackoverflow.com/questions/6083248/is-it-a-bad-practice-to-catch-throwable)

- CATCH è un controllo Con subtyping!

**IN JAVA**

- Slide java sottotipaggio

    <img src="/images/notes/image/universita/ex-notion/Gestione delle eccezioni/Untitled.png" alt="image/universita/ex-notion/Gestione delle eccezioni/Untitled">


Throwable è un tipo somma di due casi (Error, irrecuperabile) e Exception. Tutte le eccezioni tranne Runtimeexception (e.g. se finisce memoria sulla heap) è da gestire.

### Implementazione classica 🟩

Solitamente l’errore viene proprio sollevato.

Ossia se vogliamo gestire un errore in un certo **blocco protetto**, allora linkiamo questo gestore a questo blocco.

Algoritmo per le eccezioni:

- Check se il blocco attuale ha il gestore corretto (ossia supertipo dell’eccezione che ho)
- Sì runna questo codice **bindato staticamente al blocco protetto**
- Altrimenti risolleva l’errore andando al record precedente
- Continua fino ad arrivare al gestore di default

### Implementazione per ricerca binaria 🟨-

Questo solitamente per le applicazioni reali è più veloce, perché quando entro in blocco protetto non ho bisogno del leggero overhead in più per darti il gestore.

Praticamente per ogni singolo blocco io definisco una coppia :

1. Inizio del codice protetto
2. Puntatore al gestore delle eccezioni

Se non ci ho definito niente, c'è un puntatore di default, che semplicemente risollevi gli errori.

Tutti i blocchi sono tenuti in maniera ordinata, in modo da farci una ricerca binaria se ne ho bisogno. Quindi è più lenta di un fattore `log(n)`, però dato che non ho overhead a entrare, di solito è una cosa più veloce della precedente.

## In Java

### Tipologie di eccezioni (2)

<img src="/images/notes/image/universita/ex-notion/Gestione delle eccezioni/Untitled 1.png" alt="image/universita/ex-notion/Gestione delle eccezioni/Untitled 1">



# References