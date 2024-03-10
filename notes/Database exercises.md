---
layout: page
permalink: notes/database-exercises
tags: italian
title: Database exercises
---

## 2016 Feb

```sql
SELECT DISTINCT C.RV, C.Tonalità, C.Nome, C.Data
FROM Concerto AS C JOIN
Movimenti AS M ON C.RV=M.RV
WHERE Tempo="Largo"

SELECT M.RV, M.Numero, M.Tempo, M.Durata
FROM Concerto AS C JOIN
Movimenti AS M ON C.RV=M.RV
WHERE C.Data>1720
GROUP BY M.RV, M.Numero, M.Tempo, M.durata
HAVING COUNT(M.Numero) > 3
```

Sbagliato il secondo perché il group by non grouppa bene, bisogna fare query innestata


$$
\pi_{RV, Numero,Tempo, Durata}(\sigma_{Durata > 120}(Mov) \bowtie \sigma_{strumento="violino"}Strumentazione)
$$



$$
\pi_{RV, Numero, Tempo, Durata)}(\sigma_{Strumento=Cembalo}(Strumentazione) \bowtie Concerti \bowtie \sigma_{Numero=3}(mov)) - 
$$


$$
\pi_{RV, Numero, Tempo, Durata)}(\sigma_{Strumento=Cembalo}(Strumentazione) \bowtie Concerti \bowtie \sigma_{Numero>3}(mov))
$$


## Random exercises

### Relational algebra
[https://docs.google.com/presentation/d/1OuxnSOqHkj6Uq6xCSGzfK0mAlCn3xGZUVThRiFzQkrQ/edit#slide=id.g4f418699b7_0_16](https://docs.google.com/presentation/d/1OuxnSOqHkj6Uq6xCSGzfK0mAlCn3xGZUVThRiFzQkrQ/edit#slide=id.g4f418699b7_0_16)

#### Exercise 4


$$
\pi_{\text{Name}} (\sigma_{\text{Price} > \text{age} \cdot 10}(\text{PERSON} \bowtie \rho_{Id <- Person}(\text{ENROLLMENT}) \bowtie \rho_{Course <- name}(\text{COURSE})))
$$


Should be correct, the prof. solution renamed another thing

#### Exercise 5


$$
\pi_{\text{Name}, \text{Surname}} (
\sigma_{\text{Mark} = 30} (

\rho_{\text{Student} <- Id}(STUDENT)
\bowtie
EXAM

)
)
$$

Prof solution uses a property of join selection.
#### Exercise 6


$$
\pi_{\text{Name}, \text{Surname}}(
\pi_{\text{Id}, \text{Name}, \text{Surname}} (
(STUDENT)
)

-
\pi_{\text{Id}, \text{Name}, \text{Surname}} (
\sigma_{\text{Mark} = 30} (

\rho_{\text{Student} <- Id}(STUDENT)
\bowtie
EXAM
)
)
)
$$


Devo tenere l'ID perché ci potrebbero essere omonimi.

#### Exercise 7


$$
\pi_{\text{SupName}} (
\rho_{\text{SupName} <- \text{Name}}(SUPPLIER)
\bowtie_{\text{Id} = \text{SupId}}
\sigma_{Quantity > 0}(SUPPLYING)

\bowtie_{\text{ProdId} = \text{Id}}
\sigma_{\text{Name} \neq \text{PX274}}(PRODUCT)

)
$$


### SQL exercises
#### Exercise 1
```sql
SELECT DISTINT LECTURER.Surname
FROM LECTURER, STUDENT
WHERE LECTURER.surname == STUDENT.surname
```

Other solution

```sql
SELECT DISTINCT Surname
FROM LECTURER

INTERSECT

SELECT DISTINCT Surname
FROM STUDENT
```

#### Exercise 2 (da rifare)
Questo è sbagliato
```sql
SELECT L.Surname
FROM LECTURER AS L 
JOIN EDITION AS E ON L.Id == E.Lecturer
JOIN (SELECT Course, COUNT(Student) as passed
FROM EDITION
GROUP BY Course)
ON E.Course == Course
WHERE passed >= 10
```

LECTURER(Id, Surname, Dept) 
STUDENT(Id, Surname) 
COURSE(Code, Name) 
EDITION(Course, Year, Lecturer) 
EXAM(Student, Course, Year) 

SELECT DISTINCT L.Surname FROM LECTURER AS L, EDITION AS C, EXAM AS E WHERE L.Id = C.Lecturer AND C.Course = E.Course AND C.Year = E.Year GROUP BY L.Id, L.Surname, C.Course, C.Year HAVING COUNT(*) > 10 
#### Exercise3

```sql
Select MIN(Mile) as Minimum, MAX(Mile) as Maximum
FROM train
WHERE Departure = "Boston" AND Arrival = "Chicago"
```


#### Exercise 4

```sql

SELECT R.Name
FROM Region as R, Residence AS C
WHERE R.Name == C.Region
GROUP BY Region.Name
HAVING COUNT(Region.Name) < Region.Population # Questo sicuramente sbagliato! Infatti lo è!

```

GPT introduce una bella soluzione:

```sql
SELECT R._Name
FROM Region R
WHERE R.Population > (
    SELECT COUNT(*) 
    FROM Residence RS 
    WHERE RS.Region = R._Name
);

```

#### Exercise 5
```sql
Select F.title
FROM Film AS F
WHERE 7 <= (
	select AVG(Rating)
	FROM RATING
	WHERE FilmID = F.FilmId
) AND F.Year >= 1990 AND F.Year <= 2000
```

#### Exercise 6

```sql
Select MIN(User.AGE)
FROM RATING NATURAL JOIN FILM NATURAL JOIN USER
Where RATING.Rating > 8 and FILM.Title = "Blade runner"
```

#### 7
Dobbiamo in qualche modo usare tutte e quattro le relazioni, perché vogliamo comporre le informazioni

```sql
SELECT P.Name, P.Song
FROM PLAYLIST as P
WHERE EXISTS (
	SELECT
	FROM SONG as S, ALBUM as B, ARTIST as A,
	WHERE P.Song = S.ID and S.Albumb = B.ID and B.Artist = A.ID
	 and B.Year < 2001 and A.Labels = "UMG"
)
```

#### Exercise 12

```sql
SELECT R.Name, SUM(S.Profits)
FROM ROOM R JOIN SCREENING S ON R.Code = S.Room
WHERE R.City = "Rome" AND S.Date >= "01/01/05" AND S.Date <= "31/01/05"
GROUP BY R.Code, R.Name 
HAVING SUM(S.Profits) > 20000
```

#### Exercise 13

```sql
FROM FILM F JOIN SCREEENING S ON 
JOIN ROOM R
```


#### 27

Ho bisogno di un aggregato, perché devo sapere il numero di novels in cui appare

Avrò bisogno di Characters e Novel, perché questi sono le cose prese.

Un groupby CodeNov, Title e Name, potrebbe essere sensato.
Come faccio ad esprimere il concetto che sono apparsi in più di un novel?

Posso intanto creare una view in cui ho il nome del carattere e numero di 

```sql
SELECT name, sum(CodeNov)
FROM CHARACTERS
GROUP BY name
HAVING sum(CodeNov) > 1;
```
Questa query la chiamo `A1` e mi sarà utile come subquery !? Si, basta aggiungere un having e poi l'abbiamo!
Alla fine non avevo bisogno della relazione Novel.
#### 28
Ho bisogno di sapere se è italiano l'autore, e Novel, quindi dovrei fare join per selezionare solamente le Novel italiane. Poi dovrei fare join ancora per capire se ho o meno il film. E devo contare anche i films...

Seleziono Novelle italiane
```sql
SELECT N.CodeNov
FROM NOVEL AS N, AUTHORS AS A
WHERE N.Author == A.Name AND Country = "it"
```
Questa la chiamo `A1`

Posso usare questo e una dicitura Groupby per finalizzare.


```sql
SELECT N1.title, F.Code
FROM NOVEL as N1, FILM as F
WHERE N1.CodeNov = F.Novel AND N1.CodeNov in A1
GROUP BY N1.title, F.Code
HAVING sum(F.Code) > 1
```
Non so se posso rimuovere F.code fra le select.


#### 29

```sql
SELECT Title
FROM NOVEL
WHERE CodeNov not in (
	SELECT N.CodeNov
	FROM NOVEL as N, FILM as F
	WHERE N.CodeNov = F.Novel
)
```
Questa mi sembra facile, conoscendo però query innestate

#### 30


```sql
SELECT Title
FROM NOVEL
WHERE CodeNov not in (
	SELECT N.CodeNov
	FROM NOVEL as N, CHARACTERS as C
	WHERE N.CodeNov = C.CodeNov AND C.Gender = "Male"
)
```
 Mi sembra ok anche se la soluzione è diversa rispetto a quello del prof. Una cosa che non ho capito della soluzione del prof è perché ha bisogno di selezionare anche codeNov...
## Design concettuale

### Esercizio 1

Proviamo ad identificare 
1. Clinica
	1. ID Chiave
	2. address
	3. numero di telefono
2. Tool
	1. **ID** chiave
	2. descrizione
3. Specialista
	1. **ID** 
	2. Nome
	3. Cognome
	4. Numero telefono
	5. SLista (1, N)
4. Collaboratori
	1. ID 
	2. nome
	3. cognome
5. Visita
	1. Codice
	2. Date 
	3. Time

- Clinica -> Visit (1, N), Clinica <- Visit (1, 1) assign
- Visit -> Spec (1, N), Visit <- Spec (0, N) DO
- Spec -> Tool (0, N), Spec <- Tool (1, N) Use
- Coll -> Tool (1, N), Coll <- Tool (0, N) Responsabile
- Spec -> Coll (0, N), Spec <- Coll (1, N), work

### Esercizio 2
1. Corsi
	1. **Nome**
	2. prezzo
	3. max attendee
2. Membri
	1. Generalizzazione ereditarietà, esclusiva (se si può stare da una parte o dall'altra allo stesso tempo), totale (perché o è uno o nell'altro) e si indica con la freccetta riempita.
		1. **ID**
		2. Nome
		3. Surname
		4. Phone number
	2. Trainer
	3. Cliente
		1. età
3. Card
	1. **Numero progressivo + esterno (cliente)** 
	2. prezzo totale

- Cliente - Card -> (0, N), <- (1, 1) own
- Trainer - Corso, -> (0, N), <- (1, 2), responsabile, Venduto è giusto anche (1, N) in questo caso, perché non è detto.
- Cliente - Corso, -> (0, N), <- (0, N), Enroll, vincolo relazionale esterno.
- Card - Corso, -> (1, N), <- (0, N),  Made-f

- Max A >= client e anche by card.
- Costo carta < costo corsi a cui da accesso

### Esercizio 3
1. Company (financial market?)
	1. **Code**
	2. Name
	3. Share capital
	4. Registered office
		1. City
		2. state
2. Rating Agency
	1. **Code**
	2. Name
3. financial instrument
	1. **Nome + (company)**
	2. Performance
	3. Figli (esclusivo, totale in questo caso)
		1. Derivati
		2. Shares
		3. Bonds
			1. Maturity date


- Fins - ocmp, -> (1, 1) , <- (1, N), issue
	- Value
- Comp - Agency, -> (1, N), <- (1, N), rating
	- Value
- Comp - Comp, -> (1, N), <- (1, N) Hold
	- Percentuale

BR: