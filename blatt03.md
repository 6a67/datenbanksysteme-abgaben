# Aufgabe 1
```SQL
SELECT s.Name, a.Name, c.Title
FROM Student as s, attend as d, Assistent as a, Course as c
WHERE s.StuNo = d.StuNo
AND d.CouNo=c.CouNo
AND a.Boss = c.TaughtBy
```

###### tags: `todo` Reihenfolge der Joins ändern und gucken, ob das optimiert
SELECT *
FROM Student as s
INNER JOIN attend as d ON d.StuNo=s.StuNo
INNER JOIN Course as c on c.CouNo=d.CouNo
INNER JOIN Assistent as a ON a.Boss=c.TaughtBy


# Aufgabe 2)
## 1
CREATE TABLE Student
       (StuNo         INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Semester       INTEGER
        EMail        VARCHAR(255) REFERENCES EMails ON DELETE SET NULL);
        
CREATE TABLE Professor
       (PerNo         INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Rank           CHAR(2) CHECK (Rank in ('C2', 'C3', 'C4')),
        Room           INTEGER UNIQUE
        EMail        VARCHAR(255) UNIQUE REFERENCES EMails ON DELETE SET NULL);
        
CREATE TABLE Assistent
       (PerNo         INTEGER PRIMARY KEY,
        Name           VARCHAR(30) NOT NULL,
        Topic     VARCHAR(30),
        Boss           INTEGER,
        FOREIGN KEY    (Boss) REFERENCES Professor
        EMail        VARCHAR(255) UNIQUE REFERENCES EMails ON DELETE SET NULL);


CREATE TABLE EMails
       (EMail         VARCHAR(255) PRIMARY KEY,
        Daten         VARCHAR(255));
        
## 2
CREATE TABLE Lect
        (Professor    INTEGER FOREIGN KEY REFERENCES Professor(PerNo),
        Course        INTEGER FOREIGN KEY REFERENCES Course(CouNo));
        
ALTER TABLE Course
DROP COLUMN TaughtBy;


# Aufgabe 3)
## 1
```SQL
USE dbs2022;

DESCRIBE student_mat;
LOAD DATA INFILE "/var/lib/mysql/student-mat.csv"
INTO TABLE student_mat
FIELDS TERMINATED BY ';'
ENCLOSED BY '"'
IGNORE 1 LINES;
```

## 2
```SQL
USE dbs2022;

SELECT COUNT(G1) as G1Part, COUNT(G2) as G2Part, COUNT(G3) as G3Part, MAX(G1) as G1Best, MAX(G2) as G2Best, MAX(G3) as G3Best, AVG(G1) as G1Avg, AVG(G2) as G2Avg, AVG(G3) as G3Avg
FROM student_mat;

SELECT GREATEST(G1, G2, G3) AS Best, (G1 + G2 + G3) / 3 as AVG
FROM student_mat;
```