---
layout: page
permalink: notes/sistem-programming
tags: italian
title: Sistem programming
---

Ultima modifica: March 1, 2023 9:51 AM
Primo Abbozzo: November 10, 2022 3:23 PM
Studi Personali: No

# Elementi di ripasso

# Argomento

### Execs

execve runna e sostituisce

l è per list (credo variabili p adiche, invece che array terminato

### Memoria

Brk mappo gli indirizzi fisici con gli indirizzi logici.

data ci stanno sopra un pochettino alla fine.

heap sta in basso, mentre stack cresce a ritroso!!!

Ci stanno cose tipo la variabile globale. (lo stack cresce dall**indirizzo massimo!**)

### Files

Si traduce come pratica in itlaiano! Quando aperto con permessi che ci servono, andiamo a scrivere con certi modi.

**dup**,

In passato si faceva differenza fra create e open perché una era per creare i file, l’altra per aprire file già esistenti, ma alla fine

`create = open con O_CREAT | O_TRUNC | O_WRONLY`

### Devices

**ioctl** che … boh e **fcntl**,

**mount**.

**map** carichiamo cose in memoria virtuale( quindi gli sembra di avere tutta la memoria disponibile) e si sfrutta il meccnaismo di risoluzione die questi address

**Poll** In Linux, the **`poll`**
 system call is used to determine the status of a file descriptor, such as whether it is ready to be read or written to. The **`poll`**
 structure is used to specify the file descriptor(s) to be monitored and the events (such as availability of data to be read) to be checked for. The **`poll`**
 call returns a list of **`pollfd`**
 structures, each of which contains information about a file descriptor and the events that have occurred on that file descriptor.

**fd_set**

### Note syscall

Vedere System call 🟩- per note leggermente più approfondite sul processo di syscall.

Settono alcune variabili nei registri e poi manda interrupt di syscall, e il kernel esegue la syscall adatta e restituisce sempre in un registro specifico il valore di ritorno. I parametri sono **sempre 6** (non so perché sono sempre 6). Di solito se ritorna il valore -1 è errore.

**Fork** permette di distinguere l’esecuzione del figlio o del padre a seconda del valore di ritorno (il padre ha True, che è il valore del pid, mentre per il figlio è false.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
iglio o del padre a seconda del valore di ritorno (il padre ha True, che è il valore del pid, mentre per il figlio è false.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |