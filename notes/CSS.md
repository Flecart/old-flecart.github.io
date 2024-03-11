---
layout: page
permalink: notes/css
tags: italian
title: CSS
---

Ripasso: May 19, 2023
Ultima modifica: June 19, 2023 9:32 PM
Primo Abbozzo: March 6, 2023 3:14 PM
Studi Personali: No

# Elementi di ripasso

# Cascading Style Sheets

Inizialmente HTML era per la presentazione, abbiamo ancora un pò di attributi storici e tag storici per questa parte di presentazione descritto in [HTML e Markup](/notes/html-e-markup).

## Introduzione

È un linguaggio **indipendente** per la descrizione della grafica. La cosa bella è iil fatto di essere indipendente, quindi è adatto a HTML, a XML e simili.

Una cosa particolare è il **cascading** quindi il fatto che dichiarazioni più nuove sovrascrivano o espandino dichiarazione vecchie.

- Livelli di CSS (cose storiche)

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled.png" alt="image/universita/ex-notion/CSS/Untitled">


## Sulla sintassi

### Statements

- Slide struttura dei statements

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 1.png" alt="image/universita/ex-notion/CSS/Untitled 1">


La sintassi classica di uno statements CSS è in

`proprietà: valore;`

E il problema per uno sviluppatore è conoscere cosa fa una proprietà e che esista 😀

### Selettori (!!)

- Slides selettori

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 2.png" alt="image/universita/ex-notion/CSS/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 3.png" alt="image/universita/ex-notion/CSS/Untitled 3">

1. Tipologia del markup e.g. `h1`
2. Selettore di classe e.g. `.class`
3. Selettore di ID e.g. `#id`

- Slides selettori 1 pseudo elementi

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 4.png" alt="image/universita/ex-notion/CSS/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 5.png" alt="image/universita/ex-notion/CSS/Untitled 5">

1. First letter (utilizzati per il capolettera nei testi vecchi.
2. first Line
3. Before, after sono aree, che normalmente sono vuote, riempibili con `content`
4. Esempio hover, active e molte altre!
5. [https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)

- Selettori di prossimità

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 6.png" alt="image/universita/ex-notion/CSS/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 7.png" alt="image/universita/ex-notion/CSS/Untitled 7">

1. Figlio di un elemento
2. Elemento figlio diretto.
3. Successivi
4. Tutti i successivi

- Selettori di attributi

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 8.png" alt="image/universita/ex-notion/CSS/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 9.png" alt="image/universita/ex-notion/CSS/Untitled 9">

- Selettori pseudo classi strutturali

    Potrebbero essere classi ma non lo sono davvere le pseudoclassi.

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 10.png" alt="image/universita/ex-notion/CSS/Untitled 10">

- Selettori pseudoclassi

    Qui ci sono molti altr icontenuti [https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 11.png" alt="image/universita/ex-notion/CSS/Untitled 11">


### Tipi di dato

Come numero o valori assoluti (e.g. col z index, o se non specifico sono dei pixel che è pericolosa perché cambia da device a device il feeling che si avrà, la dim dei pixel cambia!) o **misure di lunghezza** che sono moltissime per CSS, vedi slide

- Slide per tipi di misura

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 12.png" alt="image/universita/ex-notion/CSS/Untitled 12">


E per i colori, come è già stato citato in [HTML e Markup](/notes/html-e-markup) :

- Slide tipi di dato per colori

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 13.png" alt="image/universita/ex-notion/CSS/Untitled 13">


## Canvas e Viewport

### Il canvas

È una area di dimensione indefinita che si amplia secondo necessità. Cresce verso destra o verso il basso.  Solitamente su screen è sempre il pixel l'unita principale, ma questo dipende dalla risoluzione degli schermi e grandezza di essi! (anche le stampanti hanno scalabilità diverse).

**offscreen drawing** è una strategia per disegnare e mostrarti solamente quando il risultato è pronto. Si disegna su coordinate negative, che non sono visibili, e poi quando è pronto copiartela in coordinata positivia.

**Viewport** è la parte visibile dello schermo. Solitamente su schermi PC ho una grandezza a piacere, è solamente una cosa che interessa principalmente ai cellulari questo viewport. esiste il tag viewport come suggerimento,  ma meglio non avere le misure di pixel.

casi in cui è ok fare pixel:

1. dire **0 pixel** per dire che non lo voglio mostrare nello schermo
2. dire **1 pixel** per avere la cosa più fine che possono avere

### Unità di misura di viewport

Sono `vh` e `vw` che rappresentano la width e height, nel pC è la dimensione della finestra, pe ri cellulari è sempre lo schermo massimo.

esistono anche cose come `vmin` e `vmax` che sono il più piccolo fra vm e vh, e il massimo, quindi utilizzo questi per sopravvivere al cambio di oreintamento per lo smartphone.

### Il flex

È la misura dello **spazio rimasto nel contenitore**. È solo una cosa che mi permette di calcolare più velocemente le dimensioni, senza che debba andare io a guardarlo.

- Slide misura del flex

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 14.png" alt="image/universita/ex-notion/CSS/Untitled 14">


## Sistema a scatole (flexbox)

Ogni elemento ha una scatola che contiene l'elemento, e se un elemento sta all'interno allora la scatola esterna conterrà l’elemento al suo interno

### Flussi, display

- Slide flussi

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 15.png" alt="image/universita/ex-notion/CSS/Untitled 15">


Per la nostra concezione occidentale questi flussi corrispondono al nostro modo di scrivere.

Solitamente se non voglio fare qualcosa di particolare non vado a specificarlo, ogni tag ha già un suo display proprio.

### Elementi della scatola (4)

- Margine
- Bordo
- Padding
- Contenuto
- Slide Scatola

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 16.png" alt="image/universita/ex-notion/CSS/Untitled 16">

- Slide tipografia per la scatola

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 17.png" alt="image/universita/ex-notion/CSS/Untitled 17">


### Flexbox

c'è moltissima altra roba sul flex box ma per ora non sono citati. È **molto flessibile** e si riesce ad adattare in modo dinamico a molte cose.

Mentre Grid assumeva di avere un coso fisso.

### Posizionamento della scatola

- Slide Position

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 18.png" alt="image/universita/ex-notion/CSS/Untitled 18">

- Slide float, left, top, bottom, right

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 19.png" alt="image/universita/ex-notion/CSS/Untitled 19">

- Z-index

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 20.png" alt="image/universita/ex-notion/CSS/Untitled 20">

- statico è il default
- Assoluto è dipendente dal canvas senza tenere conto del flusso
- Relativo è relativo alla sua posizione naturale
- fisso è relativo alla viewport.
- sticky resta in viewport quando proviamo ad uscire, altrimenti resta in canvas nella sua naturale.

Oltre `position` abbiamo anche altre proprietà, che puoi esservare in slide.

### Overflow (3)

- Overflow

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 21.png" alt="image/universita/ex-notion/CSS/Untitled 21">

1. `Visible` quando tutto il testo di overflow è visibile
2. `Hidden` quando l'overflow non si vede ed è nascosta.
3. `scroll` quando è scrollabile, e la parte di scroll toglie spazio al testo, e sono diverse nei sistemi operativi ste scrollbar, mentre in smartphone non esistono.

### Il display

- Slide display

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 22.png" alt="image/universita/ex-notion/CSS/Untitled 22">


## Fonts

**famiglia**

**Peso e stile**

**Fonts preesistenti**

**Decorazioni e spazi**

## Altre proprietà di CSS

### Ereditarietà

- Display e background non sono ereditati
- Il resto si eredita sempre.

### Important

Allora quanto caricato non viene modificato da riscritture successive.

### Ordine di cascata

- Slide ordine di cascata

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 23.png" alt="image/universita/ex-notion/CSS/Untitled 23">

- slide ordine 2

    Normali: che non sono important.

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 24.png" alt="image/universita/ex-notion/CSS/Untitled 24">


# Elementi di Tipografia (non fare)

## Introduzione

### Graphic design

- Slide riguardo storia del graphic design

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 25.png" alt="image/universita/ex-notion/CSS/Untitled 25">


Storicamente era fatta da emanuense che copiava tutto, questo lo sai, poi quando è stato inventato la stampa si è creato il nuovo mestiere del tipografo, in cui ci sono una serie di caratteri standarizzati che vengono utilizzati come struttura standard.

Divisi in 3 sezioni principali:

1. Tipografia
2. Layout (organizzazione della pagina)
3. Organizzazione iconografica (visual art della pagina diciamo)

### Tipografia

> La tipografia è la disposizione armoniosa di tipi (forme di caratteri
precostituite) al fine di creare testo leggibile e piacevole alla vista sulla
pagina e sugli schermi digitali. Si distingue dalla calligrafia, che è l'armoniosa
disposizione sulla pagina di caratteri scritti a mano ed individualmente.
>

Inizialmente era fatto con legno incavato, ma questo si rovinava molto infretta ed era molto difficile da fare. Gutemberg ebbe l'idea di farlo in piombo, utilizzando forme ben definite uguali fra di loro.

Questo è fatto in modo da mantenere un buoon **grigio tipografico**, ossia equilibrio fr aspazio bianco e stampa in nero.

Fino in questo periodo era molto difficile creare periodici e avere stampa. Questo fino a quando **linotype** (line of type) che è in grado di generare al volo la lettera di piombo dopo un tasto. Ebbe un buon successo, azienda americana. Ecco qui che si possono fare i quotidiani. (il problema è che è rumoroso, pericoloso per i fumi di piombo e il calore. etc, non è una cosa da ufficio).

**Meccanismi fotosensibili**

Questa è una stampa automatica che utilizzano un fenomeno fisico e una carta fotosensibile, questa è l'industria di stampa a freddo, ossia **cold type**. E in questo periodo nasce l'informatica, e nacque l’idea di controllare automaticamente questo processo con un programma.

**Markup languages**

Questi sono linguaggi nati per controllare le macchine per la stampa a freddo, escono linguaggi come GML, oppure POSTSCRIPTS di Adobe, al tempo una piccola startup di Silicon valley, che poi inventa anche i PDF (versione indipendente dall’hardware, semplificato e molto portabile a differenza di postscript). Questo aiuta la crezioen di **desktop publishing**, quindi facile da stampare una volta disegnato sul computer.

## Font

> Collezzioni di carattere con un certo stile che si possano disporre in modo armonioso. (solitamente per lettere, punteggiatura e numeri).
>

### Font family e font type

> Un **font** è una collezione di forme di caratteri integrate
armoniosamente per le necessità di un documento in
stampa
>

> Un **type face** (o font-family) è uno stile unico di caratteri
che viene espanso in molti font di dimensione e peso e
stili diversi.
>

### Tipologie di font (5)

Solitamente i font sono una arte occidentale, c’è molta meno teoria per i font delle altre culture.

- Slide tipologie di font

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 26.png" alt="image/universita/ex-notion/CSS/Untitled 26">


### Classificazione di Font (non farlo)

- Slide classificazioen francese Vox Atypl

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 27.png" alt="image/universita/ex-notion/CSS/Untitled 27">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 28.png" alt="image/universita/ex-notion/CSS/Untitled 28">

- Slide classificazione Novarese

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 29.png" alt="image/universita/ex-notion/CSS/Untitled 29">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 30.png" alt="image/universita/ex-notion/CSS/Untitled 30">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 31.png" alt="image/universita/ex-notion/CSS/Untitled 31">


Le componenti fondamentali di un font: (tanti modi per valutare!)

1. Cap
2. Serif or sans serif
3. The strokes
4. Ascender or descenders
5. height or x-height (altezza media delle lettere, di solito la x).
6. Letter spacing or kernel
- Slide componenti fondamentali

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 32.png" alt="image/universita/ex-notion/CSS/Untitled 32">


Bisogna fare **distinzione fra stili e pesi**, solitamente l'italico è diverso dal normale, non è solamente l’obliquo (il normale leggermente inclinato) e posso avere grandezze (aka pesi) diversi che mi vanno a determinare quanto sono bold.

**Blocchi**

Sono una organizzazione del testo, che può essere di tanti tipi.

Ci sono certe cose che i tipografi non piaccino come vedove, caccole di mosca, orfani, rivoli o header separati, bandiere

## Colore

Cosa che mi ha stupito è che l'occhio proprio riesce a percepire solamente 3 colori differenti (**wavelengths**) che poi vengono interpretati in modo differente).

- Slide spazi di colore

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 33.png" alt="image/universita/ex-notion/CSS/Untitled 33">


### RGB e RGBa

Sono una forma di colore **additivo** con un canale di Alpha. Se metto tutti i colori ho il bianco. Solitamente questo non è una cosa lineare.

- Slide RGB

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 34.png" alt="image/universita/ex-notion/CSS/Untitled 34">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 35.png" alt="image/universita/ex-notion/CSS/Untitled 35">


### CYMK

Sono dei colori **Sottrattivi**, quindi aggiungendo tutti ottengo il Nero. Nella pratica il quarto colore è necessario, anche se non lo sarebbe nel senso teorico (avrei un marrone strano senza il nero, ).

- Slide CYMK

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 36.png" alt="image/universita/ex-notion/CSS/Untitled 36">


## Page Layout

Un altro componente molto importante del design è il layout, ossia una

> Page layout è la disposizione aromoniosa degli
elementi visuali sulla pagina.
>

### Un pò di storia

Storicamente alcuni elementi come la spessore delle pagine era molto importante (perché questo implicava la visibilità o meno del carattere dall’altra parte della pagina.) Una carta di lusso era importante lo spessore, la ruvidità.

Anche lacuni problemi riconducibili ad affiancamento di pagine, che potrebbero dare un altro significato. Quindi importante andare anche a controllare il contenuto intorno.

### Aspetti di Page Layout (6)

**ORIENTAMENTO**

- Slide orientamento

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 37.png" alt="image/universita/ex-notion/CSS/Untitled 37">


Storicamente i computer sono sempre stati **landscape**, così come erano i video del cinema. Con l’arrivo dei cellulari abbiamo cominciato a preferire l’orientamento **portrait**. A livello naturale circ a 10 pollici c’è uno switch.

Questo è importante perché a seconda del nostro target decidiamo il layout.

**ASPECT RATIO**

- Slide aspect ratio

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 38.png" alt="image/universita/ex-notion/CSS/Untitled 38">


Ci dice il **rapporto fra altezza e larghezza**. E ce ne sono molti di aspect ratio.

- Il quadrato non è mai stato utilizzato in editoria, ma solamente in opere d’arte carine.
- US letter è la carta delle stampanti, anche quello per le lettere di mail
- 4/3 è quello dei film, fino ai 2002.
- 11/8 poi è messa bandina nera sopra e sotto per essere adatta a 4/3 Holliwod
- ISO216 è la carta A4 e ha certe proprietà particolari
- 16/10 è il rapporto classico dei computer, molto vicino al rapporto aureo.
- US Legal è una carta un pò più lunga utilizzata nella pubblica amminsitrazione
- 16/9 sono schermi allungati, utili per TV nuove. Molto bello quando ho dei panorami nei film, quindi schermo così meglio.
- 18/9 Per smartphone, perché per le dita non mi conviene allungarl inell’altro verso, quindi meglio farli lunghi.
- Altre su ragionamenti simili.

**DIMENSIONI**

- Dimensione

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 39.png" alt="image/universita/ex-notion/CSS/Untitled 39">


Il fatto che sia radice, è molto importante perché ci permette di **duplicare** con due fogli. Si parte con A0 che è **un metro quadro**.

**RISOLUZIONE**

- Slides risoluzione

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 40.png" alt="image/universita/ex-notion/CSS/Untitled 40">


Se siamo ancora in ambiente anglossassone, utilizziamo come unità di misura il pollice. Normalmente è di **densità** (importante soprattuto per la stampa digitali), ma attualmente è il **valore assoluto** di pixel nello schermo.

**GRIGLIE DI LAYOUT**

- Slides griglie

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 41.png" alt="image/universita/ex-notion/CSS/Untitled 41">


Lo scopo principale dei Layout è **allineare in maniera bella**. Solitamente il numero bello è 12, perché si possono creare dei bei rapporti, infatti anche twitter boostrap utilizza questo formato.

Una griglia può essere densa o con molto spazio, in questo caso si dice che le celle hanno **breathing**.

**SEZIONE AUREA**

- Slides sezione aurea

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 42.png" alt="image/universita/ex-notion/CSS/Untitled 42">

    <img src="/images/notes/image/universita/ex-notion/CSS/Untitled 43.png" alt="image/universita/ex-notion/CSS/Untitled 43">


È un rapporto che sembra molto carino.