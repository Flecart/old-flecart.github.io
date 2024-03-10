---
layout: page
permalink: notes/ambienti-di-sviluppo
tags: italian
title: Ambienti di sviluppo
---

Ultima modifica: March 24, 2023 7:35 PM
Primo Abbozzo: March 24, 2023 2:23 PM
Studi Personali: No

# Ambienti di sviluppo

Ambiente di sviluppo è diverso rispetto all’ambiente di deploy! bisognare fare delle differenze, sono dell macchine diverse, in questa sezione di documenti andiamo a parlare di norme e modi di lavorare per facilitare il metodo di sviluppo.

## Note di compatibilità

### Front-end

Le compatibilità, soprattutto per cose browser (quindi front-end) cambiano molto spesso, come fare a trackare queste cose? C'è un sito molto carino come [https://caniuse.com/](https://caniuse.com/) .

La **browser list**, è utilizzata per specificare unt browser di target per la nostra applicazione, non ho capito bene cosa serve.

I **polifylli* permettonol’esecuzione di codice recente

### Gestione versioni

Si utilizzano cose come package json, e tools come `npm e yarn` per gesitire queste dipendenze. Nei file `lock` ci sono gli hash, ti dice quale specifica versione funziona (praticamente serve per dirti esattamente tutte le cose necessarie per l’ambiente di deploy, per questo lo devi committare! come il go sum). È necessario, sennò sono in dependency hell (una dipendenza che aggiunge una dipendenza di altre dipendenze, può rallentare tutto), non riesco a gestire tutte queste velocemente!

Poi si dividono in

- devDependency quando è solamente per lo sviluppo come linter, o file cli
- dependency quando serve per l'esecuzione del programma.

**semantic versioning**

- Slide semantic versioning

    <img src="/images/notes/image/universita/ex-notion/Ambienti di sviluppo/Untitled.png" alt="image/universita/ex-notion/Ambienti di sviluppo/Untitled">


Ci danno già informazioni su compatibilità, versioni accettate e cose simili.

### Stile

- Strumenti come esling, prettier, permettono di fare contorllo sullo stile, e anche correggerle in automatico!

Queste fanno una **analisi statica** del codice e riformattano, oppure ti ritornano alcuni pezzi di roba ambigua.

Di solito conviene perché rende il codice molto più agibile e comprensibile dal team.

Cose come parentesi, indentazioni, sono importanti, anche ad esempio utilizzare stessi cases.

### Type checking

- Slide typescript

    <img src="/images/notes/image/universita/ex-notion/Ambienti di sviluppo/Untitled 1.png" alt="image/universita/ex-notion/Ambienti di sviluppo/Untitled 1">


Abbiamo tutte le garanzie di [Teoria dei Tipi](/notes/teoria-dei-tipi)! In pratica è molto buono utilizzare questo

### Traspiler

È simile alla compilazione, ma è fra linguaggi allo stesso livello (ad esempio versioni diverse di javascript, per essere comprensibile fra versioni browser diversi), mentre compilazione secondo vitali è da linguaggi di alto livello a uno di livello inferiore, anche se non credo fosse questa la definizione in [Macchine Astratte](/notes/macchine-astratte).

React utilizza molto **babel**, che è il traspilatore principale per questo.

### Minifier e obfuscating

vogliamo cercare di ridurre caratteri, in modo da minimizzare la grandezza del file di output mantenendone la semantica (quindi cosa faccia). Ci serve per esempio se vogliamo dare un file JS, ma vogliamo limitare la banda, per trasmettere le stesse informazioni.

Webpack, un bundler che vedremo dopo riesce anche a fare minify.

Questa cosa è molto diversa rispetto a offuscare!

offuscare serve per rendere il coidce illeggibile, in modo da rendere più difficile la comprensione del codice, e quindi da farci reverse engineering e scoprire vulnerabilità e simili ma anche per evitare di copiare l'applicaione e replicarlo altrove, anche questi sono fatti in automatico da certe applicazioni.

- Riassunto in breve traspiler minifier, obfuscating e compressione

    <img src="/images/notes/image/universita/ex-notion/Ambienti di sviluppo/Untitled 2.png" alt="image/universita/ex-notion/Ambienti di sviluppo/Untitled 2">


### Bundlers

Ci sono molti bundlers il più comune è webpack.

L’obiettivo è mettere assieme tutti i moduli js in modo che sia solo 1, quindi molto più efficiente da dare al web.

### Altro

Sta facendo una lista di un sacco di tecnologie!!! 😱.

Meglio andare a studiarseli da soli perché la lista non me ne facio niente, è utile però sapere che esistono.

Deve continuare dal testing

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |