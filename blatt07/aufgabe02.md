# Aufgabe 2
R(BestellNR,AuslieferungDatum,Artikel,Feiertag) \
BestellNR,Artikel -> AuslieferungDatum \
AuslieferungDatum -> Feiertag

Da vermutlich alle Informationen atomar gespeichert sind, liegt die erste NF vor. \
Aus den FDs ergibt sich, dass BestellNR,Artikel den Kandidatenschlüssel stellt. Da der Feiertag nicht von diesem abhängig ist, liegt das Schema nicht in der zweiten NF vor und somit auch nicht in der dritten NF.