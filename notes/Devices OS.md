---
layout: page
permalink: notes/devices-os
tags: italian
title: Devices OS
---

Ripasso Prox: 30
Ripasso: May 17, 2023
Ultima modifica: April 29, 2023 11:56 AM
Primo Abbozzo: March 29, 2023 11:18 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Devices OS

## Devices

### Categorizzazione (6)🟨-

1. Trasferimento dei dati
2. Accesso al device
3. sinconia del trasferimento
4. condivisone fra processi
5. Velocità del trasferimento
6. I/O direction (scrittura o lettura)

Vediamo che molte caratteristiche sono riguardo il trasferimento

- Slide categorizzazione I/O

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled.png" alt="image/universita/ex-notion/Devices OS/Untitled">


### Blocchi o caratteri 🟩-

- Slide devices blocchi o caratteri

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 1.png" alt="image/universita/ex-notion/Devices OS/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 2.png" alt="image/universita/ex-notion/Devices OS/Untitled 2">


### Tecniche di gestione devices (4) 🟨-

*BUFFERING*

Possiamo mettere un buffer per favorire la comunicazione fra i devices. la cos amigliore che fa è creare maggiore efficienza. Un altro motivo è la **velocità diversa di consumo**.

Anche le schede audio, in cui viene riempito un buffer e poi l’audio viene playato da questo (**differenza consumer e producer**), anche per questo motivo è difficile sincornizzare dispositivi differenti (se hanno buffer distinti).

**CACHE**

Invece la cache è trasparente pe ril programma, e rende il tutto più veloce.

La differenza maggiore con il buffering è che qui viene mantenuta una copia, non una istanza dell’informazione.

**SPOOLING**

Gia trattato per le stampanti in [Gestione delle risorse](/notes/gestione-delle-risorse)

**SCHEDULING I/O**

- Slides devices

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 3.png" alt="image/universita/ex-notion/Devices OS/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 4.png" alt="image/universita/ex-notion/Devices OS/Untitled 4">


### Storage area network 🟩

- Slide SAN

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 5.png" alt="image/universita/ex-notion/Devices OS/Untitled 5">


Il vantaggio principale è resilienza del server, che ho il device in altra parte. (non ho iil tight coupling fra server e disco in questo modo, prima se si rompe qualunque, si rompe il servizio).

Ora se si rompe un server, ci sarà un altro server che sostituisce, se si rompe un storage array, ci sarà ridondanza, e altro storage ti risponderebbe. Si vede che questa parte è strettamente collegata con cose fatte in Reti di Calcolatori

## Memoria secondaria

### Solid State Drive 🟨+

- Slide SSD

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 6.png" alt="image/universita/ex-notion/Devices OS/Untitled 6">


Un sacco di vantaggi come

1. Velocità di accesso
2. Meno consumo energetico
3. Meno fragilità
4. Velocità di lettura è molto veloce.
5. Poche scritture (comuqnue tante) comunque limitati cicli di scrittura.
6. Uniforme velocità in tutto il disco (questo rende l'accesso veloce :D).

Non andiamo ad approfondire sugli algoritmi di scheduling per le scritture a banco, trattiamo meglio gli HDD.

### Hard Disk Drive 🟨+

Soffrono molto i terremoti perché la testina è vicina al disco e non soffrono problemi di pressione.

Devo avere:

1. Testine settore giusto
2. La traccia desiderata si muova e mi dia le cose giuste

Questo mi crea 3 parametri per valutare questo accesso

**Velocità di rotazione**, **Tempo di seek** o di cambiare cilindro**, velocità di trasferimento**.

Solitamente il tempo più lungo è per il cilindro, poi devo andare alla sezione, e andare alla testina corretta.

- In generale sul disco:

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 7.png" alt="image/universita/ex-notion/Devices OS/Untitled 7">


Ossia solitamente mezzo giro, + tempo cambio

*VALUTAZIONE TEMPO DI ACCESSO*

- Slide tempi di accesso per dischi

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 8.png" alt="image/universita/ex-notion/Devices OS/Untitled 8">


In media 100 giri al secondo, quindi tipo 5 ms per andare a trovare la testina corretta, potrebbe essere 2.5 se è il doppio o 1, ma l’ordine di grandezza resta questo per il ritardo.

## RAID

### Introduzione ai Redundant Array of Indipendent Disks

I RAID ne abbiamo parlato in [Memoria](/notes/memoria). Come facciamo a stare su alla velocità del processore se questa va a crescere in modo esponenziale? **Parallelizzazione della ricerca!**. Ecco perché ci serve raid (oltre alla ridondanza quindi più sicuro). E possono anche fallire. → **ammette recovery**.

E una altra cosa bella dei raid è che sono **hot-swappable** cioè li puoi sostituire anche quando stanno runnando.

- Slide RAID

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 9.png" alt="image/universita/ex-notion/Devices OS/Untitled 9">


### livello 0 (striping) 🟩

I dati vengono messi su più dischi. Viene utilizzato per applicazioni in cui serve velocità, senza interesse di perdita di dati. Ad esempio in dipartimento ci mettono copie di SO per aggiornare il sistema operativo.

UTILIZZI:

- per grandi **trasferimenti di dati**,
efficiente, in particolare se la quantità di dati richiesta è
relativamente grande rispetto alla dimensione degli strip
- per un gran numero di **richieste indipendenti**
efficiente, in particolare se la quantità di dati richiesta è
paragonabile alla dimensione degli strip
- Slide RAID 0

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 10.png" alt="image/universita/ex-notion/Devices OS/Untitled 10">

    https://www.notion.so


### Livello 1 (mirroring)  🟩

Ci sono 2n dischi e metà sono delle copie esatte.

- Slide RAID 1

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 11.png" alt="image/universita/ex-notion/Devices OS/Untitled 11">


In questo caso **la scrittura è più lenta della lettura.**

Tollera un singolo guasto al massimo, o più dischi differenti (non devono essere le due copie diciamo). Si dice **fault tolerance livello 1**.

### Livello 4 🟩

- Slide introduzione raid livello 4

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 12.png" alt="image/universita/ex-notion/Devices OS/Untitled 12">


Utilizzo un intero disco solamente per la parità su un disco. così se si rompe un disco riesco a ricostruire le informazioni di quel disco.

Non è efficiente perché se cambio un dato devo andare sempre a fare **due write su dischi diversi**. E poi continuo sempre a scrivere sullo stesso disco! Quindi fai finta 4 write contemporanei, per aggiornare gli altri dischi! Per questo c'è il bottleneck

### Livello 5 🟩

- Slide intuizione raid livello 5

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 13.png" alt="image/universita/ex-notion/Devices OS/Untitled 13">


Se c'è un disco rotto si rallenta, ma non si perdono dei dati! è il **funzionamento degradato** dei raid.

Non ho problemi di bottleneck, e ho ancora la velocità del livello 1

### Livello 6 🟨++

- Slide raid livello 6

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 14.png" alt="image/universita/ex-notion/Devices OS/Untitled 14">

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 15.png" alt="image/universita/ex-notion/Devices OS/Untitled 15">

    [http://www.cs.unibo.it/~renzo/doc/p245-blaum]([http://www.cs.unibo.it/](http://www.cs.unibo.it/)~renzo/doc/p245-blaum)


Questo è per cose sicure, riesce a **tollerare livello 2** fino a due dischi rotti.

Ovviamente è una parità diversa, in modo che riesco ad avere più fault tolerance.

Si utilizza un XOR in diagonale e questo sembra funzionare, anche se non ho capito perché.

- Intuizione mia

    In pratica qualunque modo prendi due dischi non di check (se uno è un disco di check è molto ez).

    Allora puoi fare questo:

    1. Recovery dei dischi in alto a sinistra e in basso a destra, questi si possono recoverare solamente con i bits diagonali, quindi posso già farlo.
    2. Utilizzo questi strips recuperati e utilizzo quelli orizzontali per recuperare l’altro della stessa row, poi utilizzo diagonale per recuperare quelli corrispondenti in row diverse e continuo così e riesco a recuperare tutto.,

    Sarebbe molto utile fare un esempio per mostrare questo, ma spero che il me futuro quando legge questo riesca a ricordarsi l’esempio su carta.


## Algoritmi per HHD

### First Come First Served 🟩

Questo è un **algoritmo fair**, nel senso che eseguo a seconda di quanto viene, questo non general starvation. Però non minimizza il numero di seek, quindi in generale è più lento. Se invece facciamo in batch, in gruppo di richeiste alla volta sarebbe molto più semplice!

Questa è l'idea del prossimo algoritmo

### Shortest Seek Time First 🟩

> seleziona la richieste che prevede il minor spostamento della
testina dalla posizione corrente
>

può provocare **starvation**, quando arrivano tante vicine, non visito mai quelle lontane!

Quindi non abbiamo fairness, e non c’è una buona velocità di risposta per le richieste agli estremi.

### Look - Algoritmo dell’ascensore 🟩

Praticamente vado avanti indietro, e quando arrivo alla fine torno indietro, continuo così a soddisfare le richieste.

Il tempo medio di accesso non è omogeneo, le tracce centrali sono accesse più spesso.

- Esempio ascensore

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 16.png" alt="image/universita/ex-notion/Devices OS/Untitled 16">


**DISCUSSIONE DI IMPLEMENTAZIONE**

Si utilizzano due code. Una coda a scendere e una coda a salire.

Potrei creare starvation quando mi arrivano richieste sullo stesso cilindro, quindi quando succede devo mettere la richiesta nell'altra coda.

- Implementazione delle due code

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 17.png" alt="image/universita/ex-notion/Devices OS/Untitled 17">


### C-Look 🟩

È molto simile all'algoritmo dell’ascensore, ma solo che quando arrivo alla fine torno all’inizio.

Non ho ancora capito in quali casi può essere utile.

- Slide esempio C-Look

    <img src="/images/notes/image/universita/ex-notion/Devices OS/Untitled 18.png" alt="image/universita/ex-notion/Devices OS/Untitled 18">