# Aufgabe 1

<!-- ## 1
a)  A ist ein Schlüsselkandidat
b)  AB ist ein Superschlüssel
c)  C ist weder Schlüsselkandidat noch Superschlüssel
d)  E ist weder Schlüsselkandidat noch Superschlüssel
e)  BDE ist Superschlüssel -->

## 1
Man kann damit starten, dasss ABCDE einen Superschlüssel stellt.
Guckt man sich die Relationen an so ergibt sich zunächst:
1) ACDE
2) AB
3) ABC
4) ABCE
5) BDE

Als Superschlüssel. Diese sind allerdings noch nicht minimal.
Überprüft man nun für jedes Attribut auf welche Werte man mit diesen schließen kann ergeben sich:
1) A
   
Da A bereits einen Schlüsselkandidaten stellt, wird dieser aus den anderen Schlüsselkandidaten gestrichen:
1) B    🗲
2) BC
   
Da BC bereits einen Schlüsselkandidaten stellt, wird dieser aus den anderen Schlüsselkandidaten gestrichen:
1) E    🗲
2) BE

Diese lassen sich nicht weiter kürzen und somit ergeben sich folgende Schlüsselkandidaten
1) A
2) BC
3) BE


## 2
Linksreduktion: \
```
Teste für AB 

Hülle(F, A): 
    A Teilmenge von A -> AB
    AB Teilmenge von AB -> ABCDE

Daraus folgt, dass AB -> CDE zu A -> CDE reduziert werden kann
```
```
Hülle(F, B):
    A keine Teilmenge von B
    AB keine Teilmenge von B
    C keine Teilmenge von B
    E keine Teilmenge von B
    BDE keine Teilmenge von B
```

```
Teste für BDE

Hülle(F, B):
    Siehe ersten Teil

Hülle(F, D):
    A keine Teilmenge von D
    AB keine Teilmenge von D
    C keine Teilmenge von D
    E keine Teilmenge von D
    BDE keine Teilmenge von D

Hülle(F, E):
    A keine Teilmenge von E
    AB keine Teilmenge von E
    C keine Teilmenge von E
    E Teilmenge von E -> ED
    BDE keine Teilmenge von ED

Da D Teil der Hülle von E ist, ist D überflüssig und kann entfernt werden
```

**Zwischenergebnis**
1) A -> B
2) A -> CDE
3) C -> DE
4) E -> D
5) BE -> AC


Rechtsreduktion: \
Beispiel: \
    $B \in AttrHülle(F - (A \rightarrow B) \cup (A \rightarrow (A-B)), A)$ \
    $H^{\prime}=AttrHülle(\{A \rightarrow CDE,\ C \rightarrow DE,\ E \rightarrow D,\ BDE \rightarrow AC\}, A)$ \

```
Hülle(F', A):
    A Teilmenge von A -> ACDE
    C Teilmenge von ACDE -> ACDE
    E Teilmenge von ACDE -> ACDE
    BE keine Teilmenge von ACDE
=> B ist kein Element der neuen Attributhülle, somit muss B bleiben
```

```
Reduktion für FD 2:
Teste C in AttrHülle(F - FD(2) + (A -> DE), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> ABDE
        C keine Teilmenge von ABDE
        E Teilmenge von ABDE -> ABDE
        BDE Teilmenge von ABDE -> ABCDE
    
    Somit ist C Element der AttrHülle(F', A) und somit überflüssig


Teste D in AttrHülle(F - FD(2) + (A -> E), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> ABE
        C keine Teilmenge von ABE
        E Teilmenge von ABE -> ABDE
        BE Teilmenge von ABDE -> ABCDE

    Somit ist D Element der AttrHülle(F', A) und somit überflüssig

Teste E in AttrHülle(F - FD(2) + (A -> empty), A):
    AttrHülle(F', A):
        A Teilmenge von A -> AB
        A Teilmenge von AB -> AB
        C keine Teilmenge von AB
        E keine Teilmenge von AB
        BE keine Teilmenge von AB

    Somit ist E kein Element der AttrHülle(F', A) und somit benötigt

=> FD(2): A -> E
```
```
Reduktion für FD(3):

Teste D in AttrHülle(F - FD(3) + (C -> E), C):
    AttrHülle(F', C):
        A keine Teilmenge von C
        A keine Teilmenge von C
        C Teilmenge von C -> CE
        E Teilmenge von CE -> CDE
        BE keine Teilmenge von CDE

    Somit ist D Element der AttrHülle(F', C) und somit überflüssig

Teste E in AttrHülle(F - FD(3) + (C -> empty), C):
    AttrHülle(F', C):
        A keine Teilmenge von C
        A keine Teilmenge von C
        C Teilmenge von C -> C
        E keine Teilmenge von C
        BE keine Teilmenge von C

    Somit ist E kein Element der AttrHülle(F', A) und somit benötigt

=> FD(3): C -> E
```
```
Reduktion für FD(4):

Teste D in AttrHülle(F - FD(4) + (E -> empty), E):
    AttrHülle(F', E):
        A keine Teilmenge von E
        A keine Teilmenge von E
        C keine Teilmenge von E
        E Teilmenge von E -> E
        BE keine Teilmenge von E
    
    Somit ist D kein Element der AttrHülle(F', E) und somit benötigt

=> FD(4): C -> E
```
```
Reduktion für FD(5):

Teste A in AttrHülle(F - FD(5) + (BE -> C), BE):
    AttrHülle(F', BE):
        A keine Teilmenge von BE
        A keine Teilmenge von BE
        C keine Teilmenge von BE
        E Teilmenge von BE -> BDE
        BE Teilmenge von BDE -> BDE

    Somit ist D kein Element der AttrHülle(F', BE) und somit benötigt

Teste C in AttrHülle(F - FD(5) + (BE -> A), BE):
    AttrHülle(F', BE):
        A keine Teilmenge von BE
        A keine Teilmenge von BE
        C keine Teilmenge von BE
        E Teilmenge von BE -> BDE
        BE Teilmenge von BDE -> ABDE

    
    Somit ist C kein Element der AttrHülle(F', BE) und somit benötigt

=> FD(5): BE -> AC
```

**Zwischenergebnis**
1) A -> B
2) A -> E
3) C -> E
4) E -> D
5) BE -> AC

Nach zusammen fassen ergibt sich \
**Endergebnis**
1) A -> BE
2) C -> E
3) E -> D
4) BE -> AC
