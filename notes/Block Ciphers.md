---
layout: page
permalink: notes/block-ciphers
tags: italian
title: Block Ciphers
---

Utilizzano blocchi per cifra invece che stream generators.

- DES 56 bit
- 3DES 56*3 bit di chiave
- AES che può andare a 128, 196 o 256
Solitamente i stream ciphers studiati in [OTP and Stream Ciphers](/notes/otp-and-stream-ciphers) sono più veloci.
### Data Encryption Standard

- 1974 da IBM su commissione di NSA

in quel periodo era solamente fatta dalla intelligence, non c’era bisogno di comunicazioni per il pubblico in quel periodo.

- 1977 - 1998 questo era lo standard per gli stati uniti.
- best studied cipher in the world!
- Oggi insicuro, esiste una sua variante 3DES che è più sicura, ma comunque rotto

C'è una step di **creazione delle chiavi

#### Feistel network
##### Definizione Feistel  🟩
Definiziamo una funzione di feistel $$f(L^{i - 1}, R^{i - 1}, K^{i}) \to L^{i}, R^{i}$$ la seguente:

Uno state $$u^{i}$$ è diviso in due parti, che vengono cifrati in questomodo:

$$

\begin{cases}
L^{i} = R^{i - 1}\\
R^{i} = L^{i - 1} \oplus  f(R^{i - 1}, K^{i})
\end{cases}
$$

Dove $$f$$ è una funzione invertibile, se si ha la chiave.
##### Invertibilità di Feistel 🟩
La caratteristica bella è che **data la chiave** questo è facilmente invertibile, anche se $$f$$ potrebbe non esserlo. Infatti la seguente funzione inverte in modo facile

$$
\begin{cases}
L^{i - 1} =  R^{i} \oplus  f(L^{i}, K^{i})\\
R^{i - 1} = L^{i}
\end{cases}
$$

Si può verificare in modo facile che funziona questo.

#### Funzionamento DES 🟩
Quindi
1. mapping iniziale $$IP$$ che crea $$L^{0}R^{0}$$ 
2. rounds di Feistel
3. Poi output

La decryption è simmetrica con la conoscenza della chiave.

<img src="/images/notes/Block Ciphers-20240305095533560.webp" alt="Block Ciphers-20240305095533560">

#### $$f$$ function in DES 🟨+
Dove $$A$$ è il 32 bit plaintext e $$J$$ è la chiave.

<img src="/images/notes/Block Ciphers-20240305100001596.webp" alt="Block Ciphers-20240305100001596">
Le funzioni $$S$$ sono tra le più importanti per la sicurezza, perché resistono a certi tipi di attacchi conosciuti (che se riesco metto in questi appunti qui sotto).
Sono in pratica una mappa di 4 bit e 2 bit a un 4 bit.


#### Attacchi a DES 🟩
Gli attacchi maggiori (alcuni lo vengono anche come servizio commerciale) è semplicemente **bruteforce** perché la chiave di 56 bit usata non è che sia molto utile.
(In un giorno te o rompe).
Gli attacchi con known plaintext esistono, ma usano un insieme di dati non feasible. di $$2^{40}$$ coppie di plaintext-ciphertext.

#### Unicità della chiave 🟩-
È notabile osservare che è probabile sia in DES che AES che è molto probabile che sia unica la chiave usata per cifrare quello.
Questa nota è utile per dire che se trovi quella chiave, probabilmente ti funziona anche per altre comunicazioni che utilizzano roba simile.
### Altre versioni di DES
In modo semplice per renderlo più sicuro è il **3-DES** in pratica DES applicato 3 volte, con chiave lunga il triplo, quindi più resistente a bruteforce.
#### Attacco a 2-DES 🟩
Vorremmo trovare una coppia di chiavi $$k_{1}, k_{2}$$ tale che per cui $$E(k_{2}, m) = D(k_{1}, c)$$ ed è possibile con un meet in the middle, che dovrebbe diminuire lo spazio di ricerca.
<img src="/images/notes/Block Ciphers-20240305112238931.webp" alt="Block Ciphers-20240305112238931">
**Conseguenza**:
Mi basta un $$2 \cdot 2^{56}$$ non un $$2^{112}$$ per rompere la chiave con questo attacco.
Per questo motivo uso un 3-DES che non permette di fare questo.
#### DESX (non impo)
[Wikipedia](https://en.wikipedia.org/wiki/DES-X).

Considero tre chiavi e considero

$$
k_{1} \oplus  E(k_{2}, m\oplus  k_{3})
$$

In parole semplici ho due chiavi in più che uso per fare un xor prima di mandarlo in [#Data Encryption standard](#data-encryption-standard) normale.
La cosa da notare è che non cresce la complessità di quanto ci si aspetta.

## Advanced Encryption Standard

#### Note storiche di AES
Da un punto di vista storico è stata una competizione internazionale 1997 che poi è stata standardizzata nel 2000. Una conferenza per questo (in particolare al seconda) è stata fatta a Roma, cosa che era curiosa, solitamente non si faceva così).
È stato scelto in base a 
1. Sicurezza
2. Costo implementazione
3. Velocità hardware e software.
Alla fine è un algoritmo molto parallelizzabile.

#### Generazione della chiave 🟨-
La lunghezza della chiave **decide il numero di rounds**, rispettivamente 10, 12, 14. In base al fatto che usiamo 128, 192, o 256.
Vedere 4.6 di @stinsonCryptographyTheoryPractice2005. Per l'algoritmo.
La cosa è che avremo una chiave di 16 bytes in output per il numero di rounds.
#### Funzionamento del cifrario 🟨-
Definiamo le operazioni
**SubBytes** (byte-by-byte substitution using an S-box) 
**ShiftRows** (a permutation, which cyclically shifts the last three rows in the State)
**MixColumns** (substitution that uses Galois Fields, GF(2^8) arithmetic) 
**Add** Round key (bit-by-bit XOR with an expanded key
<img src="/images/notes/Block Ciphers-20240305115629432.webp" alt="Block Ciphers-20240305115629432">
L'immagine è sbagliata per la grandezza della chiave di input, per il resto è ok, buona schematizzazione del funzionamento.

### Modes of operation
#### Electronic Code Book (ECB)
Il problema principale di questo metodo naïve è il fatto che posso vedere se blocchi hanno avuto stesso input, perché non dipendono dalla posizione.

<img src="/images/notes/Block Ciphers-20240307095344292.webp" alt="Block Ciphers-20240307095344292">

Questo **non è semantically secure** secondo note in [OTP and Stream Ciphers#Semantic security (!)](/notes/otp-and-stream-ciphers#semantic-security-(!))

#### Deterministic Counter (DETCTR)
In pratica **creo stream di bytes a blocchi** per cifrare
<img src="/images/notes/Block Ciphers-20240307111202941.webp" alt="Block Ciphers-20240307111202941">

**Th:** questo cipher è semanticamente sicuro se la funzione $$F$$ usata è sicura.
Ossia ha un buone garanzie teoriche se esiste e trovo tale $$F$$.
#### Cipher Block Chaining (CBC)
Lo conosci.

<img src="/images/notes/Block Ciphers-20240307115310428.webp" alt="Block Ciphers-20240307115310428">

Una nota importante è che si può fare una analisi teorica, e sapere **dopo quanti riusi di chiave** è necessario cambiarla, al fine di mantenere garanzie di sicurezza.

Se si guarda le slides possiamo avere un risultato, che è circa di $$2^{48}$$ blocchi per CBC. Si può fare la stessa analisi per [#Data Encryption Standard](#data-encryption-standard)


**NOTA:** CBC non è sicuro con un choosen plaintext e la capacità di predire gli *IV*
Come:
1. Scelgo come mio choosen plaintext $$0$$ così ho in pratica la versione criptata di $$IV$$.
2. Poi mando $$m_{0} = IV \oplus IV_{2}$$   e $$m_{1} \neq m_{0}$$ , se $$c(m_{0})$$ è uguale al primo, allora ho indovinato il messaggio.
Questo chiaramente dà advantage 1 e rompe la definizione (non so quanto praticamente utile) di semantic security.


Una possibilità è usare un **IV** creato dalla cifrazione di un Nonce, così sei abbastanza sicuro che IV sia sicuro.

#### Counter Mode (CTR)
molto simile al counter mode per [#Electronic Code Book (ECB)](#electronic-code-book-(ecb)) però ora abbiamo IV.
<img src="/images/notes/Block Ciphers-20240312101447979.webp" alt="Block Ciphers-20240312101447979">
Anche in questo caso possiamo usare una **nonce based version**.
## Substitution-Permutation Networks
#### 2 componenti principali

Abbiamo un box di sostituzione e un box di permutazione.
La stringa iniziale viene divisa in molti blocchi di lunghezza $$m$$, e in totale avrà lunghezza $$lm$$. Con padding finale possibile.
C'è un algoritmo abbastanza generale per questo genere di cifrari, che è il 4.1 in @stinsonCryptographyTheoryPractice2005.
la cosa carina è che queste funzioni alla fine sono molto semplici da implementare, sia in hardware e software. Non so bene su security garantuess

#### Key generation and rounds
In un unico round, viene encryptato molte volte (un round è fra 10-20 cicli di criptazione) si chiamano **iterated ciphers**, e dalla chiave iniziale vengono generate 16 chiavi, una per ogni round.
Questo lo chiamiamo **round function** e la funzione che genera le chiavi per ogni round sono **key schedule**.

### Pseudo random function
#### Main definition
<img src="/images/notes/OTP and Stream Ciphers-20240307110352630.webp" alt="OTP and Stream Ciphers-20240307110352630">

#### Pseudo random permutation
#### Secure PRF