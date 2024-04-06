---
layout: page
permalink: notes/sintassi-e-ri-strutturali
tags: italian
title: Sintassi e RI strutturali
---

Ripasso Prox: 27
Ultima modifica: October 7, 2022 1:25 PM
Primo Abbozzo: October 15, 2021 10:35 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Cosa è la sintassi
    - I costituenti della BNF (ripassarreeee
    - le tre soluzioi per l'ambibuità
    - definizione di linguaggio
- Differenza funzioni matematiche ed informatiche
- Context-free-grammar per AST
- Cosa significa espandere un non terminale?

# 4 Sintassi

> Programmare e dimostrare sono sostanzialmente la stessa attività ~*Coen*
>

Ma non secondo l'industria...

## 4.1 Introduzione

### 4.1.1 Definizione e necessità

> Branca della linguistica, studia creazione di proposizione e il loro collegamento per la creazione di un periodo
>

In seguito la semantica dà un metodo a queste proposizioni in modo che abbiano un senso.

1. Utile o necessario per la definizione del linguaggio artificiale

### 4.1.2 Alfabeto, stringa, linguaggio e grammatica

**Alfabeto**: Insieme non vuoto di simboli (che spesso sono diversi fra di loro)

**Stringa** seguenza finita (vuoto è possibile) di simboli $$\epsilon = \empty$$

**Linguaggio**: insieme di stringhe (di qualunque tipo, finito o infinito).

**Grammatica** formalismo (un insieme di regole che lo rende finito) che definisce un linguaggio

## 4.2 Backus-Naur Form

Ora è descritto anche in [Descrizione linguaggio](/notes/descrizione-linguaggio)

Indicato con BNF

### 4.2.1 Perché BNF

Una formalizzazione informatica che permetta l'elaborazione di grammatiche → notazione per descrivere grammatiche

**Non è l'unica** ma per gli informatici è la migliore.

### 4.2.2 Caratteristiche

Indichiamo con $$(T, NT, X, P)$$ rispettivamente

T = **l'alfabeto**, l'insieme di simboli che usiamo

NT è un insieme di simboli diversi da T (insieme **non terminale**) Sono solamente ausigliari.

X = qualunque elemento di NT, basta che sia **iniziale**

P = simile alla grammatica, sono delle **coppie come produzioni:**  comprendono:

1. Non terminali
2. Insieme di stringhe che contengono un pò di tutto ,indicate con $$\omega_n$$

Es. $$(X, \{\omega_1 ...\omega_n\})$$ è una produzione.

Quindi questi quattro elementi riescono ad identificare in maniera univoca la semantica di un linguaggio.

Capiremo il senso di questa definizione per l'informatica fra poco.

**Indicazione**

Si può indicare con $$X ::= 0|0Y$$ e simili, utilizzando solo per produzioni come coppie è sufficiente per definire una sintassi BNF.

### 4.2.3 Definizione di un linguaggio

Di solito fra tutte è sufficiente prendere le produzioni per dire un linguaggio.(ha senso supponendo che tutti i simboli della grammatica siano utilizzati)

- Immagine di definizione

    <img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled">


Processo iterativo che parte dal non terminale e arriva a stringhe finite.

- Esercizio

    Dimostrare che 000 non appartiene a questo linguaggio

    <img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled 1.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled 1">


## 4.3 Ambiguità in BNF

### 4.3.1 Definizione ambiguità

Se si può definire in due modi diversi la stessa parola, allora si dice che il **linguaggio è ambiguo**.

### 4.3.2 Soluzione ambiguità (3)

Queste non sono sempre necessarie in ogni grammatica, ma sarebbero utili per la comprensione

1. Ordine di precedenza per operatori
2. Associatività per ogni operatore (cioè se l'operatore prende solo a destra o da sinistra)
3. Parentesi?

Così **definisco un ordine di precedenza** quindi risolvo le ambiguità, ma non dovrei fare in questo modo.

## 4.4 Albero di Sintassi astratta

Buona cosa potrebbe essere la [pagina di wiki](https://en.wikipedia.org/wiki/Abstract_syntax_tree).

Afferma che questo albero è molto utile per il compilatore (così capisce cosa stiamo provando a fare).

Un approfondimento possibile per questi alberi è la [Contex-free-grammar](https://en.wikipedia.org/wiki/Context-free_grammar) ovvero come evitare l'ambiguità del linguaggio naturale. (simile a BNF).

### 4.4.1 Definizione (4)

Prima si deve trovare una **BNF non ambigua**, poi possiamo creare un albero di questo genere.

- Definizione di albero di sintassi

    <img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled 2.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled 2">


Di solito ogni linguaggio di programmazione è prima trasformato in un albero di sintassi e in seguito il compilatore elabora su questa cosa.

### 4.4.2 Ricorsività: le sottoformule immediate

Sono figli diretti, sottoformule immediate generate dal nodo padre.

Ecco una struttura di dati ricorsiva, impareremo a sfruttare questa caratteristica della ricorsione.

Questa sottostruttura ricorsiva è molto utile perché so anche come è stato ricavato, non solo so se appartiene o meno! Più informazioni! Riusciamo ad assegnare un significato.

La cosa bella di questra struttura è che possiamo utillizzare la stessa funzione (programma o quel che si voglia chiamarlo) per risolvere il problema su alcuni dati più piccoli (sotto dati).

## 4.5 Pseudo-linguaggio funzionale puro non tipato

Altolivello- vicino dominio del problema, senza alcuni dettagli di implementazione (che farà da solo).

Basso livello- vicino al dominio della soluzione ossia tratta alivello vicino al computer.

Tutti questi linguaggi hanno un albero sotto, che cerca di utilizzare questa grammatica formale per capire ciò che è scritto.

<img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled 3.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled 3">

### 4.5.1 Significato del nome

**Pseudo linguaggio**  perché questo linguaggio non esiste realmente, è solamente qualcosa di simile, di vicino al un linguaggio reale (meno sintassi diciamo)

**funzionale** si utilizzano funzioni, sia come input, output  per memorizzare cose e simili

**Puro** senza side effect, senza storare variabili e fare cicli while o for

**Non tipato** senza che un compilatore si lamenti di come è implementato il tipo, quindi maggiore astrazione anche da questo punto di vista

### 4.5.2 Funzioni unarie (3)

Le funzioni unarie sono definite da tre parti principali:

1. Il nome della funzione
2. Un pattern $$\omega$$, di solito una stringa dell'alfabeto
    1. Variabili → Non terminali
    2. Costruttori e simili → terminali costruiti con la gramatica del linguaggio.
3. Corpo, quello che è dentro la funzione
    1. Chiamate ad altre funzioni
    2. Parametri formali e altre costanti
    3. Condizioni di control flow

### 4.5.3 Pattern matching

Questa è la definizione di matching

<img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled 4.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled 4">

In modo intuitivo: Match = se $$p$$ terminale matcha $$\omega$$ se partendo da $$\omega$$ si può creare $$p$$

**Chiamate di funzione**

In questo linguaggio funzionale, andremo ad utilizzare Haskell, la chiamata di funzione avviene per pattern match.

Passo a sostituire i parametri formali a seconda di cosa matchi, ricostruendo tutto continuando.

### 4.5.4 Side effects

Questi linguaggi funzionali non devono avere side effects, ossia non devono accedere a locazioni di memoria fuori dal loro scope, o fuori dai propri parametri formali, quindi molto più controllabile.

Ma questo significa che non abbiamo la libertà di allocare memoria e simili.

### 4.5.5 Potenza espressiva

Noi non possiamo programmare tutto quello che la matematica può fare.

Ma certe cose si possono fare in un linguaggio e non in un altro. Ma qualunque funzione in qualunque altro linguaggio potrebbe essere espresso nello pseudo-codice attuale (quando questa cosa accade **Turing-completezza**).

Ma dato che non abbiamo side effect non ci interessa I/O  e video o simili.

## 4.6 Ricorsione strutturale

<img src="/images/notes/image/universita/ex-notion/Sintassi e RI strutturali/Untitled 5.png" alt="image/universita/ex-notion/Sintassi e RI strutturali/Untitled 5">

### 4.6.1 Solito ragionamento per ricorsione

Come di solito le ricorsioni, se è un caso base allora risolvo subito, in modo diretto.

Altrimenti risolvo ricorsivamente un sotto problema più facile, ma è ancora lo stesso problema, ecco perché strutturale → Hanno la stessa struttura, quindi sto utilizzando la stessa funzione per risolvere lo stesso problema ma per input diversi.

Quindi risolvo problemi più piccoli e poi le ricompongo alla maniera iniziale.

1. Strutture uguali (cioè i sottodati devono essere ancora dei tipi dei dati iniziali, se ho in input lista di qualcosa e poi ho totalmente altro non posso fare).
2. Risolvo così problemi più semplici in modo ricorsivo.

### 4.6.2 Errori comuni

DI solito la ricorsione è difficile perché le persone tendono a cercare di scoprire in che modo sia implementata la ricorsione, cioè cercano di comprendere cosa faccia la ricorsione a livello troppo basso.

- Chiamate ricorsive non sui sottoproblemi
- Struttura della ricorsione è errata (usando produzioni inesistenti)
- Mancare di qualche produzione

### 4.6.3 Esercizi Ricorsione strutturale

Questi esercizi sono importanti dato che poi all'esame dovrai risolvere qualcosa di simile!

- Es 1

    ```haskell
    -- Problema 1: data una lista (di numeri)
    -- calcolare l'insieme potenza della lista
    ```

- Es 2

    ```haskell
    -- Problema 1: data una lista (di numeri)
    -- calcolare la lista di tutte le permutazioni
    -- della lista in input
    -- Es: dato 1:2:3:[], restituire
    -- (1:2:3:[]):(1:3:2:[]):(2:1:3:[]):(2:3:1:[]):
    --  (3:1:2:[]):(3:2:1:[]):[]
    -- Soluzione: per l1
    ```

- Es 3

    Uno tostino come esercizio è definire una funzione che ritorni vero se e solo se un elemento compare due volte nell'insieme.

- Es 4

    **N ::= O | S N**

    dove il
    simbolo terminale O rappresenta lo 0 e il simbolo terminale S, letto
    "successore", dato un numero naturale N forma il numero naturale S N che
     segue N nella numerazione.

    Esempio: 3 viene rappresentato in base 1 come S (S (S O)))  e 5 come S (S (S (S (S O)))).

    Nota:
     la rappresentazione corrisponde al modo con cui i bambini imparano a
    contare, usando le dita. O è il pugno chiuso e ogni S corrispondere ad
    aggiungere un dito.

    **Problema 1**: definire per ricorsione strutturale una funzione + sui numeri naturali in base 1 che ne implementi la somma

    Esempio:  S (S O) + S (S (S O))) = S (S (S (S (S O)))))

    Suggerimento: procedere per ricorsione strutturale sul primo argomento

    **Problema 2:**

    definire per ricorsione strutturale una funzione * sui numeri naturali in base 1 che ne implementi il prodotto

    Esempio: S (S O) * S (S O) = S (S (S (S O))))

    Suggerimento: per implementare il * potete usare il +

    **Problema 3:**

    definire per ricorsione strutturale una funzione ^ sui numeri naturali
    in base 1 che elevi il primo numero alla potenza indicato dal secondo

    Esempio: S (S O) ^ S (S (S O))) = S (S (S (S (S (S (S (S O))))))))

    Suggerimento: scegliere bene su quale input procedere per ricorsione strutturale


Questi dovrebbero essere difficili, se sai risolvere questi, dovresti essere in grado di farlo per tutti.

## 4.7 Induzione strutturale

Questa è una **tecnica dimostrativa** per dimostrare che una struttura gode di una certa proprietà.
È strettamente legata alla ricorsione perché la ricorsione è il calcolo della soluzione mentre l'induzione la dimsotrazione della correttezza.

Questa forma di dimostrazione è valida per ragioni molto simili alla ricorsione strutturale, perché ogni passo è giustificato dal precedente, di cui il caso base è assunto come vero.

Quindi bisogna prima capire quali siano le differenze fra induzione e strutturale.

### 4.7.1 Il procedimento

1. L'output deve essere una dimostrazione
2. Si suppone che valga per tutti i sottocasi di questo di input (in pratica uguale alla ricorsione, per tutti gli sottoinput immediati stiamo supponendo che valga) come in matematica puoi affermare che valga per tutti i numeri minori di n come **ipotesi induttiva.**

## 4.8 Confronto funzioni mate e info

Questo paragrafetto si rifà all'iniziale introduzione sui [Logica meta-linguistica](/notes/logica-meta-linguistica) sui paradossi in matematica e informatica.

### 4.8.1 Matematica

Rappresentazione è fatta con relazioni, sottoinsieme del prodotto cartesiano. Questa è **inefficiente** dal punto di vista del calcolo in quanto non ci da un modo per creare un calcolo. (non posso scorrere perché le liste restano illimitate).

Si in questo caso stai pensando alle [Relazioni fra insiemi](/notes/relazioni-fra-insiemi) non al modo per calcolarle.

### 4.8.2 Informatica

Di solito gli algoritmi ragionano in modo simile in basi diverse, that is l'efficienza degli algoritmi è molto simile in basi diverse, tranne in base 1 che è esponenzialmente più grande rispetto alle altre basi.

- Esempio di def. di funzioni somma

    ```haskell
    O `+ m = m
    S n `+ m = S (n `+ m)
    -----
    n +' ) = n
    n +' S m = S (n +' m)
    ------
    O ``+ m = m
    S n ``+ m = n ``+ S m
    -------
    n +" O = m
    n +" S m = S n +" m
    ```

    Queste sono quattro procedure di calcolo per la somma non uguali in quanto calcolano diversamente.

    Il prof. ha detto (non ho capito il motivo) per cui quelli con un singolo apice utilizzano la stack, mentre invece quelli con due apici utilizzano la heap), non ho capito perché,  ma tanto lo spiegherà ad architettura.


### 4.8.3 Specifiche di funzioni

Possiamo utilizzare le dimostrazioni per induzione strutturale per verificare la correttezza di una funzione.

Per esempio una funzione di concatenzazione dovrebbe soddisfare questi teoremi

Di cui il primo mantiene il numero , il secondo appartenenza, il terzo l'ordine.

1. $$|l_1  fl_2| = |l_1| + |l_2|$$
2. $$x\in l_1 \implies$$ $$l_1fl_2$$
3. $$\forall n, n \leq |l1| \implies$$ nth n l1 = nth n (l1@l2) $$\wedge$$ $$\forall n, n\leq |l2| \implies$$ nth n l2 = nth (|l+1| +n) (l1@l2)

Se una funzione soddisfa questi teoremi allora possiamo definire in modo rigoroso una funzione.

- Funzioni helper per questo

    ```haskell
    cat [] l2 = l2
    cat (t:l) l2 = t:cat l l2

    length [] = 0
    length (n:l) = 1 + length l

    -- nth n l tira fuori n-elemento di l
    head [] = []
    head (n:l) = n

    tail [] = []
    tail (n:l) = l

    nth 0 l = head l
    nth (S n) l = nth n (tail l)

    nthCorto 0 (t:l) = t
    nthCorto (S n) (t:l) = nthCorto n l
    ```

    E poi dovrei verificare ogni singola funzione di questo...


Spesso nella vita reale non c'è bisogno di questo, si scriva specifica parziale
n) (t:l) = nthCorto n l
    ```

    E poi dovrei verificare ogni singola funzione di questo...


Spesso nella vita reale non c'è bisogno di questo, si scriva specifica parziale

# References