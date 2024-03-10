---
layout: page
permalink: notes/polimorfismo
tags: italian
title: Polimorfismo
---

Ripasso Prox: 20
Ripasso: May 31, 2023
Ultima modifica: May 14, 2023 4:31 PM
Primo Abbozzo: April 4, 2023 10:15 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Polimorfismo

## Introduzione

### Monoforfo 🟩

Quando non posso utilizzare un tipo come parametro. Ossia non possiamo definire una funzione generica.

- Slide monomorfismo

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled.png" alt="image/universita/ex-notion/Polimorfismo/Untitled">


## Polimorfismo

Polimorfismo, come dice il nome, significa avere tante forme, in questo caso tanti tipi. Ma avere tanti tipi non è una cosa ambigua? Questa cosa si risolve solitamente a compile time (facendo checks di sottotipo, oppure dispatch della funzione corretta).

### Tipologie di Polimorfismo (3) 🟩

- Slide tipologie di monomorfismo

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 1.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 1">

- **ad-hoc polymorphism** questo è anche chiamato overloading in cui vado a definire un nuova funzione (con lo stesso nome) che accetti il nuovo tipo di dato.
- **subtype polymorphism**
- **parametric polymorphism**

### Ad-hoc (3) 🟩

- Slide ad-hoc polimorphism

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 2.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 3.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 4.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 4">


Questo è molto simile al tipo somma, solamente fatto da un punto di vista funzionale (**i domini devono essere separati**).

In C sono molto conosciute questa tipologia di polimorfismo. Però ci sono anche forme comuni, come l’operatori aritmetici.

L’invocazione è anche chiamato **dispatch** , quando abbiamo risolto l’overloading, ossia abbiamo fatto il dispatch dell’invocazione, allora l’overloading scompare e viene eseguita una specifica funzione. Questa funzione può essere fatta in modo statico oppure dinamico.

Riassumento:

- Definisco stesso nome che prendono tipi diversi
- Avviene un dispatch statico o dinamico
- Una volta avvenuto il dispatch, la funzione eseguita è univocamente identificata.

*Statico o dinamico nel dispatch*

Dispatch è il processo che va a decidere la funzione overloadata da chiamare, questo processo si può classificare come **dinamico** se avviene durante il runtime (come solitamente è per le interfacce) oppure **statico** quando avviene e a tempo di compilazione (come solitamente avviene per le funzioni overloaddate).

## Di sottotipo

Possiamo andare a dire che un tipo S è sottotipo di un tipo T, indicato con $$S <: T$$, quando S può essere utilizzato in qualunque occasione al posto di T. Questo è anche chiamato come **principio di sostitutione di Liskov**.

### SetTheory per sottotipi 🟩—

- Slide polimorfismo di sottotipo

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 5.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 6.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 6">


Questo concetto l’abbiamo anche accennato in [Algebra dei tipi](/notes/algebra-dei-tipi) quando abbiamo parlato di coercizione.

praticamente quando abbiamo un tipo più specifico $$S$$ che andiamo ad indicare con $$S <: T$$, allora quando ho S e devo utilizzare T, lo posso fare, questo perché S contiene tutte le caratteristiche di T.

Solitamente questa è una relazione di **preordine** ossia riflessiva e transitiva, spesso anche antisimmetrica, quindi è spesso un **ordine parziale**.

Si può dire che esiste un **rapporto di specificazione** (parola da utilizzare nell’orale per bella figura lel) perché S è più specifico di T, in questo senso possiamo utilizzare S in ogni posto in cui c’è T.

### Tipologie di sottotipaggio (2) 🟩

- Slides subtyping con records

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 7.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 8.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 9.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 9">


Per questa parte possiamo andare a definire un concetto di **sottotipaggio per profondità o per larghezza**.

*Per laghezza*: basta che il sottotipo abbia molti più campi! in questo senso Dog < Animal, perché anche dog posso utilizzarlo come un animal, dato che ha tutte le cose di animal. (l’unica differenza col duck typing è il fatto che T qui è esplicito, mentre nel duck typing non mi importa del tipo, solamente dello stesso utilizzo).

- Differenza fra duck e width subtyping per chatGPT

    Width subtyping is a form of subtype polymorphism where a type is considered a subtype of another type if it has at least the same properties and methods as the supertype. This means that a subtype can have more properties and methods than the supertype, but it must at least have all of the ones that are defined in the supertype. This is called "width" because it is based on the width of the type's interface.

    Duck typing, on the other hand, is a more dynamic approach to type checking where the type of an object is determined by its behavior at runtime rather than its static type. In other words, if it walks like a duck and quacks like a duck, then it must be a duck. This means that two objects with different types can still be treated as if they have the same type if they share the same behavior.

    In summary, width subtyping is based on the interface of a type and allows for subtype polymorphism, while duck typing is based on the behavior of an object at runtime and allows for more dynamic type checking.


*Per profondità*: Quando un campo ha un tipo che sia un sottotipo di un altro. Questo è visto molte meno volte, però si può fare. Questa ha però delle particolarità, è importante introdurre il concetto di **covariante** per tipi quando le parti del record mantengono la stessa direzione di sottotipaggio. Quando abbiamo due tipi che sono covarianti, possiamo utilizzarli solo per le **letture**. In scrittura però potremmo avere dei campi non inizializzati, quindi non va molto bene. (nell'esempio avremmo un animale in output in scrittura, mentre gli abbiamo dato un dog e ci aspettavamo un dog in output). (queste nozioni di covarianza comunque sono sempre in funzione del contesto).

In pratica vado a rimpazzare i campi del record con dei sottotipi, questo è buono per cose immutabili, for example, you can assign 1.5 to the 'x' field of a real point (a record with two real fields), but you can't do the same to the 'x' field of an integer point (which, however, is a deep subtype of the real point type) because 1.5 is not an integer.

### Covariante e Controvariante e consumo (!!) 🟨++

- Slide covariante, controvariante e consumi e produzione

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 10.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 10">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 11.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 11">

- Esempio strano

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 12.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 12">


Questa nozione si basa sull’inversione fra produzione e consumazione.

Avevamo detto che abbiamo una relazione di sottotipo, perché DogHouse < AnimalHouse quindi sono covarianti rispatto a Dog < Animal House. Ma nella fase di consumo, questo si inverte, quindi si può dire che siano controvarianti.

In breve:

1. Consumo (input) → Controvariante
2. Produzione (output) → Covariante

Il motivo per cui succede è che Dog fn utilizza i campi di Dog, che sono più estesi, posso sostituire a questo consumo anche animal, che utilizza i campi di animal, quindi sono anche presenti in Dog, ecco che il rapporto si inverte

Possiamo fare un parallelo fra le funzioni di consumo e quelle di produzione.

- Slide esempio covariante e controvariante easy

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 13.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 14.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 14">


### Sussunzione 🟨

Con sussunzione andiamo a parlare di quando possiamo fare **l’inferenza di sottotipaggio** ossia se è vero o meno che un tipo è sottotipo di un altro (e quindi possibile utilizzare S al posto di T in qualunque luogo).

- Slide sussunzione metodi

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 15.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 15">


Possiamo fare la sussunzione in modo estensionale o intensionale quindi o:

1. Caratterizzando tutti gli elementi del sottotipo
2. Parlare di predicati e domini.

Tipo estensionali o intensionali 🟩- abbiamo parlato di estensionale o intensionale

- Esempi di sussunzione

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 16.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 16">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 17.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 17">


## Polimorfismo parametrico

### Tipi parametrici 🟩

- Slide tipi parametrici

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 18.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 18">


Quando abbiamo delle operazioni anche se non conosciamo esattamente cosa c’è sotto, però riguardo la struttura so bene cosa vanno a fare. (un esempio riguardo a questo è il sort).

Questa parametrizzazione ci permette di definire delle cose per tutti i tipi che possiedono quella funzione (ricorda i tratti di rust), ed è per questo che possiamo dire che sia un **tipo universale**. Questa cosa che vale per tutti ci permette di poter provare dei teoremi aggratis.

- Esempio di teorema for free

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 19.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 19">


### Ibridazione con polimorfismo di sottotipo 🟨

- Slide ibrido con pol di sottotipo

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 20.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 20">

    <img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 21.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 21">


A volte non vogliamo che la nostra funzione vada per tutti, senza quindi conoscere come è fatto sotto, vorremmo avere certe funzioni (quindi un sottotipo del tipo generale), per esempio nei tratti di rust possiamo dire che questa nostra funzione vada per tutte in cui è definita una certa funzione/interfaccia/tratto, in questo senso andiamo ad utilizzare un sottotipo

Array c’erano già all’inizio, lo puoi utilizzare covariante in entrambe le direzioni, mentre altrimenti non ti permetterebbe di utilizzare in entrambe le direzioni (vuole che tu sia prima sicuro se vuoi utilizzarlo come consumer o producer. un buon modo per ricordarsi è **PECS** producer deve estender, mentre consumer deve fare super.

Abbiamo sempre che è safe, nel senso che ritorna sempre un tipo senza bloccarsi (e posso sapere a tempo di compilazione cosa vada a ritornare).

### Esempi di utilizzo di polimorfismo parametrico e di sottotipo

<img src="/images/notes/image/universita/ex-notion/Polimorfismo/Untitled 22.png" alt="image/universita/ex-notion/Polimorfismo/Untitled 22">

### Tipi maybe e result 🟩

Questi sono alcuni tipi ispirati alle monadi, solamente capire in che formato sono:

- Maybe: Some<qualcosa> + None
- Result: come le promises di js, possiamo esprimere i risultati di errore e nel caso sia andato tutto bene.

# Registro ripassi

| 01/05/23 | Boh, direi che sia apposto, dovremmo vedere come fare gli esercizi ma per la maggior parte direi che siano apposto.. |
| --- | --- |
| 14/05/23 | Non mi ricordavo esattamente definizioni di tipi monomorfi o polimorfi. Non mi ricordavo alcune cose come polimorfismo parametrizzato esplicito oppure implicito.
Non mi ricordavo le cose di static dispathc o dinamic dispatch del polimorfismo ah-hoc.
Non mi ricordavo i metodi per l’ibridizzazione col poli di sottotipo (in generale per il parametrico universale non posso proprio supporre nulla). |
|  |  |
spatch del polimorfismo ah-hoc.
Non mi ricordavo i metodi per l’ibridizzazione col poli di sottotipo (in generale per il parametrico universale non posso proprio supporre nulla). |
|  |  |