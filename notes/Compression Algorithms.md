---
layout: page
permalink: notes/compression-algorithms
tags: en
title: Compression Algorithms
---

### Lempel-Ziv-Welch Algorithm
#### Introduzione sul funzionamento
1. Primo scan con un dizionario indexato dei singoli caratteri
2. Poi viene cercato di raggruppare caratteri a coppie.
3. Se una coppia è già presente nel dizionario, allora aggiungo al dizionario una cosa più lunga e metto un code diverso
4. <img src="/images/notes/Introduction to Algorithmic Information and Complexity-20240217115716857.webp" alt="Introduction to Algorithmic Information and Complexity-20240217115716857">
Esempio di sopra.
La cosa carina è che il dizionario si può ricostruire in fase di decoding.

Tutti gli altri, tipo zip, gzip, png si basano poi su questa idea.
Per certi versi la cosa di raggruppare è simile a [Byte pair encoding](/notes/tokenization). 


### Huffman Codes
Questa parte probabilmente è stata anche trattata in modo molto breve al corso di algoritmi.
Basato sul paper di 1952 "A method for the construction of minimum redundancy codes". Di Huffman
L'idea principale è creare un albero di codifica in modo che le cose frequenti siano in cima, ossia hanno un codice molto breve, mentre cose lunghe abbiano codici più lunghi.

Il codice di Huffman è un algoritmo che nella media ha compressione migliore lossless.
Ossia si ha $$L^{*}(C_{huffman}) \leq L(C)$$ per qualunque altro carattere. Ha anche relazioni con le prefix strings, ne si parla di più in [Entropy](/notes/entropy).

Assumiamo che ogni carattere abbiano una frequenza.
#### Algoritmo di Huffman
1. Creo una lista ordinata dalla frequenza
2. Inizio ad assegnare codici a questa lista volta per volta partendo dai più bassi
3. Inserisco in cima creando nuovi nodi (che reinserisco) volta per volta sempre prendendo il più basso di frequenza
4. Si crea un prefix-code in questo modo che si può utilizzare a piacere.
Una volta creato questo albero, posso usarlo per codificare e anche decodificare.
```python
""" Huffman code generator -- after
[https://stackoverflow.com/questions/11587044/how-can-i-create-a-tree-for-huffman-encoding-and-decoding](https://stackoverflow.com/questions/11587044/how-can-i-create-a-tree-for-huffman-encoding-and-decoding)
"""
GRAPHIMAGE = 'HuffmanGraph' # for Huffman tree display.
SOURCETXT = 'texts/English.txt' # for statistics
######################################
# Huffman coding #
##################### ########
def assign_code (nodes, label, result, prefix = ''):
	childs = nodes[label]
	tree = {}
	if len(childs) == 2:
		tree['0'] = assign_code (nodes, childs [0], result, prefix+'0')
		tree['1'] = assign_code (nodes, childs [1], result, prefix+'1')
		return tree
	else:
		result[label] = prefix
		return label

def Huffman_code(_vals):
	vals = _vals.copy()
	nodes = {}
	for n in vals: # leafs initialization
		nodes [n] = []
		
	while len (vals) > 1: # binary tree creation
		s_vals = sorted (vals.items (), key-lambda x:x[1])
		al = s_vals[0][0]
		a2 = s_vals[1][0]
		vals[al+a2] = vals.pop(al) + vals.pop(a2)
		nodes [al+a2] = [al, a2]
	code = {}
	root = al+a2
	tree = {}
	tree = assign_code (nodes, root, code) # assignment of the code for the given binary tree
	return code, tree
```