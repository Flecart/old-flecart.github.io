---
layout: page
permalink: notes/teoria-dei-tipi
tags: italian
title: Teoria dei Tipi
---

Ripasso Prox: 30
Ripasso: June 6, 2023
Ultima modifica: May 14, 2023 6:13 PM
Primo Abbozzo: March 13, 2023 9:20 AM
Studi Personali: No

# Elementi di ripasso

# Teoria dei Tipi

## Introduzione

### Definizione 🟩—

> Un metodo sintattico **praticabile** per dimostrare
l'assenza di determinati comportamenti del
programma, fatto classificando le unità sintattiche in
base ai tipi di valore che assumono
>

Vogliamo che fosse praticabile nel senso che effettivamente lo possiamo implementare, cioè ci permettono di avere certe tipologie di garanzia. ma ancora è una definizione molto ampia. E di solito si può fare una analisi statica del comportamento del programma.

Un altro modo per definirlo (questo molto più buono) è

> Collezioni di valori omogenei e rappresentabili e una serie di operazioni su di esse.
>

Ossia omogenei nel senso che hanno tutti certe proprietà, e rappresentabili perché effettivamente possiamo metterli in memoria (per esempio non posso avere come tipo i Reali in modo primitivo, perché non è rappresentabile).

- Esecuzione corretta, + ottimizzazione da parte del compilatore.

### Utilizzo dei tipi (4+) (!!!)  🟨—-

- Slide sull'utilizzo dei tipi organizzazione concettuale

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled">

- Slide astrazione

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 1.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 1">

- Slide correttezza

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 2.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 3.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 4.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 4">

- Slide implementazione

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 5.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 5">

1. **Progettazione**: posso descrivere in modo *concettuale* cosa fa il programma e aiutare a verificare la correttezza del programma, “separare logicamente elementi concettualmente diversi” (posso creare tipi per certi concetti e quindi ragionare meglio, pensa sviluppare solo in assembly!) **Documentazione**: ci danno informazioni in più riguardo il ruolo della variabile nel nostro programma. Una idea bella è parlare di tipi come se fossero commenti
2. **Astrazione**: in fase di implementazione possono aiutare a gestire meglio il nostro progetto, solitamente attraverso interfacce (a questo tipo ho certe operazioni, non ho niente di sotto), ci permette di modulizzare e gestire meglio, ++manutentibilità, ++ comprensibilità del progetto.
L’astrazione su un concetto di cambia il modo di ragionare riguardo l'implementazione, o l’idea sottostante comunque.
3. **Correttezza**, possiamo utilizzare i tipi per avere errori di programmazione, quindi se faccio qualcosa con un tipo, io mi aspetto di ricevere altro. (ad esempio se mi aspetto che una funzione mi ritorni qualcosa, ma mi ritorna qualcosal’altro o non sempre quel tipo, posso darti errore staticamente parlando).
Per cose di **refactoring** è molto comodo, se cambi un tipo e una strtutura vorresti cambiarla anche da altre parti (se lo fai tipo in python è molto più difficile per sto motivo che non ha tipi all’esterno).
O per la cosa della **safety**, è impossibile sbagliare quando hai un buon sistema dei tipi (ti fa sbagliare in fase di compilazione lel, come Rust). Proprio per questa cosa che hai delle garanzie quando programmi, riesci a predire cosa ti ritorna e quindi predisci il modo con cui si comporta il programma. Possiamo dire che un programma è sicuro quando **rispetta sempre i vincoli del suo tipo**.
Per lui C non ha la caratteristica della safety, quindi puoi andare oltre alle limitazioni di utilizzo del singolo tipo (tipo array puoi accedere anche fuori dal suo range, un tipo buono non dovrebbe permettere queste cose), si potrebbe considerare quindi weakly typed, ma è una cosa strana
4. **Implementazione**: possiamo fare certe ottimizzazioni col sistema dei tipi. non servirebbero controlli dinamici per la sicurezza con un buon sistema dei tipi. Per esempio possiamo anche utilizzare offset per accedere in memoria quindi guadagniamo anche da quel punto di vista.
Si migliora anche l'impatto che si ha sull quantità di memoria utilizzata, forse… non sono sicuro da questo.

Tipo theorem provers e simili

- Altre applicazioni

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 6.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 6">


> Un sistema di tipi (e, per estensione, un linguaggio) è sicuro relativamente ai tipi (o *type safe*) quando nessun programma può violare le distinzioni tra tipi definite in quel linguaggio. Detto in altri termini, un sistema di tipi è sicuro quando nessun programma durante l'esecuzione può generare un errore non segnalato che derivi da una violazione di tipo.
>

### Dynamic and static typing 🟩—

**STATICO**

Quando il controllo dei tipi avviene a livello di struttura del testo. Solitamente queste informazioni sono poi rimosse nel file compilato, almenoché non serva per runnare.

Dato che eventuali errori sono individuati in tempo di compilazione, il prezzo in genere che si paga per un linguaggio statico è il tempo di sviluppo del linguaggio! Solitamente un compilatore che abbia static typing e che sia safe richiede molto molto più tempo.

**DINAMICO**

Quando i controlli di tipi è fatta a runtime, e quindi bisogna runnarlo per capire cosa runna. Questo aggiunge un leggero overhead, perché ho bisogno di un descrittore a runtime che contenga le informazioni sul tipo, e ci sia la verifica in questo momento.

Dato che dobbiamo eseguire per trovare un errore di tipo dinamico, questo errore potrebbe essere scoperto solo nella fase finale, quando il nostro prodotto è già in produzione, e ha clienti!

Importante osservare che la divisione fra dinamico e inferred è indipendente al fatto che sia dinamic o static!

### Manifest vs Inferred typing 🟩

La differenza fra manifest ed inferred typing riguarda la **quantità di informazioni** che il programmatore deve dare al compilatore per creare il sistema dei tipi

L'inferred typing non è altro che un typing manifesto automatico, nel senso che il compilatore stesso riesce a capire che tipo stai dichiarando. Queste cose già esistono in c++ nuovo e anche golang Rust.

Invece il manifest tiping è quando il programmatore va ad annotare ili tipo di tute le variabili.

### Tipo estensionali o intensionali 🟩-

- Slide estensionali o intensionali

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 7.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 7">


**INTENSIONALE**

Quando gli abitanti del tipo sono descritti secondo un **predicato** che è una proprietà che è soddisfatta da tutti gli abitanti.

Salviamo molta memoria per tipi grossi e ci permette anche di rappresentare (fino a un certo punto i tipi infiniti).

**ESTENSIONALE**

Quando si va a listare tutti gli abitanti nel nostro tipo, la stessa cosa che si fa con gli enums

## Sistemi di tipi

### Caratterizzazione di base (4) (!) 🟨+

1. Tipi di base
2. Poter definire nuovi tipi
3. Controllo dei vincoli, che siano statici o dinamici non ci importa, ma ci importa che siano rispettati
4. Computare sui tipi (equivalenza, compatibilità, inferenza dei tipi).
- Slide sistemi di tipi

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 8.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 8">


### Tipi di base 🟩

Sono i **valori denotabili del linguaggio**. Si dice **abitante**, una variabile che faccia parte di questo tipo. Cose come float, caratteri interi etc.

**VOID/UNIT**, è un tipo di base che contiene solamente il singoletto, per questo è anche chiamato unit, in java per esempio è il NUll, mentre in C è il void (che però ha la differenza che non si può assegnare, perché starei assegnando il niente!), e che non si può assegnare. Solitamente è il valore delle funzioni che non ritornano nulla, utilizzato spesso per ritornare il controllo delle funzioni.
In C void è utilizzato per distinguere procedure e funzioni e rende difficile fare le composizioni (che non so cosa sia), unit è per avere ancora funzioni, che deveono per forza avere un codominio non nullo.

**TIPI BOOLEANI**

Che hanno vero o falso come abitanti, e ho tutte le operazioni logiche, come congiunzione disgiunzione negazione etc. La cosa particolare è che utilizziamo un byte invece di un bit per rappresentare un bool, perché per accedere al valore è molto veloce se è allineato.

**TIPO CARATTERE**

Sono i caratteri Unicode, oppure ascii,operazioni classiche sarebbero comparazione, comparazione (perché  c’è un ordine fra i caratteri nell’encoding, come abbiamo detto in [Codifica dei caratteri](/notes/codifica-dei-caratteri)), e il resto è dipendente dal linguaggio.

**TIPI INTERI**

Solitamente spaziano fra $$[-2^{r - 1}, 2 ^{r - 1} - 1 ]$$hanno tutte le operazioni fra interi come uguaglianza, ordine, tutte le operazioni aritmetiche.

**TIPO REALE**

Sono un subset dei reali, in particolare solamente i razionali rappresentabili, hanno stesse operazioni degli interi (importanti per ragioni di compatibilità e conversione con gli interi!), ricorda che ci sono fixed point or floating point representation. Abbiamo fatto principalmente floating point di IEEE745 in Calcolo di numeri finiti .

- Fixed point slide

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 9.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 9">


**TIPO COMPLESSO**

Anche questo, subset dei numeri complessi, stesse operazioni degli interi, con forse qualcosina in più.

**ENUMS**

Questo è il nostro primo tipo non di base, perché è un costruttore di tipo possiamo infatti **dichiarare nuovi tipi**, e enums sono un modo per farlo. In pratica si dichiara un nuovo tipo  con definizione di abitanti appartenenti a questo.

In C non c’è differenza fra interi e enums, quindi non c’è una chiara differenziazione dei tipi, quindi difficile andare a checkare la correttezza fra i due.

## Tipi composti

Come si fa a definire alcuni tipi più complessi, composti utilizzando alcuni tipi primitivi?

### Arrays

Sono unacollezzione di elementi **omogenei** indexati da una chiave (questo mapping riesce a dare in un certo senso un ordine) (che non necessariamente devono essere degli interi, credo che su questa scia anche le hashtable sono classificati come tipo array).

Infatti le mappe sono chiamate **associative arrays**.

Si potrebbe considerare il **costruttore di tipo**, che prende in input un tipo e crea un array di una certra dimensione (quindi fa eccezzioni se provi ad accedere oltre) e crea un altro tipo, che è l’array di certa dimensione.

- Esempi di notazioni con array

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 10.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 10">

- Proprietà del tipo array

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 11.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 11">

- Ordine di storage degli array (row column major)

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 12.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 12">


Se la grandezza dell’array è conosciuta a tempo di compilazione si può allocare in stack, altrimenti si mette in heap, e si utilizza un descrittore, chiamato **dope vector** per accederci sulla heap. Di solito in rust o golang sono gli slice

- Esempio di dope vector

    Ecco tutte le informazioni per il descrittore :D, stride ci dice ogni quanto saltare per avere il prossimo elemento.

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 13.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 13">


**CONTROLLO**

Una delle operazioni fondamentali affinché abbiamo un tipo di array che sia safe è il fatto **check** **all’accesso**, in modo da evitare out of bounds, è la cosa migliore che ho in termini di sicurezza.

Altre operazioni utili sono assegnamento, confronto

### Sets/Insiemi (3)

**Unici e orderless e omogenei** sono gli elementi dei set. Quindi l’unica differenza è il fatto che siano unici e quindi siano tutti distinti fra di loro secondo l’operatore di uguaglianza.

Operazioni importanti sono unione, intersezione, differenza, complemento, etc. tutte le operazioni belle sugli insiemi.

Un esempio di operazioni fra i set sono unioni (e tutti gli amici degli insiemi) quindi per esempio se provo ad unire due insiemi con gli stessi elementi, restano gli stessi.

- Appartenenza, Unione, intersezione, complemento etc…

**IMPLEMENTAZIONE SETS**

L’implementazione più semplice dei set è avere un **bitset**, che il valore del bit ci dice se l’elemento è presente o meno in essa. Ma non funziona per sets che sono molto larghi. Quindi di solito si utilizzano gli hash tables per sti set.

Un altro modo è utilizzare una **hashset** in pratica ogni valore ha una hash, e questo viene utilizzato per vedere se è presente o meno (spesso funzioni fra dominio a un mio)

Un altro modo per fare **set** è utilizzare un albero binario, come fa C++ in set.

### Reference Types

NOTA: i puntatori sono abitanti di questi **reference types**, però non sono gli unici! (esempio URL, reference alla risorsa. Via di casa, reference alla tua casa).

Sono le **reference** a qualcosa! Questo permettono di creare strutture di dati ricorsive.

Operazioni tipiche sono, creazione, check uguaglianza, dereferenziazione. Il pointer è l’implementazione più semplice di questo tipo di dato.

**CASI SPECIALI REFERENCE TYPES (3)**

Senza certe tipologie di checks, le references possono causare molti problemi, come le reference **wild** (quando ho dei pointer non inziializzati e quindi posso avere random della stack)

Per questi è meglio sempre assegnare a Null per evitare questo, se non lo fa già il linguaggio.

**dangling** (quando si riferisce ad elementi già liberati, o ci sono altre cose). Questo è principalmente causato dal fatto che solitamente sono soluzioni basso livello, che interfaccia praticamente direttamente sulla memoria.

**Memory leak**, quando sto perdendo memoria, nel senso che non ho più nessuna reference, quando per esempio dislinko un puntatore, senza averla marcata come libera (quindi perdo un sacco di memoria, che non posso più allocare).

**OPERAZIONI CLASSICHE (4)**

- Slide reference types

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 14.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 14">


**Creazione** di un certo referenze ad un oggetto

**Dereferencing**, cerco il dato puntato da questa referenza

**Equality**, per vedere se è uguale la reference

OPERAZIONI GENERALI CON I REFERENCES.

**Variabile referencing operator**, in pratica vorrei che creasse una variabile che abbia come r-value la l-value di una certa variabile (descritto in [Valutazione Espressioni](/notes/valutazione-espressioni)), ossia il suo indirizzo o contenitore, la sua reference

**Allocazione e deallocazione dinamica**, ma questa non è che dovrebbe essere operazione su questo tipo

### Power sets

Questo sono i primi tipi che non abbiamo visto in un linguaggio di programmazione, alla fine è sempre un Sets/Insiemi, ma con qualche informazione in più.

<img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 15.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 15">

Definizione di powerset P, partendo da un set iniziale S.

Questo soprattutto è un modo molto utile per rappresentare **tuple**, ossia coppie ordinate, molto naturali con dei powerset.

- Osservazione powerset per due

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 16.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 16">


Con l’osservazione di sopra abbiamo detto che la tupla definita in quel modo, che segue la definizione di kuratowsky in 3.1.1 Definizione di Kuratowsky, è un elemento del powerset del powerset, quello è proprio il prodotto cartesiano! Chiachiamo **product types**, o **tipi prodotto** come combinazioni una o più strutture (quindi non più omogeneo come prima)

**PAIRS AND TUPLES**

- Slide pairs and tuples

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 17.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 17">


Abbiamo la stessa informazione con gli array (solo che possono non essere omogenei!) abbiamo sempre informazione sulla posizione, e un valore all’interno della posizione. La coppia generalizzata è una tupla.

**RECORDS**

Se astraiamo le tuple, aggiungendoci un nome per ogni tipo ad una certa posizione, allora abbiamo i records, che non sono altro che delle **strutture**.

Quando andiamo a prendere un elemento stiamo facendo una **proiezione monomorfa**, perché da tutto quell’array di elementi stiamo andando a prenderne un singolo.

**PATTERN MATCHING**

Questo è una struttura molto comune nei linguaggi funzionali, ma anche presente in rust. Sono buoni da poter definire all’interno di un tipo prodotto.

- Slide pattern matching

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 18.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 18">


Praticamente vorremmo fare una partizione completa degli abitanti di un tipo, per questo motivo posso fare una specie di casework completo per gestire in modo esplicito tutti i casi. Questa partizione è fatta in modo libero con delle regole :D.

**TIPI RICORSIVI**

Questi tipi sono definiti per la prima volta grazie ai pairs (quelli con riferimento erano invece delle cose diverse, anche se concettualmente è simile). Possiamo definire che questo sia un tipo ricorsivo nel senso che si potrebbe descrivere come un powersets infinito (credo).

Dalla lezione ora mi sembra abbia detto che deve necessariamente avere una **reference** dello stesso tipo

### Sum Types

- Slide introduttiva sum types

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 19.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 19">


I tipi di somma ci permettono di avere abitandi di più mondi.

Nell’esempio di sopra gli insiemi sono taggati per non confondere un elemento di un insieme con un altro! anche chiamato **or types, choice types, tagged unions, union types, variant types**, perché può assumere un inabitante a caso fra tutti i tipi che costituiscono questa unione.

Abbiamo già visto le **ENUMS** che fanno cose simili, ossia può avere abitanti di tipi diversi, quindi stiamo comunque catturando la somma dei tipi. È interessante osservare che dal punto di vista teorico prendere un elemento di union implementato per enumerazione è simile a tirare fuori da un pacchetto.

**UNION DATATYPES**

Come in C, posso avere le union data types, in cui stessa zona di memoria posso metterci i dati che ho scelto (solo che non mi fa check statico a vedere cosa ci può stare!!), cioè a differenza degli enums, non ho il controllo dell’accesso, decido io come guardarlo.

**RECURSIVE TYPES**

Anche con i sum types posso andare a descrivere i tipi ricorsivi (solamente che alla fine invece di dire che Null è un inabidante delle reference, gli dico che è un abitante di qualcos’altro!) Questo mi rende molto carina la sua struttura (e mi permette anche pattern matchin senza nessun problema (è un modo più sicuro per aprire, dato che posso fare matching).

- Slide recursive types with sum

    <img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 20.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 20">


### Function types

Praticamente sono elementi di  $$A^B$$, con B partenza A arrivo. L’operazione fondamentale di questi tipi sono **l’applicazione**.

<img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 21.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 21">

<img src="/images/notes/image/universita/ex-notion/Teoria dei Tipi/Untitled 22.png" alt="image/universita/ex-notion/Teoria dei Tipi/Untitled 22">

# Registro ripassi

| 25/04/23 | Questa parte mi sembra solamente una lunghissima lista di nomi bruh. |
| --- | --- |
|  |  |
|  |  |