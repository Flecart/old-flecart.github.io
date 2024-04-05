---
layout: page
permalink: notes/fisica-del-wireless
tags: en
title: Fisica del Wireless
---

Ripasso Prox: 18
Ripasso: May 17, 2023
Ultima modifica: May 5, 2023 5:39 PM
Primo Abbozzo: March 24, 2023 10:16 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Reti wireless

## Introduzione

### Radio 🟩

- Slide radio

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled">


Antenna: converte corrente in segnali radiorequenza e viceversa. le segnali radiofrequenza sono onde radio con frequenza diversa per rappresentare 1 o 0. Un altro modo per mandare 1 o 0 sarebbe semplicemente cambiare l’intensità della onda, mantenendo la stessa frequenza.

Viene utilizzata una variazione di potenziale elettrico per creare il segnale, dovrebbe essere un oscillatore armonico in pratica credo.
Creando questo flusso di elettroni, crea anche un campo elettromagnetico a lui ortogonale, questa è l’onda radio, che si propaga alla velocità della luce.

Essì per capire questa parte serve ripassare un pò di fisica, in old_unused_files/flecart-zone/Control Center/Tutte le note di scuola/Onde elettromagnetiche (in realtà c’è molto poco qui).

Il prof ha spiegato questo fenomeno in 20 minuti, [questo video](https://www.youtube.com/watch?v=FWCN_uI5ygY&ab_channel=Lesics) sembra buono per comprendere questa cosa.

### Caratteristiche dell’onda elettromagnetica (3) 🟩

L’onda radio utilizzata in wireless è solamente un sottotipo delle onde radio.

*FREQUENZA ONDA*

La relazione fra lunghezza d’onda e frequenza dell’onda con la velocità dell’onda è conosciuta: $$v = f\lambda$$ Comunque la frequenza è un altra caratterizzazione importante per l’onda.

- Slide frequenza

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 1.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 1">


Nota: questo è un range di frequenza! Questo ci permette di creare molti **canali** con frequenze diverse.

Un problema molto difficile è la scomposizione delle frequenze, così possiamo isolare i singoli canali. Le onde sono additive, sono tutte messes assieme!

NOTA: **massima efficienza** per la creazione di onde è quando la lunghezza dell’antenna è stessa lunghezza dell’onda radio, ma anche sottomultipli binari sembrano andare bene.

**AMPIEZZA ED INTENSITÀ**

Poi l’intensità, ossia l’ampiezza dell’onda, è l’altro carattere importante

- Slide ampiezza onda

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 2.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 2">


È strettamente correlato con l’energia utilizzata per generare l’onda, cioè se ho ampiezza maggiore ho speso in generare più energia per generare quell’onda.

Nota: L’energia dell’onda decade **in distanza quadratica**, (se voglio raggiungere doppia distanza, devo quadruplicare la potenza) quindi perde energia molto velocemente. In modo intuito il motivo per cui questo succede è che l’energia iniziale è la stessa, idealmente dopo un certo momento è ancora la stessa energia (nel senso che non la perdo), però è dispersa in una area molto maggiore, che si espande quadraticamente con la distanza, ecco che quando andiamo a ricevere stiamo prendendo solamente un pezzo molto piccolo di questa energia iniziale.

- Esempio del panino con la nutella

    Questo è un esempio che il prof. ha fatto in aula, è un modo molto visivo per dare l’intuito di questa decadimento di potenza.

    1. Mettiamo caso che prendiamo un cucchiaione di nutella e la spalmiamo sulla fetta. In questo caso la fetta è bona, si sente bene la nutella.
    2. Mettiamo caso che di nuovo prendiamo il cucchiaione, la mettiamo sulla fetta. E ops, la fetta diventa in un secondo grosso 300km, la nutella è sempre la stessa, ed è spalmata uniformemente, ora la sento ancora la nutella?
    3. Se c’è anche un muro poi mi perndi anche la nutella quando la fetta si espande! ne ho ancora di meno

Ovviamente se diventa troppa poca l’eneergia, poi non riesco a sentire cosa dice! cioè non detecto il segnale

- Slide decadenza di potenza

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 3.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 3">


**FASE DELL'ONDA**

Una terza caratterizzazione, oltre l'ampiezza e la frequenza è la **fase** dell’onda. ossia quanto sono spostate rispetto a un periodo assoluto (questo shift di fase è in radianti o gradi)

Un onda spostata rispetto al riferimento, posso considerarla o in anticipo o in posticipo, la somma delle due però è 360, quindi è lo stesso modo di descrivere le due.

- Slide phase shift

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 4.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 4">


Si hanno problemi con la fase quando questa rimbalza con qualcosa e va a interferire con sé stesso.

### Classificazione zone di segnale (3) 🟨+

Andiamo a definire una **signal detection limit**, ossia il punto da cui dopo non e` piu` detectabile il segnale, e quindi non comprendo più cosa mi viene comunicato.

Su quanto definito sopra potremmo definire 3 zone correlata alla distanza fra il sender e il ricevente:

- Slide zone di propagazione segnale

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 5.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 5">


La capacità del ricevente influenza in quale zona stai (come se avessi l’orecchio più fine o meno!)

1. **Trasmission range** quando riesco a comprendere un un errore bitrate molto basso
2. **Detection range** non si riesce a capire cosa viene trasmesso, ma si nota che si trasmette qualcosa
3. **Interference range** quando i segnali potrebbero anche non essere rivelati perché troppo deboli

A volte se ho molte sources, un buon metodo potrebbe essere mettere un filtro che filtri un certo tipo di canale, se ascolto sto ascoltanto un certo misto di segnale. (una cosa carina è che la radiazione di fondo si mischia con questi 😛)

### Problemi della rete wireless (3) 🟨-

1. intensità del segnale che decade in fretta
2. intereferenza con stessa frequenza da sorgenti diversi
3. Interferenza con sé stesso (se percorre distanze diverse, rimbalzando da qui e la, e giunte sfasato! O passare ostacoli?)

**OSTACOLI! (3)**

1. Dietro l'ostacolo faccio fatica ad avere segnale
2. L'ostacolo fa rimbalzare l’onda radio
3. Il materiale influenza fortemente questo comportamento dell’onda (anche rifrazione!)
- Slide ostacoli assorbono

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 6.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 6">

- Slide influenze ostacoli

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 7.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 7">


In generale se l'onda è a bassa frequenza, passa l'ostacolo, se è alta è molto facile che si blocchi.

Quindi abbiamo un tradeoff di questo tipo:

1. Onda bassa frequenza, va lontano, ma contiene poche informazioni al secondo
2. Onda alta frequenza non va lontano, ma tante informazioni! (motivo per cui la cella 5g deve essere per forza piccola)

E ci sono alcuni fenomeni come **terminale nascosto o fading**, sempre per caratteristiche di ostacoli e evanescenza del segnale che interferiscono fra di loro.

**PUNTI CIECHI DELLE ANTENNE (1)**

Se posiziono l'antenno in un certo modo, questa non riesce proprio a leggere le onde radio in una certa posizione (a causa della polarizzazione)

- Slide punti ciechi (polarizzazione)

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 8.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 8">


Se sto allo stesso orientamento dell'antenna, riesco a leggere tutto bene le informazioni delle antenne, mentre invece se sto ortogonale non potrei vedere niente. Questa è anche chiamata **polarizzazione dell’onda.**

- Slide polarizzazione (con esempio di foro per intuito)

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 9.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 9">


La soluzione a questo problema è utilizzare più antenne di **diverse orientazioni**. Quindi comunque riesco a prendere qualcosa (se lo metto in modo ortogonale, a L, riesco a ricavare il segnale iniziale sempre).

NOTA: **indoor** ho i muri che *rimbalzano*, quindi alla fine comunque mi arriva di direzione giusta, e non ho un problema di sensibilità tale.

NOTA2: i satelliti sono fighi, non hanno nessun ostacolo per comunciazione onde radio, forse le nuvole sono il più grande problema, che riescono ad assorbire e riflettere anche qui le onde radio.

### Effetti sull'uomo (non fare) 🟩

300 MHz and 300 GHz sono **il range delle microonde**, quando il cellulare emette certe onde di quella requenza, allora è proprio questo! Solamente di intensità molto minore. (sono milliwatt contro centinaia di watt), quindi un pò comunque scalda! E attraversa comunque un pò la materia, e scalda l’acqua a questa frequenza.

[https://www.fda.gov/radiation-emitting-products/cell-phones/do-cell-phones-pose-health-hazard](https://www.fda.gov/radiation-emitting-products/cell-phones/do-cell-phones-pose-health-hazard)

approfondimento carino: vedere come funziona la risonanza, e se questo è il fenomeno che fa scaldare l’acqua.

- Slide effetti sull'uomo

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 10.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 10">


Come fanno le onde radio ad arrivare alle auto? Se la cabbia di faraday proprio va a schermare il tutto? Evade molto poco, e quello è quello che va nell'access point.

## La trasmissione del segnale

### Guadagno del segnale (2) 🟩

Si dice guadagno del segnale quando incremento la potenza del segnale, in un certo rapporto in confronto a quanto trasmesso. Si misura in DECIBEL.

1. **guadagno attivo** questo è quello che vanno a fare gli amplificatori, che hanno bisogno di energia dall'esternom prende le onde in input e utilizza l’energia per rigenerare il segnale, sono quello che fanno i repeaters.
2. **guadagno passivo** quando non ho bisogno di energia all’esterno. Per esempio è così che funzionano i dischi delle parabole, che riescono a prendere molto segnale, e concentrarla in un unico punto.

### Perdita di segnale 🟩-

1. **Intenzionale** questa è utile per gestire l’energia (e.g. far passare 6 ampere in un circuitino sarebbe troppo, quindi trasformo in calore prima di far entrare nel circuito) (oppur esempio un connettore, che riflette in parte e fa passare con intensità minore, e questo è proprio misurabile id dB)
2. **ostacoli** come acqua. perdita del segnale ‘non voluta’, dovuta ad ostacoli, ad esempio
in caso di nebbia, che rappresenta un ostacolo per le microonde che scaldando le particelle
d’acqua di cui è composta la nebbia, facendo ridurre l’energia del segnale (e quindi
l’ampiezza), riducendo la distanza che può percorrere il segnale.
- Slide tipologie di effetti di ostacoli

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 11.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 11">


### Multipath propagation (2) 🟨—

Il segnale può giungere da molte direzioni, e il segnale ricevuto può essere in una fomra strana (phase shifted, tre echi meno energetici, parzialmente sovrapposti.

- Slide multipath

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 12.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 12">


Gli effetti principali della multi path sono:

- I segnali possono arrivare in momenti diversi e fare interferenza con sé stesso
- I segnali possono arrivare phase shiftati.

### Effects of mobility (non fare?) 🟥

Ci sono proprio delle zone in cui il segnale è migliore e altre in cui non va per il wifi, in cui cambiano subito questa parte di segnale

- Slide mobilità

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 13.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 13">


L’effetto principale è la **variabilità del segnale** quando ci muoviamo, possiamo avere alti e bassi e continuamente ci connettiamo a ripetitori diversi (questo è anche un modo per ricostruire il tuo percorso, a seconda di quale dispositivo ti sei connesso vicino).

Cambiano anche distanza dal destinatario e dagli obstacoli.

### Voltage Standing Wave Ratio 🟨+

È proprio necessario utilizzare la stessa impedenza! Altrimenti diventa molto inefficiente,

VSWR è una perdita del segnale quando l'impedenza della sorgente e del ricevente sono diversi fra di loro. C'è un effetto resistivo quando le correnti si spotano in questo modo, che crea calore. (corrente genera Se il valore di impedenza è diverso ho:

1. Irregolarità (anche ritorno di energia), perdita di energia.
2. bruciare delle componenti.

Calcolato come **rapporto delle impedenze del trasmettitore e ricevente**.

### Intentional radiator e regulations 🟩-

**Intentional radiator** è il trasmittitore più cavi e connettori con l'antenna

**Intentional radiator Power output:** quanità di energia data all'antenna dall'intero componente dietro l’antenna, quindi cavi connettori e il generatore (i cavi fanno perdere un pò di energia, in questo senso l'antenna non riceve l’energia del trasmettitore come da sorgente, ma quella decaduta dalla corrente.

Su questo IR Poutput **si mettono le regulations**, ossia massimo energia a livello antenna, ma si potrebbe fare che l'energia che riceve siano dentro i limiti, ma utilizzo una antenna in modo da focalizzare il raggio, rendendolo molto più denso.

Per questo motivo bisognerebbe mettere il la regolazione non sul power output, che si può concentrare, ma sul **EIRP (Equivalent isotropically radiated power)**, ossia la potenza radio **irradiata dall’antenna** con anche gli effetti passivi (ossia concentrati diciamo), una volta che sono al massimo dell Power output.

## Misura della potenza

### Il WATT 🟩

Quelli che ci interessano sono soprattuto i **watt**, che sono una misura della potenza, la quantità di lavoro fatto al secondo.

In pratica è una misura di

> energy needed (in a given time unit) to apply a
given “pressure” to a given “amount of charge”, by resulting in
a flow of current.
>

Le formule classiche sono le **leggi di OHM** che qui però saltiamo.

- Slide misura della potenza

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 14.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 14">


### I decibels 🟩

Spesso andare a ragionare in watt è molto scomodo, perché la potenza cade in modo logaritmico (non era quadratico??) dato che è logaritmico meglio utilizzare i decibels

> Decibel (dB) measures the logarithmic *relative* strength between two
signals (mW are a linear absolute measure a energy)
>

NOTA: è molto importante il fatto che i decibels siano relativi!

- Slide sui decibels

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 15.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 15">


**CALCOLO DEI DECIBELS**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 16.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 16">



$$
dB = 10 \times \log_{10}(\dfrac{W_{Receiver}}{W_{Sender}})
$$


Formila inversa:


$$
W_{receiver} = W_{sender}\exp(dB \log(10)/ 10)
$$


- Esempi di calcolo

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 17.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 17">

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 18.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 18">


Il vantaggio principale è che  invece a stare modificare moltiplicazioni e divisioni, sto utilizzando somme e sottrazioni che creano numeri molto più gestibili, (questo è sempre isomorfismo prodotto e somma in un certo gruppo credo).

Una cosa carina è che tipo 3 decibels è moltiplicare o dividere per 2.

### Normalized decibels dBm 🟩

Praticamente diciamo che $$1 mW = 1dBm$$

- Slide utili decibells

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 19.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 19">



$$
P_{dBm} = 10 \log(P_{mW}) \\
P_{mW} = \exp(P_{dBm} / 10)
$$


Con qualche costante messa bene per i logs.

- Scala decibells milliwatt

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 20.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 20">


### Isotropic decibels dBi 🟩

I decibels isotropici misurano il **guadagno passivo** dato dall’architettura dell’antenna confrontandolo con il caso ideale di un antenna isotropica, con efficienza 100%, equiparabile a un dipolo di lunghezza nulla.

- Slides isotropic decibels

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 21.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 21">

    <img src="/images/notes/image/universita/ex-notion/Fisica del Wireless/Untitled 22.png" alt="image/universita/ex-notion/Fisica del Wireless/Untitled 22">


### dB-dipole 🟩

Questo è solamente un dipole translato di 2.14 se mi ricordo bene, solamente il compare di una antenna dipolo con una isotropica i suppose, quindi non molto di differenza.