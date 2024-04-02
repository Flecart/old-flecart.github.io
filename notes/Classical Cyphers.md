---
layout: page
permalink: notes/classical-cyphers
tags: italian
title: Classical Cyphers
---

Ripasso Prox: 21
Ultima modifica: November 29, 2022 10:56 AM
Primo Abbozzo: November 1, 2022 7:59 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Introduzione a Crittografia

al corso di crittografia di Christof Paar su Youtube, con aggiunte del corso Unibo.

## Classifications and definitions

Classification nowadays as many many applications like, and it’s a increasing important field

<img src="/images/notes/image/universita/ex-notion/Introduzione/Untitled.png" alt="image/universita/ex-notion/Introduzione/Untitled">


### Cryptology (2) 🟩

La branca comunemente riferita come crittografia è divisa principalmente in due campi **crittografia e cryptanalysis** in cui una cerca di creare nuovi metodi per cifrare i messaggi, e l’altro prova ad attaccare questi messaggi ritrovando il messaggio originale.

### Relazione con Sicurezza informatica 🟩

Questo campo si può considerare una piccola branca della sicurezza informatica, che è praticamente necessaria per la sicurezza, però allo stesso tempo non può essere utilizzata da sola, ha bisogno anche di sistemi operativi sicuri, hardware sicuro etc…

### Cryptography 🟩

Questo è quello che ci interessa, ed è ciò che il corso tratta.

1. Symmetrical ciphers
2. Asymmetrical ciphers
3. Protocols

### Classification of cryptoattacks 3 🟩-

We define **attack vector** as a possible way to attack a cipher

1. Classical Cryptanalisys
    1. Bruteforce
    2. Analytical attacks (Properties of the Cipher, useful to decrypt it)
2. Social engineering (like a people that gives you the key) (phishing)
3. Implementation attacks (Attack hardware to discover key)
    1. Side channel analysis (eg. power consumption related to the key).

Ovviamente questi sono molto diversi rispetto ai reali (nella vita reale ci sono molti attack vectors), secondo la Jocelyne, sembra che crypto sembra una scienza perché definisci metodi di risoluzione di errore per singolo attack vector, che puoi dimostrare come solido, ma nella vita reale credo che hai bisogno che sia valido per ogni tipologia di attacco (ne basta una per distruggerti e ritrovare la chiave diciamo).

## Symmetric cryptography

Vogliamo cercare di trovare un modo di comunicare attraverso un canale di comunicazione insicuro, questo è il problema principale di questa critografia.

Canali insicuri possono essere per esempio

1. Internet
2. Wifi
- Setting classico del problema di comunicazione

    <img src="/images/notes/image/universita/ex-notion/Introduzione/Untitled 2.png" alt="image/universita/ex-notion/Introduzione/Untitled 2">

    Allora introduco uno step di criptazione e decrittazione fra il pirmo e l’ultimo comunicante.

<img src="/images/notes/Introduzione a crittografia-20240222094332860.webp" alt="Introduzione a crittografia-20240222094332860">
Questo è un scenario leggermente più generale, in cui nel mezzo c'è un attaccante, solitamente un *eve* o altro che ha accesso a $$c$$ e prova a decrittare.

### On security of cipher

One important note is that the security of the cipher is **not** enough to mantain a security of the algorithm. But experience says it’s not!  (Ma nonostante questo è stato fatto per centinaia e centinaia di anni, ora sappiamo che è cosa stupida).

And a bad thing about this is that there is no clear way to know if a cipher is secure or not, usually what is done is that the algorithm is made public and if nobody knows how to break it is considered secure.

And it’s very easy to build something that is breakable!!!

### Kerckhoffs’ Principle 1883
#### Enunciato kerckhoff 🟩-

This is the most important principle of the course!

> A cryptosystem should be secure even if the attacker (oscar in this case) knows all the details about the system, with the exception of the secret key.
>

How can we make sense of this? This is counterintuitive. Maybe because in the past there were like two keys, the key and the algorithm itself, seems like that this setting didn’t help to have a better security.
But historically speaking, this principle seems to hold.

### Substitution cipher
Vedere [#Affine and Caesar Cipher](#affine-and-caesar-cipher) per definizione formale.

This was one of the oldest ciphers in history. (Old and stupid ciphers by the Professor).

1. Historical ciphers
2. Operates on letters (solitamente delle permutazioni)
3. Replace ever plaintext letter by a fixed ciphertext letter, this was the main idea.

**Examples**

1. Caesar Cipher, replace with a shift (bruteforce easy attack! The keyspace is very small)
2. Function that replaces each letterwith another letter with bijective.
    1. **bruteforce**, it’s too big for a braindead bruteforce to attack this function. 26!
    2. **Frequency attack** because in the language the letters are not equally distributed! And this works. (when the most frequent letter is discovered a big part of ciphertext is found!)
    And a bad thing is that same letter to same letter (frequency attack)!!!!

#### Attacco di frequenza 🟩
In teoria la chiave è una permutazione (nel caso di **vigenere**, quindi avremmo $$26! \approx 2^{88}$$ di keysize, però un attacco di frequenza è troppo forte per questo genere di cifrari.
<img src="/images/notes/Introduzione a crittografia-20240222100147432.webp" width="550" alt="Introduzione a crittografia-20240222100147432">
Fatto per la prima volta da Al-Kindi 800 AD.
#### Attacco brute-force 🟩

Un modo semplice, ma non molto pratico per fare questa definizione è la corrente:
dati una coppia $$M, C$$ di plaintext e ciphertext, un attacco bruteforce su un insieme di chaivi $$K = \left\{ k_{1}, k_{2}, \dots \right\}$$ consiste nel provare almeno una chiave (solitamente unica) per cui vale

$$
D(C, k_{i}) = M
$$

Ossia la chiave che usando $$D$$ abbiamo il plaintext.
Solitamente questo valore non si può calcolare, perché avremmo bisogno di $$M$$, quindi abbiamo il problema dei **falsi positivi** all'interno del nostro spazio di interesse. (vedere sezione 5.2 di @paarUnderstandingCryptographyTextbook2010)


### Vigenère Cipher
#### Esempio intuitive Vigenère 🟩
<img src="/images/notes/Introduzione a crittografia-20240222100456865.webp" alt="Introduzione a crittografia-20240222100456865">

#### Tentativo formalizzazione 🟩
Consideriamo una chiave $$k = (k_{1}, k_{2}, \dots, k_{l})$$
Ognuno equivalente al shift presente in cesare [#Affine and Caesar Cipher](#affine-and-caesar-cipher).
Ripetiamo la chiave più volte e cifriamo col shift cipher corrispondente ogni lettera. Questo fa nascere l'idea dei rotori senza problemi!

#### Attacco a Vigenère 🟩
- Guess the length of the key l using some methods
- Divide the cyphertext into l shift cipher encryptions
- Use frequency analysis on each shift cipher
È una specie di algoritmo, e si riutilizza la vulnerabilità presente sui shift ciphers normali.
L'attacco a frequenza diventa più difficile rispetto a Cesare, ma ancora possibile (molti ciphers indipendenti).

Per il primo steps un plaintext attack è facilissimo per esempio!
Qualcuno ha fatto la domanda su come scoprire la lunghezza chiave alla prof. La prof non sa come attaccarlo, e ha detto solo bruteforce su lunghezza. Poi ha citato un caso di plain-text senza chiamarlo plain-text. Ma è stata molto vaga. Bad. Ha detto anche entrare nel sistema per trovarlo... lol.

### Rotor machines
#### Main idea of rotors 🟨-
Queste macchine sono nate principalmente nel secolo scorso, da queste idee
- Multiple rounds of substitution, encryption consists of mapping a letter many times ○ M
- Mechanical/electrical wiring to automate the encryption/decryption process

La meccanizzazione è stata risolta dal punto di vista del red team da Turing, che ha dato un contributo fondamentale @turingCOMPUTINGMACHINERYINTELLIGENCE1950.

#### Esempi storici di rotor machines
<img src="/images/notes/Introduzione a crittografia-20240222101158992.webp" alt="Introduzione a crittografia-20240222101158992">
<img src="/images/notes/Introduzione a crittografia-20240222101359665.webp" alt="Introduzione a crittografia-20240222101359665">
I moderni simili sono DES e AES, li tratteremo un po' più avanti.
### Security of the Key

#### Note sulla lunghezza della chiave (non fare)
Andiamo in questa parte a misurare la sicurezza di una chiave di fronte agli attacchi. Una prima nota molto importante è il fatto che questa misura della lunghezza ha senso solamente quando si parla di bruteforce, infatti la lunghezza della chiave non può difendere contro side-channel oppure frequency-attacks.

1. La lunghezza della chiave per cifrari simmetrici e asimmetrici cambia.

<img src="/images/notes/image/universita/ex-notion/Introduzione/Untitled 3.png" alt="image/universita/ex-notion/Introduzione/Untitled 3">

#### Segretezza perfetta 🟩-
Secondo Shannon 1949.
Consideriamo un cifrario $$E, D$$ su $$K, M, C$$, allora si dice che si ha perfect secrecy quando 
$$\forall m_{0},m_{1} \in M$$ tale per cui $$\mid m_{0} \mid = \mid m_{1} \mid$$ , dove $$k$$ è presa uniforme. e $$\forall c \in C$$ 

$$
\mathbb{P}(E(k, m_{0}) = c) = \mathbb{P}(E(k, m_{1}) = c)
$$


Detto in altre parole, se ho un certo cipher-text, ho la stessa probabilità di avere qualunque messaggio possibile di una certa lunghezza rispetto al messaggio iniziale.  Quando succede questo 
there are no computational assumptions about the attacker, this is why this is also called **unconditional security or perfect security.**

Il cyphertext potrebbe essere *qualunque messaggio!*, cioè non posso attaccare il $$c$$ sapendo solo $$c$$ con la segretezza perfetta.
Altri autori come Stinson definisco tale per cui $$P(E|M) = P(E)$$. 
Attualmente non mi è chiaro se le due definizioni sono equivalenti.


L'idea è **limitare qualunque informazione** che si può trovare dalla chiave come
1. Non posso ritrovare la chiave dai processi di $$E$$ e $$D$$
2. Non posso ritrovare il plain-text da ciphertext.
Una definizione equivalente sembra essere:
dato un $$M$$ deve essere che $$\forall e \in E, P(e|M) = P(e) \not = 0$$ ([https://www3.cs.stonybrook.edu/](https://www3.cs.stonybrook.edu/)~omkant/L02-short.pdf)
Questo significa che il $$e$$ è **indipendente da M** quando non si conosce la chiave, nel senso che non riesci prendere nessuna informazione (se inverti con bayes dovresti avere stesso valore).

Si può dimostrare che la seconda definizione, più l'ipotesi che $$\lvert K \rvert = \lvert P \rvert = \lvert C \rvert$$ è equivalente alla prima (il contrario dovrebbe essere facile!?).

#### Segretezza perfetta e lunghezza chiave 🟨+
Si può dimostrare che per avere segretezza perfetta è necessario avere 


$$
\lvert K \rvert  \geq \lvert M \rvert 
$$

Questa proprietà rende cifrari come [OTP](/notes/otp-and-stream-ciphers) molto difficili da usare nella pratica, perché non riusciamo a comunicare questo valore, che tra l'altro dovrebbe essere utilizzato una singola volta.

**Proof:**
[https://cs.ioc.ee/yik/schools/win2006/massey/slides1.pdf](https://cs.ioc.ee/yik/schools/win2006/massey/slides1.pdf)
<img src="/images/notes/Introduzione a crittografia-20240227093802054.webp" alt="Introduzione a crittografia-20240227093802054">
Dove $$H$$ è l'informazione Shannon. quindi $$H(P) = \sum_{x} P(x)\log\left( \frac{1}{P(x)} \right)$$, e la lunghezza è strettamente dipendente dall'entropia.
Questo Shannon lo ha dimostrato nel 1949.

Una altra dimo è su @stinsonCryptographyTheoryPractice2005 3.3, abbastanza ez.
#### Unconditional security 🟩
<img src="/images/notes/image/universita/ex-notion/Stream Ciphers/Untitled 5.png" alt="image/universita/ex-notion/Stream Ciphers/Untitled 5">

La nota importante è il fatto che sia **infinito**, anche se ho il tempo dell’universo o maggiore non posso mai rompere un cifrario sicuro incondizionalmente. (molti cifrari sicuri nella pratica quindi non sono sicuri sequendo questa definizione).
Questo dovrebbe essere equivalente alla definizione di sopra si segretezza perfetta.

Come vedremo c’è un cifrario teoricamente sicuro, ma nella pratica di poco utilizzo

### Affine and Caesar Cipher
#### Definizione shift cipher 🟩
Sono definizioni 1.4.3 presenti su @paarUnderstandingCryptographyTextbook2010.
**Shift Cipher**

Siano $$x,y,k \in \mathbb{Z}_{26}$$
Allora l'encryption è

$$
e_{k}(x) \equiv x + k, \mod 26
$$

Mentre il decryption è

$$
d_{k}(y) = y - k \mod  26
$$


#### Definizione affine cipher 🟩
**Affine cipher**
Siano $$x, y, a, b \in \mathbb{Z}_{26}$$
Encryption:

$$
e_{k}(x) = y \equiv a\cdot x + b \mod 26
$$

Decription

$$
d_{k}(y) = x \equiv a^{-1}\cdot(y - b) \mod 26
$$

Con la restrizione del fatto che affinché $$a$$ sia invertibile dobbiamo avere $$gcd(a, 26) = 1$$


## Aritmetica modulare

Guardare [Algebra modulare](/notes/algebra-modulare), perché è praticamente quella stessa roba, molto importante crittografia, ma andiamo a trattare in un altro modo

### Sul modulo 🟩

1. Il resto non è unico! ci possono essere molte cose che soddisfano quelle cose
2. Il resto si può considerare una **classe di equivalenza**.

### Anelli 🟩

Un anello è un insieme di elementi su cui sono definite certe proprietà di interesse.

1. Esiste somma e prodotto e sono chiusi. E ci sono molte altre cose…
- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione/Untitled 6.png" alt="image/universita/ex-notion/Introduzione/Untitled 6">

    L’inverso non ci deve stare