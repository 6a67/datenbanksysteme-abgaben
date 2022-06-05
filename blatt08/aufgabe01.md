# Aufgabe 1

A -> B \
B -> A \
AB -> CDE \
C -> D \
D -> C \
D -> E \
E -> D


## Linksreduktion 1
A -> B \
B -> A \
A -> CDE \
C -> D \
D -> C \
D -> E \
E -> D

### Rechtsreduktion 1.1
A -> B \
B -> A \
A -> D \
C -> D \
D -> C \
D -> E \
E -> D 


### Rechtsreduktion 1.2
A -> B \
B -> A \
A -> C \
C -> D \
D -> C \
D -> E \
E -> D

### Rechtsreduktion 1.3
A -> B \
B -> A \
A -> E \
C -> D \
D -> C \
D -> E \
E -> D

### Zusammenfassung 1.1
A -> BD \
B -> A \
C -> D \
D -> CE \
E -> D

### Zusammenfassung 1.2
A -> BC \
B -> A \
C -> D \
D -> CE \
E -> D

### Zusammenfassung 1.3
A -> BE \
B -> A \
C -> D \
D -> CE \
E -> D


## Linksreduktion 2
A -> B \
B -> A \
B -> CDE \
C -> D \
D -> C \
D -> E \
E -> D

### Rechtsreduktion 2.1
A -> B \
B -> A \
B -> C \
C -> D \
D -> C \
D -> E \
E -> D

### Rechtsreduktion 2.2
A -> B \
B -> A \
B -> D \
C -> D \
D -> C \
D -> E \
E -> D

### Rechtsreduktion 2.3
A -> B \
B -> A \
B -> E \
C -> D \
D -> C \
D -> E \
E -> D

### Zusammenfassung 2.1
A -> B \
B -> AC \
C -> D \
D -> CE \
E -> D

### Zusammenfassung 2.2
A -> B \
B -> AD \
C -> D \
D -> CE \
E -> D

### Zusammenfassung 2.3
A -> B \
B -> AE \
C -> D \
D -> CE \
E -> D


# Aufgabe 2
Nein, da bei der Linksreduktion AB zu A sowie die darauf folgenden Rechtsreduktionen haben jeweils mehrere Möglichkeiten und sind daher nicht eindeutig. Siehe dafür Aufgabe 1