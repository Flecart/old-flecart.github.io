---
layout: page
permalink: notes/basi
tags: italian
title: Basi
---

Ripasso Prox: 60
Ripasso: December 19, 2021
Ultima modifica: December 14, 2021 3:43 PM
Primo Abbozzo: October 3, 2021 10:19 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 1 Variabili ed espressioni

## 1.1 Identificatori e dichiarazioni

### 1.1.1 Il nome simbolico/simbolico e fisico

**Nome simbolico:** nome leggibile da esseri umani diverso dal nome numerico con cui se lo ricorda il computer

<aside>
💡 Fai attenzione alle possibili variabili per il nome simbolico!

</aside>

- Attenzione

    <img src="/images/notes/image/universita/ex-notion/Basi/Untitled.png" alt="image/universita/ex-notion/Basi/Untitled">


### 1.1.2 Dichiarazione dei nomi

esempio:

```cpp
int n;
```

Quello che il programma fa sotto è **creare memoria** per la variabile.

## 1.2 Tipi di dato

Ricordarsi che

### 1.2.1 **Int**

4 bytes in memoria

Ha operazioni come basiche somme sottrazioni, moltiplicazioni e divisioni

Comparazione

il resto %

### 1.2.2 **Double**

8 bytes in memoria

Sono molto utili nelle **applicazioni scientifiche**

Stesse operazioni per int ma senza il resto

- operazioni di libreria.
- Cast

**Imprecisione di double**

### 1.2.3 Bool

Verità...

### 1.2.4 Char

stora un carattere, può essere ragruppato in array

### 1.2.5 const

Non si può modificare.

## 1.3 Espressioni e Type safety

### 1.3.1 Espressioni

Una espressione è una operazione che **ritorna un valore dato.**

può essere di 4 tipi:

- espressioni

    <img src="/images/notes/image/universita/ex-notion/Basi/Untitled 1.png" alt="image/universita/ex-notion/Basi/Untitled 1">


E la precedenza è dato da valori di precedenza...

### 1.3.2 Type safety

Bisogna **utilizzare una entità in accordo al tipo**.

Quindi:

1. Dichiarare variabie
2. Usare operazioni predefinite della variabile.
3. Leggere eventuali errori del compilatore per sapere di errori.

## 1.4 Input/output

### 1.4.1 Input

L'operatore di input è

```cpp
cin >> n;
```

Con le >> doppie freccie verso destra per dire che sto mettendo dentro n;

### 1.4.2 Output

```cpp
cout << n;
```

Per dire sto mettendo dentro cout il valore n così me lo printa.
 freccie verso destra per dire che sto mettendo dentro n;

### 1.4.2 Output

```cpp
cout << n;
```

Per dire sto mettendo dentro cout il valore n così me lo printa.