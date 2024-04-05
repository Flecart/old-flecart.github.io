---
layout: page
permalink: notes/l’intelligenza
tags: en
title: l’intelligenza
---

Ripasso Prox: 30
Ultima modifica: January 26, 2023 10:03 PM
Primo Abbozzo: June 28, 2022 8:53 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

August 22, 2022

# 1 Introduzione

L’intelligenza artificiale è un campo in velocissima espansione, con già un mercato enorme di un trillion dollars.

Inoltre il suo campo di studi spazia da moltissimi campi, è per questo che quasi potresti considerarla **universale**.

## 1.1 L’intelligenza artificiale

### 1.1.1 Cosa è (2)

Nel tempo si è cercato di definire con esattessa cosa sia l’intelligenza artificiale. In generare si è basato su alcuni parametri cardine ossia:

- La capacità di replicare attività umane / la capacità di applicare attività razionali
- La capacità di ragionare / il comportamento intelligente

Su questi due binomi sono stati fatti dei modelli, andiamo ora a scoprire in che senso l’intelligenza artificiale è intelligente.

### 1.1.2 Modelli generali

Tra i modelli presenti quello di maggiore interesse nel tempo è stato l’ultimo, per il resto vanno a toccare molti campi che sono un pò fuori dalle competenze dell’informatico. (credo)

**Agire umanamente**

Come il test di turing, definisce l’intelligenza artificiale come un software che riesce ad emulare il comportamento umano, talmente che non riusciresti a riconoscerlo.

Ma i ricercatori hanno preferito cercare di capire cosa è l’intelligenza in sé, invece di cercare di emulare quella umana.

**Pensare umanamente**

Questo modello ha un campo molto fiorente nelle *scienze cognitive*, attraverso scan delle immagini, o comunque una conoscenza approfondita in primo luogo della stessa conoscenza umana, vogliamo cercare di costruire un intelligenza artificiale che ne emuli le capacità (pensiero interiore, psicologia etc).

**Pensare logico**

Questo è stato uno dei primi metodi per costruire un software che si potesse considerare intelligente. Si basa sugli sviluppi della logica come campo di studi: ossia la possibilità di costruire software che siano in grado di dimostrare tutto il possibile.

Oppure utilizzando una analisi probabilistica, per analizzare la realtà.

**Agire logico**

L’immagine dell’agente è stato il metodo più florido nella storia dell’intelligenza artificiale nel momento in cui se ne voleva costruire una. Tanto che l’obiettivo della costruzione di un ente che potesse agire in modo logico in un ambiente si potrebbe considerare come se fosse un modello standard per la costruzione di un intelligenza artificiale.

Un problema però sorge: allineamento dei valori: a volte fare la cosa logicamente più corretta non è la migliore soluzione, esempio se l’obiettivo fosse vincere a tutti i costi una partita a scacchi, l’agente, con la possibilità di agire sull'ambiente circostante, potrebbe compiere azioni che solitamente considereremmo ingiuste, al solo scopo di raggiungere questo obiettivo! → vorremmo costruire qualche agente che sia in grado di portare un beneficio provato (dimostrato).

## 1.2 L’agente

Definiamo in modo molto generale, l’agente come qualcosa che possiede **attuatori e percettori** per interagire e percepire l’ambiente (che può essere molto vario).

Un concetto importante è che l’agente può basare il suo output attraverso solamente ciò che ha percepito (dall'inizio fino al tempo corrente) quindi potremmo considerare l’esistenza di una **funzione agente** che mappa sequenza input → azione. e l’implementazione di essa.

### 1.2.1 La razionalità

Vogliamo cercare di dare una definizione di razionalità in qualunque agente, e si può formalizzare in questo modo: **PEAS FRAMEWORK** (performance, env, actuators, sensors)

1. Una funzione di performance
2. L’insieme delle conoscenze a priori sul mondo
3. L’insieme delle azioni possibili sul mondo
4. La sequenza di percepimento

Con questi 4 oggetti, definiamo che l’agente è intelligente se la funzione che prende in input la sequenza di percezione e le conoscenze sul mondo, dia in output l’azione che massimizza la performance.

**La misura della performance**

Il modo migliore che abbiamo per misurare la performance è sulle conseguenze che ha sull'ambiente. Quindi valutare se l’effetto che ha è positivo (sempre in funzione alla positività descritta da chi ha progettato l’agente) o negativo.

Una nota: è importante costruire la performance secondo gli effetti sull'ambiente, e non secondo il modo con cui si dovrebbe comportare l’agente!

Ma non è detto che sia il modo migliore per fare ciò, è un problema più filosofico (quello sugli effetti uguali, ma uno sta basso e fa sempre, mentre l’altro è molto efficiente a momenti e per il resto del tempo sta proprio fermo).

**Onniscienza ed autonomia**

Non possiamo avere un agente che sappia tutto, bisogna tarare la performance su questa osservazione: l’azione scelta non deve essere la migliore possibile in assoluto (altrimenti l’agente dovrebbe sapere tutto) ma dovrebbe essere la migliore azione in guadagno atteso.

Questo comporta la migliore decisione che possa massimizzare scelte future (come *raccolta delle informazioni* si spende un pò di tempo per raccogliere più informazioni sull’ambiente) oppure l’azione stessa nel caso si abbia già conoscenza sull’ambiente.

È da notare che il caso in cui si ha una totale conoscenza sull’ambiente a priori (caso anche di alcune specie di animali come lowly dung beetle o sphex wasp) toglie di autonomia (ossia la capacità di agire a seconda di input ambientali e non solo secondo conoscenze a priori) all’agente, e potrebbe non dare le soluzioni volute (in questi casi l’agente agisce soltanto, perché pensa di sapere già tutto).

### 1.2.2 L’ambiente

Ci sono una moltitudine di variabili che possono risultare utili per classificare un ambiente tra cui:

1. Determinismo-nondeterminismo o stocastico
2. Osservabilità parziale-totale
3. singolo-multi agente
4. episodico - sequenziale (si basa o no su eventi passati?)
5. statico o dinamico (o semidinamico) (l’ambiente può cambiare quando l’agente pensa sul da farsi?)
6. discreto o continuo (gli stati sono infiniti o finiti?)
7. conosciuto o sconosciuto (i risultati delle azioni sono conosciute a priori, come se fossero leggi della fisica).

Per esempio, il progetto mnk-game è un ambiente che è  Determinista, totalmente osservabile, agente multiplo, sequenziale, statico, discreto e conosciuto.

Questi direi sono i 7 cardini che definiscono ad alto livello un ambiente.

## 1.3 Tipologie di agente

In questa parte vengono descritti le tipologie di agente a cui si è pensato. Parlando in generale è come se fossero dei modelli che vengono costruiti uno sopra l’altro, in senso crescente, fino ad arrivare all’agente che apprende come modello finale (correntemente più gettonato).

I modelli qui presentati sono molto astratti, utili per semplicità e chiarezza, ma non ci aiuta in alcun modo per capire come implementare tale modello, tutti gli agenti qui presentati saranno di questo tipo

### 1.3.1 Basati su riflessi

L’agente che si basa sui riflessi è il più semplice degli agenti che possono essere presenti. Come dice il nome si basa sul concetto di riflesso molto simile al riflesso umano, come sbattere le ciglia, scattare via da una fonte di calore simili azioni.

Si tratta di un agente che agisce sulla singola percezione e trova l’azione corrispondente a seguito di questa. Le percezioni passate non interessano proprio, sa già agire subito dalla percezione presente.

**Caratteristiche di questo agente:**

- Staticità nelle azioni, esegue solo ciò per cui è programmato, quasi fosse un if-then agent, infatti dovremmo parlare di regole di condizione-azione
- Necessità di osservabilità totale, altrimenti è difficile che faccia l’azione più intelligente
- Modello in breve

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled.png" alt="image/universita/ex-notion/l’intelligenza/Untitled">

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 1.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 1">


### 1.3.2 Basati su modelli

Questo modello si può considerare una espansione al modello precedente. Si cerca piano piano di rendere l’agente più flessibile, e non soltanto qualcosa di programmato, come se fosse un singolo algoritmo:

Ora l’agente possiede un modello interno del mondo, che è cambiato a seconda della percezione nel momento. Quindi l’azione ora non è presa solamente secondo la percezione attuale, ma anche secondo il modello del mondo, e la percezione attuale.

**Caratteristiche**

1. Funzione di transizione del modello, che serve per aggiornare il modello interno del mondo a seconda dei cambiamenti percepiti
2. Funzione di sensore, che traduce le informazioni percepite in funzione dello stato del mondo (es. se ho la telecamera sporca di acqua per la pioggia, l’input sarà un pò diverso)

Quindi maggiore flessibilità in confronto alla precedente.

- Modello in breve

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 2.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 3.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 3">


### 1.3.3 Basati su obiettivi

L’ulteriore espansione di questo agente rispetto alla precedente è che ora il modello tiene conto anche delle possibili conseguenze future delle proprie azioni in funzione del raggiungimento o meno del proprio obiettivo

**Caratteristiche**

1. Esistenza di un obiettivo ben dichiarato proprio (che condiziona la funzione di valutazione)
2. Possibilità di rimpiazzare l’obiettivo precedente con uno simile (flessibilità)
3. Aggiornamenti su conseguenze delle proprie azioni sullo stato del raggiungimento per l’obiettivo
- Modello in breve

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 4.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 4">


### 1.3.4 Basati su utility

cerca di valutare se è una conseguenza buona o cattiva, a seconda di una propria *funzione di valutazione* che cerchi di rispettare il meglio possibile la funzione di valutazione dell’ambiente in cui è presente.

È buono in caso ci possano essere degli obiettivi che si eliminano uno a vicenda, è buono per trovare i tradeoff **comune in molte situazioni (es. voglio arrivare più in fretta possibile, ma non voglio investire persone).

**Caratteristiche**

1. Una funzione di valutazione che cerca di *massimizzare il valore atteso della propria azione.*
- Modello in breve

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 5.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 5">


### 1.3.5 Basati su apprendimento

Al fine di avere un agente flessibile che possa adattarsi in ambienti anche molto differenti fra di loro, vorremmo creare un metodo per cui l’agente possa imparare dai propri errori. Questo modello si prefissa l’obiettivo di creare un framework generale per un agente che impara.

**Caratteristiche:**

1. Critico: cerca di valutare le azioni prese dall’agente e pone consigli su cosa cambiare
2. Elemento apprendimento: che cambia lo *stato di conoscenza interna* dell’agente in modo che possa prendere decisioni migliori, grazie al feedback del critico
3. generatore di problemi che propone nuovi problemi/esperimenti che possono migliorare altri tratti dell’agente.
- Modello in breve

    L’agente vecchio è interamente raccolto nel performance element

<img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 6.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/l’intelligenza/Untitled 6.png" alt="image/universita/ex-notion/l’intelligenza/Untitled 6">


# 2 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
dello in breve