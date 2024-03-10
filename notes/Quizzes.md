---
layout: page
permalink: notes/quizzes
tags: italian
title: Quizzes
---

Ultima modifica: February 25, 2023 2:07 PM
Primo Abbozzo: December 29, 2021 12:42 PM
Studi Personali: No

# Rappresentazione delle informazioni

### Mini-quiz

1. Cosa è una codifica posizionale? Darne degli esempi
2. Codificare -189 in 9 bit utilizzando modulo o segno, complemento a 1 a 2 e in eccesso
3. Cosa sono underflow e overflow per la codifica dei floating point? Perché i floating point hanno questa imprecisione mentre la codifica di interi no?
4. Come sono codificati i caratteri nei calcolatori?
5. Quali sono le cause più comuni per errori di trasmissione?
6. Cosa sono i codici correttori?
7. Cosa è la distanza di hamming?
8. Giustificare il motivo per cui è necessaria una distanza di hamming di almento k + 1 per trovare k errori e 2k + 1 per correggere k errori.
9. Cosa è il bit di parità? In che modo è utilizzato nel codice di hamming?
10. È stato ricevuto un codice 1000110100110 Analizzarlo usando il codice di hamming

### Soluzioni scarne

1. Un sistema di numerazione **posizionale** è un sistema di numerazione in cui i simboli (cifre) usati per scrivere i numeri assumono valori diversi a seconda della posizione che occupano nella notazione. ([wiki]([https://it.wikipedia.org/wiki/Sistema_di_numerazione_posizionale#:~:text=Un%20sistema%20di%20numerazione%20posizionale,posizione%20che%20occupano%20nella](https://it.wikipedia.org/wiki/Sistema_di_numerazione_posizionale#:~:text=Un%20sistema%20di%20numerazione%20posizionale,posizione%20che%20occupano%20nella)%20notazione.) :D).
Quindi è il sistema di numerazione comune. La base cambia il formato. Comunemente è utilizzato base 10 perché gli esseri umani hanno cominciato a contare con le proprie 10 dita, mentre base 2 per i calcolatori.
2. 189 = 128 + 61 = altro+ 32 + 29 = altro + 16 + 13 = altro + 8 + 5 = altro + 4 + 1
1011 1101,
    1. se utilizziamo la codifica a segno, è negativo quindi ci metto un 1 1 1011 1101
    2. per il complemento a 1, cambio ogni bit. 1001000010
    3. Per il complemento a 2 sommo 1 al complemento a 1 1001000011
    4. Per la codifica in eccesso devo codificare -189 + 256 = 67 = 64 + 2 = 1 = 001000011
3. Underflow e overflow esistono a causa della natura dei floating point. Infatti i floating point sono costituiti da tre parti: un bit per il segno, un insieme di bit per l’esponente e una mantissa per una parte decimale. Quindi un floating point è sempre memorizzato secondo la notazione scientifica e.g. 0.756 * 10e7, ma invece di essere in base 10 è in base 2.

Se l’esponente è eccessivamente alto o eccessivamente basso può occorrere che la parte dell’esponente non sia sufficiente a mantenere questa informazione.
Inoltre ci possono essere delle frazioni che non possano essere esprimibili in modo discreto (per esempio numeri periodici in base 2) e che quindi comportano un imprecisione nella mantissa. Questi errori sono ben più visibili con un alto valore assoluto di un esponente.
4. Anche i caratteri sono codificati come se fossero dei numeri. La codifica principale è la codifica ASCII. Ma potendo codificare solo una quantità molto limitata di caratteri (un centinaio), ultimamente si è passati alla codifica unicode che possiede 2 byte invece che 1. Esiste anche una codifica UTF-8 che è dinamica dal punto di vista dei byte utilizzati:
invece che sempre 2 byte può averne da 1 a 4.
5. Interferenze di trasmissione, raggi cosmici, disturbi fisici dell’apparecchio di trasmissione.
6. I codici correttori sono codici che possiedono una quantità sovrabbondante di informazioni in modo che, nel caso in cui ci sia stato un errore di trasmissione, sia possibile ricavare il messaggio originale.
7. La distanza di hamming fra due numeri è uguale al numero di 1 rimasti dopo lo xor fra questi due.
Per un insieme di numeri, è la distanza minima che esiste fra ogni coppia di numeri dell’insieme
8. Difficile
9. Il bit di parità di un codice è 1 se ci sono pari numeri di 1, 0 altrimenti. È altresì riassumibile come lo xor fra tutti i bit del codice.
Nel codice di hamming è utilizzato per tenere conto di alcuni bit in certe posizioni. L’applicazione nel prossimo esercizio spiega meglio di come sto tentando di fare ora.
10. 1000110100110

!<img src="/images/notes/image/universita/ex-notion/Quizzes/Untitled.png" alt="image/universita/ex-notion/Quizzes/Untitled">
 di alcuni bit in certe posizioni. L’applicazione nel prossimo esercizio spiega meglio di come sto tentando di fare ora.
10. 1000110100110

!<img src="/images/notes/image/universita/ex-notion/Quizzes/Untitled.png" alt="image/universita/ex-notion/Quizzes/Untitled">