# Aufgabe 2
## 1
Enthält ein Prädikat mehrere Variablen, so lassen diese sich zuerst "manuell" umbenennen (z. B. wird p(X,Y,Z) zu p(A,B,C)).
Dies tut man dann auch entsprechend für die Variablen, welche im Rumpf des Prädikats vorkommen (z. B. wird p(X,Y,Z) :- s(X,Y), t(Z) zu p(A,B,C) :- s(A,B), t(C)).
Enthält dabei der Kopf doppelte Variablen, so müsste diese dann mit dem = im Rumpf umbenannt werden (p(X,Y,X) wird zu p(A,B,C) :- C=A)
Enthält der Kopf weniger Variablen als erwünscht, so lassen sich einfach beliebig viele Variablen hinzufügen, welche nicht weiter genutzt werden(p(A,B) wird zu p(A,B,C,D))


## 2

p(’ASDF’, U, V) :- r(U,V, V).  
p(U, V, U) :- r(V, U, V).


p(A, B, C) :- r(B, C, C), A=’ASDF’.  
p(A, B, C) :- r(B, A, B), C=A.


## 3

Beispiel Werte in dem Ausgangsbeispiel eingetragen:  
p(’ASDF’, '1', '2') :- r('1','2', '2').  
p('3', '4', '3') :- r('4', '3', '4').

Beispiel Werte in das umgeformte Beispiel eingetragen:  
p(’ASDF’, '1', '2') :- r('1', '2', '2'), A=’ASDF’.  # egal was für A eingesetzt werden würde, A ist am Ende immer ’ASDF’  
p('3', '4', '3') :- r('4', '3', '4'), C=A.          # C und A haben immer den gleichen Wert