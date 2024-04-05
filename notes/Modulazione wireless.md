---
layout: page
permalink: notes/modulazione-wireless
tags: en
title: Modulazione wireless
---

Ripasso Prox: 7
Ripasso: May 28, 2023
Ultima modifica: May 19, 2023 1:57 PM
Primo Abbozzo: April 19, 2023 1:43 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Modulazione del segnale

### Introduzione

### Digital modulation  🟨

- Slide introduzione

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled">


Modulazione digitale: prendiamo un dato digitale e trasmesso con un segnale analogico, come le RF.

ASK: amplitude shift keying

FSK: frequency shift

PSK: phase shift

Questi sono i tre metodi principali, che dipendono dalle caratteristiche dell’onda descritte in [Fisica del Wireless](/notes/fisica-del-wireless).

**TRE CARATTERISTICHE**

Power

Resistenza interferenze. (robustezza)

**ANALOG MODULATION**

Per modulare un segnale analogico si utilizzano principalemente **AM o FM**, amplitude o frequency modulation, raramente si utilizza PM.

In AM la frequenza è la stessa, ma posso cambiare la ampiezza, in pratica con l’ampiezza provo a ricalcare l’ampiezza dell’onda iniziale (credo che intuitivamente onda radio ha frequenza molto più alta del suono, quindi riesco a descriverlo bene, credo, probabilmente sbaglio).

### Modello trasmittente e ricevente 🟩

- Struttura trasmittente

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 1.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 1">


Il primo prova a rappresentare il segnale digitale in un segnale sinusoidale. (probabilmente trasformate here).

Il secondo blocco prende la codifica in segnale analogico e la trasforma in una onda radio (modulata in un certo modo). (prende in input anche il canale in cui codificare le cose), e questa è data all’antenna che genera RF.

- Struttura ricevente

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 2.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 2">


Il segnale nel frattempo:

- Ha perso intensità
- Può avere shift di fase a seconda dei rimbalsi

Dal ricevente modula l’onda radio che riceve in un segnale analogico, che ora però **possiede itnerferenze** quindi non è una onda clean, e prova a fare una interpretazione.

## Algoritmi di modulazione digitale

### ASK FSK PSK 🟩

- slide ASK e FSK e PSK

    Nella parte tagliata c’è scritot “Signal modulation (Shift keying)”

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 3.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 3">


ASK

La tecnica più semplice è **amplitude shift keying (aka modulazione digitale con amplitude)** che non è altro che trasmettere onde di frequenza precisa per canale per 1 silezio per 0. (ma come faccio a gestire le interferenze? Non c'è silenzio in questo modo!) Credo che questo sia molto simile al morse.

Ad esempio se la distanza è troppo larga, leggerebbe 0.

Se il rumore di fondo è troppo alto leggerebbe 1. ecco interferenze

FSK

Il segnale digitale è codificato **attraverso la frequenza del valore**, per esempio se utilizziamo una metafora fisica, se il segnale è rosso ho 1 se viola 0, cambia colore diciamo :).

Questo è più resistente alle interferenze.

PSK

È più difficile da implementare. Viene mantenuta sia la frequenza sia l’ampiezza.

### Rappresentazione del segnale 🟩

- Slide rappresentazione

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 4.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 4">


Tre tipologie di grafici, la terza, in cordinate polari è la più utilizzata, anche se non ci dice la frequenza (la frequenza è quella mantenuta durante la radio carrier nel sistema di modulazione accennato prima). I punti su questo grafico sono chiamati **simboli**

Nella sconda perdiamo la fase, poco utilizzata.

Nella prima ha praticamente tutte le infomrazioni (la fase però credo sia solo relativa).

### Binary Phase Shift Keying e QPSK 🟩

- Slide BPSK e QPSK

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 5.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 5">


Abbiamo dato ai **simboli** del grafico alcuni valori binari, questo ci da un modo per andare a **interpretare i segnali**  seguendo quel grafico.

### QAM and HIerarchical modulation 🟩

Solo che la densità dei simboli è ora ancora maggiore, utilizzo **sia intensità sia fase**

- Slide QAM

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 6.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 7.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 7">


**HIERARCHICAL MODULATION**

È una cosa ancora più precisa!

- Slide HM

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 8.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 8">


Si utilizza un trucco di codifica di utilizzo della nuvola di segnali e una codifica interna!

Quesot si utilizza anche per **mobile video call** in modo che la voce sia codificata meglio.

- Slide mobile video call nice

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 9.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 9">


## Spread spectrum techniques

Solitamente potremmo utilizzare delle **narrowband** spectrum, solo che queste sono molto sensibili ad interferenze nella narrowband, per questo motivo si preferisce andare su **spread spectrumn** e andiamo ora a parlare di alcune tecnologie utilizzate per questo.

### Direct sequence spread spectrum 🟩-

In pratica vado a definire una **chipping spectrum** che possiede certe proprietà statistiche che vengono interpretate come rumore di sottofondo (non correlate fra di loro) nel caso in cui non si conosca il codice.

- Slide funzionamento del chipping sequence

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 10.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 10">


La codifica col chiping sequence non è altro che un **xor**, con il bit che vogliamo inviare e la chipping sequence

- Slide codifica e decodifica del codice

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 11.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 11">


Questo processo di xor è descritto sotto in  Code division multiple access 🟩. È questa tecnologia di code division multiple access. che permette questa trasmsisione su frequenze molto diverse, ed essere comunque ricevuto.

### Code division multiple access 🟩

Fa sì che utilizzando **chipping sequence** poco (preferibilmente niente) correlate fra di loro, il segnale viene interpretato come segnale di sottofondo (white noise) e quindi il ricevitore, come per magia, riesce comunque a comprendere il segnale iniziale.

- Esempio di trasmissioen corretta di CMA

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 12.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 12">


Praticamente a lato ricevente esiste un **integratore** che fa la somma e viene utilizzato questo per andare a decidere se è un bit 0 oppure 1 (per comodità solitamente lo 0 viene codificato come se fosse un -1).

### Frequency hopping spread spectrum 🟩

Viene utilizzata l'energia per mandare in modo pseudorandomico (secondo il seed, credo ne abbiamo già parlato in precedenza con la cosa di hedy lamarr).

- Slide FHSS

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 13.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 13">


Praticamente il segnale è unico (cioè non è disperso su una banda larga di segnale, ma è narrowband) comuqnue per chi non conosce il codice sembra rumore di fondo

Si utilizza **host_master come seed**

Fast and slow hopping a seconda del numero di bit mandati prima di switchare segnale.

### Orthogonal Frequency Division Multiplexing 🟩

> signal transmission technology that separates a single high-speed data stream into multiple sub-carrier signals that are transmitted simultaneously. Each sub-carrier signal uses a different frequency, presenting a unique path for data transfer. By using multiple sub-carriers in a single channel, OFDM technology can transmit data more efficiently and reliably, even in noisy and highly congested RF environments
>

Abbiamo pacchetti di dati poco distanziati (quind il bitrate nominale è molto alto, tutto viene fatto in parallelo).

- Slide OFDM

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 14.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 14">

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 15.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 15">


**STRUTTURA**

Quattro carrier sono utilizzati per **gestire il canale** quindi per dire che il canale non va, bisogna cambiare, rallentare etc. In modo simile ai pacchetti di gestione della congestione nei routers.

È molto efficiente dal vista del bandwith (servono 9.76 kilohearz per un sub carrier) e se ho 20 Mhz ho 2048 subcarrier (questo ci fa venire in mente il perché è lungo quella quantità di band withd :D)

La cosa bella è anche l’indipendenza con i subcarriers!

1 milione per ogni subcarrier (basta fare qualche calcolo, tipo massimo di tutti i canali sono circa 3 Gbit per questa tecnologia). questa è **WiMax**

- Slide WiMax

    250k bit per subcarrier che sono comunque 500 Mb su distanza larga.

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 16.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 16">


### Funzionamento di OFDM 🟨

Si utilizzano magie matematiche per questa tecnologia, ed è molto intelligente :D

Abbiamo un teorema che ci dice che le funzioni di seno e coseno sono tutte fra diloro **ortogonali** ossia l’intergrale del segnale è sempre 0 sopra il periodo di tutti.

<img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 17.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 17">

Slide segnali ortogonali

Questo permette di sapere che la somma di tutti gli altri segnali danno somma zero e io so in che modo andare a leggere. In questo senso i segnali interferiscono sì, ma lo fanno in un modo predicibile che mi permette di ritrovare la informazione iniziale.

<img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 18.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 18">

<img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 19.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 19">

Esempio decodifica

Intuitivamente le FFT ci permettono di cambiare frame of view, se prima erano tutte compattate sul tempo, ora è compattato sulla frequenza, per questo motivo riuscimo a distinguerle per bene (quindip ossiamo distinguere anche il bit trasmesso per il singolo subcarrier)

20Mhz con 52 subcarrier con 4 pilot e il resto dei dati. e utilizza 250k modulazioni l secondo (questo è il massimo!).

Nelle slides c'è una D, che sta per differential, perché sta relativo al precedente (non è 0, o  180, ma è differenza rispetto al precedente credo, ma comunque ha detto che non è per niente importante questa cosa. Esistono **bits di convoluzione** che sono utilizzati per fixare errori di trasmissione.

**ESEMPI:**

- Slide OFDM

    <img src="/images/notes/image/universita/ex-notion/Modulazione wireless/Untitled 20.png" alt="image/universita/ex-notion/Modulazione wireless/Untitled 20">


Esempio per DBPSK: 1 bit per 48 subcarrier, la metà sono utilizzati per dato, l'altra per protezione, ho 24 carriers per durata, quindi 24 * 250k bits al secondo che è proprio 6kk!

Se prendo DQPSK allora ho 3/4 per dati, e questo fa tanti calcoli, ma poca roba..

Una cosa che accade con 64 QAM che invece di fare 1/2 di protezione viene fatto solamente un terzo perché se raggiungi quel punto vuol dire che il canale è già molto forte.

E c’è un programma di controllo che decide quale codifica andarea d utilizzare (tornando indietro se non (riceve gli acks)

Nel caso io abbia bisogno di ancora altri bit potrei aggiungere altri subcarriers (e si può fare in modo dinamico, si chiama **channel bonding**. (canali di frequenza arbitraria in base a quanto ne ho bisogno ! esempi di tecnologie che lo utilizzano: 802.11 af ac)