---
layout: page
permalink: notes/astrazione-sul-controllo
tags: en
title: Astrazione sul controllo
---

Ripasso Prox: 46
Ripasso: May 27, 2023
Ultima modifica: May 6, 2023 12:48 PM
Primo Abbozzo: March 20, 2023 10:46 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Astrazione sul controllo

## Significato di astrazione

L'astrazione è una cosa fondamentale nell'informatica, l’abbiamo visto anche nella prima lezione in assoluto per architettura, il sistema a strati di [Architettura e livelli 1, 2](/notes/architettura-e-livelli-1,-2) reti e simili.

Il principali metodi sono **astrazioni sul controllo e sui dati** sui dati stiamo cominciando a parlarne in [Teoria dei Tipi](/notes/teoria-dei-tipi).

Le astrazioni sono utili a **nascondere dettagli** per qualche fenomeno o simile (ricorda l'esempio della mappa, che non è il territorio è una astrazione su essa, che contiene ancora informazioni utili). Vogliamo quindi **concentrarci su quanto ci interessa**

una cosa che a noi è molto interessante è la astrazione funzionale

### Astrazione funzionale 🟩

Vogliamo creare una associazione fra funzione e procedura, ossia esporre solamente cose come intestazione della funzione, parametri e valore di ritorno per descrivere una funzione, la implementazione non ci interessa.

Si può ben notare che meno la funzione interagire con l’ambiente non locale, ossia più è indipendente, ha meno side effect, meglio è fatta sta astrazione.

### Comunicazione con l’ambiente (3) 🟩

la comunicazione con l’ambiente può avvenire mediante tre metodi principali.

1. Parametri
2. Ambiente no nlocali
3. Il valore di ritorno

### Formali e attuali e 3 comunicazione 🟩

Nella dichiarazione di funzione si parla di parametri formali, nel senso che sono delle **variabili legate**, se rinominate correttamente attraverso funzioni definite in [Logica](/notes/logica) si può cambiare nome.

Un parametro attuale è quello effettivamente mandato, che si fa mediante la chiamata di funzione.

- Slide formali e attuali

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled">


Anche il flusso di informazione può essere diviso in più modi.

1. in entrata (come il passaggio per valore)
2. In uscita (boh, si assegna il valore ebbasta, senza leggerle).
3. In entrata e uscita (come le reference)

## Passaggio di parametri

### Passaggio per valore 🟩

Questo è il classico passaggio di funzione che abbiamo in C.

- Viene calcolato il valore (r-value)
- il valore viene messo sulla pila, quindi come se fosse una variabile locale.
- Distruzione quando si ritorna dalla funzione
- Molto costoso per dati grossi perché devo fare la copia
- non ho modo di comunicare usando quella variabile direttamente al parametro.
- Slide per passaggio valore

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 1.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 1">


la cosa carina è che è una copia, non ho trasmissione delle informazioni.

### Passaggio per riferimento 🟩

In questo caso passo il riferimento, o l-valore dell’oggetto, quindi la sua locazione o riferimento. (in java in pratica è un riferimento perché si utilizza la reference model come descritto in [Valutazione Espressioni](/notes/valutazione-espressioni).

- Slide passaggio per riferimento

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 2.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 2">

- Slide riassunto valore e riferimento

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 3.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 3">


Un concetto qui importante è la **trasparenza referenziale**, nel senso che non ci importa di come è stato chiamato, tanto è una copia (per il passaggio per vlaore) quindi riesco ad avere quanto mi interessa. (questo non vale per reference, perché dipende da con cosa lo ho chiamato!)

Come fare un passaggio con semantica semplice come il passaggio di valore e senza problemi di aliasing come reference, e con anche comunicazione.

- Esempio di problema di aliasing

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 4.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 4">


### Passaggio per costante 🟩

**VALORE NON MODIFICABILE**

Solo in una direzione, solo che non si può modificare. È come un passaggio per valore, solo che si potrebbe implementare per riferimento per ragioni di efficienza. Ma comunque dipende dall’implementazione della macchina astratta.

### Passaggio per risultato 🟩

Questo è il duale del passaggio per valore, perché alla chiamata di funzione assegno la funzione a questa variabile (alla fine assegno il valore del formale al parametro attuale), quindi è molto utile per **trasmettere valore dalla procedura al main**.

Ossia ho una copia del valore formale **(aka valore attuale) al parametro attuale*, ma lo ho solo alla fine della funzione.

- Slide passaggio per risultato

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 5.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 5">


### Passaggio per valore risultato 🟩

Questo permette il passaggio in entrambe le direzioni (si fa la copia e si assegna alla fine). Alcuni linguaggi implementano questa cosa attraverso la reference, sempre per il concetto che è molto più efficiente tenere le reference, solo che c'è il problema di **aliasing**, quando mando la stessa reference.

- Esempio di valorerisultato differente da reference

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 6.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 6">


### Passaggio per Nome (!) 🟩

In pratica sostituisco il nome del parametro attuale al posto del parametro formale, senza cattura.

> una chiamata alla procedura P è la stessa cosa che eseguire
il corpo di P dopo aver sostituito i parametri attuali al posto
dei parametri formali
>

Si può notare come se fosse la macro espansione in assembly (di cui credo le macro di C sono molto simili)

- Esempi di cose del passaggio per nome

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 7.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 7">


**PROBLEMI DI SCOPING**

- Slide scopes

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 8.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 8">


Questo sarà il problema che permetterà il passaggio dell’ambiente molto utilizzato per le variabili di ordine superiore come le funzioni.

IIMPLEMENTAZIONE DEL PASSAGGIO PER NOME

L’implementazione di questo passaggio è molto interessante, perché dovrei passare anche l’ambiente iniziale affinche’tutta l’espressione abbia senso! l’operazione fondamentale è lo **scoping**.

- Slide implementazione per nome

    <img src="/images/notes/image/universita/ex-notion/Astrazione sul controllo/Untitled 9.png" alt="image/universita/ex-notion/Astrazione sul controllo/Untitled 9">


Solitamente è molto **costoso** perché per valutare devo sempre andare in un ambiente diverso dall'attuale, poi anche dal fatto che il valore è rivalutato ad ogni occorrenza!



# References