# Aufgabe 2
## 1
Im Grund gibt es dabei drei verschiedene Fälle.
Erster Fall, die Variablen haben eine andere Reihenfolge z. B. p(A,B) und p(B,A), dann lassen diese so dem = Prädikat so umbenennen, dass diese den gleichen Kopf haben. (Bsp: p(B,A) :- X=A, A=B, B=X, ...)

Im zweiten Fall könnte auftreten, dass eine Regel mehr Argumente annimmt als eine andere. Dabei lässt sich zu der Regel mit weniger Argumenten die zusätzlichen Argumente hinzufügen, welche danach dann einfach nicht weiter verwendet werden.

Im dritten Fall könnte auftreten, dass eine Regel im Kopf doppelte Argumente hat und eine andere nicht (z. B. P(A,B,A) und P(A,B,C)). Dort kann man dann das doppelte Argument wie folgt umbenennen und muss die umbenannten doppelten auf Gleichheit prüfen: P(A,B,A) wird zu: P(A,B,C) :- A==C, C=A, ...

Wird ein Argument aus dem Kopf der Regel gar nicht verwendet, so ist es egal, was mit diesem getan wird

## 2

p(’ASDF’, U, V) :- r(U,V, V) .
p(U, V, U) :- r(V, U, V) .


p(A, B, C) :- U=B, V=C, r(U, V, V) .
p(A, B, C) :- A==C, U=A, V=B, r(V, U, V) .    # da nur der erste Wert für U verwertet wird