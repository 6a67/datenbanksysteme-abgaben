# Aufgabe 1
## 1.
### A
Man geht zwei Teilmengen, α und β, an Attributen durch und guckt, ob die eine Teilmenge α -> β gilt

Lager -> Ort \
Ort -> Lager

Teil,Lager -> Menge (bzw. Teil,Lager -> Menge,Ort und Teil,Ort -> Lager,Menge)

Teil,Menge -> Lager,Ort

Lager,Menge -> Teil,Ort (bzw. Ort,Menge -> Teil,Lager)

Teil,Lager,Menge -> Ort \
Teil,Ort,Menge -> Lager \
Teil,Lager,Ort -> Menge \
Menge,Lager,Ort -> Teil

### B
Mit den FDs lassen sich die Super- oder Kandidatenschlüssel bestimmen und somit aus diesen dann auch ein möglicher Primärschlüssel.
Da es dafür dann aber mehrere mögliche Primärschlüssel gibt, kann damit dann aber nicht eindeutig bestimmt werden, welcher Kandidatenschlüssel beim anlegen der Tabelle als Primärschlüssel gewählt wurde. 

## 2.
Teil,Lager -> Menge,Ort \
Lager -> Ort \
Ort -> Lager

Teil,Lager und Teil,Ort sind Schlüsselkandidaten \
Zusätzlich existieren folgende Superschlüssel: \
Teil,Lager,Menge \
Teil,Lager,Ort \
Teil,Ort,Menge \
Teil,Lager,Menge,Ort


## 3.
Assi(PerNo,Name,Group,Boss) \
PerNo -> Name,Group,Boss

Da PerNo der Schlüsselkandidat ist: \
RName(PerNo,Name), RGroup(PerNo,Group), RBoss(PerNo,Boss)

oder

RNG(PerNo,Name,Group), RNB(PerNo,Boss)