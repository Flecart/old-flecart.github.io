---
layout: page
permalink: notes/metadati-web-e-web-semantico
tags: italian
title: Metadati web e web semantico
---

Ripasso: May 19, 2023
Ultima modifica: May 11, 2023 8:38 PM
Primo Abbozzo: May 5, 2023 2:21 PM
Studi Personali: No

# Elementi di ripasso

[https://csunibo.github.io/tecnologie-web/lucidi/teoria/23-metadati.pdf]([https://csunibo.github.io/tecnologie-web/lucidi/teoria/23](https://csunibo.github.io/tecnologie-web/lucidi/teoria/23)-metadati.pdf)

[https://csunibo.github.io/tecnologie-web/lucidi/teoria/24-a-web-semantico-lod-rdf-json-ld.pdf]([https://csunibo.github.io/tecnologie-web/lucidi/teoria/24-a-web-semantico-lod-rdf-json](https://csunibo.github.io/tecnologie-web/lucidi/teoria/24-a-web-semantico-lod-rdf-json)-ld.pdf)

# Metadati web

### inconfrontabilità del sapere

- Stessa informazione in forme diverse
- Stessa parola per cose diversa.

### Serializzazione

<img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled">

La semantica è relegata alle **applicazioni** che devono decidere in che modo interpretarli, oppure esseri umani.

### PICS

**Platform for Internet Content Selection** vuole cercare di tenere sotto controllo i materiali del film. È un sistema di rating. → **tanti criteri di classificazione** a seconda dei criteri ideologici su cui voglio andare a basarmi.

- Classificare e categorizzare, non`e una cosa centralizzata da parte di un governo.
- Fonte terza, non è né l'usufruitore ne il creatore → metadati = dati sui dati.

### Metadati

- Slide medatati

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 1.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 1">

- vantaggi e svantaggi

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 2.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 2">


## Tesauri e tassonomie

Si parla di gerarchizzazione e di relazione fra parole dello stesso livello

### Tassonomia

- linneo
- Esempio di tassonomia
- La cosa che generalizza

### Esempi di relazioni

- has_a
- is_a
- instance of

### Classificazione a faccette

possibilità di descrivere un oggetto complesso attraverso un insieme di
affermazioni appartenenti ad uno schema fisso di proprietà, ciascuna
delle quali in grado di usare valori da un apposito tesauro.

### Ontologie

- Vocabolario controllato
- Organizzato in thesaurus

Una ontologia è un sistema di classi, descritta da proprietà che hanno valori puri o riferimenti ad istanze di altre classi (credo che questa cosa sia molto simile anche in database o simili).

- Critica alle ontologie

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 3.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 3">


> Complessivamente, sono un approccio costoso, ingessato, non democratico,
centralizzato e riduzionistico.
>

### Folksonomie

# Semantic web

### Resource description framework - RDF

Sono delle triple soggetto predicato e oggetto, e posso creare degli alberi che sembrano delle tassonomie a riguardo.

Una cosa interessante è che **tutto è identificato da URI**, nomi, predicati e oggetti, a volte ci sono degli elementi vuoti chiamati **blank nodes**.

bisogna distinguere questo formato di triple con il formato di serializzazione che è la forma in cui sono rappresentati sottostante.

### Problema delle relazioni n-arie

### Reificazione 🟥

La differenza principale con la modellizzazione a relazione n-aria è che il blank era il soggetto e tutti erano oggetti di questo, mentre ora ogni cosa può essere soggetto oppure oggetto. In particolare rdf:statement  sub, pred, obj,  ci sono sempre queste predicati per la reificazione.

- Slide reificazione

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 4.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 4">


Ma ha un problema per i databases perché non vengono trovati le relazioni soggetto - predicato - oggetto classici.

### Named graph

- Slide named graph

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 5.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 5">


ossia ho sempre delle triple, ma queste sono messe a livello differente.

## Serializzazioni

Serializzazione significa dare una **sintassi** per andare a descrivere le informazioni di rdf in modo che sia possibile metterli in database.

### Turtle

### RDF/XML

### JSON-LD

## Generazione di conoscenza

- utilizzare il database RDF per andare a generare nuove informazioni
- Andare a verificare la coerenza delle informazioni che abbiamo già

### RDF schema

È l'insieme dei concetti possibili per un certo RDF.

- Slides rdf schema

    <img src="/images/notes/image/universita/ex-notion/Metadati web e web semantico/Untitled 6.png" alt="image/universita/ex-notion/Metadati web e web semantico/Untitled 6">


### Web Ontology language (OWL)

### SPARQL

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |

4 esercizi

- 5 domande di base da rispondere (regola css tag html?, in cui bisonga essere veloci, valgono 6 sui 34 totali)
- HTML CSS in cui si va a ricreare una pagina HTML. 10 punti su questo
- Javascript, che sono tutit identific secondo il prof, in cui bisogna interrogare un servizio serverside, e visualizzarle in modo sensato, con anche delle operazioni da fare. 12 punti
- O semantic web , o componenti in angular, react o vue. 6 punti., con anche dei bonus.
e un servizio serverside, e visualizzarle in modo sensato, con anche delle operazioni da fare. 12 punti
- O semantic web , o componenti in angular, react o vue. 6 punti., con anche dei bonus.