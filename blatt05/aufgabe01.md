# Aufgabe 1
```SQL
ALTER TABLE Assistant
ADD COLUMN salary int default(450);
```
Es wird eine neue Spalte in Assistant eingefügt, welche als default-Wert 450 besitzt


```SQL
SELECT t1.Boss, t2.Boss
FROM (
 	SELECT Boss,SUM(salary) as s
	FROM Assistant
	GROUP BY Boss
) as t1,
(
 	SELECT Boss,SUM(salary) as s
	FROM Assistant
	GROUP BY Boss
 ) as t2
 WHERE t1.s=t2.s AND t1.Boss<>t2.Boss;
 ```
Dabei werden zuerst die Kosten für jeden Prof ermittelt. Dies wird dadurch realisiert, dass man die Tabelle der Assistenten nach Prof grouped und von denen dann das salary addiert. Diese Tabelle existiert dann zweimal und wird auf die Gesamtkosten des Profs gejoined um die Profs zusammenzuführen, welche die gleichen Kosten für die Assistenten haben. Es werden dabei die Zeilen raus gelassen, in denen die beiden Profs mit den gleichen Kosten auch jeweils die gleichen Profs sind.





<!-- ```SQL
USE dbs2022;


DROP TABLE IF EXISTS attend;
DROP TABLE IF EXISTS requires;
DROP TABLE IF EXISTS examine;
DROP TABLE IF EXISTS Course;
DROP TABLE IF EXISTS Student;
DROP TABLE IF EXISTS Assistant;
DROP TABLE IF EXISTS Professor;


CREATE TABLE Student
       (StuNo          INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Semester       INTEGER);

CREATE TABLE Professor
       (PerNo          INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Rank           CHAR(2),
        Room           INTEGER UNIQUE);

CREATE TABLE Assistant
       (PerNo          INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Topic          VARCHAR(30),
        Boss           INTEGER,
        FOREIGN KEY    (Boss) REFERENCES Professor(PerNo));

CREATE TABLE Course
       (CouNo          INTEGER PRIMARY KEY,
        Title          VARCHAR(30),
        SCH            INTEGER,
        TaughtBy       INTEGER REFERENCES Professor(PerNo));

CREATE TABLE attend
       (StuNo          INTEGER REFERENCES Student ON DELETE CASCADE,
        CouNo          INTEGER REFERENCES Course ON DELETE CASCADE,
        PRIMARY KEY    (StuNo, CouNo));

CREATE TABLE requires
       (Predecessor    INTEGER REFERENCES Course(CouNo) ON DELETE CASCADE,
        Successor      INTEGER REFERENCES Course(CouNo) ON DELETE NO ACTION,
        PRIMARY KEY    (Predecessor, Successor));

CREATE TABLE examine
       (StuNo          INTEGER REFERENCES Student(StuNo) ON DELETE CASCADE,
        CouNo          INTEGER REFERENCES Course(CouNo),
        PerNo          INTEGER REFERENCES Professor(PerNo),
        Grade          INTEGER CHECK (Grade between 1 and 5),
        PRIMARY KEY    (StuNo, CouNo));


INSERT INTO Professor (PerNo, Name, Rank, Room)
VALUES
    (2125, "Sokrates", "C4", 226),
    (2126, "Russel", "C4", 232),
    (2127, "Kopernikus", "C3", 310),
    (2133, "Popper", "C3", 52),
    (2134, "Augustinus", "C3", 309),
    (2136, "Curie", "C4", 36),
    (2137, "Kant", "C4", 7);


INSERT INTO Course (CouNo, Title, SCH, TaughtBy)
VALUES
    (5001, "Grundzüge", 4, 2137),
    (5041, "Ethik", 4, 2125),
    (5043, "Erkenntnistheorie", 3, 2126),
    (5049, "Mäeutik", 2, 2125),
    (4052, "Logik", 4, 2125),
    (5052, "Wissenschaftstheorie", 3, 2126),
    (5216, "Bioethik", 2, 2126),
    (5259, "Der Wiener Kreis", 2, 2133),
    (5022, "Glaube und Wissen", 2, 2134),
    (4630, "Die 3 Kritiken", 4, 2137);

INSERT INTO requires (Predecessor, Successor)
VALUES
    (5001, 5041),
    (5001, 5043),
    (5001, 5049),
    (5041, 5216),
    (5043, 5052),
    (5041, 5052),
    (5052, 5259);

INSERT INTO Student (StuNo, Name, Semester)
VALUES
    (24002, "Xenokrates", 18),
    (25403, "Jonas", 12),
    (26120, "Fichte", 10),
    (26830, "Aristoxenos", 8),
    (27550, "Schopenhauer", 6),
    (28106, "Carnap", 3),
    (29120, "Theophrastos", 2),
    (29555, "Feuerbach", 2);


INSERT INTO attend (StuNo, CouNo)
VALUES
    (26120, 5001),
    (27550, 5001),
    (27550, 4052),
    (28106, 5041),
    (28106, 5052),
    (28106, 5216),
    (28106, 5259),
    (29120, 5001),
    (29120, 5041),
    (29120, 5049),
    (29555, 5022),
    (25403, 5022);

INSERT INTO Assistant (PerNo, Name, Topic, Boss)
VALUES
    (3002, "Platon", "Ideenlehre", 2125),
    (3003, "Aristoteles", "Syllogistik", 2125),
    (3004, "Wittgenstein", "Sprachtheorie", 2126),
    (3005, "Rhetikus", "Planetenbewegung", 2127),
    (3006, "Newton", "Keplersche Gesetze", 2127),
    (3007, "Spinoza", "Gott und Natur", 2126);

INSERT INTO examine (StuNo, CouNo, PerNo, Grade)
VALUES
    (28106, 5001, 2126, 1),
    (25403, 5041, 2125, 2),
    (27550, 4630, 2137, 2);
    

``` -->