---
layout: page
permalink: notes/l’-algoritmo-di-google
tags: italian
title: L’ algoritmo di Google
---

Ultima modifica: October 19, 2022 5:01 PM
Primo Abbozzo: April 25, 2022 12:27 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

È una cos extra

# 20 Pagerank

È un algoritmo molto utile (base) per il motore di ricerca di Google.

1. Quanto è importante la pagina
2. Quante frecce partono da una pagina (che ha valore più concentrato con meno voti)

Cerchiamo di definire quindi una fuinzione che sia definita con le caratteristiche precedenti:

L’importanza di una pagina $$x_i$$ è uguale a $$\sum_{x_j \in L} x_j/n_j$$ con $$n_j$$ il numero di frecce che partono da questa pagina.  Questa x da in un certo senso il concetto di autorevolezza di una pagina (che in questo algoritmo di base è considerata uguale di partenza per tutti.)0

### La Matrice che si crea

Possiamo creare una matrice dalla uguaglianza fra la sommatoria lì sopra. Si può ancora approfondire sta cosa 🙂...