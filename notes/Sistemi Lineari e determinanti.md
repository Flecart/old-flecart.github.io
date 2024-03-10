---
layout: page
permalink: notes/sistemi-lineari-e-determinanti
tags: italian
title: Sistemi Lineari e determinanti
---

Ripasso Prox: 20
Ripasso: June 3, 2022
Ultima modifica: October 19, 2022 5:00 PM
Primo Abbozzo: March 31, 2022 11:17 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 4 Sistemi lineari e determinanti

## 4.1 Sistemi lineari

La cosa buona è che possiamo analizzare il sistema lineare utilizzando tutti i teoremi che abbiamo sviluppato finora, quindi siamo molto più potenti per attaccare questo problema.

Definiamo un sistema lineare così

$$Ax = b$$ con A la matrice associata.

### 4.1.1 Preimmagine

Data una applicazione lineare $$F:V \to W$$, allora la controimmagine è l'insieme dei vettori di V che fanno a finire in quel punto, in matematichese:

$$F^{-1}(w) = \{v \in V | F(v) = w\} \subseteq V$$, un esempio di preimmagine è Ker F.

Possiamo anche definire un concetto di suriettività in questo modo:

Una funzione è suriettiva, se per ogni elemento dell'immagine, ho un elemento nel dominio, quindi l'insieme preimmagine deve essere diverso da vuota

Ker e Imm sono qui

### 4.1.2 Relazione preimmagine e immagine e nucleo 6.1.4 (chiede)

<img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled">

Fare attenzione a dimostrare la doppia inclusione per l'uguale! Stiamo utilizzando sempre l'assioma dell'estensionalità, ricordatelo!

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 1.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 1">


### 4.1.3 Rango righe di righe e colonne uguali (6.2.3) !!!

<img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 2.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 2">

Possiamo definire il rango righe come la dimensione dello spazio riga di A

Mentre il rango colonna la dimensione dello spazio colonna (questo è ovvio conoscendo i teoremi sulle matrici!, ricorda che con le operazioni di gauss riuscivi a trovare una serie di vettori indipendenti e generatori!)

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 3.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 3">

    Il rango colonne, per un teorema precedente che diceva base di uno è base anche dell'altro, è uguale alla dimensione dell'immagine, quindi se la dimensione dell'immagine è uguale al rango righe, ho che i due ranghi sono uguali, allora posso considerare solo un unico rango per la matrice.

    - Dimostrazione della 5.7.4

        <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 4.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 4">


    La dimostrazione di 5.7.4 dovrebbe essere banale, una volta che generalizzi la soluzione di gauss per il nucleo (lo puoi sempre scrivere come spazio generato da n - rr(A) variabili libere per le proprietà credo delle riduzione matriciale di gauss.


### 4.1.4 Rouché - Capelli (chiede)

<img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 5.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 5">

- Dimostrazione da libro

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 6.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 6">

- Dimostrazione (informale)

    Le soluzioni sono le preimmagini della nostra funzione, ha soluzione se la preimmagine di b non`e nulla e per questo deve essere che b deve appartenere al sottospazio generato dalle colonne di a (perché queste generano l'intera immagine) e per la 3.1.8 allora lo spazio colonna di A è uguale allo spazio colonna di A con b, allora hanno la stessa dimensione perché sono uguali, allora i ranghi sono uguali. (4.2.4?)

    preimmagine 0 coimplica b nello spazio immagine

    b nello spazio immagine coimplica generato con e senza b è uguale

    questo coimplica dimensioni uguali quindi finito entrambe le frecce

    ---

    Passando per la seconda parte della dimostrazione, sappiamo che l'insieme delle soluzioni, ossia la controimmagine, si può scrivere in questa forma:

    $$f^{-1}(w) = \{ v + z | f(v) = w \land z \in ker(f)\}$$

    allora nel caso in cui io abbia che le due matrici siano uguali come al punto 1, posso creare un insieme infinito di soluzioni partendo da questa cosa.


## 4.2 Determinanti

### 4.2.1 Definizione

Non abbiamo una definizione diretta del determinante, per cui la definiamo in modo **indiretta** facendo una lista delle proprietà

Vedremo che l'inversa di una matrice esiste sse il determinante è diverso da 0, ed è l'aspetto più importante del determinante per la nostra analisi

Si può dimostrare (ma non si è fatto) che la funzione associata al determinante esiste sempre ed è unica.

- Proprietà (4)

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 7.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 7">

    Le proprietà 1, 2 ci dicono come comportarci rispetto alla somma (distributiva) e la moltiplicazione scalare **per singole righe**.

    La proprietà 3 ci da un relazione con la combinazione lineare (e quindi dipendenza)

    La 4 ci permette di calcolare :D

- Conseguenze delle proprietà (3)

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 8.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 8">

    La proprietà 3 è molto utile per il calcolo, direi che è la proprietà più importante per fare i calcoli

    - Hint di dimostrazione
        1. Considero la matrice somma, che per la proprietà 1 è uguale alla somma dei determinanti di A e B. Allora questa ha due righe uguali, quindi è uguale a 0. Riscrivendo la somma si ha la sol.
        2. Considero la riga scritta come combinazione lineare come somma di due di determinanti di due matrici. Una di queste avrà due righe uguali, quindi è 0. I due determinanti sono uguali.
        3. Partendo dalla triangolare inferiore, posso trovare la matrice diagonale con matrici con combinazioni lineari.
- Teorema di Binet

    Questa proprietà non si dimostra senza aver considerato la base di dimostrazione con permutazioni.

    Però dice che se ho due matrici, si ha che il determinante della matrice prodotto è uguale al determinante delle singole matrici.


### 4.2.2 Metodo savius

Per le matrici 3x3, il classico

### 4.2.3 Metodo Laplace (ricorsivo)

<img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 9.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 9">

## 4.3 L'inversa della matrice

### 4.3.1 Definizione e unicità

L'inversa di una matrice $$A \in M_{n\times n}(\R)$$  è una matrice $$B$$ nello stesso spazio tale che

$$AB = BA = I$$.

Quando si fa il controllo della matrice inversa, dovresti dimostrare che $$AB = BA$$ che di solito non vale, però dimostri che l'inversa è unica quindi ti basterebbe fare un unico controllo

- Dimostrazione unicità dell'inversa

    Sia $$A^{-1}$$ l'inversa di $$A$$, supponiamo che esista $$B$$ che sia l'inversa e tale per cui $$A^{-1} \neq B$$, allora ho che

    $$AB =I \implies A^{-1}AB = A^{-1}I \implies I B = A^{-1}I \implies B = A^{-1}$$


### 4.3.2 Equivalenza di invertibilità col determinante (!!)

Si può dimostrare che $$A$$ è invertibile nel caso in cui la determinante è diverso da 0.

- Dimostrazione

    $$\implies$$Se è invertibile, il determinante di A è diverso da 0.

    Perché per binet, se $$I = AB$$ allora $$\det(I) = \det(AB) = \det(A)\det(B)$$ se fosse 0 allora sarebbe impossibile, quindi è diverso da 0, e posso dire che

    $$\det(B) = \dfrac{1}{\det(A)}$$

    $$\impliedby$$

    Devo dimostrare che se il determinante di A è diverso da 0 allora è invertibile. Facciamo una dimostrazione costruttiva, cioè diciamo qua proprio come è fatto la matrice inversa.

    Posso costruire la matrice inversa in questo modo:

    $$b_{ij} = \dfrac{1}{\det A} \Gamma_{ji}$$ ora devi controllare questa cosa e sei apposto.


### 4.3.3 Calcolo dell’inversa con GAUSS

SI può calcolare l'inversa di una matrice utilizzando gauss su una matrice del tipo

$$A|I$$, fino ad andare ad ottenere la matrice $$I|B$$ con B la inversa.

### TEOREMONE (!!!!)  7.6.1

- Enunciato (11)

    <img src="/images/notes/image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 10.png" alt="image/universita/ex-notion/Sistemi Lineari e determinanti/Untitled 10">


Tutte le dimostrazioni fra 1 e 9 compreso sono sono tutte già state spiegate in precedenza, l'unica cosa nuova è l'equivalenza fra 1 e 10

- Dimostrazione (1-10)

    Se dimostro che 1 è equivalente a 10, ho dimostrato l'equivalenza anche per 1-11 perché 10 è equivalente a 11 per il teorema questo.

    Allora dimostriamo $$\implies$$.

    Supponiamo di avere una funzione bigettiva. Allora posso prendere la sua funzione inversa, che esiste per la biiettività. Considero la matrice associata all'inversa, allora posso concludere che $$f \cdot g \approx AA^-1$$ che termina la dimostrazione perché ho la matrice inversa.


Possiamo enunciare le equivalenze fra cose riguardo le applicazioni lineari

- Nota su composizione di funzioni

    Sia A la matrice associata a f e B associata a g.

    Allora si può dimostrare che la matrice associata a $$f \cdot g$$  è $$AB$$, questo si dimostra utilizzando l'associatività della moltiplicazione matriciale.


# Registro ripassi

| 09/04 | 👍 |
| --- | --- |
| 20/04 | Tutta la prima parte sulle soluzioni dei sistemi lineari è ok, anche iil resto è ok, dovrei fare qualche es ora.... |
|  |  |
le.


# Registro ripassi

| 09/04 | 👍 |
| --- | --- |
| 20/04 | Tutta la prima parte sulle soluzioni dei sistemi lineari è ok, anche iil resto è ok, dovrei fare qualche es ora.... |
|  |  |