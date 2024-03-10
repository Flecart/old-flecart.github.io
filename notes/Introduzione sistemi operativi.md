---
layout: page
permalink: notes/introduzione-sistemi-operativi
tags: italian
title: Introduzione sistemi operativi
---

Ultima modifica: March 1, 2023 9:52 AM
Primo Abbozzo: October 16, 2021 6:09 PM
Studi Personali: Yes

# Elementi di ripasso

# 1 Introduzione

In questa sezione andiamo ad indagare cosa fa il sistema operativo

## Note Generali

### 4 Parti di un sistema di calcolo

### Struttura Memoria

Vedi [Memoria](/notes/memoria) per il corso di [Architettura](/notes/architettura)

### Tipologie di SO

### Bimodalità SO

Utente e Kernel

### Interrupt, Trap, System or Supervisor Call

System call 🟩- per maggiori info sui modi di chiamata delle syscall

System call vs chiamate di funzione di libreria? Quali sono le differenze?

1. Sicurezza. (perché l’utente non può accedere a nient’altro che le sue istruzioni e la memoria concessagli, se vuole accedere a qualcosa di fuori deve fare richiesta). Vogliamo creare un **accesso mediato** con le system call alle risorse, quindi **sistema operativo protetto**, dato che i processi sono isolati.

**Operazioni delle syscall**

1. Input Output e periferiche.
2. Creare e gestire i processi.
3. Gestione dei file e della memoria (tutto è un file)
4. Gestione dei segnali

## Gestione dei processi

### Cosa è un processo

### CPU parallele ??

### Multiprogrammazione

### Bimodalità CPU

### Protezione e sicurezza

## Reti
**

1. Input Output e periferiche.
2. Creare e gestire i processi.
3. Gestione dei file e della memoria (tutto è un file)
4. Gestione dei segnali