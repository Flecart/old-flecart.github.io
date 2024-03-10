---
layout: page
permalink: notes/programmi-concorrenti
tags: italian
title: Programmi Concorrenti
---

Ripasso Prox: 120
Ripasso: July 1, 2023
Ultima modifica: April 1, 2023 9:03 AM
Primo Abbozzo: September 28, 2022 11:20 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# 1 Programmazione concorrente

Vorremmo cercare di stabilire una teoria riguardante programmi che vengono eseguiti appunto concorrentemente, senza una esecuzione classica uno dpo l’altro

- Esempio mini-programma rallentamento

    ```cpp
    #include <stdio.h>
    #include <pthread.h>

    void test(void *s) {
        for (int i = 0; i < 10; i++) {
            printf("%s\n", s);
            for (int j = 0; j < 100000000; j++);
        }
    }

    int main(int argc, char *argv[]) {
        pthread_t t1, t2;
        pthread_create(&t1, NULL, (void *)test, "Uno");
        pthread_create(&t2, NULL, (void *)test, "Due");
        pthread_join(t1, NULL);
        pthread_join(t2, NULL);
    }
    ```

    Example output:

    Due
    Uno
    Uno
    Due
    Uno
    Due
    Due
    Uno
    Due
    Uno
    Due
    Uno
    Due
    Uno
    Due
    Uno
    Due
    Uno
    Due
    Uno

- Esempio 2 mini-programma rallentamento

    ```c
    #include <stdio.h>
    #include <pthread.h>

    int count = 0;
    void test(void *s) {
        for (int i = 0; i < 100000; i++) {
            count+= 1;
        }
    }

    int main(int argc, char *argv[]) {
        pthread_t t1, t2;
        pthread_create(&t1, NULL, test, "Uno");
        pthread_create(&t2, NULL, test, "Due");
        pthread_join(t1, NULL);
        pthread_join(t2, NULL);
        printf("%d\n", count);
    }
    ```


Vogliamo creare un **modello** teorico che riesca a rappresentare il concetto di processi concorrenti, questo è il modello concorrente

## Processi

### Differenza col programma 🟩

Il programma è statico, mentre il programma è dinamico. Questo perch'e il processo è un programma attivo, in esecuzione. Un filo esecutivo, qualcosa che evolve in modo autonomo.

Invece il programma è la sequenza di istruzioni.

### Finite progress 🟩

> Ogni processo viene eseguito a velocità finita **non nulla**
>

### Descrizione del processo (3) 🟩

Questa parte è descritta meglio in [Processi e thread](/notes/processi-e-thread)

Possiamo descrivere lo stato di un processo memorizzando alcuni dati molto precisi, questi sono:

1. Stato di avanzamento (Istruzione da eseguire e il suo stato)
2. La sua memoria utilizzata (dati, stack e file aperti)
3. Memoria nel processore (i dati nel registro e simili)

## Concorrenza

- Concorrenza e dove trovarla

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled">


### Definizioni concorrenza e Race C 🟩

**Esecuzione concorrente**

> Due processi si dicono in esecuzione concorrente se
vengono eseguiti in parallelo (con parallelismo reale o
apparente)
>

**Concorrenza**

Un insieme di notazioni e tecniche per rappresentare e risolvere problemi di esecuzione concorrente.

**Race condition**

> Si dice che un sistema di processi multipli presenta una race
condition qualora il risultato finale dell'esecuzione dipenda
dalla **temporizzazione** con cui vengono eseguiti i processi
>

### Tipologie di concorrenza (3) 🟩

**Multiprogramming**

È un parallelismo apparente perché la CPU è solamente quella, ma esegue tante cose e così velocemente che sembra star eseguendo in modo parallelo. Si parla infatti di **interleaving**.

**Multiprocessing**

parallelismo reale perché effettivamente ho tante CPU, o tanti core in cui far eseguire programmi in modo contemporaneo, in questo caso, come anche nell'esempio seguente si parla di **overlapping** (distanti nello spazio)

**Distributed processing**

Parallelismo reale ma a una scala più grande che va oltre al singolo computer dato che ho un sistema di più computer che eseguono più processi

### Esempio di problema di concorrenza 🟩-

- Codice slide cattivo

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 1.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 1">


Succede un problema molto simile a **read after write**, che un programma ha uno stato non aggiornato e fa una operazione con informazioni vecchie che sovrascrivono le informazioni nuove.

- Esempio multiprogramming di esecuzione errata

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 2.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 2">

- Esempio multiprocessing di esecuzione errata

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 3.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 3">


Possiamo andare a cercare le cause di questi problemi, che sono principalmente causati da

**Cause principali (comuni a multiproc e multiprog)**

1. Accesso a memoria condivisa
2. Sconosciuta velocità di esecuzione del singolo processo.

## Interazione fra progressi(2)🟩

Vogliamo cercare di avere alcuni metodi affinché due processi differenti si possano coordinaree cooperare.

**Conoscenza indiretta**

Quando condividono un pezzo di memoria e comunicano in questo modo indiretto.

**Conoscenza diretta**

Quando un processo conosce un ID di un altro processo e manda proprio dei messaggi e cose all’altro programma

### Proprietà cooperazione (2) 🟩-

Proprietà vogliamo dire una caratteristica che rimane vera per ogni esecuzione del programma, come se fosse un teorema per il programma.

**Safety → Correttezza**

Vuol dire che il programma non fa cose cattive (se può scegliere fra due valori, devono scegliere lo stesso valore).

un programma non interferisce con un altro.

**Liveness → Terminazione**

Ossi ail programma continua ad eseguire rimane vivo e ritorna il suo risultato e fa quello che deve fare (ossia deve arrivare a soluzione).

Un programma non deve essere interrotto ininterrottamente (ossia non deve continuare all'infinito) (possiamo dire che non c'è starvation in questa parte).

### Mutua esclusione, Deadlock e starvation 🟩

> l'accesso ad una risorsa si dice mutualmente esclusivo se ad
ogni istante, al massimo un processo può accedere a quella
risorsa
>

**Deadlock**

È un problema che è risolto dalla mutua esclusione (in cui due programmi interferiscono fra di loro e causano questo blocco).

Da vedere l’esempio dei programmi

- Esempio in figura degli incroci

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 4.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 4">

- Esempio programmi

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 5.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 5">


**Starvation**

È un problema di liveness dato che può capitare che un processo sia sempre messo davanti a un altro, e quindi un certo programma non verrebbe mai eseguito.

- Esempio coda

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 6.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 6">

- Esempio programmi

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 7.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 7">


### Azioni atomiche 🟩

Proprietà:

1. Indivisibile
2. O avviene o non avviene niente

Nel linguaggio c in particolare, dipende da processore e compilatore (perché potrebbe utilizzare istruzioni che non si traducono in una singola in codice macchina).

- Esempi atomicità di istruzioni in C

    <img src="/images/notes/image/universita/ex-notion/Programmi Concorrenti/Untitled 8.png" alt="image/universita/ex-notion/Programmi Concorrenti/Untitled 8">


**Parallelismo reale**

questa azione atomica non interferisce con altri

Al fine di raggiungere questo obiettivo viene utilizzato un sistema di arbitraggio dei bus. (quindi un processo prende prima dell’altro).

**Parallelismo apparente**

il context switch avviene prima o dopo l’azione. Questo è possibile perché l’interrupt è sempre runnato prima o dopo quell’azione.

## Note sul C (non importante, + pratica)

Inizialmente questo linguaggio è nato proprio per scrivere sistemi operativi, non si scrive in assembly perché questo linguaggio non è portabile su macchine diverse.

### Caratteristiche di linguaggio per SO

1. Possibilità di gestione completa dei dati nella memoria.
2. Leggibilità di un linguaggio di alto livello

[https://so.v2.cs.unibo.it/wiki/index.php/Prin_C_ples](https://so.v2.cs.unibo.it/wiki/index.php/Prin_C_ples)

**Esempietto boostrap**

[Esperimento didattico: portabilità dei compilatori]([https://so.v2.cs.unibo.it/wiki/index.php/Esperimento_didattico:_portabilit%C3](https://so.v2.cs.unibo.it/wiki/index.php/Esperimento_didattico:_portabilit%C3)%A0_dei_compilatori)

Ho un linguaggio di alto livello L, e una macchina fisica M e una macchina intermedia N, vorrei fare un compilatore da L a M.

Allora ho un compilatore da L a M che gira in N molto scrauso. Mi scrivo il compilatore da L a M che gira in N, lo compilo e ho un compilatore da L a M scritto in M

# Registro ripassi

| 23/10 | Nessun problema |
| --- | --- |
| 12/12/22 | Tutto Ok. |
| 14/01/23 |  Direi tutto ok. |
| 01/04/23 | Tutto ok. |
 e ho un compilatore da L a M scritto in M

# Registro ripassi

| 23/10 | Nessun problema |
| --- | --- |
| 12/12/22 | Tutto Ok. |
| 14/01/23 |  Direi tutto ok. |
| 01/04/23 | Tutto ok. |