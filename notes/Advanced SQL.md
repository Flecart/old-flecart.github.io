---
layout: page
permalink: notes/advanced-sql
tags: en
title: Advanced SQL
---

### Check function
A volte può essere molto pesante, perché 
#### What does check do?
Viene utilizzato per introdurre un **constraint** check per avere sicurezza su un range.
<img src="/images/notes/Structured Query Language-1697711487638.jpeg" alt="Structured Query Language-1697711487638">
#### Check e innestamenti 🟩-
Può essere che certe implementazioni non permettano il check innestato, questo è una cosa molto pesante, perché ogni modifica deve andare a **rifare la modifica ai subalterni**, quindi questo è pesante pesante.
#### Assertions 🟩--
Sono dei **check** fatti al **livello dello schema**, quindi valgono sempre, e possono essere riutilizzati in table diversi credo.
Un altro aspetto è che è **database wide**.
```sql
create ASSERTION AtLeastOneEmployee
	check (1 <= (select count(*) from Employee)))
```

### View

#### L'uso del view 🟩
```sql
create view ViewName [(attrlist)] as
	selectstatement
[ with [local | cascaded ] check option]
```
viene utilizzato per prendere dati esistenti, e metterli in una forma utile a una sotto-organizzazione, che vuole informazioni specifiche diciamo.

- Check: viene utilizzato se update è sensato (soddisfa ancora la check).
- Grouping, posso creare view con informazioni aggregate, e poi posso usare le informazioni aggregate simile a sopra.
#### Cascaded vs local
- **Cascaded** significa che ogni modifica e view, viene riflessa su altri schema e view fisici effettivi
- **Local** significa 
### Recursive queries 🟥+
In questi casi viene proprio definito un approccio ricorsivo (anche se non ricordo benissimo la sintassi) andiamo a definire cose come caso base, e caso induttivo e poi si fa la query in questo modo.

In pratica costruisco una view **in modo ricorsivo**, e su questa posso farci delle query.
Un esempio:

```sql
with recursive Ancestors(Ancestor, Descendant) AS (
select Father, Son
from Fatherhood
union all
select Ancestor, Son
from Ancestors, Fatherhood
where Descendant = Father
) 
select * from Ancestors
```
In pratica nel primo select popolo inizialmente la view, poi in modo ricorsivo, prendo gli elementi dentro la view, prendo alcuni elementi dentro son, e aggiungo tutti gli elementi che soddisfano quella condizione.
### Other expressions
#### Coalesce 🟥
Ci permette di fare l'equivalente del default in alcuni linguaggi di programmazione per me.
In pratica **restituisce il primo elemento non nullo in una lista**, quindi se per caso ho due elementi, e il primo è nullabile, allora prende il default il secondo.

Esempio:
```sql
select number, coalesce(Mobile, PhoneHome)
from Employee
```

Se non esiste mobile, si va su phonehome. Si può fare una cosa come `coalesce(Dept, "None")
per mettere il default.
#### Scalar functions 🟨
**String**
**Time**
- current_date
- extract(yearExpresison)
Esempio:

```sql
SELECT EXTRACT(YEAR from orderDate) AS orderyear,
FROM  Orders
WHERE DATE(orderDate) = current_date()
```

**Casting**
#### nullif
Semantica: ritorna null se la condizione è vera.

È buono per far tornare Null se un valore assume un certo valore hardcodato, ad esempio se il default è "Unknown" per qualcosa, posso fargli tornare NULL se valore uguale a quella stringa hardcodata.

Esempio:

```sql
select Surname, nullif(Dept, "unknown")
from employee
```
Se è vera la comparazione, si ritorna Null in automatico

#### Case expressions 🟨--

<img src="/images/notes/Advanced SQL-1703581213809.jpeg" alt="Advanced SQL-1703581213809">
### Transactions
#### ACID framework 🟩
- Atomic: o tutto o niente, è una transazione atomica
- Consistency: tutto deve soddisfare i constraints
- Isolation: simile ad atomico, le transazioni non devono influenzarsi fra di loro per tempo.
- Durability: non è su ram diciamo
#### Example in sql for transactions
![ 600](/notes/structured-query-language-1697712948716.jpeg-)


### Authorization
#### Privileges (6)
Questa parte si ricollega in qualche modo con la parte di renzone, vogliamo **specificare una risorsa** e dire chi può fare cosa su quella risorsa.
La risorsa in questo caso può essere lettura modifica o eliminazione su una tavola.
Posso
- Dare permessi (privilegi)
- Togliere permessi
- Specificare utenti che hanno permessi
- Propagazione di privilegi.

I privilegi sono esattamente 6, descritti dall'immagine sotto 
<img src="/images/notes/Structured Query Language-1697712596136.jpeg" alt="Structured Query Language-1697712596136">
#### Grant privileges
```sql
grant < Privileges | all privileges > on
Resource
to Users [ with grant option ]
```

#### Revoke privileges
```sql
revoke Privileges on
Resource
from Users [ restrict | cascade ]
```

- Restrict -> non implica anche altri utenti
- Cascade -> la revoca è estesa ad altri utenti anche, una reazione a catena.
#### Privilegi come view RBAC
È più facile usare il modello chiamato **RBAC**, ossia definiamo ruoli, una view, e i ruoli possono accedere solamente a certe view.
<img src="/images/notes/Structured Query Language-1697712856327.jpeg" alt="Structured Query Language-1697712856327">



Usare i ruoli è un metodo classico, potremmo considerarlo come una astrazione su cosa ogni utente deve fare sul database (quindi le sue operazioni ideali) e da quello andare a descrivere cosa esattamente ha bisogno di poter fare.
In questo modo definisco i permessi su questi ruoli ideali invece di andare a farli sui singoli utenti, magari anche ripetendo un sacco di queries.



# References