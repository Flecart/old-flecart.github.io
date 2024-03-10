---
layout: page
permalink: notes/logica-del-primo-ordine
tags: italian
title: Logica del Primo ordine
---

Ripasso Prox: 4
Ripasso: December 14, 2021
Ultima modifica: October 18, 2022 6:01 PM
Primo Abbozzo: December 1, 2021 9:56 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Definizione per induzione strutturale delle variaibli libere
    - Cosa sono le due funzioni n-arie definite nella sintassi?
    - Riguardare registrazione 09/12 (10 minuti iniziali in cui riassume tutta la logica del primo ordine)
    - i nomi tecnici per dire termini e proposizioni
- Ancora da definire
    - Le proprietà delle equivalenze logiche notevoli
    - Quali sono le equivalenze notevoli del per ogni e dell'esiste?
    - Rivedere sostituzione in logica di primo ordine
    - Registrazione 16/12  per prove di sostituzione o dim con primo ordine.

# 10 Logica del primo ordine

## 10.1 Introduzione

Questa è la logica più utilizzata dai matematici

### 10.1.1 Limitatezza della logica proposizionale

La logica proposizionale classica non è in grado di ragionare sull'infinito

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled">


Fino ad ora abbiamo utilizzato una metalogica per giustificare il per ogni e l'esiste nelle dimostrazioni fin'ora.

Dobbiamo quindi dare una definizione più formale dei **quantificatori**.

### 10.1.2 Obiettivo della logica del primo ordine

Si può quindi identificare come l'obiettivo della logica di primo ordine l'introduzione dei quantificatori dell'universale e dell'esiste

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 1.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 1">


Possono denotare

## 10.2 Sintassi

In questa sintassi stiamo dividendo in Termini e proposizioni (le proposizioni che si possono trovare nella logica proposizionale classica).

- Sintassi

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 2.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 2">


Come si può osservare nella sintassi di logica del primo ordine estende la logica proposizionale classica perché per P 0 ho le singole proposizioni

Quindi si divide in un **dominio di discorso**, ossia l'insieme dei termini possibili come costanti e le**formule o proposizioni** che possiedono un valore di verità.

### 10.2.1 Perché primo ordine

Si chiama logica di primo ordine perché non si possono utilizzare le funzioni sulle variabili nel dominio di discorso.

Questa è l'ultima logica in cui vale ancora la completezza, e la correttezza, nelle logiche superiori non sarà più possibile catturare tramite un concetto sintattico il valore semantico.

Questa è la logica di primo ordine che basta ai matematici per fare tutto (questo perché le funzioni dei matematici in realtà sono degli insiemi, non qualcosa che calcola).

### 10.2.2 Possibili denotazioni

- Possibili denotazioni

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 3.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 3">

1. Oggetti ignoti nel dominio
2. Oggetti fissati
3. Connotazioni di denotazioni oggetti
4. Connotazioni di denotazioni di valori di verità

## 10.3 Semantica

- Introduzione

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 4.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 4">


Questa parte è approfondita dopo con mondo ed interpretazione

## 10.4 Binder

I binder sono un concetto fondamentale nell'informatica (soprattutto a chi andrà a fare i compilatori). Quindi stiamo astraendo un livello di semantica! Connettivi ancora più astratti.

> I binder legano una **variabile** e uno **scope** (Cattura una variabile (o serie di varaibile) in uno scope che viene valutato più e più volte).
>
1. Formula matematica (uno scope nel senso di derivata, integrale sommatoria e simili)
2. I Simboli logici per ogni esiste.

Vado a valutare una unica formula all'interno di uno scope (e continuo ripetutamente a sostituire e calcolare su tanti valori, e restituisco il risultato sintetizzato).

### 10.4.1 Shadowing

Nei binder non si può accedere alle variabili esterne se hanno lo stesso nome, si dice **shadowing** (quello interno nasconde l'esterno, quindi fa ombra, nasconde).

Un esempio è ridichiarare un parametro formale in una funzione.

### 10.4.2 Diagrammi di legame

Sono molto utili per capire le variabili del binder e lo scope di queste variabili

Cose da fare:

1. Legare variabile a ogni binder e lo scope
2. Esistono le variabili che non vengono mai legate, si dicono variabili libere queste (come libreria o variabili globali), queste si indicano conuna freccia all'infinito con il nome

### 10.4.3 Variabili libere

Queste variabili non sono modificabili (come provare a cambiare il nome di una funzione di libreria esterna).

- Definizione per induzione strutturale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 5.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 5">


## 10.5 alfa-convertibilità

Si chiama alfa perché una branca dell'informatica che studiava i lambda, cuore del linguaggio di programmazione funzionale.

> Si dice che una serie di formule sono alfa-convertibili se il diagramma di legame creato dalle formule è uguale → **relazione di equivalenza**
>

Essendo una relazione di equivalenza possiamo lavorare su una classe di equivalenza, quindi sarebbe bene ragionare al livello di **insieme quoziente delle formule**.

- Esempi

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 6.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 6">

    Nell'esempio in giallo, la Z fa shadowing, ha cambiato una variabile che in primo momento apparteneva a uno scope esterno.

- Altro esempio

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 7.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 7">


### 10.5.1 Sostituzione in logica primo ordine

Praticamente questa nozione ci dice che una funzione ha lo stesso output anche se quello che ci va dentro è una variabile con un nome diverso. Questa nozione ha una certa similitudine con la funzione di sostituzione, in quanto entrambi parlano di invarianza sulla sostituzione di variabili.

La differenza principale è che questa parla di binder mentre quella di prima parla di stesso valore di verità di una proposizione.

Possiamo allora definire una funzione di sostituzione anche per la logica del primo ordine che faccia attenzione anche ai diagrammi di flusso e i binder

- Sostituzione

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 8.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 8">


## 10.6 Mondo o interpretazione

Non è più sufficiente avere un mondo indicato solamente come una v, ma **è necessaria una coppia ordinata**: (A, l) dove A è l'insieme non vuoto di denotazioni, mentre l è simile alla vecchia funzione semantica v, però associa degli elementi in A altri elementi in A, non dice niente sulle connotazioni.

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 9.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 9">


### 10.6.1 Nozione semantica di per ogni ed esiste

- Esempi di formalizzazione sintattica errata

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 10.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 10">

    Per esempio: elefante è una connotazione, mentre la denotazione è quell'animale in carne ed ossa, non posso manipolare delle denotazioni in questo caso, quindi non avrebbe senso utilizzarlo.

    Nel secondo caso sto testando molte più cose (connotazioni sono molti di più rispetto alle denotazioni in quanto esistono i sinonimi)


L'idea principale è tenersi una lista (una mappa) che associ nomi (connettivi) e denotazioni del mondo, questa è **l'ambiente** indicata con la lettere csi.

### 10.6.2 Semantica della logica primo ordine

- Ricorsione strutturale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 11.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 11">


### 10.6.3 Conseguenza logica in Primo ordine

Dobbiamo prendere in questo caso considerazione della definizione più complessa del mondo (ricordarsi che nelle logiche di ordine superiore è proprio questa ulteriore complessità che non permette di avere una completezza).

Quindi dobbiamo tenere conto del significato di **(A, l), $$\xi$$.**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 12.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 12">


## 10.7 Proprietà esiste e per ogni

Queste proprietà espandono la lista CAIDANA delle proprietà presenti in [Connettivi Logici, correttezza, variabili](/notes/connettivi-logici,-correttezza,-variabili).

### 10.7.1 Completezza debole

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 13.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 13">


### 10.7.2 Commutatività e non

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 14.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 14">


chiaramente se Sono gli stessi x e y in due per ogni es $$\forall A, \forall B$$ questo è uguale a dire $$\forall B, \forall A$$, stessa cosa per l'esiste.

Ma il senso della frase cambia nel caso in cui abbia un per ogni e in seguito un esiste.

### 10.7.3 Semidistributività

In certi casi (non per tutti) posso spostare (addirittura eliminare!) i quantificatori

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 15.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 15">


### 10.7.4 De morgan

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 16.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 16">

### 10.7.5 Equivalenze notevoli

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 17.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 17">

- Altro ancora

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 18.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 18">


## 10.8 Deduzione naturale

In questa sezione di appunto andiamo ad indagare le regole della deduzione naturale per la logica di primo ordine, per questo motivo linko la deduzione naturale in ambito proposizionale [Deduzione naturale](/notes/deduzione-naturale)

Vogliamo utilizzare delle cosa uguali a meno di alfa conversione.

### 10.8.1 Introduzione Per ogni

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 19.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 19">

    Attento che Y non deve affatto appartenere alle variabili libere delle foglie!

    Questo mi dice che devo utilizzare solamente solamente una variabile che non è stata già presa (quindi libera, data dall'esterno)

    **Suggerimento:** per non sbagliare mai ti basterebbe prendere una variabile mai presa prima.

    /to

- Correttezza ed invertibilità intuizionista

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 20.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 20">

- Correttezza classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 21.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 21">

    Io sintatticamente ci metto y e il mondo mi risponde xi y. Ora l'ambiente xi mi dice che x vale xi di y e quindi è la stessa. Ma lo devo dimostrare per induzione strutturale.

- Invertibilità classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 22.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 22">


### 10.8.2 Eliminazione per ogni

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 23.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 24.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 24">

    Dovrei passare per la formula più complessa a volte! A volte è più semplice dimostrare il generale che il particolare perché possiedo induzione strutturale e simili.

- Correttezza intuizionista e classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 25.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 25">

    Anche da questo possiamo sapere che non possiamo andare a cercare tutte le variabili, sono infiniti! L'algoritmo non concluderebbe mai.


### 10.8.3 Introduzione Esiste

Questa dimostrazione è praticamente uguale all'eliminazione del per ogni, mentre l'eliminazione è simile all'introduzione

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 26.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 26">


### 10.8.4 Eliminazione dell'esiste

In questa forma io non ho nessuna informazione sulla x, non posso prendere una x che è già stata utilizzata nella conclusione C oppure nelle foglie.

**Deve essere una variabile libera!**, non deve avere nessuna altra ipotesi presa da altro.

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 27.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 27">


## 10.9 Completezza ed incompletezza di Godel 🟥

- Angelo was here 18/10/22

### 10.9.1 Primo teorema

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 28.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 28">

    Gamma voglio identificare un singolo mondo.

    Se contiene l'aritmetica ho i numeri la somma i prodotti e simili. Se gamma è consistente (quindi interessante, sennò tutto e dimostrabile, è anche un modo per dire che non ho più mondi).
    Allora **non posso filtrare in maniera da tenerne solamente uno.** il gamma deve tenere anche dei mondi in più.

    Quindi quando gamma parla di artimetica non si può filtrare fino a un singolo mondo.

    Quindi qualunque aritmetica prendo, non posso mai filtrare fino a singolo mondo!

    è una incompletezza di Gamma, ma non è una incompletezza delle regole!

- Abbozzo

    È una delle prime assolute codifiche!

    bigezione fra formule ed alberi, e la sintassi dimostrazione e poi utilizza il paradosso del mentitore (io mento) crea un numero che dice che non è dimostrabile, quindi fonde livello e metalivello per cui non può né essere dimostrabile né essere indimostrabile (altrimenti sarebbe inconsistente). Entrambe sono false

    Io sono dimostrabile se e solo se io non sono dimostrabile, quindi entrambe devono essere false.


Uno dei teoremi più storpiati dai divulgatori scientifici. Ma allo stesso tempo è uno dei teoremi più profondi della logica.

Se abbiamo abbastanza ipotesi da poter identificare solamente un singolo mondo, allora vale il concetto di terzo escluso, quindi o vale F conseguenza logica del mondo oppure not F è conseguenza logica

(nel caso contrario posso avere sia non G sia G  non sono conseguenze logiche di più mondi).

Godel **trova la P**, però quel singolo P è ben conosciuto, non è molto interessante.

### 10.9.2 Secondo teorema

Questo ha un apporto molto maggiore, molto importante, la base dell'informatica.

- Enunciato

    <img src="/images/notes/Logica del Primo ordine/Untitled 29.png" alt="Logica del Primo ordine/Untitled 29">

    Non riesco mai a concludere la consitenza della logica, dovrei rimettermi al metalivello continuamente, senza finire mai.

    Non possiamo **mai essere sicuri della consistenza di una teoria**, e alla fin fine la logica, la matematica si può paragonare alla religione da questo punto di vista. Noi non siamo sicuri che sia vero. Serve l'atto di fede.
a di una teoria**, e alla fin fine la logica, la matematica si può paragonare alla religione da questo punto di vista. Noi non siamo sicuri che sia vero. Serve l'atto di fede.