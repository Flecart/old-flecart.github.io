---
layout: page
permalink: notes/memoria
tags: italian
title: Memoria
---

Ripasso Prox: 40
Ultima modifica: March 30, 2023 3:39 PM
Primo Abbozzo: September 21, 2021 7:10 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi da ripassare

- Vecchi dubbi
    - Principio di località e temporalità
- Le tipologie di raid
- November 29, 2021 9:22 PM

# 4 Memoria

## 4.1 Caratteristiche della Memoria

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled.png" alt="image/universita/ex-notion/Memoria/Untitled">

La gerarchia della memoria, più si va giù più spazio si ha, più è lento il caricamento delle informazioni

### 4.1.1 Catalogazione della memoria

Le tipologie di memoria sono presenti a fianco.

In generale più la memoria è veloce da riprendere, più è costosa da memorizzare (c'è poco spazio)

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 1.png" alt="image/universita/ex-notion/Memoria/Untitled 1">

### 4.1.2 Byte e Word

Il libro a pagina 74 parte con la discussione del perché si è preferito **evitare la BCD** (Binary coded decimal, in cui i numeri da 0 a 9 erano codificato da 4 bit), per questioni di efficienza.

La memoria è, in modo spiccio, **una serie di cellette numerate**, ognuno può contenere qualche informazione.

Nacque nel 1960 circa con IBM 360 nacque la definizione di **byte**.

**Word** è una seguenza di byte → unità di dato che non stanno solamente in un singolo indirizzo.

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 2.png" alt="image/universita/ex-notion/Memoria/Untitled 2">

### 4.1.3 Endianess

Questi termini descrivono l'organizzazione dei bytes all'interno della memoria. A volte è molto conveniente netere i bytes al contrario per facilità di accesso.

### 4.1.4 RAM

Abbiamo presentato il funzionamento hardware della RAM nel momento in cui abbiamo descritto il funzionamento di [Circuiti Sequenziali](/notes/circuiti-sequenziali) come LATCH SR, D, DFF.

### 4.1.5 Paginazione - Caricamento

Una altra funzione della gerarchia di memoria è utilizzare la paginazione, ossia il caricamento di risorse utili nella ram veloce e scaricamento nella memoria secondaria di ciò che non viene utilizzato.

È gestito dal sistema operativo.

Sono dei blocchi di data nella memoria principale che vengono caricati nella memoria principale nel momento del bisogno.

Quindi ci sono proprio degli **algoritmi per caricare e scaricare** le pagine di memoria dalla memoria principale, gestiti dal sistema operativo.

## 4.2 Memoria Cache

La cache è una zona di memoria condivisa alle CPU, di facile accesso (meno facile in confronto ai registri, ma comunque veloce) ma senza molto spazio.

È *sempre consultata* ** prima di andare nella memoria.

Se va a cercare un word in memoria, questa viene messa nella cache dopo essere ritrovata.

Una caratteristica principale della cache è che non è necessario al programmatore sapere che esiste o meno, è solo **qualcosa che si interpone in modo TRASPARENTE** che può rispondere subito nel caso possieda una certa informazione.

Ma l’idea di tenere una memoria più veloce intermedia per dati più utili del prossimo futuro è una idea che si utilizza anche in altri ambiti (come Disco, accesso messaggi, e simili) e **migliora molto la velocità**.

### 4.2.1 Livelli memoria Cache

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 3.png" alt="image/universita/ex-notion/Memoria/Untitled 3">

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 4.png" alt="image/universita/ex-notion/Memoria/Untitled 4">

### 4.2.2 Principio di l**ocalità spaziale e temporale**

> Programmi eseguiti vicini nel tempo sono messi in luoghi in memoria vicini
>

Si spera di guadagnare tempo in questo modo, così è più facile ritrovare delle informazioni utili quando si eseguono dei comandi vicini nella cache.

Chiaramente se un programma continua a saltare da un indirizzo della memoria a un altro questo principio non ha più senso e la cache servirebbe a poco.

**Località spaziale e temporale**

Un programma naturale di solito utilizza la cache (un programma potrebbe essere progettato in modo che usi 0 cache, ma sarebbe uno spreco di risorse).

**Temporale:** la stessa cella viene acceduta a breve distanza di tempo (come Stack)

**Spaziale:** celle vicine possono essere prese a breve tempo di distanza. (per esempio accedere ad un array, accesso sequenziale che ha un nome suo di località sequenziale)

È molto facile che la cache debba accedere alla stessa risorsa in termini brevi di tempo

**Località secondo [WIKI](https://en.wikipedia.org/wiki/Locality_of_reference)**

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 5.png" alt="image/universita/ex-notion/Memoria/Untitled 5">

### 4.2.3 Efficienza della cache

La velocità d'accesso alla cache è di granlunga minore rispetto a quello della memoria, di solito il tempo speso per memorizzare qualcosa qui viene sempre recuperato.

Usiamo un pò di matematica ora per descrivere questa cosa un pochino più rigorosamente:

$$c << m$$ con $$c$$ il tempo per accedere alla cache e $$m$$ il tempo per accedere alla memoria.

Allora si ha che il tempo medio per accedere alle informazioni, tenendo $$h$$ come *hit rate* è di:


$$
hc + (1 - h)(c + m) = c + (1-h)m
$$


### 4.2.4 Cache ad accesso diretto

Linee di cache, vanno k mod n, ogni linea di cache di dimensione m. ok? È una cosa temporale, a seconda di cosa ci sia ora.

Data: è effettivamente il data che sto prendendo

n è il numero di linee di cache (che decide quanto grande sia la cache).

Tag serve per sapere quale blocco sto utilizzando (quindi se 0-31 oppure 65536 e simili)

Valid se è un blocco valido, se è 0 vuol dire che non è roba interessante.

- Esempio di query cache

    Teniamo 5 bit per l'indicizzazione dentro i 32 bit di data.

    11 bit per sapere quale linea di cache utilizzare

    16 bit per confrontare con il tag e vedere se è giusto oppure no.

    Così riesco a trovare in modo univoco la linea di cache che mi serve.


<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 6.png" alt="image/universita/ex-notion/Memoria/Untitled 6">

### 4.2.5 Cache hit and miss

Si dice che si ha un cache hit oppure cache miss a seconda del caso in cui la cache è riuscita a dare la richiesta oppure meno.

**Miss**

1. **Riportare la cache in memoria centrale** in quanto potrebbe essere modificata ora, è un aggiornamento della roba nella memoria centrale
2. **Caricare la nuova memoria**.

Se però si tenta di accedere alla cache allo stesso momento, si possono esserci **data race** e quindi bisognerebbe bloccare l'accesso all'inizio

Se vuoi approfondire su algoritmi per la gestione della cache:

[https://en.wikipedia.org/wiki/Cache-oblivious_algorithm](https://en.wikipedia.org/wiki/Cache-oblivious_algorithm)

e altro ancora

## 4.3 Memoria secondaria

Storicamente le velocità delle CPU si sono sviluppate molto più velocemente rispetto alle memorie secondarie.

### 4.3.1 Hard Disk (4)

I dischi magnetici oppure **Hard disk** sono generalmente in tre parti:

- **Settore** è il nome di una traccia specifica di memoria di dimensione fissata.
- **Traccia** è una sequenza di bit circolari
- **Testina** che magnetizza e modifica il contenuto nel disco.
- **Controllore Disco** .

Ogni settore comincia con un preamble che dovrebbe aiutare a diminuire gli errori di lettura.

Per dare un senso, circa in un centimetro di Hard Disk ci possono stare parecchi giga di informazioni.

I dati posso essere messi in due modi:

- Stessa densità per angolo (più rientri più hai i dati in modo compatto)
- Diverso numero di settori (la parte esterna del disco contiene più settori)

**Processo di recupero di dati:**

1. La CPU dice di andare a recuperare un blocco in un certo indirizzo di memoria
2. La testina gira e va fisicamente a recuperare la zona di memoria

### 4.3.2 SSD

**SSD** or Solid State drive non hanno nessuna parte che si muove quindi sono meno soliti a rompersi meccanicamente, *tutto elettronico*.

Storicamente sono state utilizzate per portatili per resistenza ad urti, ma poi si possono utilizzare anche per altro data la loro velocità (per minore spazio).

## 4.4 **RAID**

[https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

Redundant array of indipendend disks (originariamente inexpensive, per contrapporla a Single Large Expensive Disk ossia SLED, ma poi hanno scoperto che anche RAID costa, LMAO.

### 4.4.1 Vantaggi generali

Redundant Array of Inexpensive Disks.

- Ridurre il gap di efficienza fra CPU e HD
- Utilizzo di più dischi in contemporanea + lettura di dati
- Facilità di correttezza di dati e verifica errori

### 4.4.2 6 Tipologie di RAID

Diminuire di 1 l'intera lista, perché RAID va da 0

Non redundant data striping (C'è solo una copia di dati nel disco) **Velocità**, no info retrieval

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 7.png" alt="image/universita/ex-notion/Memoria/Untitled 7">

Redundant, c'è una copia esatta dei RAID e sono **entrambi striped**

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 8.png" alt="image/universita/ex-notion/Memoria/Untitled 8">

C'è bisogno di una grande sincronizzazione in quanto i dati sono divisi fra i dischi a livello bit.

1. Possono avere solamente una richiesta, a differenza di RAID 1 che può gestirne tanti

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 9.png" alt="image/universita/ex-notion/Memoria/Untitled 9">

Unico raid mai utilizzato, però introduce Hamming per la corrrezione!

Uguale al terzo ma c'è un bit di parità per controllo errori invece che codice hamming, spesso bit di parità è bastato.

1. Solo una richiesta

https//en.wikipedia.org/wiki/Parity_bit disk with each color representing the group of blocks in the respective [parity](https://en.wikipedia.org/wiki/Parity_bit) block (a stripe)](Memoria%20f3746a630031414b935cca93dd06f1ad/Untitled%2010.png)

A RAID 4 setup with dedicated [parity](https://en.wikipedia.org/wiki/Parity_bit) disk with each color representing the group of blocks in the respective [parity](https://en.wikipedia.org/wiki/Parity_bit) block (a stripe)

Ritornano gli stripe, ma stavolta un intero disco è utilizzato per verificare che la scrittura è stata corretta,

1. è brutto se vogliamo scriverci

![Anche questo utilizzato poco
Diagram of a RAID 3 setup of six-byte blocks and two [parity](https://en.wikipedia.org/wiki/Parity_bit) bytes, shown are two blocks of data in different colors.](Memoria%20f3746a630031414b935cca93dd06f1ad/Untitled%2011.png)

Anche questo utilizzato poco
Diagram of a RAID 3 setup of six-byte blocks and two [parity](https://en.wikipedia.org/wiki/Parity_bit) bytes, shown are two blocks of data in different colors.

Risolve una lentezza del punto 5 distribuendo le sezioni di controllo sui vari dischi.

https//en.wikipedia.org/wiki/Parity_bit block (a stripe). This diagram shows *Left Asynchronous* layout](Memoria%20f3746a630031414b935cca93dd06f1ad/Untitled%2012.png)

RAID 5 layout with each color representing the group of data blocks and associated [parity](https://en.wikipedia.org/wiki/Parity_bit) block (a stripe). This diagram shows *Left Asynchronous* layout

Non so quale sia la differenza con il 5, per saperlo vai a leggere i raid su [Devices OS](/notes/devices-os). In pratica fault tolerance maggiore.

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 13.png" alt="image/universita/ex-notion/Memoria/Untitled 13">

## 4.5 Errori

Controllare come sono causati gli errori
E tipologie di errori

Questa parte è scritta molto meglio in [Rappresentazione delle informazioni](/notes/rappresentazione-delle-informazioni)

dove si parla di hamming distance e correzione errori.

### 4.5.1 Cause degli errori

Gli errori possono essere causati da:

- Raggi cosmici provenienti dal sole
- Vibrazioni fisiche

### 4.5.2 Hamming Distance

## 4.6 Altri dispositivi

### 4.6.1 Dischi ottici

Un laser va a leggere i pattern di Pit-land e Land-pit, pit-pit presenti sul compact disk.

I dischi sono sostanzialmente uguali per quanto riguarda l'encoding di 1 e 0 ma sono diversi per quanto riguarda *il materiale impiegato*, il raggio impiegato **lo spazio presente fra le varie linee di informazioni (la compattezza dei bit) e simili.

<img src="/images/notes/image/universita/ex-notion/Memoria/Untitled 14.png" alt="image/universita/ex-notion/Memoria/Untitled 14">

### 4.6.2 Output-Input

Per gestire tutti i pixel c'è la necessità di avere architetture molto complicate, circa devono fare update di milioni di pixel in decimi di secondo (altrimenti l'occhio capisce che c'è la distanza)

- Core complessi per la gestione di di milioni di Pixel.
- Linguaggi di programmazione specifici perché più efficienti della CPU per programmi non grafici e.g. Cuda-C.

### 4.6.3 Bus per dispositivi

sono legati tramite BUS, collegamenti elettrici.

- BUS di dati
- BUS di indirizzi

I bus trasportano piccole quantità di informazioni. Si possono dividere in **sotto-bus.**

I bus si sono evoluti nel tempo, partendo da standard ISA (industry standard architetture) sono state creati moderni bus molto più veloci PCI, PCIe e simili.

**Collegamento con memoria e CPU**

- Controller collega gli attacchi ai dispositivi ai Bus che si collegano all'unità di controllo. (la scrittura sul bus è controllata dalla CPU)
- Altri dispositivi parlano direttamente alla memoria **DMA** mandano e ricevono degli interrupt. (se non usasse interrupt altra soluzione sarebbe continuamente inviare delle richieste per chiedere se sta ancora andando o meno)

**Direct Memory Access**

Di questo ne parliamo un pò meglio, anche se alla fine è lo stesso concetto in [Note sull’architettura](/notes/note-sull’architettura)

Per saperne di più su interrupt e trap

Sarebbe molto inefficiente leggere e inviare continuamente, quindi mettiamo un trasferimento RAM → Disco senza passare dalla CPU. Quando finisce il trasferimento il dispositivo invia un **Interrupt** che viene gestito subito dalla CPU interrompendo il processo corrente, iniziando un **interrupt handler** che gestisca eventuali errori del dispositivo e informa il sistema operativo che è finito il processo di I/O.
l processo corrente, iniziando un **interrupt handler** che gestisca eventuali errori del dispositivo e informa il sistema operativo che è finito il processo di I/O.

# References