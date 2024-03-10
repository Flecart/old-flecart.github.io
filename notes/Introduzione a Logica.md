---
layout: page
permalink: notes/introduzione-a-logica
tags: italian
title: Introduzione a Logica
---

Ripasso Prox: 23
Ripasso: December 29, 2021
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: September 22, 2021 9:38 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

Tutti i ripassi per scuola

[logica0.pdf](Introduzione%20a%20Logica%2028233c6cf8fe409e84e13237ededa891/logica0.pdf)

# 0 Introduzione

Lo scopo della logica è

- **Correttezza** del ragionamento, anche verificata attraverso algoritmi predittivi.
    - Si svilupperanno linguaggi logici
    - I metodi per la veridicità di una sentenza.
- **Possibilità** e metodi del ragionamento logico
- **Completezza e non-deducibilità** di alcuni ragionamenti
    - Necessità di completezza delle ipotesi: più ipotesi = ragionamento valido?
    - Completezza delle tesi, impossibile.

Una necessità della logica è Meta-logica:

La logica si deve cercare di basare su certe basi, spesso queste non sono certe, però danno un certo grado di sicurezza → Se la base è solida allora tutto il ragionamento di una parte è giusta

### 0.1 Storia

Questo campo di studi è nato dopo una necessità del secolo precedente quando si tentava di dare delle basi solide alla matematica → La matematica (e informatica)si fonda sulla logica.

Guardare la storia di Russel, Godel.

### 0.2 Tipologie di logica

<img src="/images/notes/image/universita/ex-notion/Introduzione a Logica/Untitled.png" alt="image/universita/ex-notion/Introduzione a Logica/Untitled">

### 0.3 Processo di ragionamento

<img src="/images/notes/image/universita/ex-notion/Introduzione a Logica/Untitled 1.png" alt="image/universita/ex-notion/Introduzione a Logica/Untitled 1">

Slide 18 per esempio di problema risolto con questo processo.

### 0.4 Differenze con la matematica

La matematica si interessa principalmente sull'**esistenza di soluzioni**, e dimostrazioni, ma non rigorose quanto le dimostraizoni logiche. L'informatica applicata classica è meno rigorosa, si basa principalmente sui test, anche se un logico può dimostrare la correttezza di una soluzione informatica.

Inoltre l'informatica indaga la possibilità di implementazione di alcune soluzioni matematiche, cioè il modo per calcolare possibili soluzioni, anche con la limitatezza delle risorse.

## 0.5 Logica in programmazione

### 0.5.1 Usi e costi

C'è un **altissimo costo per la dimostrazione formale** di un programma, secondo i dati Intel c'è bisogno di circa *10x mesi uomo* per creare una dimostrazione assistita di questo genere.

Per questo genere viene utilizzato **solamente in software critico** cioè il codice che controlla processi che se buggati possono creare ingenti danni economici, come centrali nucleari, smartcard, microprocessori Intel, controlli aereo e simili

### 0.5.2 Processo di dimostrazione

1. Definire la **specifica del software** in modo che possa fare sempre ciò che deve fare
2. Creare la **semantica** del programma, come il programma è eseguito.
3. **Formula logica** che è la descrizione formale del funzionamento del programma.
4. Creare una **implicazione** fra ciò che il software deve fare secondo la semantica e ciò che veramente fa.

## Non perdere punti

<img src="/images/notes/image/universita/ex-notion/Introduzione a Logica/Untitled 2.png" alt="image/universita/ex-notion/Introduzione a Logica/Untitled 2">

# 1 Logica Proposizionale

### 1.1 Senso e denotazione

**Sentenza**

- Dichiarativa quando è *assertiva*, ovvero dichiara una proposizione di verità.

**Nomi**

- Può avere funzioni denotative e connotative (il senso), spesso questo concerne solamente il problema denotativo

**Proposizioni**

- Sono delle sentenze che hanno un chiaro valore di verità
- Possono essere *atomiche* o *composte.*
esso questo concerne solamente il problema denotativo

**Proposizioni**

- Sono delle sentenze che hanno un chiaro valore di verità
- Possono essere *atomiche* o *composte.*