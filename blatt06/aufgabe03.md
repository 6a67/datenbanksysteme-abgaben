# Aufgabe 3
## 1
### 1.
![picture 2](_resources/686cf2fbee1b3b5424bb4dbc3cb85be0478e541f7aba4558b036efac00ef83fd.png)  

Der Graph ist serialisierbar, da in dem Serialisierbarkeitsgraph kein Zyklus existiert


### 2.
![picture 1](_resources/a0edd158add09ab25cde2fbd0d2782a35a073a14d24509249eea0dca7ffefb88.png)  

Der Graph ist serialisierbar, da in dem Serialisierbarkeitsgraph kein Zyklus existiert

## 2
### A
#### 1.
$T_3, T_2, T_1$

#### 2.
$T_1, T_2, T_3, T_3$ oder $T_1, T_3, T_2, T_3$

### B
Die hier gegebenen Historien sind nicht rücksetzbar, sondern nur serialisierbar, da die commits immer erst ganz am Ende durchgeführt werden.

Die selbst aufgestellten seriellen Historien sind serialisierbar, rücksetzbar, Historien ohne kaskadierendes Rücksetzen und strikt, da serielle Historien eine Teilmenge von all diesen sind.