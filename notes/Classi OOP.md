---
layout: page
permalink: notes/classi-oop
tags: en
title: Classi OOP
---

Ripasso Prox: 9
Ripasso: May 5, 2023
Ultima modifica: July 10, 2023 8:41 PM
Primo Abbozzo: May 15, 2023 9:17 AM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso

# Classi e OOP

## Introduzione

Per la definizione di classe andare a guardare [Object orientation](/notes/object-orientation), però lo ripeto in questa occasione, è solamente un modello su cui andare a costruire degli oggetti.

### Capisaldi (!!) (4) 🟩

1. Incapsulazione
2. Astrazione
3. Ereditarietà
4. Dispatch dinamico

### Costruttori 🟩-

- Slide costruttori

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled.png" alt="image/universita/ex-notion/Classi OOP/Untitled">

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 1.png" alt="image/universita/ex-notion/Classi OOP/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 2.png" alt="image/universita/ex-notion/Classi OOP/Untitled 2">


Il costruttore è un codice utilizzato per **inizializzare correttamente lo stato** interno. Le regole sono le stesse dei metodi sovraccaricati (dinamica per la chiamata, statica per il numero dei parametri che prende in input).

## Incapsulazione

### Carat incapsulazione 🟩

ossia la distinzione fra **pubblico e privato,** il fatto che posso decidere quanto nascondere e quanto esporre. All'esterno sono esposte solamente le **interfacce** che sono solitamente pubblici.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 3.png" alt="image/universita/ex-notion/Classi OOP/Untitled 3">

Solamente le cose dichiarate come pubbliche sono esposte, mentre tutto lo stato interno è nascosto e non è accessibile all'esterno.

### Sottotipi (liskov) 🟩

Questo è il **principio di sostituzione di liskov,** che in pratica ci dice che se S è sottotipo di T, allora posso utilizzare S in qualunque posto di T.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 4.png" alt="image/universita/ex-notion/Classi OOP/Untitled 4">

Se utilizizmao una notazione matematica, allora se ho unap roprietà per un oggetto in T allora questa proprietà vale anche per un oggetto in S.

### Differenza tipo e classe 🟩

C'è una differenza fra struttura delle operazioni (quindi il tipo, cosa prendo e cosa ritorno) con l’implementazione effettiva delle funzioni, i check per privati e pubblici (implementati dalle classi). Quando dichiariamo alla classe è come se dichiarassimo allo stesso momento una interfaccia per essa.

> consideriamo la definizione di una classe come **accompagnata da una definizione
implicita di un'interfaccia** della vista pubblica di quella classe.
>

In questo senso la classe diventa un elemento nel nostro sistema dei tipi.

### Astrazione (!) 🟩

La nozione di astrazione è strettamente legata all'interfaccia implicita che la classe induce.

L’astrazione di permette di andare ad elaborare con alcuni concetti che nativamente non esistono, per esempio non esiste nativamente il tipo Euro, ma può essere implementata attraverso il tipo concreto degli interi. Le classi forniscono delle interfacce che permettono una modifica controllata dell’oggetto che viene rappresentato, questo è il significato di astrazione.

> le interfacce ci permettono di
fornire ai clienti una **descrizione del
"contratto"** che i nostri oggetti promettono
di soddisfare, senza costringerci a fornire
la loro effettiva implementazione.
>

ossia descrive ciò che prende in input, ciò che deve andare a ritornare. senza dire esattamente come è implementata quella logica.

### Classi astratte 🟩

Sono una **via di mezzo fra interfaccia e classe** nel senso che possono lasciare delle funzioni non implementate

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 5.png" alt="image/universita/ex-notion/Classi OOP/Untitled 5">

## Ereditarietà

### Sottotipaggio ed ereditarietà (2)

Ci sono due **keyworks** principali quando andiamo a parlare di sottotipaggoi ed ereditarietà, sono **extends and implements.**

- Extends: prende anche i metodi (proprio l'implementazione) di tutti metodi e gli stati del genitore. Doppia operazione:
    - Relazione di sottotipaggio col tipo da cui estende
    - Prendere tutti i metodi dichiarati sono presenti ora anche qui.
- Implements: crea l'implementazione dell’interfaccia astratta.

C'è una leggera differenza fra queste keywords se utilizzate per interfacce oppure per classi. Credo l'unica cosa che cambia è che per extends nelle classi mi porto dietro anche stati e funzioni e anche i vincoli di incapsulamento.

In breve: sottotipi parlano di operazioni, e manipolazione i interfacce fre la varie classi, mentre l’ereditarietà va a parlare di metodi che possono essere utilizzate o meno.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 6.png" alt="image/universita/ex-notion/Classi OOP/Untitled 6">

Differenza principale fra sottotipaggio ed ereditarietà

### Shadowing

Come gestire i casi di ereditarietà in cui una stessa variabile è stata dichiarata con esattamente lo stesso nome?

**Regole di scoping statico!** In pratica il parent è visto come uno scope più esterno, e si risolve in questo modo.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 7.png" alt="image/universita/ex-notion/Classi OOP/Untitled 7">

### Overriding dei metodi

Coerentemente al principio di astrazione, posso cambiare il contenuto (quindi la semantica) di una funzione senza cambiarne la signature, sulla stessa logica posso reimplementare un metodo in un child class.

> Una differenza tra l'overriding dei metodi e
lo shadowing delle variabili è che il primo è
risolto dinamicamente, mentre il secondo è
risolto staticamente.
>

### Modificatori di visibilità (2)

Ci sono dei modi per andare a modificare la visibilità durante le relazioni di ereditarietà fra le classi, queste son ooil **packaged e protected**

- packaged: se sei un figlio allora puoi vedere i metodi privati (tutto lo stesso pacchetto può vedere questi metodi.
- Protected: tutte le sottoclassi, anche in moduli diversi possono utilizzare le funzioni ereditate protected, solo che l'esterno non può comunque andare ad accederci.

### Tipi intersezione

Questi tipi intersezione prendono in input due classi e creano una classe che abbia **entrambe le caratteristiche** delle due classi. Sono diverse dai tipi unione, perché questi tipi unione possono essere o uno o l’altro, nel senso che non sono entrambi in contemporanea!.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 8.png" alt="image/universita/ex-notion/Classi OOP/Untitled 8">

In un certo senso sono **concatenati** questi valori. Una cosa interessante è che il grafico delle inheritance è un **DAG**

### Ereditarietà multipla problemi: diamante

- Slide introduzione dei problemi di ereditarietà (2 sol)

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 9.png" alt="image/universita/ex-notion/Classi OOP/Untitled 9">


Questa implementazione ha molti problemi quando eredito due cose che hanno una intersezione, come per esempio un metodo con lo stesso nome. Allora come si risolve questo problema?

Il problema principale è la **diamond of death**

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 10.png" alt="image/universita/ex-notion/Classi OOP/Untitled 10">

## Dynamic dispatch

### Early and late binding

Late: quando ho l’oggetto io vado a cercare l’oggetto, se lo trovo allora lo eseguo, se non c’è allora continuo la ricerca finché non lo trovo, allora do errore: è una cosa molto simile al prototyping.

Early: Utilizza infomrazioni statiche per risolvere l’ambiguità, questo dovrebbe farlo C per esempio.

### Metodi statici

Niente ci vieta di andare a definire dei metodi statici che vengono risolti in modo statico.

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 11.png" alt="image/universita/ex-notion/Classi OOP/Untitled 11">

<img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 12.png" alt="image/universita/ex-notion/Classi OOP/Untitled 12">

### Implementazione degli oggetti (link)

SI potrebbe tenere una lista linkata fra tutte le ereditarietà, solo che diventa una cosa molto lenta, perché potrebbero esserci molti accessi: vado a cercare fino al top se ci sia o meno questo metodo per una certa classe.

### Early and late binding

Accesso via offset: per accedere allo stato, faccio in modo molto simile alle struct, che in pratica vanno a calcolare offset rispetto a qualcosa, il calcolo dell’offset per il singolo stato è molto veloce, una cosa leggermente più complicata è la ricerca del metodo corretto, se questo è stato sovrascritto o simile. (fa ricerca lineare, va su finché non trova il metodo.

**CHIAMATA DEL METODO**

Non solo vogliamo andare a creare uno stack frame, variabili locali e parametri abbiamo in più anche le variabili di istanza! Semplicemente prende il this e ci applica l’offset per prendere le informazioni, le slides lo fanno molto più complicato.

### Vtables(!!)

Ogni oggetto ha un puntatore alla propria vtable della propria classe, con già tutti i puntatori alle funzioni corrette per le funzioni.

- Slides ereditarietà

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 13.png" alt="image/universita/ex-notion/Classi OOP/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Classi OOP/Untitled 14.png" alt="image/universita/ex-notion/Classi OOP/Untitled 14">


Dovrebbe funzionare solamente per ereditarietà singola, non so per la multipla come funziona questa della vtable.

### Classe base fragile

C’è il problema della **composizionalità**, nel senso che non possiamo andare a compilarli in modo diverso, se cambiamo una classe padre, allora bisogna andare a ricompilare tutti childs, è un problema di ingegneria del software questo.

### Type parameter erasure

### In Java fragile

Ci sono alcuni metodi per andare a gestire il problema della classe fragile. Come gestire questo problema quando l'intera classe è stata compilata a sé stante. Viene risolto a caricamento e la prima reference viene risolta e sostituita al codice di ricerca col riferimento al codice effettivo.