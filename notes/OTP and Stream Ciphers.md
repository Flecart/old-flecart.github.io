---
layout: page
permalink: notes/otp-and-stream-ciphers
tags: en
title: OTP and Stream Ciphers
---

### XOR operation
È una operazione binaria abbastanza semplice  però ci sarà importante per andare ad analizzare dei cifrari di un certo genere. Come il ONE TIME PAD che faremo fra poco in [OTP and Stream Ciphers.](/notes/otp-and-stream-ciphers.)

#### Teorema cifratura con XOR
Prendiamo $$X$$ una variabile aleatoria in $$\left\{ 0,1 \right\}^{n}$$ **uniforme**, sia $$Y$$ una variabile aleatoria su uno stesso dominio come vogliamo. Tali per cui $$X, Y$$ siano indipendenti
Allora avremo che $$C = X \oplus Y$$ è una variabile aleatoria **uniforme**.

Questo è necessario per la sicurezza di OTP.
**Dimostrazione**:
Supponiamo $$n=1$$ poi credo si possa estendere a $$n$$ più grande senza troppi problemi:

$$
\mathbb{P}(C=0) = \mathbb{P}((X,Y) = (0,0)) + \mathbb{P}((X, Y) =(1,1))
= \frac{p_{0}}{2} + \frac{p_{1}}{2} = \frac{1}{2}
$$

Quindi $$\mathbb{P}(C=1) = \frac{1}{2}$$ e si continua provando ad aggiungere parti.



## One Time Pad Cipher
Inventato da Vernam 1917. e 1926 sempre lui, infatti questo è il cipher che è nella teoria veramente unbreakable! Lo ha chiamato BSS = Binary Symmetric source, vedi: [https://cs.ioc.ee/yik/schools/win2006/massey/slides1.pdf](https://cs.ioc.ee/yik/schools/win2006/massey/slides1.pdf)

#### Descrizione del cipher 🟩
Prendiamo $$K, M, C \in \left\{ 1, 0 \right\}^{n}$$
Allora 

$$
E(k, m) = k \oplus  m
$$

e decrittazione diventa

$$
D(k, C) = k \oplus C
$$


La cosa importante è che $$k$$ è usato solo una volta, altrimenti ho problemi di sicurezza molto importanti (vedi many-time-pad).
Una altra cosa importante è che $$k$$ sia uniforme, che poi usando il teorema di XOR di sopra, possiamo avere massima sicurezza (entropia massima)

#### Necessità del mezzo comunicativo 🟨++
Ci sono anche restrizioni sulla **generazione** e sulla **conoscenza** della chiave dai due parties che cercano di comunicare!
<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 6.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 6">

#### Dimostrazione segretezza perfetta 🟩
Si basa sulla definizione in [Classical Cyphers#Security of the Key](/notes/classical-cyphers#security-of-the-key).

Vogliamo dimostrare $$\mathbb{P}(E(k, m_{0}) = c) = \mathbb{P}(E(k, m_{1}) = c)$$ .

Allora nel nostro caso abbiamo:

$$
\forall m,c: \mathbb{P}(E(k, m) = c)] = \frac{\#\text{Chiavi tali per cui } E(k,m) = c}{\lvert K \rvert }
$$

Va vale il fatto che $$\forall m, c$$   $$\#\left\{ k \in K: E(k, m) = c \right\} = 1$$
Quindi abbiamo la segretezza. (è 1 perché con OTP è unica la chiave che viene utilizzata per ottenere quello).

#### Svantaggi OTP 🟩
La difficoltà di utilizzo di OTP, nonostante le forti garanzie teoriche è dalla lunghezza della chiave.
Vedi [Classical Cyphers#Security of the Key](/notes/classical-cyphers#security-of-the-key) per maggiori dettagli.

1. La chiave deve avere **stessa** lunghezza del messaggio (overhead, difficoltà per mandare messaggi lunghi)
2. Distruzione della chiave dopo l’utilizzo (che si fa solo una volta!)
3. La comunicazione della chiave.

Per questo motivo non si utilizza per applicazioni commerciali.
### Attacks on OTP
#### Many time pad attack 🟨+
Se ho $$c_{1} = m_{1} \oplus PRNG(k)$$ e $$c_{2} = m_{2} \oplus PRNG(k)$$
Io so che solitamente da $$m_{1} \oplus m_{2}$$ riusciamo a ricavare $$m_{1}$$ e $$m_{2}$$ per ridondanze del linguaggio TODO: approfondire.
Quindi avendo i due ciphertext posso avere il valore sopra, perché

$$
c_{1} \oplus  c_{2} = k \oplus m_{1} \oplus  k \oplus  m_{2} = m_{1} \oplus  m_{2}
$$


Questo è stato usato nel **verona project** ('41 - '80) 
> American National Security Agency decrypted Soviet messages that were transmitted in the 1940s. That was possible because the Soviets reused the keys in the one-time pad scheme.

#### No integrità 🟩
Un attaccante può cambiare a suo piacimento il valore del *plaintext iniziale*, questo è soprattutto utile se sa bene cosa cambiare, altrimenti un umano probabilmente può capire che il messaggio è senza senso, ma nella teoria è giusto, il ricevente non può capire se il messaggio è stato modificato, o originariamente è stato mandato così:

Se attaccante modifica $$c$$ creando $$c^{*} = c \oplus p$$ il ricevente avrà $$m \oplus p$$ quindi è modificato, e non sa che è stato cambiato.

**NOTA particolare**
Questo attacco è particolarmente pericolo quanso
1. Si sa la posizione del testo da cambiare
2. Si sa il contenuto del testo cifrato in quella posizione.
Se si hanno queste informazioni posso metterci un valore a piacere in quella zona. Questa cosa dovresti riuscire a capire perché sia così.
Ad alto livello ti dico: fai xor con quella parte di testo, così hai 0 in plaintext, poi rifai xor col tuo messaggio per metterci quello che ti pare.
### Real-world attacks 
L'unico takeaway è non usare chiavi ripetute, che vedi sopra.
#### Windows NT PPT (non fare)
Perché veniva ripetuta la chiave sia client che server
#### WEP (non fare)
1. IV veniva ripetuta ongi 16M frames, che era presente
2. Le chiavi generate per i vari frame sono molto correlate, perché cambia solo IV in sequente (dice la prof. che inviava anche in chiaro). Non so esattamente i dettagli ma non dovrebbe essere importante.
# Stream Ciphers

Now we talk about stream ciphers, next about block ciphers, after that asymmetric cipher..,  con questra struttura

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled">

## Introduction

### Motivation and basic stuff 🟩

LSM was first kind of crypto for cellphones, and it was a stream cipher (fast, at least 12 y ago confronted with the other ciphers that existed).

1. Encrypting **individual bits!** when block ciphers encrypt blocks of it.
2. This leads to simple encryption and decryption operations. (this is a big addendum! most of embeeded devices use this because its easy  and fast!) The hardware is nice for these cyphers.

### Standard template of encrypt decrypt (non fare)

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 1.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 1">

And we can note it’s an shift cipher (affine cipher) discussed in the [Classical Cyphers](/notes/classical-cyphers).

A note is that the decryption uses the Plus! This is because we are in modulus 2, and a sum is actually a **xor operation**. (see the logic table of it).

- Proof of why the two operations are the same

    <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 2.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 2">


Sempre dalla tavola logica si può vedere che uno 0 può essere criptato 50% a 0 e 50% a1, quindi è resistente ad attacchi di analisi delle frequenze (ma questo solo se ho un generatore randomico buono !).

## Random generators

As the security of the scream cipher is dependent on the keys, we need to have a way to generate random keys.

### Categories of random number generators (3) (non fare)
Cercare su [Randomness](/notes/randomness) per descrizione sul tema.

1. True Random Number Generators  **tipically from random physical processes** ma non riesco a farlo moltro in fretta
    1. Lancio di dati
    2. Rumore
    3. Movimento del mouse.
    4. Random keyboard types. (e distanza tempo fra di essi).
2. Pseudo-random Number Generators (vorremmo qualcosa di random, ma che possa produrre la stessa sequenza **deterministic**
    1. Most of these are not criptografically secure! (are usually predictable, so useless for cryptography).
    2. But they satisfy important statistical properties necessary for randomness (and tests)
    - Forma classica di computazione

        <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 3.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 3">

3. Cryptographically Secure PRNGs (same as PRNGs, but with **unpredictability**).
    - Definition of unpredictability

        <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 4.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 4">

    1. Cioè non riesco a predire in che modo la sequenza può continuare in tempo polinomiale, data una sequenza di bits di output.

### Definizione PRNG
Per la Jocelyne è una funzione $$\left\{ 0, 1 \right\}^{s} \to \left\{ 0, 1 \right\}^{n}$$ in cui $$s \ll n$$ in teoria gli algoritmi possono generare cose infinite, ma per quanto ci interessa, vogliamo restringerci solamente a un numero finito di bit in output (che è cosa nella pratica abbiamo)
Una cosa è che l'algoritmo che li genera è **deterministico**, compattabile diciamo con [Kolmogorov complexity](/notes/kolmogorov-complexity), ma con buoni security guarantees e anche statistiche, vedi [Randomness](/notes/randomness).

#### OPT tramite PRNG 🟩
<img src="/images/notes/OTP and Stream Ciphers-20240222112904461.webp" alt="OTP and Stream Ciphers-20240222112904461">

Possiamo usare [#One Time Pad Cipher](#one-time-pad-cipher) usando i PRNG! Così risolviamo il problema di comunicazione di cose troppo grosse.

#### Analisi sicurezza stream cipher con PRNG
Solamente che abbiamo la nota teorica in [Classical Cyphers#Security of the Key](/notes/classical-cyphers#security-of-the-key) che non possiamo avere sicurezza se la chiave reale è minore rispetto a quella reale.

Stiamo spostando la sicurezza dell'OTP sul seed che genera.

### Examples of PRNGs
Questi sono stati analizzati tempo fa da Knuth nell'art of computer programming.
#### Linear Congruential Generator 🟩
abbiamo una sequenza $$r_{0} = seed$$ e $$r_{i+1} = a \cdot r_{i} + b \mod p$$
Sembra che questa cosa molto semplice abbiamo proprietà statistiche [Randomness](/notes/randomness) molto carine, ma molto facile da scoprire.

#### glibc random (non impo)
$$r_{i} = (r_{i - 3} + r_{i - 31}) \mod 2^{32}$$ in cui gli index sono dei singoli bit credo
Poi viene ritornato $$r_{i} /2$$ per qualche motivo

Nota: questo non è sicuro però come generatore!

### Security necessities for PRNGs
#### Non predictability (!)
Possiamo definire che un PRNG è **predictable** se esiste $$i \in N$$ tale per cui avendo la sequenza $$x_{0}, x_{1}, \dots, x_{i}$$ esista un algoritmo computabile secondo [La macchina di Turing](/notes/la-macchina-di-turing) e che sia anche efficiente tale per cui possa calcolare $$x_{i+1}, \dots$$. con una probabilità alta.
Se vale questo, e possono trovare l'algoritmo che computa questo algoritmo, avrei tutto poi per decifrare, anche se non conosco la chiave iniziale.

La prof la definisce così:
$$\exists A, \exists i : 1 \leq i \leq n - 1$$ tale per cui

$$
\mathbb{P}_{k \leftarrow K} \left[ A(G(k)|x_{1},x_{2}, \dots, x_{i}) = G(k)|x_{i+1}\right]  \geq \frac{1}{2} + \varepsilon
$$

con $$\varepsilon = \frac{1}{2^{30}}$$. Quindi se riesce a farlo in modo migliore del random già diciamo che è predictable.

Una domanda interessante è perché lo si definisce in modo probabilistico.

#### Statistical Tests e Advantage
Qui viene definito solo come un algoritmo che outputta 0 o 1 dopo che gli diamo la stringa iniziale in input. Note migliori dovrebbero essere in [Randomness](/notes/randomness).
Con questo test e la possibilità di definire una sequenza *truly random* $$r$$ possiamo definire il concetto di **advantage** che in breve è quanto bene riusciamo a distinguere la PRNG dal random vero.
<img src="/images/notes/OTP and Stream Ciphers-20240229100443638.webp" alt="OTP and Stream Ciphers-20240229100443638">

A me sembra abbastanza inutile questa definizione.
Però può essere utile per definire che il PRNG non è abbastanza simile al random.
L'algoritmo $$A$$ è spesso chiamato **oracolo**.
#### Security with advantage
Secondo la prof. questa "advantage" è una misura di quanto il sistema è rompibile. Se è simile a 1 sono abbastanza sicuro, altrimenti è 0. 

A PRNG $$G : K \to \left\{ 0, 1 \right\}^{n}$$ è sicuro se per ogni test possibile (e questo è già molto irrealistico) è vero che

$$
Adv_{PRNG}[A, G] \leq \varepsilon
$$

dove $$\varepsilon$$ è molto molto piccolo, *negligible si potrebbe dire*. Sembra che questo problema si riduca a $$P \not= NP$$ per qualche motivo strano. Queste sono definizioni con **oracolo** perché assumiamo di avere un $$r$$ che è *truly random*.

La cosa interessante con questa definizione è che se è sicura, allora non è predicibile, e questa conclusione intuitivamente non è molto difficile. yao ´82 sembra dimostrare che c'è proprio una equivalenza, se non è predictable, allora è sicuro sotto questa definizione.

Questa definizione comunque secondo @stinsonCryptographyTheoryPractice2005 chapt 6.9 è molto difficile da raggiungere, perché troppo facile da rompere, perché tratta di leaks di informazione, ma solitamente di molto poco conto.

### Semantic security (!)
Why is semantic security important? [see here](https://chat.openai.com/share/3de4a58b-707c-465b-8874-1090c23be472).
It relates to the notion "no information about hte plaintext from the ciphertext".
#### Definizione semantic security
Da [https://en.wikipedia.org/wiki/Semantic_security](https://en.wikipedia.org/wiki/Semantic_security)
> a **semantically secure** [cryptosystem]([https://en.wikipedia.org/wiki/Cryptosystem](https://en.wikipedia.org/wiki/Cryptosystem) "Cryptosystem") is one where only negligible information about the [plaintext]([https://en.wikipedia.org/wiki/Plaintext](https://en.wikipedia.org/wiki/Plaintext) "Plaintext") can be feasibly extracted from the [ciphertext]([https://en.wikipedia.org/wiki/Ciphertext](https://en.wikipedia.org/wiki/Ciphertext) "Ciphertext").

Da un punto di vista teorico, questo è un rilassamento della nozione di [Classical Cyphers#Security of the Key](/notes/classical-cyphers#security-of-the-key), in cui si richiede che siano uguali, in questo setting richiediamo che siano solo vicine le due probabilità. Solo che sembra che sia inutile la nozione per sé quindi introduciamo l'esperimento.

Nelle slides si fa un gioco di questo genere:
1. Challenger e adversary
2. L'avversario invia due messaggi in chiaro,
3. Challenger invia i messaggi cifrati
L'obiettivo dell'avversario è identificare quale cyphertext coincide a quale messaggio, se si può fare, non è sicuro secondo la definizione di semantic security di sopra, anche se non so nella pratica quanto sia vero.
Questo è vero quando [#Security with advantage](#security-with-advantage) è *negligible*, quindi non si può fare.

Per il prof. è leggermente diverso rispetto a questo:

> Probabilità di associare il ciphertext al corrispettivo plaintext.

Questo si può riassumere in questo:
<img src="/images/notes/OTP and Stream Ciphers-20240307112804651.webp" alt="OTP and Stream Ciphers-20240307112804651">

Ossia **non è in grado di distinguere** la funzione fatta con chiave da una funzione a caso nell'insieme delle funzioni.

#### Semantic security for many-time key

Abbiamo ora che la chiave è usata più di una volta, quindi abbiamo molte coppie, magari anche qualche **plaintext**. Infatti può **scegliere quale plaintext avere** a suo piacimento, si chiama **chosen plaintext**.

Ossia può scegliere quanti messaggi vuole per un certo esperimento

<img src="/images/notes/OTP and Stream Ciphers-20240307114233707.webp" alt="OTP and Stream Ciphers-20240307114233707">

#### Nonce based-security
L'idea è la stessa di cui abbiamo parlato in [Sicurezza delle reti](/notes/sicurezza-delle-reti) per un protocollo di autenticazione.
Un esempio carino di questo è in [Block Ciphers#Cipher Block Chaining (CBC)](/notes/block-ciphers#cipher-block-chaining-(cbc)) per cercare di randomizzare l'IV.

#### Randomized encryption
Sono delle funzioni che ritornano cyphertext in modo probabilistico (non sempre la stessa)

## Practical stream ciphers

In questo caso andiamo ad utilizzare un PRNGs, non più truly random, per le ragioni di efficienza di comunicazione…

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 7.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 7">


la chiave sono i valori delle cose affini nel LCG.. (forse anche il seed? boh)

### RC4 cipher
Non so bene come è stato creato questo algoritmo, probabilmente provato cose a caso???
Questo è stato inventato da Ron Rivest, lo stesso che ha inventato l'algoritmo di RSA del 1987.
#### Inizializzazione
Usiamo il seed $$s$$ per inizializzare una permutazione dei primi 256 numeri
```txt
S[i] <- arange(0, 257)
s = len S
j <- 0
for i <- 0 to 255 do:
	k <- S[i mod s]
	j <- (j + S[i] + k) mod 256
	swap(s[i], s[j])
```
Con questo algoritmo in pseudocodice

#### Generazione (non fatta)
<img src="/images/notes/OTP and Stream Ciphers-20240222115340902.webp" alt="OTP and Stream Ciphers-20240222115340902">
#### Attacchi 🟨
Non segue la definizione di [Classical Cyphers#Security of the Key](/notes/classical-cyphers#security-of-the-key), c'è del bias in quanto generato che si può sfruttare in modo abbastanza semplice, per esempio si può attaccare WEP che usava questo algoritmo in questo modo.
### Content Scrambling System (non fatto)

### eStream Cypher
Si ha solitamente un **nonce** in questo caso, lo stesso che abbiamo usato in [Sicurezza delle reti](/notes/sicurezza-delle-reti). Quindi un valore randomico utilizzato una singola volta

#### Salsa 20
È un algoritmo moderno di stream cipher, solitamente implementato in hardware per velocità.
Prende una chiave 256 bit e un nonce di 64.
Utilizza questo per fare un  mix di 20 rounds e poi produrre ili bit stream utilizzato per encodare il plaintext iniziale.
Questo è ancora sicuro, attacchi esistenti non riescono a romperlo totalmente [pagina wiki]([https://en.wikipedia.org/wiki/Salsa20](https://en.wikipedia.org/wiki/Salsa20)#Cryptanalysis_of_Salsa20)
Veloce che fa
Mezzo giga al secondo di cifrazione.
## Linear Feedback Shift Registers

This is a way to create a stream of bits to xor with the message. This stream is generated with a key.
One of the advantages is that it’s low power in hardware.

### Shift registers

You have to remember flip flops by [Circuiti Sequenziali](/notes/circuiti-sequenziali) in architecture.
1. Coso per storare un **singolo bit** sincronizzato dal clock del computer.

La cosa interessante quando si collegano input e output fra flipflops diversi, è che ad ogni ciclo di clock, si ha una specie di onda che shifta tutti i bit!
Quando l’output è rixorato in certi modi e rimesso all’inizio, ecco che riusciamo ad avere il feedback lineare!

- Esempio di mini Linear feedback Shift register

    <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 8.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 8">

- Esempio di LFSR generalizzato

    <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 9.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 9">


### Matematical Description

Con p, per dire se è 0 o 1 (o aperto o chiuso). E poi in pratica è l’operazione di +, o xor.

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 10.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 10">

We want to have a LSFR which has a very **long period**

Possiamo anche descrivere un LSFR con dei polinomi. In particolare è importante sapere

1. il numero dei registri
2. Le porte che sono aperte e quelle che sono chiuse.

Quindi si può rappresentare come

$$
P(x) = x^{m} + p_{m - 1}x^{m - 1} + \dots + p_{1}x + p_{0}
$$

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 11.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 11">

Però non so ancora perché questa rappresentazione del LSFR è utile, boh, lasciamo star.

### Theorem on the period of LSFR

<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 12.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 12">

L’idea della dimostrazione è tipo che gli stati interni della LSFR è al massimo $$2^m - 1$$, quindi al massimo il periodo è quello. (non posso avere 0 perché sennò avrei periodo di 1, che non serve a niente).

Ma non tutti hanno periodo massimo! Forse centrano qualcosa i polinomi ciclotomici, però sta fuori dalla mia capacità matematica lol.

- Esempi di LSFR massimi e non

    <img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 13.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 13">


### Known Plaintext Attacks

Il nemico conosce

- Tutto il ciphertext
- il grado dell’LSFR (se non lo sa fa bruteforce, e quindi è come se lo sapesse)
- Conosce i primi 2m bits del plaintext, quindi sa i primi 2m bits generati.

Dal plaintext conosciuto, vorremme ricavare tutti i bits successivi di questo stream cipher. (basta ricavare i valori dei p, ora vediamo un metodo per ricavarli).

Dato che possiede 2m bits conosciuti e conosce m, deve risolvere un sistema di m incognite e m equazioni, e questo si fa, quindi così riesce a **ricavare LSFR** da queste!