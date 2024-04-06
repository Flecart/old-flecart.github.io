---
layout: page
permalink: notes/porte-logiche
tags: italian
title: Porte Logiche
---

Ripasso Prox: 40
Ripasso: December 22, 2021
Ultima modifica: October 27, 2022 12:16 PM
Primo Abbozzo: September 27, 2021 3:02 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Exercise

    As it is mentioned in the question that there are two motorcycle gang in the area and one of them always tells truth and the other always tell lies. The missionary also does not know which gang tells the truth and which do not. So, there are two possibility that could happen :

    1. The missionary can ask both the gangs if the road goes to the disneyland but there would be a confusion because one of the gang is ought to be lying than the other so he would get one yes and one no.
    2. Sam goes if he would ask the question indirectly as if the road does not go to the disneyland then also he would get one yes and one no which will again create the confusion.

    So, to ask a question which will solve the problem without creating the confusion would be :

    - So, the missionary should actually ask both the gangs about what would be answer of the other gang for the question that if the road goes to the disneyland or not and in this way he would get either a yes or a no from both the gangs.

    So, we get the correct answer by taking technique with both the gangs.

- Vecchie domande
    - Codice gray, cosa è?
    - Forma canonica di una funzione
    - Mintermini
- Perché la porta nand è concettualmente in grado di creare tutte le porte logiche possibili?
- December 14, 2021 3:43 PM

# 5 Porte Logiche

## 5.1 Boole

Un signor Boole ha creato le basi dell'algebra booleana su cui si basano le porte logiche dei computer moderni.

### 5.1.1 Tabelle di verità

Le tabelle di verità sono sufficienti per descrivere il funzionamento di una porta logica.

Questa cosa è possibile grazie alla limitatezza delle funzioni all'interno dell'insieme $$\{0,1\}$$ dominio di partenza e fine dell'algebra booleana.

### 5.1.2 Proprietà nell'algebra di Boole

Prova a spiegare da solo queste leggi:

- Proprietà: 9
    - Identità
    - Null
    - Idempotenza
    - Inverso
    - Commutativo
    - Associativo
    - Distributivo
    - Assorbimento
    - De morgan
- La tabella con le leggi

    <img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled.png" alt="image/universita/ex-notion/Porte Logiche/Untitled">


**Esercizio in classe:**

$$\bar{A} + A \not= \bar{A}A$$ Dimostrare sta cosa usando le leggi di de Morgan ( e non dicendo che è la legge dell'inverso), in pratica dire che $$\bar{A} + A = \overline{\bar{A}A}$$. dsafds

### 5.1.3 Funzione booleana

Si possono utilizzare delle funzioni booleane per mappare gli zeri e uno a certi

- Esercizio in classe

    Scrivere la tabella di verità per

    $$
    A + \overline{(B + C)}B
    $$

    La soluzione è che vale solo per $$A$$, il secondo addendo è tutto


**Mintermini**

È una variabile o la negazione di una variabile

Su $$n$$ termini è l'AND fra tutti il min termine, attraverso relazioni di mintermini si può creare una funzione booleana.

È l'unica combinazione booleana in cui in una riga sola è uno mentre in ogni altra riga è falsa

**Una forma canonica**

È una somma di alcuni mintermini, e questa è unica per ogni funzione **booleana.

> La forma canonica o funzione canonica di una espressione booleana è un'espressione logica **contenente tutte le variabili booleane in forma vera o negata**, in forma di prodotti fondamentali o somme fondamentali di essi. Essa si ricava dalla tabella della verità.
>

**Circuiti combinatori**: Sono l'implementazione della funzione booleana, e sono deterministici.

## 5.2 Transistor e Array

### 5.2.1 Struttura di un transistor

Un transistor è composto da tre parti principali:

1. Un collettore che *riceve una corrente esterna stabile*
2. Una base che riceve una corrente esterna e cambia la struttura del transistor a seconda che ci sia o no
3. Un emettitore che lascia passare se c'è corrente, altrimenti si comporta come resistenza infinita.

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 1.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 1">

### 5.2.2 Nand, Not e Nor

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 2.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 2">

### 5.2.3  Array programmabili

Un insieme di And e Or che rappresentano la forma canonica per un elemento. Si possono programmare fondendo o lasciando alcuni fusibili per simulare l'uso del not, come in figura.

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 3.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 3">

## 5.3 Mappa di Karnaugh

### 5.3.1 Introduzione

È un metodo che prende la forma canonica e cerca di semplificarla con qualcosa di molto più facile da implementare (prende una forma canonica e restituisce elementi semplificati) **Non fa peggio della forma canonica** ergo una forma semplificata o uguale che dia stessi output.

Si può fare anche a 3D o 4D per permettere l'uso per più input ma non sempre è facile immaginarsi 4 dimensioni, queste devono soddisfare il codice grey.

### 5.3.2 Codice gray (specchio)

La mappa di Karnaugh deve essere un codice Gray

Costruisco con la **tecnica a specchio** cioè da una riga all'altro sto cambiando solamente una singola cifra.

Utilizzando invece la numerazione delle tabelle di verità non funziona in quanto non possiede questa proprietà.

Dalla [pagina di wikipedia](https://it.wikipedia.org/wiki/Codice_Gray)

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 4.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 4">

### 5.3.3 Esempi di applicazione

**Disegno**

Si possono scrivere in due modi, a seconda di come piace

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 5.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 5">

**Raggruppamento**

bisogna creare grossi raggruppamenti ossia catturare più uni possibile con pochi, fatto questo sono sicuro di creare una forma minimale.

<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 6.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 6">

Dopo questo scegli il raggruppamento più piccolo e sarai abbastanza sicuro che sia minimale

## 5.4 Circuiti integrati

Di solito sono **pezzi di silicone** che variano di grandezza e struttura a seconda degli input e dei output per quello che si deve fare (questi sono anche chiamati Chip)

### 5.4.1 LGA PGA

Large Grid Array, Pin grid Array.

Ci sono due tipologie di Pin per i circuiti integrati

!<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 7.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 7">
sti sono anche chiamati Chip)

### 5.4.1 LGA PGA

Large Grid Array, Pin grid Array.

Ci sono due tipologie di Pin per i circuiti integrati

!<img src="/images/notes/image/universita/ex-notion/Porte Logiche/Untitled 7.png" alt="image/universita/ex-notion/Porte Logiche/Untitled 7">

# References