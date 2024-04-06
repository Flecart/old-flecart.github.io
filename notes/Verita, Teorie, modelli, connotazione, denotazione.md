---
layout: page
permalink: notes/verita,-teorie,-modelli,-connotazione,-denotazione
tags: en
title: Verita, Teorie, modelli, connotazione, denotazione
---

Ripasso Prox: 17
Ripasso: December 22, 2021
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: November 3, 2021 9:14 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - ripassare da inconsistenza in poi.

- Modello è una funzione semantica?

# 5 Verità e conseguenza Logica

Questa è una necessità per stabilire il significato di una sintassi definiti.

## 5.1 Verità e Realtà

La verità ha solamente senso quando lo si relaziona con un mondo sensibile, ossia il mondo che si può percepire con i nostri sensi.

### 5.1.1 Verità parametrica e assoluta

Se un esperimento è ripetibile all'interno del mondo sensibili allora questa è considerata come una **verità parametrica**, ossia dipende da uno stato del mondo sensibile.

**verità assoluta** come le costanti della fisica.

### 5.1.2 Scienze pure e scienze molli

La differenza fra queste due è che le scienze pure non stanno parlando del mondo sensibile, ma crea un mondo a sé, astratto, in cui ha senso tutto ciò che viene detto riguardo a questo mondo preciso. Anche l'informatica è teorica.

Ma cosa è la verità senza il mondo sensibile? L'esempio che abbiamo fatto prima non funziona più.

> Le scienze molli descrivono la realtà sensibile mentre le scienze pure descrivono un mondo astratto inesistente nella realtà. (quindi fisica non è pura, secondo questo).
>

### 5.1.3 Teoria matematica

È come una storia descritta prima: **insieme di sentenze**,connotazioni.

1. Enti primitivi di un mondo
2. Assiomi che valgono in certi mondi

<aside>
💡 Gli assiomi sono come le leggi fisiche di un mondo fantastico: descrivono delle regole che valgono in un mondo preciso, e quindi si possono derivare delle conseguenze e le interazioni fra queste.

</aside>



### 5.1.4 Modello matematico

Interpretare i concetti primitivi in modo che valgano tutti gli assiomi, questo è il modello.

Quindi il modello matematico è una **interpretazione** degli enti primiti e edegli assiomi del mondo!

Non è definito a priori ma si dà il senso

- Esempio in classe

    Per esempio il mondo con i numeri colorati, quella relazione resta la stessa, posso colorare come mi pare, allora la prima proposizione della slide sono falsi

- Esempio teoria e modello

    <img src="/images/notes/Verità, Teorie, modelli, connotazione, denotazion/Untitled.png" alt="Verità, Teorie, modelli, connotazione, denotazion/Untitled">


## 5.2 Il mondo

Il mondo è una **descrizione completa** delle caratteristiche e regole del mondo (quindi oggetti, leggi e simili). Ovviamente questa è solamente una descrizione ipotetica in quanto non possiamo conoscere tutto di un mondo (non conosciamo tutto nemmeno nel mondo in cui viviamo).

Un assioma è valido solamente in alcuni mondi precisi, spesso ci interessa indagare solamente quei mondi. (È utile indagare solamente un mondo in cui quel determinato assioma valga o meno.)

Il concetto di verità **non ha senso come concetto a sé stante** in quanto dipende dal mondo in cui la proposizione è valutata

Le teorie e i modelli matematici hanno senso solamente se interpretati in un mondo particolare. Da soli no. Una proposizione ha un concetto di verità solamente se ha poi senso all'interno del mondo.

### 5.2.1 Conseguenza logica

> Data una teoria T(un insieme di sentenze) si dice conseguenza logica F di T quando F vale per tutti i modelli di T, ovvero in tutti i mondi in cui valgono le sentenze della teoria.
>

Due cose:

1. Vera per tutti i modelli T
2. Vera in tutti i mondi in cui le ipotesi G1 G2 etc è vero, ossia tutti gli assiomi sono veri.
- Miniriassunto

    Con gli assiomi sto filtrando nei mondi in cui questi assiomi siano veri, quindi prendiamo solamente mondi in cui siano veri questi assiomi, con questi assiomi e enti primitivi creiamo un mondo. Allora poi possiamo avere una semantica, un modo di interpretare che è il modello e da qua possiamo avere proposizioni e conseguenze logiche

- Detto in altri modi

    Gli assiomi creano dei sottomondi in cui esse valgono (sto filtrando sui mondi).

    F (un insieme di modelli matematici) è una conseguenza logica di T se vale in tutti i mondi in cui valgono tutte le ipotesi (assiomi) (sentenze) G1 G2 etc... di T

    Nota: più ipotesi che ho, più sto restringendo nell'insieme dei mondi, quindi avrò più conseguenze logiche, quindi diventa una cosa più interessante.


### 5.2.2 Equivalenza logica

Due sentenze sono dette equivalenti se sono soddisfatte esattamente dagli stessi mondi. (ossia filtrano sugli stessi mondi) (assiomi rindondanti uno con l'altro)

- Relazione di equivalenza per equivalenza logica

    **Considera solamente i mondi in cui valgono**

    Nel secondo caso nella slide ho come ipotesi che entrambi hanno gli stessi mondi cin cui valgono, allora è ovvio che si ha il contrario

    In modo simile si ha per il terzo caso


## 5.3 Valutazione della teoria

Quando è interessante?

Non ha senso chiedersi se un assioma è vero o falso, nemmeno se è giusto o falso, ha solamente senso chiedersi se è vero o falso in un mondo preciso. Vale allora la teoria di consistenza

### 5.3.1 Inconsistenza di una teoria

> Una teoria è inconsistente quando **non ammette nessun modello**. (ossia non ammette nessuna interpretazione degli enti primitivi in modo che valgano tutti gli assiomi)
>

Si può anche dire che l'assurdo è conseguenza logica di una teoria inconsistente, quindi è tutto vero, tutto vero per assurdo!?

Ci sono troppi vincoli, quindi sto parlando di niente (ho un insieme vuoto di modelli e quindi sto parlando del vuoto) (tutto è conseguenza logica in questo caso)

Questo vale anche il contrario, però non è dimostrabile in modo semplice anche l'altra freccia.

Quindi se è falso questo, allora ho almeno un mondo in cui tutto ciò che ho è vero! Quindi che sia consistente! (e poi la cosa bella sarebbe cercare le applicazioni pratiche di queste cose)

La Logica studia la conseguenza logica! [Introduzione a Logica](/notes/introduzione-a-logica)



### 5.3.2 Interpretazione

Si può considerare **interpretazione una funzione semantica che per ogni connotazione associa una unica denotazione**, considerato un oggetto di un mondo preciso. (enti primitivi sono connotazioni di un mondo, considerati connotazioni atomiche).

La funzione di interpretazione è descritta meglio in [Logica Proposizionale](/notes/logica-proposizionale)

Le connotazioni sono interpretate come denotazioni del mondo.

Poi ci sono funzioni del mondo e simboli del mondo.

Di solito le connotazioni composte sono ottenute da connotazioni atomiche (denotazioni del mondo) combinate tramite connettivi logici.

## 5.4 Connotazione denotazione

In informatica sono sintassi e semantica. Sarà ciò che mi serve per evitare l'uso meta-linguistico, invarianza per sostituzione è il primo teorema che serve per questo

### 5.4.1 Intuizione iniziale

In linguistica la connotazione è il significato psicologico di una parola, mentre la denotazione è la prima cosa che di solito di dà il dizionario, ossia cosa è detto effettivamente.

In breve: (→ indica il significato in informatica)

1. Connotazione: ciò che voglio comunicare, come voglio cominciare (per la logica i messaggi subliminali non sono utili) → **Sintassi** il modo in cui lo sto dicendo
2. Denotazione cosa è detto → **Semantica** ciò che voglio dire, anche considerabile come l'oggetto che viene considerato in questo mondo.

Nel caso dell'informatica l'uso metalinguistico è parlare sulle connotazioni

### 5.4.2 Teorema Invarianza delle denotazioni

> Data un qualunque contesto (un buco di una frase) e una connotazione, se sostituita con una altra connotazione, le denotazioni delle frasi restano le stesse allora quelle due connotazioni sono equivalenti.
>

Possiamo utilizzare il test di invarianza per vedere se qualcosa è metalinguistico o meno.

Se due connotazioni che possiedono la stessa denotazione hanno output diversi per certi contesti allora questo fa uso metalingusitico

**Fondamentale per l'uso metalinguistico**

### 5.4.3 Connettivi logici Intro

Per maggiore precisione sui connettivi logici guardare [Connettivi Logici, correttezza, variabili](/notes/connettivi-logici,-correttezza,-variabili)

Abbiamo bisogno di tenere certe cose fisse in modo da tenere un ordine generale fra i mondi. Questi sono i connettivi logici che hanno lo stesso senso ovunque.

Possono essere

**Binari**

Unari

0-ari

E poi quantificatori come esiste e per ogni
 in modo da tenere un ordine generale fra i mondi. Questi sono i connettivi logici che hanno lo stesso senso ovunque.

Possono essere

**Binari**

Unari

0-ari

E poi quantificatori come esiste e per ogni

# References