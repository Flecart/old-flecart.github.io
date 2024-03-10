---
layout: page
permalink: notes/tecnologia-wireless
tags: italian
title: Tecnologia Wireless
---

Ripasso Prox: 10
Ripasso: May 21, 2023
Ultima modifica: May 14, 2023 5:18 PM
Primo Abbozzo: April 12, 2023 3:02 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Tecnologia Wireless

## Introduzione

### Spettro del wireless networks (skip)

- Slide spettro Wirelesss networks

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled">


Questo solamente la classica differenziazione fra radio, visibile, raggi x raggi gamma etcetera.

Se andiamo a guardare le onde radio, quelle che ci interessano, se ho frequenza alta ho densità di frequenza alta, se ho frequenza bassa ho alta capacità di suparamento di ostacoli.

ISM è una banda da 2 a 5.0 GHz e c'è tutto il WiFi, bluetooth. (anche wifi a 5 ghz.

GSM prima rete cellulare a 900, poi 1800 nella seconda versione.

- Divisione statica delle frequenze

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 1.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 1">


Avre una frequenza comprata è una miniera d'oro, attualmente il prof sta facendo della ricerca su come andare a

### Trasmissione via wireless : bandwidth (!) 🟩

- Slide bandwidth

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 2.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 2">


Solitamente è una **ampiezza di frequenza** ossia quando è grande un insieme di frequenza (questa è anche la definizione formale da utilizzare). Però è erroneamente utilizzata anche per descrivere il numero di bits trasmessi (che è il **bitrate nominale**), è un errore voluto perché solitamente se hai una bandwidth maggiore riesci a trasmettere più dati.

Notare che la velocità del segnale è sempre la stessa che è quella della radiofrquenza (quella della luce), è solamente l'alternarsi di quelle scatolette di colore diverso (codifica diversa).

Se **il segnale è più lungo** allora è più facile andare ad interpretare se è uno 0 oppure è uno 1, diciamo che c'è il tradeoff sulla reliability del segnale credo, anche se è principalmente limitato dalla capacità del ricevente

### def: connettività di link 🟩

- Slides connettività

    Il primo è una partizione, poi unidirezionali e bidirezionali.

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 3.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 4.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 5.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 6.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 6">


Nota: **solamente sui link direzionali** possiamo andare a definire un link simmetrico o asimmetrico.

Le parole principali sono:

- Unidirezionale
- Bidirezionale
- Partizione.

## Tipologie di wireless

- Slide introduzione alle tecnologie wireless

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 7.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 7">


### Narrowband system 🟩

- Slide narrowband system

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 8.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 8">


È un frequenza molto piccola in cui si può comunicare (statica diciamo).

- Problemi di privacy perché mi posso connettere alla frequenza e ascoltare quanto viene mandato.
- Problemi di interferenza se voglio comunicare su questa frequenza con canali diversi

### Frequency Hopping 🟩

- Slide frequency hopping

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 9.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 9">


Possiamo utilizzare **pseudogeneratori** per andare a saltare in modo pseudorandom in spettri di frequenza diversi.

Abbiamo bisogno di una **sincronizzazione** di questi salti, quindi un clock comune sarebbe molto comodo. (però dell’hardware per filtri per quelle frequenze ci dovrebbe essere).

Questo era soprattuttto un modo per trasmettere nel tentativo di non essere ascoltati. In questo senso di hop, è protetto by design.

CURIOSITA: inventata da una attrice di hollywood, Hedy Lamarr (perché il suo canto andava fuori sinc lol) donato poi senza brevetto per salvare i soldati americani.

### Direct sequence spread spectrum 🟨

Ne parliamo un pò meglio in [Modulazione wireless](/notes/modulazione-wireless)

- Slide direct sequence spread spectrum

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 10.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 10">


Ossia mando il segnale encodato su **tutto lo spettro** con un chipping code. E qui si può riutilizzare la metafora del vagone e del treno, nel senso che se è lungo allora riconosco meglio il valore del bit encodato con quella forma.

In un certo senso è anche sicura rispetto al narrowband, perché devi conoscere il pattern del chip code per poterlo decodificare correttamente. (vari interlocutori avrebbero un codice **non correlata** fra di loro, cioè la comunciazione sovrapposta sembra una interferenza casuale) Questo ci permette di riestrarre da molte comunicazioni la nostra comunicazione iniziale.

In breve sembra che questa forma di trasmissione sia quella più affidabile per errori (anche la natura in modo naturale può dare interferenze)

### Note sulle generazioni (skip)

1G era solamente come codifica della voce, la differenza principale con la 2G è con la digitalizzazione, con 2G possiamo trasmettere megabytes, però era pagato per la durata di trasmissione (era telefonare per trasmettere bits lol, però era lenta, quindi pagava tanto, questa parte l'abbiamo accennata in [Introduzione a reti](/notes/introduzione-a-reti), dato che la banda era occupata per tempo).

Con 2.5G andiamo a sfruttare il tempo libero delle altre comunicazioni, ecco la differenza fra commutazione a pacchetto rispetto a commutazione a circuito

3G era bono 1Mbit si pensava risolveva tutto.

## Infrastruttura wifi

### Struttura WWAN WMAN 🟨-

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 11.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 11">

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 12.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 12">

C'è il problema di scoprire access points, e connettersi ai access point e anche predire il movimento delle persone per prevenire il collegamento alla rete.

Un altro problema è tipo il cambio dell’indirizzo IP ad ogni cambio di rete connettendoci ad access point diverso, per questo motivo si utilizza una forma mobile di IPv4 per mantenere lo stesso IP (se cambiasse sempre allora non potrei sostenere video o simili quando mi sposto).

**Geostazionario**: che gira insieme alla terra, quindi l’abbiamo costantemente sopra la nostra testa questo satellite.

### WLAN

Queste sono delle reti ad hoc peer to peer, **senza infrastruttura**, sono solamente dei nodi che si trovano nella stessa stanza!

Non abbiamo costi di gestione e manutenzione se siamo senza infrastruttura e possiamo comunicare localmente senza problemi

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 13.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 13">

### Bridges with wires

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 14.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 14">

Solitamente potremmo avere un access point che sia **dual stack** con due interfacci una che va in wireless, l’altra in wire, a livello 3 posso fare delle bridging functions,

### Svantaggi wireless 🟨—

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 15.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 15">

<img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 16.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 16">

Location tracking è la cosa di più rilievo riguardo a questo, e anche la cosa più figa perché l’informazione per trackare le persone ci sarebbe 😀

## Multiplexing wireless

- Slide multiplexing

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 17.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 17">


Da cui vediamo che abbiamo 4 modi per fare multiplexing dello stesso segnale

1. Codice
2. Frequenza del sengale
3. Tempo  (non credo abbiamo molto controllo suq uesto lol)
4. E spazio

Vogliamo rendere non ambiguo la trasmissione, più dispositivi che utilizzino la stessa risorsa (mezzo di trasmissione di RF diciamo).

### Frequency 🟩

- Slide frequenza

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 18.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 18">


Le energie di canali diversi dovrebbero essere separate, se comunque si vada ad invadere, il filtro dovrebbe essere sufficiente per ignorare gli altri canali, oppure possiamo separare di più le frequenze, questi spazi vuoti sono **spazi di guardia**

Un altro lato negativo è che il canale è occupato, quindi quando c'è una asimmetria rispetto al modo in cui è occupato, allora c'è uno spreco.

### Time multiplexing 🟩

- Slide time multiplex

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 19.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 19">


Si va in round robin in pratica, c’è uno spazio di guardia nel tempo. Che è uno spreco.

e c’è bisongo di **sincronizzazione tra i mezzi trasmissivi** molto forte. Il vantaggio principale è che posso fare una trasmissione molto densa. (va diciamo a burst, quindi anche questo è uno svantaggio).

### Time and frequency multiplexing 🟩

- Slide time and frequency

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 20.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 20">


Viene utilizzato in GSM wifi. (è il provider che fornisce per ogni collegamento il seme per la gene), anche per quesot motivo era una comunicazione per tempo. (pagare telefonate per comunicare 9600 bit al secondo avevano di bitrate, costava molto).

Serve coordinamento preciso:

1. Mappa dei salti deve essere conosciuto

- Doppio spazio di guardia, sia per tempo sia per frequenze. (quindi anche qui utilizziamo molto spreco!

### Code multiplexing 🟩

La magia del CDMA in [Modulazione wireless](/notes/modulazione-wireless)

- Slide code multiplexing

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 21.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 21">


Questo sembra molto antiintuitivo, come facciamo ad utilizzare lo stesso canale per comunicare informazioni differenti?

Utilizzo un codice che mi permette di riestrarre! Che figa la cosa che si può riestrarre dal caos.

- **bandwidth efficient** ossia maggior bitrate con la minore banda.
- dal punto di vista dell’user è più lento (singolarmente più lento, ma complessivamente di maggiore utilizzo).
- Un pò di computazione in più per ricevere e mandare.

### Space multiplexing 🟩-

- Slide space multiplexing

    <img src="/images/notes/image/universita/ex-notion/Tecnologia Wireless/Untitled 22.png" alt="image/universita/ex-notion/Tecnologia Wireless/Untitled 22">


Ossia posizioniamo le nostre antenne in zone differenti. (abbiamo tipo tiling problem) (5G prova a ridurre al minimo l’area del segnale)

# Registro ripassi

| 22/04/23 | Boh, okey, direi. |
| --- | --- |
| 29/04/23 | La parte sull’infrastruttura WiFi non l’ho proprio capita, molto meglio la parte sul multiplexing. |
| 06/05/23 | Ancora, fare meglio la parte sull’infrastruttura. |
-- |
| 29/04/23 | La parte sull’infrastruttura WiFi non l’ho proprio capita, molto meglio la parte sul multiplexing. |
| 06/05/23 | Ancora, fare meglio la parte sull’infrastruttura. |