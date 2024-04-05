---
layout: page
permalink: notes/html-e-markup
tags: en
title: HTML e Markup
---

Ripasso Prox: 37
Ripasso: June 3, 2023
Ultima modifica: June 18, 2023 11:27 PM
Primo Abbozzo: February 27, 2023 3:19 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# HTML

## Markup

### Introduzione alle funzioni del markup 🟩

La semantica di una parola è caratterizzata dalla mia scelta (design sul significato). Non mi dice molto, quindi proviamo a raccontare qualcosa in più.

> Definiamo markup ogni mezzo per rendere esplicita una particolare interpretazione di un testo.
>

In particolare è un modo per esplicitare qualche significato. (un pò come la punteggiatura, che da qualche altra informazione oltre le singole parole, rende più chiaro l'uso del testo).

Le informazioni aggiuntive possono essere riguardanti:

1. La struttura del testo
2. La formattazione del testo
3. Relazioni fra parti del testo.

### Tipologie di Markup (6) 🟨+

**Puntuazionale**

Questo è un markup che l’autore stesso dà. ed è fortemente ambiguo!.

> Il markup puntuazionale consiste nell’usare un insieme
prefissato di segni per fornire informazioni perlopiù
sintattiche sul testo.
>

**Presentazionale**

Effetti grafici per comunicare fine capitolo o altri simili

- Slide

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled.png" alt="image/universita/ex-notion/HTML e Markup/Untitled">


**Procedurale**

Questo è una tipologia di markup che utilizza delle istruzioni per definire la presentazione. (quindi in questa parte ci sono dei comandi!) (esempi credo siano latex o Tex)

**Descrittivo**

Vuole descrivere la struttura e la semantica di frammenti di testo. (non è procedurale, perché non gli dico pezzo per pezzo la grafica), io dico se è un testo, se è una didascalia, in modo simile a quanto fatto qui su Notion.

**Referenziale**

Quando faccio riferimento a cose esterne per risolvere il significato. Di solito fa usi di SIGLE o abbreviazioni di qualcosa

**MetaMarkup**

Se utilizzo un linguaggio per creare un linguaggi di Markup, un esempio è Word, perché con quello utilizzo il linguaggio di markup (descrittivo, su font e simili), anche HTML.

> (6Il metamarkup consiste nel fornire regole di
interpretazione del markup e permette di estendere o
controllare il significato del markup.
>

### Metodi di classificazione di markup

- Standard privato oppure pubblico
- Se è interno o esterno (nel senso se si riferisce al testo interno oppure al testo esterno)
- binario o leggibile (per dire se è più fruibile per le macchine oppure se è fatto per essere fruibile per esseri umani)
- Poi si fa anche una distinzione fra procedurale (latex o troff like) oppure dichiarativi, nel senso che si taggano parti per indicarne l'utilizzo (come pe rl’HTML).

### Alcuni linguaggi di Markup (non impo) 🟥+

**GROFF TROFF, NROFF**

Questi sono scritti i linguaggi di markup per i manuali tecnici di Linux.

**TEX e LATEX**

Software di impaginazione autoomatica, principalmente per formule matematiche, perché ci metteva troppo a fare il suo libro che la casa editrice sbagliava le formule. C'è anche un **metafont** utilizzato per astrarre la fomra dei caratteri… È poi turing completo, molto difficile, moltissime keyword. È molto difficile quindi Leslie Lamport crea una libreria molto più facile da utilizzare.

**Markdown**

Una semplificazione molto semplice, con formattazioni ad hoc, utili per testi semplici, senza molta possibilità di avere cose tipografiche precise.

**JSON e YAML**

JSON (Javascript Object Notation) è un formato dati per facilitare lo scambio di dati in internet.

YAML è molto python like, che utilizza spazi come delimitatori (è superset di json, quindi capisce anche quello.). Per il resto è uguale a JSON, ma ha i commenti.

**XML**

È un sottoinsieme di SGML, che ha molte più garanzie formali. (infatti definiamo ora con BNF, ed è una complessità assurda!)

1. Ben forma (puramente sintattico)
2. Validità del documento (a seconda delle regole della grammatica cheho definito)
- Slide documenti ben formali

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 1.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 1">


### **SGML** 🟨-

> SGML (Standard Generalized Markup Language) è
uno **standard** di IBM rilasciato gratis.
SGML è un **meta-linguaggio** non proprietario di
markup descrittivo.
Facilita markup leggibili, generici, strutturali,
gerarchici.
>

È una tipologia di markup chiara, leggibile, strutturata, descrittiva e gerarchica, i primi fisici erano molto felici per questo metalinguaggio di markup.

**Struttura di un documento SGML**

1. Dichiarazione SGML
2. DOCTYPE, o dichiarazione dei nomi utilizzabili all'interno del documento
3. Istanza del documento
- Slide

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 2.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 2">

- Esempio SGML

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 3.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 3">


È uno dei Markup più importanti perché possiamo dire che sia il precursore dell'HTML

**Costituenti base di SGML**

- Elementi

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 4.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 4">

- Attributi

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 5.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 5">

- Entità

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 6.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 6">

- PCDATA

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 7.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 7">

- Commenti

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 8.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 8">

- Processing instructions

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 9.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 9">


Questa parte dovrebbe essere molto importante se si parla della parte teorica, però nella pratica mi sembra che siano in verità utilizzate pochissimo, sono comuqnue interessanti sapere che esistano

### XML

Questo è un sottoformato di SGML, ed è utilizzato principalmente per fare una **verifica formale** che tutti i tags dichiarati siano a validi e cose simili.

- Slide XML, strumenti di checks

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 10.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 10">


Un esempio è il tag che non contiene niente, allora è nella forma `<.../>`senza un altro tag che lo chiuda. E poi ci sono tutti i checks per attributi (che devono esere per forza con le virgolette, differentemente rispetto a HTML lasco che potrebbe permetterne anche senza, anche attributi senza niente potrebbe permettere per esempio, questo perché provano i browser ad accettare tipologie di documenti molto ampi.

## Un pò di storia

È importante capire un pò di storia per vedere che strano robo abbiamo oggi.

Due linee di sviluppo, uno è uno standard di W3C, l'altro è il living standard. È di fortissimo cambiamento, quindi di difficile definizione! (cambia significato sia di semantica e che di sintassi).

Nel 1997 abbiamo HTML4 che è stata considerata la versione finale, per cui un sacchissimo di siti web fino al 2008 sono stati implementato con questo HTML

### Tag Soup 🟩

I browser permettono molti tag, senza voler dare errore con l'obiettivo di essere comprensivi. Abbiamo quindi un sacco di tags, molti dei quali non sono conformi a nessuno standard. Non abbiamo una correttezza sintattica o semantica dei tags. Abbiamo in pratica troppe eccezioni.

Il problema allora diventa, quando vogliamo andare a creare un parser per questo genere di html, come andare a crearne uno che riesca a gestire queste tipologie di tags?

- Slide quirks and strict mode

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 11.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 11">


In particolare abbiamo con HTML5 una standarizzazione delle regole di parsing quindi possiamo andare ad utilizzare lo strict mode e avere più garanzie sulle pagine.

### XHTML e HTML

Le aziende dei webbrowser avevano già il codice per parsare il HTML brutto, con molti codici, e non volevano creare un nuovo parse per XHTML, molto più formale e che riusciva a garantire più codice (ossia ci sarebbe un modo unico per scrivere del codice corretto!). L'hanno proposto ai tizi del W3C che l'hanno rifiutato. Così è stato creato il working group WHATWG in cui si lavorò a una versione intermedia di HTML, che estese con alcuni tag. Dentro questo gruppo erano già presenti i maggiori player per i browser come mozilla, microsoft, e poi ci è entrato Google assumendo Ian per la creazione di chrome.

In questo moto ha vinto HTML5, che viene chiamato solamente HTML e un **living standard** che viene aggiornato ogni poche settimane.

Questo albero che viene creato dal parsing di quel modello è utile per la creazione del DOM trattato più sotto.

## HTML

### Struttura del documento 🟩

Ci deve essere una intestazione DOCTYPE che ci specifica che tipologia di documento stiamo andando a parsare (se non c'è credo sarebbe sintatticamente invalido ma ciononostante il browser è in grato di inferire come intenderlo!)

- html che include tutto
- head che include informazioni generali sul documento
- body che contiene il contenuto del sito.
- Esempio di file HTML

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 12.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 12">

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <title> Document title </title>
    </head>
    <body>
    <h1> Major Header </h1>
    <p>This is a complete paragraph of a document. I write and
    write until I fill in several lines, since I want to see how
    it wraps automatically. Surely not a very exciting
    document.</p>
    <p>Did you expect <b>poetry</b>?</p>
    <p>Here you can see a paragraph <br>
    split by a &lt;br&gt;</p>
    <hr>
    <p> A list of important things to remember: </p>
    <ul>
    <li>Spaces, tabs and returns</li>
    <li>Document type declaration</li>
    <li>Document structure</li>
    <li>Nesting and closing tags</li>
    </ul>
    </body>
    </html>
    ```


### Elementi inline 🟩

Molti sono **stati deprecati** (o non li usa nessuno), perché dovrebbero essere usati CSS per la parte grafica. Solo i, e B sono ancora presenti, o small, perché sono caratteri tipografici molto comuni!

- Esempi di elementi inline

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 13.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 13">


### Elementi di blocco e di lista 🟩

Sono i blocchi classici per rappresentare struttura di  headers, di paragrafi, e blocchi generici, o citazoini, autori.

Blocchi sequono una sequenza di lettura fra le letture!

esempio:

- <div>, un elemento anonimo, che deve essere totalmente stilato.
- <span>, la stessa coda del div, che però **non è blocco ma INLINE.**
- <h1>, <h2> …, <h6> etc

NOTA: **whitespace** è praticamente sempre ignorato, tranne all’interno del tag pre. (esiste **white-space: pre**, che permette di utilizzare whitespaces

- Slide

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 14.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 14">

- Esempio

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 15.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 15">


**Elementi di lista**

- Slide

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 16.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 16">


- Esempio elementi lista

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 17.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 17">

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 18.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 18">


### Elementi di struttura 🟩

Non vorremmo avere dei div come elementi di struttura, questo non è che sia molto chiaro dal punto di vista semantico!

Quindi introduciamo

- <section> che descrive un qualcosa di annidabile
- <article> che prende qualcosa di **self-contained** che può essere utilizzato a sé, e quindi potrei rimuoverla o inserirla senza problemi!
- Slide tags struttura

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 19.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 19">

- Slide header e footer

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 20.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 20">

- Slide nav

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 21.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 21">


- Esempio confronto HTML 4 / HTML5

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 22.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 22">

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 23.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 23">


### Anchors and images 🟩

**Anchors**

Posso metterci un fragment per gli a, questo non camibano niente nella transazione client e server, ma è il browser che capisce la locazione dopo aver scaricato tutto.

Si noti che l'attributo name non cambia la visuale del blocco, a differenza di href (che manda fuori).

- Slide anchors

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 24.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 24">


**Immagini**

Ha ancora degli attributi altezza e witdt, che rimangono ancora nonostante siano attributi rappresentazionali. Però precalcola l'occupazione dell'immagine e quindi il tutto carica più in fretta.

- Slide immagini

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 25.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 25">


Potrei includerla con una immagine, e specificare height o width (se li includo entrambi avrò resize dell’immagine senza rispettare le proporzioni, se non metto niente avrei l’immagine di grandezza naturale (px original) altrimenti se ne metto sono una avrò una resize che mantenga le dimensioni iniziali).

**srcset**, vogliamo avere tantissime immagini, che si scalino in modo automatico aseconda del device, definisco srcset e delle sizes.

- Slide srcset

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 26.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 26">


**figure **è un tag con un caption in pratica, niente di che…

### **Form** 🟨-

esistono da sempre, quindi già dall'inizio sembrava che fossero utili per fare applicazioni con un rapporto in clientside.

Creare una schermata per specificare i dati da passare a una applicazione server-side, per **creare punti di raccolta di informazioni,** e fare un **submit** all'applicazione server side, chiamata *ACTION*, .

- Slide struttura di un form

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 27.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 27">


Solitamente i metodi sono GET o POST, ma vedremo dopo con HTTP questa differenza.

I **widget** sono le cose visibili nel form, come **textarea, radio,, input select, **button*.

- Interactive forms

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 28.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 28">

- New input forms

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 29.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 29">


### Tags generali 🟩-

**Embedding**

*object* è un tag per oggetti che non sono capibili dal browser naturalmente, infatti bisogna specificare un engine con cui runnarlo.

Questo è un embedding molto, troppo generale, quindi vogliamo creare i **tags per embedding specifici**, che rende il tutto più chiaro.

- Slide per tags di embedding

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 30.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 30">


**Tabelle**

Cose come th per dire table header, or **tr** per dire table row., **td** per dire table data., e **table** per inizializzare le table

Solitamente è composta da **tre parti**. head, foot, e body, solitamente per questioni di efficienza foot deve essere messo subito dopo le head, perché ha i numeri più grandi, quindi non devo andare a ricalcolare la grandezza della tabella.

Una altra cosa interessante per le tabelle è che ci sono stiling come attributi (esempio di questo sono colspan, rowspan etc), ma dovrebbe essere di CSS, infatti questo era un modo per farlo prima di CSS.3.

Tipicamente utilizare le tabelle per fare layout è una delle cose meno accessibili che esistono! Quindi non ha più nessun senso utilizzare le tabelle di layout. (non utilizzarle, penalizza!).

## DOM

Questa parte è fatta meglio in [Javascript](/notes/javascript)

Document object model, l’obiettivo della WHATWG era costruire un parser che potesse aiutare a creare una struttura di dati utile per la creazione di applicazioni, quindi molto più tollerante rispetto a quanto proposto dal W3C e specifiche più rigide come XHTML.

> **Document Object Model**, una struttura di dati con alcune funzioni e strutture built in che permettono la facile manipolazione fornisce API. Dovrebbe essere facile creare un DOM da codice HTML così come il constrario. È esattamente quello che si vede sullo schermo!
>

*“l’importante è arrivare ad una struttura
dati in memoria unica su cui costruire applicazioni*

Dato che deve funzionare per HTML secondo la filosofia più estesa del WHATWG, è praticamente la struttura del XHTML ampliata per includere altro, questo permette al codice JS di intervenire direttamente sul DOM.

### Struttura del DOM 🟩

- Slide struttura del dom

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 31.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 31">


Ci sono alcune classi fondamentali per poter comprendere il DOM

1. Documento
2. Nodo del DOM
    1. Nodo di testo
    2. Nodo di elemento
    3. Nodo di attributo
3. Poi ci sono molte altre classi, come commendi, Datasection e molti altri che di solito si vedono poco, quelli più importanti sono il Document e i nodi descritti sopra

### Alcune classi del dom 🟩—

- Slide DOMNode

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 32.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 32">

- Slide DOMDocument e Selettori

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 33.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 33">

    Solitamente è complicato lavorare col DOM vanilla, tanto che l'hanno chiamato sadico chi ne è stato detrattore.

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 34.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 34">

- Slide DOMElement

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 35.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 35">


### Inner e OuterHTML 🟩

Andare a modificare l’HTML è molto verboso, utilizzando questi metodi è più veloce andare a creare nuovi elementi.

L’unica differenza fra i due è che Outer include anche il contenitore nella modifica, inner è solo per il contenuto

- Slide Inner e OuterHTML

    <img src="/images/notes/image/universita/ex-notion/HTML e Markup/Untitled 36.png" alt="image/universita/ex-notion/HTML e Markup/Untitled 36">


## Altre note

### Whitespaces in HTML 🟩

1. Whitespace è ignorato (soprattutto in elementi strutturali come i table)
2. Whitespace è collassato in un unico whitespace
3. in <pre> il whitespace è mantenuto.

### Cose saltate

Queste cose per completezza le cito, e sono presenti sulle slides, ma le salto per pigrizia

- Tipi di dati
- Attributi globali
- Attributi data e aria
- Entità predefinite
- Peculiarità sintattiche
- Il contenuto dell'elemento HEAD