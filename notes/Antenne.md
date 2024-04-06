---
layout: page
permalink: notes/antenne
tags: en
title: Antenne
---

Ripasso Prox: 10
Ripasso: May 23, 2023
Ultima modifica: May 14, 2023 5:20 PM
Primo Abbozzo: April 5, 2023 2:24 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Antenne

## Omnidirezionali

### Antenne omnidirezionali 🟩

- Slides antenne omnidirezionali

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled.png" alt="image/universita/ex-notion/Antenne/Untitled">


Il senso di omnidirezionale è in tutte le direzioni dell'antenna (nota: non è isotropico, perché non è da un singolo punto).

in passato era importante andare a guardare la direzione per trovare la polarizzazione migliore. Praticamente irradia a 360 gradi sul piano permedicolare all’antenna.

- Esempio pattern di radiazione

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 1.png" alt="image/universita/ex-notion/Antenne/Untitled 1">


Questo genere di antenne sono **irrealizzabili** la più simile è la antenna dipolo dipolo, ma comunque non rispetta le antenne in questo verso diciamo. ricorda i dBi che abbiamo citato in [Fisica del Wireless](/notes/fisica-del-wireless).

### Guadagno passivo in ominidirezionali 🟩

- Slide guadagno passivo

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 2.png" alt="image/universita/ex-notion/Antenne/Untitled 2">


Si può concentrare **l'energia nella shape** del dipolo. Per esempio se lo faccio più schiacciato, ho un range molto più forte orizzontalmente, ma appena su o appena giù perdo segnale.

Mentre al contrario, se ho una forma più arrotondata ho segnale solo se gli sto vicino, ma molta meno importanza stare sopra o sotto.

- Esempio del guadagno passivo e attivo delle antenne

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 3.png" alt="image/universita/ex-notion/Antenne/Untitled 3">


NOTA: posso avere un **guadagno fino a 10 Db** quindi 10 volte tanto.

Ed è anche per questo motivo che andiamo a misurare l’EIRP e non la potenza che finisce nell’antenna, anche chiamata **Intentional radiator Power output.**

*POSIZIONAMENTO DELL ANTENNE*

Andiamo a chiederci in che modo mettere le antenne in modo che più utenti possibili possano usufruire del segnale.

Una soluzione potrebbe essere **inclinare l’antenna:**

- Slide inclinazione dell’antenna

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 4.png" alt="image/universita/ex-notion/Antenne/Untitled 4">


## Antenna semidirezionale

### Semidirezionale (3) 🟩

Questi sono i più comuni, sparano principalmente energia di fronte (quindi metterllo su un muro è cosa buona).

- Esempi di antenne omnidirezionali

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 5.png" alt="image/universita/ex-notion/Antenne/Untitled 5">


Di solito si mettono nel muro (sono **panel** o patch, che praticamente cambiano di costruzione, ma alla fine hanno la stessa funzione ).

Mentre gli **yagi** sono sparati nella direzione in cui punta (e mirano alla posizione del ripetitore, perché da lì ricevono meglio.

**beam width (!!!)** è un valore che è espresso in angoli, e misura quando largo o concentrato il segnale, è lo spazio necessario per **dimezzare il segnale**, partendo dall'asse di direzione. Questa concezione ci serve per parlare di antenne altamente concentrate.

### Highly-directional antennas 🟩-

- Slide esempio highly dir

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 6.png" alt="image/universita/ex-notion/Antenne/Untitled 6">


Esempi sono **grid e parabolic dish** che perdono energia attorno molto molto velocemente, però se sei nel beam width lo ricevi molto bene (va lontano si possono utilizzare per antenne lungo raggio come satelliti).

Potrei anche s.ettorializzare la trasmissione: ogni antenna si prende solamente un certo angolo

**Line of Sight** ossia la linea raggio dritta fra trasmissione e ricevitore.

### Fresnel zone 🟩—

Definiamo al centro della line of size come **la zona di fresnel**, sarebbe meglio metterlo libera da ostacoli. Si concentrano il **massimo numero di onde additive** quindi se c’è qualcosa mi toglie molto.

- Slide zona di fresnel

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 7.png" alt="image/universita/ex-notion/Antenne/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 8.png" alt="image/universita/ex-notion/Antenne/Untitled 8">


Se è più di 20 percento occupata, allora è meglio andare sugli ostacoli (altrimenti non ottengo maggiore ricezione, continuo a perdere energia negli ostacoli e ho inquinamento dei raggi).

Se non è ostruita sto permettendo l’energia ad arrivare con massima efficienza al ricevitore.

NOTA: la distanza è dipendente **solo da frequenza e distanza**

- fresnel e curvatura terrestre

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 9.png" alt="image/universita/ex-notion/Antenne/Untitled 9">


### Settorializzazione di antenne direzionale (boh) 🟥

Si parla di **multiplexing spaziale** perché possiamo andare ad utilizzare lo stesso canale, ma in zone diverse perché il segnale è concentrato solamente in quella direzione.

### Azimuth and elevation charts 🟩

- Slide azimuth and elevation charts

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 10.png" alt="image/universita/ex-notion/Antenne/Untitled 10">


Questo grafico è utilizzato per guardare in ogni angolo dell'antenna, quanto è l’energia che viene trasmessa.

Mentre azimuth gira in orizzontale (quindi visuale dall’alto), elevation gira in modo verticale (quindi visuale da terra diciamo).

Inoltre è importante dislocare le antenne in posizioni sparse. Così se ricevo un segnale posso provare a ricavare il segnale originale provando a buttare via il noise. Di questa parte si potrebbe ricollegare allo space multiplexing citato in [Tecnologia Wireless](/notes/tecnologia-wireless)

Se li metto a lambda mezzi, allora almeno una delle due antenne prendono un segnale buono, l’altra potrebbe essere in opposizione (mi sembra comunque un sacco di fisica che ignoriamo qui).

Sotto serve un controllore che riesca ad annullare e scegliere i segnali o gli sfasamenti o annullamenti. (questo controllore dovrebbe rifasare il segnale e rendere il segnale additivo.

- Slide antenna diversity

    <img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 11.png" alt="image/universita/ex-notion/Antenne/Untitled 11">


**Beam forming**

Avendo queste antenne, io riesco a creare un raggio RF, ritardando in modo opportuno certi piatti, e posso mandarlo dove mi pare. (controllo sulla direzione, solamente ritardando le fasi di certe antenne).

### Path loss in free space 🟨-

<img src="/images/notes/image/universita/ex-notion/Antenne/Untitled 12.png" alt="image/universita/ex-notion/Antenne/Untitled 12">

Slide path loss

Notiamo che la perdita di segnale dipende dalla frequenza e dalla distanza → frequenza alta implica segnale perso più in fretta. 36.6 è una costante che funziona sulla Terra.

Si noti che duplicando la distanza, l'energia cade 4 volte e questo risultato è coerente con questo dato.

Per vedere se -86 dB è sufficiente bisogna guardare la soglia di ricezione del nostro dispositivo. Se il link budget è positivo allora si riceve, il nostro obiettivo è **progettare sistemi a link-budget positivi**.

Si noti che non è necessario che questo link-budget sia positivo, significa che sto consumando un sacco di energia.

1. Spreco energia nella trasmissione
2. Disturbo trasmissione di altri

Vogliamo il minimo link-budget positivo.

Questo si chiama **system operative margin** o valore operativo del sistema.

Il margine extra è chiamato **fade margin** per resister al path loss, fase, e riflessioni e simili, in generale questo fade margin è un +10 fino +20



# References