## Aufgabe 2
### 1
```SQL
CREATE TABLE email_Adressen (
    email VARCHAR(255) NOT NULL,
    details VARCHAR(255) ,
    PRIMARY KEY(email_Adressen)
);
```
```SQL
ALTER TABLE Professor
ADD COLUMN email VARCHAR(255),
FOREIGN KEY(email) REFERENCES email_Adressen(email) ON DELETE SET NULL;
```
```SQL
ALTER TABLE Student
ADD COLUMN email VARCHAR(255), 
FOREIGN KEY(email) REFERENCES email_Adressen(email) ON DELETE SET NULL;
```

### 2
```SQL
CREATE TABLE unterrichtet (
    PerNo INT NOT NULL,
    CouNo INT NOT NULL UNIQUE,
    FOREIGN KEY(PerNo) REFERENCES Professor(PerNo),
    FOREIGN KEY(CouNo) REFERENCES Course(CouNo)
);
```
```SQL
ALTER TABLE Course
DROP COLUMN TaughtBy;
```