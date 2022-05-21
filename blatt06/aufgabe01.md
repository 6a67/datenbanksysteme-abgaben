# Aufgabe 1
1)  Ausgang: \
    A -> B,C,D,E,F \
    B -> C,D,E,F \
    A,I -> J,K,L,M \
    F -> G \
    C,I -> B

    Linksreduktion: \
    Es wird nichts wegreduziert

    Rechtsreduktion: \
    A -> B \
    B -> C,D,E,F \
    A,I -> J,K,L,M \
    F -> G \
    C,I -> B

    Keine leeren Abbildungen vorhanden und kein Zusammenfassen möglich, daher ist das Ergebnis nach der Rechtsreduktion die Kanonische Überdeckung

    Endergebnis des Synthese-Algorithmus: \
    R2 := {<span style="text-decoration: underline">A</span>,B} \
    R3 := {<span style="text-decoration: underline">B</span>,C,D,E,F} \
    R4 := {<span style="text-decoration: underline">A</span>,<span style="text-decoration: underline">I</span>,J,K,L,M} \
    R5 := {<span style="text-decoration: underline">F</span>,G} \
    R6 := {<span style="text-decoration: underline">C</span>,<span style="text-decoration: underline">I</span>,B}

2)  FDs: [A -> BCDEF, B -> CDEF, AI -> JKLM, F -> G, CI -> B] \
    R = [A, B, C, D, E, F, G, I, J, K, L, M]

    Dekomposition = {R}


    [A, B, C, D, E, F, G, I, J, K, L, M] nicht in BCNF, daher zerlege mit A -> BCDEF

    R_1_1 = [A, B, C, D, E, F] \
    R_1_2 = [A, G, I, J, K, L, M]

    Überprüfe danach, ob die nun neu entstandenen Relationen in BCNF sind:

    Überprüfe ob R_1_1 = [A, B, C, D, E, F] in BCNF ist mit FDs [A -> BCDEF, B -> CDEF]: \
    Superschlüssel der FDs ist A, somit keine Zerlegung mit A -> BCDEF, aber mit B -> CDEF

    R_2_1 = [B, C, D, E, F]  \
    R_2_2 = [A, B]

    Überprüfe danach R_1_2 = [A, G, I, J, K, L, M]:

    Überprüfe ob [A, G, I, J, K, L, M] in BCNF ist mit FDs [AI -> JKLM]:  \
    AI ist kein Schlüssel, da G damit nicht erreicht werden kann.

    zerlege [A, G, I, J, K, L, M] mit AI -> JKLM:  \
    R_3_1 = [A, I, J, K, L, M]  \
    R_3_2 = [A, G, I]




    Aktuell bleiben dann noch in R:  \
    R_2_1 = [B, C, D, E, F]  \
    R_2_2 = [A, B]  \
    R_3_1 = [A, I, J, K, L, M] \
    R_3_2 = [A, G, I] 

    Überprüfe ob [B, C, D, E, F] in BCNF ist mit FDs [B -> CDEF]: \
    B ist Schlüssel, daher ist die Relation in BCNF.

    Überprüfe ob [A, B] in BCNF ist. Es gibt keine FDs für die Attributmenge, daher ist es auch in BCNF.

    Überprüfe ob [A, I, J, K, L, M] in BCNF ist mit FDs [AI -> JKLM]: \
    AI ist Schlüssel, daher ist die Relation in BCNF.

    Überprüfe ob [A, G, I] in BCNF ist. Es gibt keine FDs für die Attributmenge, daher ist es auch in BCNF.

    Endergebnis \
    R_2_1 = [B, C, D, E, F] \
    R_2_2 = [A, B] \
    R_3_1 = [A, I, J, K, L, M] \
    R_3_2 = [A, G, I] 

3)   
   - Die durch den Dekompositionsalgorithmus entstandene BCNF hat eine Relation weniger als die 3NF, welche durch den Synthese-Algorithmus entstanden ist.
   - Nach der Vorlesung wird bei dem Synthese-Algorithmus die Abhängigkeitserhaltung und Verlustlosigkeit garantiert
   - Der Dekompositionsalgorithmus berechnet eine verlustlose Zerlegung eines Schemas
   - Bei dem Dekompositionsalgorithmus geht die Abhängigkeit F -> G verloren
