---
layout: page
permalink: notes/normalizzazione-dei-database
tags: en
title: Normalizzazione dei database
---

### Introduzione alla normalizzazione

#### Perché si normalizza? 🟩

Cercare di aumentare la qualità del nostro database, perché praticamente andiamo a risolvere delle anomalie possibili al nostro interno, e questo aiuta per la qualità.

#### Tipologie di anomalie (!) (4) 🟨+
- **Ridondanze**, non vorrei avere la stessa informazione espressa più volte in troppi punti.
- **Update non consistente**, quando per aggiornare un singolo valore devo aggiornare moltissime altre tuple dipendenti da essa.
- **Deletion non consistente**, la presenza di certe entità è strettamente dipendente da presenza di altri, nell'esempio in questione sulle slides, se elimino tutti gli utenti, elimino anche i progetti su cui hanno partecipato, mentre invece dovrebbero essere separati.
- **Insertion**, ad esempio se non posso inserire un certa entry finché una altra proprietà legata (ma per il resto indipendente non è stat definita, nell'esempio del prof provare ad inserire un lavoratore, ma senza progetto.)

### Dipendenze funzionali

Vogliamo cercare di identificare le dipendenze funzionali e separarle, questo aiuta a creare qualità nel database
La dipendenza funzionale è un **vincolo di integrità** speciale, simile a quello relazionale spiegato in [Relazional Model](/notes/relazional-model)
#### Definizione formale di dipendenza funzionale 🟩
Data una relazione $$r$$ sullo schema $$R(X)$$ due sottoinsiemi non vuoti di attributi $$Y$$ e $$Z$$ sono detti funzionalmente dipendenti per ogni coppia di tuple $$t_{1}$$ e $$t_{2}$$ in $$r$$ con stessi valori per tutti gli attributi in $$Y$$ abbiamo che questi hanno gli stessi valori anche su $$Z$$.

**Osservazioni**:
1. Funzione, perché in un certo senso il primo insieme è il dominio, e il secondo è il codominio, ed è come se ci fosse una funzione che li associ.
2. Esistono **dipendenze funzionali banali** quelli il cui il secondo insieme di attributi è un sottoinsieme del primo.
3. **Dipendenza funzionale con chiave** essendo unica, non abbiamo duplicati di chiave, quindi l'implica implicito nella definizione ha sempre l'ipotesi falsa, quindi è sempre vero (guarda logica per capire il senso della mia frase).


#### Definizione formale Boyce e Codd (!) 🟩
> Una relazione $$r$$	si dice in *forma normale di Boyce e Codd* se per ogni dipendenza funzionale non banale $$X \to A$$ definita sulla relazione, $$X$$ contiene una chiave $$K$$ di $$r$$, cioè $$X$$ è una super-chiave di $$r$$
> 

Ossia vogliamo solamente dipendenza funzionali tramite chiavi, e non in altro modo, altrimenti probabilmente avrò una ripetizione.

#### Definizione terza forma normale 🟨--
È una forma leggermente più rilassata, utile per normalizzare anche quando BC non è possibile fare.

> Una relazione $$r$$ è *in terza forma normale* se per ogni dipendenza funzionale $$X \to Y$$ non banale vengono verificate una delle due condizioni:
> - $$X$$ ha una chiave di $$r$$
> - ogni attributo di $$Y$$ appartiene ad almeno una chiave di $$r$$



Il primo dovrebbe corrispondere a Boyce Codd.
Il secondo credo sia nuovo, possiamo dire quindi che sia una estensione, che permette la definizione di normalizzazione essere applicata a più cose.
Questa decomposizione è **sempre possibile**, abbiamo un teorema che lo dice.

### Metodi di normalizzazione

#### Decomposizione senza perdita. 🟩
> Sia dato un insieme di attributi $$X$$ e una decomposizione, non partizione, in $$X_{1}$$ e $$X_{2}$$, abbiamo che la relazione $$r$$ *si decompone senza perdita* su $$X_{1}$$ e $$X_{2}$$ quando la join delle due è uguale a $$r$$. ossia: $$\pi_{X_{1}}(r) \bowtie  \pi_{X_{2}}(r) = r$$

Questa è una necessità per **ricostruire le informazioni iniziali** senza nessuna perdita.
Si può notare che talvolta seguendo in modo cielo le dipendenze funzionali che si possono trovare seguendo una via di Boyce and Codd, non è sufficiente per mantenere questa proprietà tanto importante.

Prendiamo un esempio con perdita (perché vado a ricostruire un esempio con più informazioni):
<img src="/images/notes/Normalizzazione dei database-1703751658408.jpeg" alt="Normalizzazione dei database-1703751658408">



Questa non è una cosa che vogliamo!

Un modo per risolvere questo è aggiungere degli attributi fittizi che ci aiutano a discriminare sulle cose che ci servono. Ci fanno da specie di chiave.
#### Conservazione delle dipendenze 🟩

Questo permette di **mantenere i vincoli di integrità**.

> Una decomposizione **preserva la dipendenza** se ogni dipendenza funzionale dello schema originale ha attributi che compaiono nello stesso schema, altrimenti non è possibile rilevare le dipendenze funzionali (Atzeni, pagina 332)

Cioè se spezzo una dipendenza funzionale in tavole diverse, questa proprietà non viene soddisfatta, perché non sarei più in grado di trackarlo.

Prendiamo un esempio in cui questa caratteristica si dimostra utile

#### Normalizzazione nello schema concettuale 🟨--
Possiamo utilizzare questa idea anche nella parte di sviluppo  di schemi E-R.
Se riconosco a questo livello che c'è una dipendenza funzionale, questo mi da indicazioni su come continuare lo sviluppo di questo. Nell'esempio sulle slides motiva un partizionamento verticale, vedi [Database logical design](/notes/database-logical-design).