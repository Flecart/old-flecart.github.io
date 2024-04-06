---
layout: page
permalink: notes/deduzione-naturale
tags: italian
title: Deduzione naturale
---

Ripasso Prox: 15
Ripasso: December 22, 2021
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: November 10, 2021 9:33 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No


La deduzione naturale è un possibile sistema deduttivo che utilizza il linguaggio naturale per questo motivo più beginner friendly. Lo facciamo prima per la [Logica Proposizionale](/notes/logica-proposizionale) che è molto facile

## Il sistema deduttivo

Poniamo l'esistenza di Assiomi (formule in una certa logica) e [regole di inferenza](#regole-di-inferenza) definite sotto.
Esempi sono $$P \vdash \varphi$$ se $$\varphi$$ è un assioma. O altre cose simili con $$\land$$ e simili...

Una **dimostrazione** allora è una sequenza di $$\varphi_{1}, \dots, \varphi_{n}$$ dove $$\varphi_{i}$$ è derivata con le regole di inferenza e $$\varphi_{1}, \dots, \varphi_{i - 1}$$.

La differenza con la deduzione naturale è che solitamente non ci sono assiomi

## Sintassi

### Caratteristiche della sintassi (4)

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled">

Si utilizza una BNF bidimensionale per rappresentare la ramificazione di una dimostrazione in deduzione naturale (così possiamo capire bene in quale parte del ramo viene utilizzata l'ipotesi).

1. **Radice** è la conclusione, anche indicata come top.
2. **Nodi** sono rappresentate da alcune formule
3. Le **foglie** sono formule **scaricate** (con parentesi quadre), queste sono ipotesi locali che valgono solo in quel ramo (come l'analisi per l'or).
4. Le **foglie non scaricate**  rappresentano le ipotesi del problema

### La ricorsività

Come caratteristica delle BNF io opero in modo ricorsivo su sotto-alberi più semplici.

Per ogni albero utilizzo delle regole di eliminazione o di introduzione  per collegare gli alberi insieme, ecco che **utilizzo le regole di introduzione ed eliminazione per collegare le regole fra di loro** e così faccio la verifica di correttezza della dimostrazione.

## Regole di inferenza

### Sintassi delle regole di inferenza

Doppia lettura (top-down, bottom up)!

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 1.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 1">

Dove al corrispondente del numeratore si hanno le ipotesi necessarie (che nel caso siano 0 si dicono **assioma**, in modo differente rispetto all'utilizzo finora)

1. Formula di $$\Gamma$$ sono chiamati assioni
2. Regole senza ipotesi sono assiomi

Quindi questa definizione di assioma può avere più denotazioni, (ambigua?) no! perché è un insieme più grande che comprende entrambe le possibilità.

Devo dimostrare anche la verità di quelle ipotesi, posso allargare l'albero sopra!

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 2.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 2">

In modo più generale

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 3.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 3">

### Regole di introduzione ed elimitazione

Queste regole sono state per la prima volta utilizzate in [Teoria assiomatica degli insiemi](/notes/teoria-assiomatica-degli-insiemi) per i primi esercizi.

Come faccio a concludere qualcosa sapendo qualcosa?

Cosa viene ricavata da una conoscenza?

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 4.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 4">

### Regole Bottom up e top down

Di solito le dimostrazioni sono presentate come bottom up, perché è considerato più elegante, ma di solito si lavora sulla conclusione nel caso di troppe ipotesi (due letture per BNF)

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 5.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 5">

### Correttezza di una regola

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 6.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 6">

Poi si potrà dimostrare che si avrà conseguenza logica per regole assemblate fra di loro. (ipotesi scaricate, devono essere rappresentate con un implica, ricorda che scaricate vuol dire che hanno ipotesi locali).

### Invertibilità di una regola

Motivo: Ci permette di dire che le regole che stiamo dimostrando saranno poi ancora conseguenze logiche per la nostra tesi finale.

- Non scegliere regole non invertibili se posso ancora utilizzare una regola invertibile
- Valutare intuitivamente la "pericolosità" di questa regola. (come se fosse un se solo se)
- (equivalenza logica fra tante formule, mentre di solito è una formula sola);

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 7.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 7">

## Dimostrazione correttezza e invertibilità di regole classiche

### 7.3.1 AND **∧**

**L'AND intro**- corretta e invertibile.(per invertibilità, devo espandere secondo le regole della semantica).


$$
\dfrac{A \,\,\, B }{A\wedge B}
$$


Quindi la dimostrazione della regola di introduzione dell'and è vera, posso sempre spezzare quando mi pare.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 8.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 8">


**AND elim -** La regola di eliminazione ci permette di utilizzare una ipotesi a scelta collegate con il connettivo dell'and

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 9.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 9">

Regola di eliminazione classica

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 10.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 10">

- Non invertibilità

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 11.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 11">


<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 12.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 12">

Formula di eliminazione più generale

- Dimostrazione

    Ricorda associatività a destra di $$\implies$$

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 13.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 13">

- Non invertibilità parziale

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 14.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 14">


Ma si può vedere che non sia invertibile

### 7.3.2 OR **∨**

**Introduzione**

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 15.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 15">

- Correttezza

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 16.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 16">

- Non invertibilità

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 17.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 17">

    Perché è invertibile in un caso, e non nell'altro utilizzando le regole di eliminazione dell'OR ma non è ancora conseguenza logica)


Questa regola non è invertibile! Spesso  non va bene utilizzarlo.

- Esempio non-invertibilità.

    Consideriamo l'opzione $$A \vee \neg A$$ , quest è conseguenza logica in tutti mondi, la dimostrazione è molto semplice. quindi $$\Vdash A \vee \neg A$$

    Però A / quello di sopra, non è vero in tutti i mondi, quindi possiamo dire che le due non sono equivalenti, quindi non è invertibile.

    Quindi $$\not\Vdash A$$ e $$\not \Vdash \neg A$$.

    La best practice è utilizzare le ipotesi, e la top down non vale sempre, bisogna avere più ipotesi....


**Eliminazione**

In generale mi devo ridurre a ragionare nei mondi in cui solamente F1 o F2 valgono (un mondo più particolare), e poi ricompongo per dimostrare F3.

perché è possibile restringersi su un mondo particolare prima di analizzarli? Perché alla fin fine li sto analizzando tutti, ma in tempi (o rami diversi)

È una regola molto molto invertibile, quindi è da utilizzare subito!

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 18.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 18">

- Correttezza

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 19.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 19">

- Invertibilità simile a AND

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 20.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 20">


### 7.3.3 Bottom e Top

**Bottom**

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 21.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 21">


Si può notare che c'è l'armonia anche qua, non c'è nessun caso di introduzione e quindi non ho ipotesi nell'eliminazione.

Questa non è una regola invertibile, ossia non è vero che $$F \Vdash \bot$$ perché bot è sempre falso.

**Top**

Il Top è un assioma, unico assioma in questa sintassi in quanto non ho bisogno di ipotesi per dimostrarlo. (Notare che non è una foglia).

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 22.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 22">


L'eliminazione del top è inutile, perché è già insita l'ipotesi in un altro, però puoi notare che è invertibile. infatti $$F \Vdash \top$$

### 7.3.4 Implicazione materiale

**Introduzione**

Questa regola è molto forte, sia corretta sia invertibile, perché la dimostrazione possiede sia LHS sia RHS le stesse cose quasi

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 23.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 23">

- Dimostrazione invertibilità e correttezza

    $$F_1 \implies F_2 \Vdash F_1 \implies F_2$$ ovvia....


**Eliminazione**

La cosa strana è che in questo caso devo dimostrare anche l'ipotesi.

Ecco che questa non è invertibile... È la cosa che mi rende difficile la dimostrazione perché dopo quelle regole invertibili ho queste ipotesi con implicazioni e non è sempre ovvio.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 24.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 24">

- Correttezza

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 25.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 25">

- Non invertibilità

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 26.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 26">


### 7.3.5 Negazione

Questa è quello che creerà la necessità di una altra logica, perché il not me lo rende complesso..

Si può dire che Non F è una altra denotazione di questa implicazione: $$F \implies \bot$$ perché gli unici casi in cui vale questo è che le ipotesi siano false.

**Introduzione**

- Enunciato

    $$F_1 \implies \bot \Vdash\neg F_1$$

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 27.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 27">

- Invertibilità

    Molto simile a quello sopra, riesco a dimostrare l'assurdo


**Eliminazione**

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 28.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 28">


Quando riesco a dimostrare l'assurdo posso dimostrare qualunque cosa, la teoria è inconsistente.

Questo mi elimina il Not, però mi rende tutto inconsistente.‼️ In questo ramo tutto diventa invertibile! ‼️ Diventa solamente un gioco meccanico.

### 7.3.6 RAA Reductium ad abdsurdum

Questa regola è molto simile all'introduzione del not ed è necessario per avere la completezza per la deduzione semantica

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 29.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 29">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 30.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 30">


## 7.4 Derivabilità

Intuitivamente

Queste regole di derivabilità sono molto utili per stabilire l'eguaglianza fra regole diverse (quando una è derivabile dall'altra e viceversa..

<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 31.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 31">

### 7.4.1 Dimostrazione per induzione strutturale

Intuitivamente:

Date due insieme delle regole, posso fare la dimostrazione utilizzando le regole con l'altro insieme e la dimostrazione è uguale.

!<img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 32.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 32">

### 7.4.2 Derivabilità delle eliminazioni di AND

Questo teorema e dimostrazione è molto utile per stabilire l'equaglianza delle due regole, in altre parole ci sta dicendo che le due regole siano identiche.

- Enunciato e dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 33.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 33">

    NOTA: per la seconda parte sto prendendo in esame solamente un sotto-albero di interesse.


## 7.5 Armonia delle regole

Sembra che il numero delle regole di eliminazione corrisponda con il numero di regole di introduzione per ogni connettivo. (e ognuno viene corrisposto)

Eliminazione ha un caso per ogni caso di introduzione e questa utilizza le regole di introduzione.

NOTA: questo principio è molto utile per guidarci nella creazione di regole

### 7.5.1 Armonia OR

- Slide

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 34.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 34">


### 7.5.2 Armonia AND

- Slide

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 35.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 35">


## 7.6 Teorema completezza e correttezza

meglio in [Connettivi Logici, correttezza, variabili](/notes/connettivi-logici,-correttezza,-variabili)

### 7.6.1 Correttezza

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Deduzione naturale/Untitled 36.png" alt="image/universita/ex-notion/Deduzione naturale/Untitled 36">


Il teorema di correttezza stabilisce la correttezza di tutte le regole date

- Notenotenote

    Dimostrazioni di conseguenza logica

    Devi fissa il mondo porre coso giutsto e poi utilizzare la semantica del mondo.


## 7.7 Deduzione naturale in logica di primo ordine

Possiamo estendere la deduzione naturale con alcune regole di $$\forall, \exists$$ [qui](/notes/qui)
are la semantica del mondo.


## 7.7 Deduzione naturale in logica di primo ordine

Possiamo estendere la deduzione naturale con alcune regole di $$\forall, \exists$$ [qui](/notes/qui)

# Registro Ripassi

- Vecchi dubbi
    - Come si dimostra la correttezza e l'invertibilita di una regola?
    - il concetto di derivabilità
    - Perché la eliminazione della negazione non è l'introduzione del bottom?
- il concetto di armonia DA CHIEDERE

# References