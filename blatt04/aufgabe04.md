# Aufgabe 4
## 1
MngNr -> MngName, CEONr \
MaNr -> MngNr, Projekt \
AbNr -> AbName, Staat, Stadt, CEONr \
CEONr -> CEOName, Sekr 

## 2
MaNr, AbNr

## 3
Angenommen die Attribute der Namen enthalten nur die Nachnamen oder nur die Vornamen der Personen, so befindet sich die Relation in der ersten Normalform.
Da z. B Sekr nicht von dem Schlüsselkandidaten abhängig ist, befindet sich das Schema nicht in der zweiten NF

## 4
BCNF:
Keine Linksreduktion notwendig, da nur einzelne Attribute dort stehen
Rechtsreduktion zeigt, dass kein Attribut weggestrichen werden kann. Daher befindet sich das Schema bereits in der BCNF.

MngNr -> MngName, CEONr \
MaNr -> MngNr, Projekt \
AbNr -> AbName, Staat, Stadt, CEONr \
CEONr -> CEOName, SekrNF.

Manager: {[<span style="text-decoration: underline">MngNr</span>, MngName, CEONr]} \
Mitarbeiter: {[<span style="text-decoration: underline">MaNr</span>, MngNr, Projekt]} \
Abteilung: {[<span style="text-decoration: underline">AbNr</span>, AbName, Staat, Stadt, CEONr]} \
CEO: [{<span style="text-decoration: underline">CEONr</span>, CEOName, Sekr}]

Verknüpfung: [{<span style="text-decoration: underline">MaNr</span>, <span style="text-decoration: underline">AbNr</span>}]

## 5
Anhand der Konstruktion sind bereits alle Anforderungen für die BCNF gegeben: Alle Attribute hängen jeweils von den Kandidatenschlüsseln ab

## 6
Bei jedem Schritt werden dei Attribute der Relation, welche nicht Teil des Schlüssels sind raus gestrichen:

Firma(CEONr, CEOName, Sekr, AbNr, AbName, Stadt, Staat, MngNr, MngName, MaNr, Projekt)

#### 1
Firma(CEOName, Sekr, AbNr, AbName, Stadt, Staat, MngNr, MaNr, Projekt) \
Manager(MngNr, MngName, CEONr)

#### 2
Firma(CEOName, Sekr, AbNr, AbName, Stadt, Staat, MaNr) \
Manager(MngNr, MngName, CEONr) \
Mitarbeiter(MaNr, MngNr, Projekt)

#### 3
Firma(CEOName, Sekr, AbNr, MaNr) \
Manager(MngNr, MngName, CEONr) \
Mitarbeiter(MaNr, MngNr, Projekt) \
Abteilung(AbNr, AbName, Staat, Stadt)

#### 4
Firma(AbNr, MaNr) \
Manager(MngNr, MngName, CEONr) \
Mitarbeiter(MaNr, MngNr, Projekt) \
Abteilung(AbNr, AbName, Staat, Stadt) \
CEO(CEONr, CEOName, Sekr)


## 7

Die Zerlegung ist nicht abhängigkeitserhaltend. Die Abhängigkeit AbNr -> CEONr geht verloren.