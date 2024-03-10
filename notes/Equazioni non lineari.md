---
layout: page
permalink: notes/equazioni-non-lineari
tags: italian
title: Equazioni non lineari
---

Ripasso Prox: 25
Ripasso: December 24, 2022
Ultima modifica: January 2, 2023 3:24 PM
Primo Abbozzo: October 27, 2022 11:31 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

[Risoluzione di equazioni non lineari.pdf](Equazioni%20non%20lineari%20566c3ea2c78b4803be052b4bb9348a27/Risoluzione_di_equazioni_non_lineari.pdf)

Per trovare i zeri di una funzione continua non lineare **non esistono** alcuni metodi diretti che ci portano subito a una soluzione. Per questo motivo andremo ad analizzare molteplici pasis iterativi per trovare i zeri di una funzione.

La discussione di convergenza di ordine p è stata già discussa qui Note introduttive convergenza e iterazione , per quanto riguarda i metodi iterativi per risolvere sistemi di equazioni lineari

- Globale e local
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled">

Ricordiamo di  [Norme e Condizionamento](/notes/norme-e-condizionamento), in cui il condizoinamento era più o meno una stima di quanto cambia la soluzione quando cambia brevemente l'input. Ma ora vogliamo estendere il concetto per equazioni non lineari.

- Slide dimo (non chiede)
    espsilon è una perturbazione gestita da una funzione h
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 1.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 1">


**Cose da ricordare**

1. Se è uno zero con moltiplicità maggiore di 1 è sempre mal condizionato
2. Altrimenti è nell'ordine dell’inversa della derivata calcolata in quel punto
- Slide di questa ultima roba

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 2.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 2">



## Metodo di bisezione

### Introduzione al metodo di bisezione
Questo metodo funziona per **funzione continua** in un intervallo e $$f(a)f(b) < 0$$, per il teorema degli zeri esiste una soluzione, allora dobbiamo andare ad iterare l’argomento fin quando non abbiamo una stima abbastanza precisa del punto.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 3.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 3">


In pratica va a **dimezzare** sempre ad ogni iterazione l’intervallo in cui può essere presente il nostro numero.

### Convergenza e Costo
Una cosa bella di questo, in confronto ai metodi per equazioni lineari è che **posso stimare il numero di iterazioni**

- Slides

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 4.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 5.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 5">


Il costo di questo metodo dipende dalla funzione che bisogna essere calcolata ad ogni iterazione, ma al massimo facciamo un numero di iterazioni logaritmico rispetto al nostro intervallo, quindi qualcosa del tipo


$$
O(\log(b - a) \times O(f))
$$


Talvolta può succedere che è sempre costante la variabile in mezzo, quindi non posso diminuire di più l’intervallo, vedi esempio in toggle

- Imprecisione floating point, e non convergenza

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 6.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 6">


Per risolvere questo **aggiungo** eps dell’intervallo, in modo da rilassare la cosa, ed evitare che rimanga bloccato.

- Esempio blocco se non uso questo

    a = 98.5, 98.6 =b e epsilon = 0.004, precisione macchina è 0.01 / 2 (da 1/2 beta t - 1)

    Quindi si ferma se 0.004 + 0.01/2 * 98.6 = 0.004 + 0.986 / 2 quindi effettivamente si dovrebbe fermare. perché la differenza è minore di 0.5 tipo.


### Note sulla implementazione (2)
Si preferisce di calcolare il punto medio in questa forma

$$a + (b  -a)/2$$, invece che $$(a + b)/ 2$$ per limitare gli errori.

- Esempio di questo vantaggio

    0.983, 0.984, F(10, 3, -5, 5)

    La somma è 1.967, che normalizzato troncato è 0.196 1e1,, diviso diventa 0.980, oppure 0.985 se arrotondo al più vicino, in ogni caso è errato. Mentre con l’altro metodo ottenevo

    0.983 + (0.001 = 0.1 1e-2), 0.05 1e-2 = 0.5 1e-3 la somma è 0.9835, che è 0.983 quindi è ancora dentro l’intervallo.


Oltre a questo introduco la funzione **sign** e non lo calcolo il prodotto ella funzione, quindi vado a considerare

$$sign(f(a)) sign(f(b)) <0$$

## Analisi dei punti fissi

- Slide idea

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 7.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 7">

- Idea dagli appunti pisani
    In pratica andiamo a dire che **è più facile trovare punti fissi**
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 8.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 8">


Invece di trovare uno zero per f, cerco di trovare uno zero per la funzione di g equivalente, tale che sia un **punto fisso**. Probabilmente perché è più facile trovare dei punti fissi ed è per questo che vado a cercarlo. La funzione $$\Phi(x)$$ di supporto è maggiore di 0.


[Banach fixed-point theorem - Wikipedia]([https://en.wikipedia.org/wiki/Banach_fixed-point_theorem](https://en.wikipedia.org/wiki/Banach_fixed-point_theorem)#Statement)

Quello sopra è il teorema principale utile a giustificare l’esistenza del punto fisso, e anche dell’unicità. Chiaramente non sappiamo cosa siano gli spazi metrici, e costa troppo in termini di tempo provare a capire il motivo.

Ti basti sapere che la funzione deve essere:

1. Continua in [a, b]
2. Una contrazione, ossia soddisfare questa relazione: $$|g(a) - g(b)| \leq L|a - b|$$

### Esistenza del punto fisso
1. La funzione deve essere **continua**
2. La funzione deve essere una **contrazione** nell’intervallo prestabilito.
3. L’immagine deve essere contenuta al dominio, altrimenti non posso utilizzare l’immagine come input.
- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 9.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 9">


Nota; questo teorema è abbastanza importante (e anche tosto se si vuole far bene), lo puoi trovare in questa pagina di [wiki]([https://en.wikipedia.org/wiki/Banach_fixed](https://en.wikipedia.org/wiki/Banach_fixed)-point_theorem)

Nota: derivabilità e contrazione:
Se il modulo della derivata è minore di 1 allora è una contrazione! (non il perché ti basta ricordare sta cosa lel).
Un altra nota è che se sono soddisfatte quelle due cose, si può dimostrare che **converge sempre!**
TODO: velocità di convergenza? Criteri di convergenza??

### Convergenza delle contrazioni
Molto simile al teorema di esistenza e di unicità, questo invece stabilisce la convergenza, ed è sufficiente che la funzione sia una **contrazione** per ogni punto in un intorno del punto fisso.

<img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 10.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 10">


- Slide
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 11.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 11">


Cioè è fatta su una **variazione** su applicazione successive, e sul valore della funzione che deve essere abbastanza vicina allo 0.

Oppure si può fare su errori relativi oppure frazione del massimo della funzione. Ad ogni modo è a seconda di tolleranze prefissate.

In ogni modo con questo vogliamo cercare di

1. Vedere che la nostra funzione abbia raggiunto un valore vicino allo zero.
2. Vedere quanto varia ancora la soluzione proposta, non vorremmo che variasse ancora tanto.


- Slide

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 12.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 12">


Ti basti sapere che è **lineare**, sul perché non lo so. Ma è lineare lel.


## Metodo di Newton (delle tangenti)
È molto simile al metodo delle approssimazioni successive, ma in questo caso vogliamo utilizzare la derivata, come funzione ausiliaria. Vogliamo cercare di riassegnare la x a seconda di dove tenda a 0.


<img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 13.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 13">

Da notare che è una **convergenza quadratica** quindi molto veloce! Solo che si spende il tempo per calcolare la funzione due volte per sé stessa e la derivata

alla fine si avrà una successione nella forma


$$
x_{n + 1} = x_n - \dfrac{f(x_n)}{f'(x_n)}
$$


### Note velocità di convergenza
- Caso lineare (metodo approssimazioni classico)

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 14.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 14">

- Caso convergenza quadratica

    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 15.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 15">


Per il metodo di newton, la convergenza è q**uadratica!**

### Condizioni di convergenza locale (3)
Significa che riesce a trovare il minimo locale per la funzione

- Slide
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 16.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 16">


### Condizioni di convergenza globale
Significa che riesce sempre a trovare il minimo globale della funzione, come vedremo ci sono un sacco di condizioni restringenti (poi con

- Slide
    <img src="/images/notes/image/universita/ex-notion/Equazioni non lineari/Untitled 17.png" alt="image/universita/ex-notion/Equazioni non lineari/Untitled 17">

    Convergono anche tutte le variazioni possibili, sempre con a e b opposti (ma in modo diverso), e derivata seconda fatta in modo diverso


Se la derivata seconda è minore o ugualedi 0, parto da quello alto, altrimenti, da quello basso (non ho capito bene la 4 condizione boh).

TODO: Capire enunciati di questo


| 08/11/22 | Enunciati più o meno bene, dovrei semmai approfondire con dim o, Newton sembra essere particolarmente interessante…  |
| --- | --- |
| 14/11/22 | Boh, okey. |
| 02/12/22 | Boh okey x2 |
| 02/01/22 |  Dovrei farmi un po meglio le condizioni, ma più o meno ci sono ancora |