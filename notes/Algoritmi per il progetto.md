---
layout: page
permalink: notes/algoritmi-per-il-progetto
tags: en
title: Algoritmi per il progetto
---

Ultima modifica: September 10, 2022 12:24 PM
Primo Abbozzo: August 8, 2022 12:52 PM
Studi Personali: No

### Euristiche, capitolo 3.6 del libro intelligenza artificiale

# Database degli algoritmi

Algoritmi da provare

Algoritmi da provare

## Cose da guardare

### Null move

In chess sembra che una null move heuristics (in pratica fai fare 2 mosse all'avversario) sia utile per stabilire il valore di una posizione, si potrebbe fare qualcosa di simile?

# Libri

- Norvigs

    [Intelligenza_artificiale_Un_approccio_moderno_Volume_1_4th_S_Russel.pdf](Algoritmi%20per%20il%20progetto%20e605ee7a02b94e23a5fc84cae859f644/Intelligenza_artificiale_Un_approccio_moderno_Volume_1_4th_S_Russel.pdf)

    [Artificial Intelligence - A Modern Approach (3rd Edition).pdf](Algoritmi%20per%20il%20progetto%20e605ee7a02b94e23a5fc84cae859f644/Artificial_Intelligence_-_A_Modern_Approach_(3rd_Edition).pdf)


### Forward pruning

È un modo per eliminare branches di ricerca subito, c'è un rischio che si elimini una branch bella.

Da guardare sono:

1. Beam search
2. Futility pruning
3. Late move reduction.

### Papers

- Euristiche generali

    [p276-286.pdf](Algoritmi%20per%20il%20progetto%20e605ee7a02b94e23a5fc84cae859f644/p276-286.pdf)

- Implementation of The game and of the AI CHUA HOCK CHUAN 2017 (non interessati, molto basilare la funzione di eval in base a quanti consecutivi)


    [Tic-tac-toe - Java Game Programming Case Study](https://www3.ntu.edu.sg/home/ehchua/programming/java/JavaGame_TicTacToe.html)

    [Tic-tac-toe AI - Java Game Programming Case Study](https://www3.ntu.edu.sg/home/ehchua/programming/java/JavaGame_TicTacToe_AI.html)

- Developing a Memory efficient Algorithm for Playing mnk games

    [MICS_2016_paper_28.pdf](Algoritmi%20per%20il%20progetto%20e605ee7a02b94e23a5fc84cae859f644/MICS_2016_paper_28.pdf)

    Viene applicata l’euristica dei maggiori modi di vincere possibili, algoritmo qui proposto non tiene conto delle mosse del nemico (lo dice lui stesso), quindi propone anche un fix subito dopo lol.

- Stackoverflow on 10x10 5 game

    [Minimax Alpha Beta Pruning Algorithm takes too much time to solve Tic Tac Toe (10x10 board)](https://stackoverflow.com/questions/51364491/minimax-alpha-beta-pruning-algorithm-takes-too-much-time-to-solve-tic-tac-toe-1)

    Presenta alcune tecniche generali per migliorare il minimax, ad esempio hashtable per stati già cercati, cosa che credo funzioni solo per questi casi piccoli, il 50x50 farci la table non credo proprio riesca…

    - Solving 7,7,5

        [ICG-180061.pdf](Algoritmi%20per%20il%20progetto%20e605ee7a02b94e23a5fc84cae859f644/ICG-180061.pdf)


## Note su Java

### Ottimizzazioni su final

[](https://www.baeldung.com/java-final-performance)

# Vecchi MNKGame

simone e la giuglia

[GitHub - Follisim/mnk-game](https://github.com/Follisim/mnk-game)

Questo non utilizza thread, quindi sarebbe utile compararlo col nostro ⬇️

[https://github.com/NotXia/unibo-MNKGame](https://github.com/NotXia/unibo-MNKGame)

lineare

[MNKGame2.0/mnkgame at main · PasqualeRic/MNKGame2.0](https://github.com/PasqualeRic/MNKGame2.0/tree/main/mnkgame)

indeterminati

[GitHub - mattyk0207/progetto-ASD: giocatore virtuale per MNKgame](https://github.com/mattyk0207/progetto-ASD)

alpha beta

[GitHub - Murkrow02/MNKGame](https://github.com/Murkrow02/MNKGame)

[https://github.com/FoxySeta/monkey](https://github.com/FoxySeta/monkey)

[https://github.com/specialfish9/LittleMan](https://github.com/specialfish9/LittleMan)

[https://github.com/giammirove/mnk-game](https://github.com/giammirove/mnk-game)

[https://github.com/takenX10/BottargaPlayer](https://github.com/takenX10/BottargaPlayer)

[https://github.com/University-Works-Projects/MNKGame](https://github.com/University-Works-Projects/MNKGame)

 Con voto 26 questo.

Idee per minimax forte
//github.com/takenX10/BottargaPlayer)

[https://github.com/University-Works-Projects/MNKGame](https://github.com/University-Works-Projects/MNKGame)

 Con voto 26 questo.

Idee per minimax forte

# References