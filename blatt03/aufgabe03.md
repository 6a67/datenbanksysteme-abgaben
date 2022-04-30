## Aufgabe 3
### 1
```SQL
USE dbs2022;

LOAD DATA INFILE "/var/lib/mysql/student-mat.csv"
INTO TABLE student_mat
FIELDS
    TERMINATED BY ';'
    ENCLOSED BY '"'
IGNORE 1 ROWS;
```

### 2
```SQL
USE dbs2022;

SELECT COUNT(G1) as G1Part, COUNT(G2) as G2Part, COUNT(G3) as G3Part, MAX(G1) as G1Best, MAX(G2) as G2Best, MAX(G3) as G3Best, AVG(G1) as G1Avg, AVG(G2) as G2Avg, AVG(G3) as G3Avg
FROM student_mat;

SELECT GREATEST(G1, G2, G3) as Best, (G1 + G2 + G3) / 3 as AvgG
FROM student_mat;
```