# Aufgabe 3
1. jahrgang, buchst -> klassenlehrer, klassensprecher, klassenraum

Angenommen der Klassenlehrer sowie Klassensprecher sind atomare Attribute, so liegt die erste NF vor.
Alle Attribute sind von den Schlüsseleinträgen abhängig, daher liegt auch die zweite NF vor.
Kein Fakt ist mehrfach gespeichert, daher liegt auch die dritte NF vor.
Da die drei Attribute von beiden Attributen des Schlüsselskandidatens abhängen, liegt die BCNF vor.

2. - jahrgang, buchst -> klassenlehrer, klassensprecher, klassenraum
   - einschulungsdatum -> jahrgang
   - jahrgang -> einschulungsdatum

Angenommen der Klassenlehrer, Klassensprecher sowie das Einschulungsdatum sind atomare Attribute, so liegt die erste NF vor.
Alle Attribute sind von den Schlüsseleinträgen abhängig, daher liegt auch die zweite NF vor.
Da Einschulungsdatum und Jahrgang in eigene Relationen ausgelagert wurden, ist auch kein Fakt mehrfach gespeichert und es handelt um die dritte NF.
Angenommen das Einschulungsdatum lässt sich durch den Jahrgang bestimmt, so ist das Einschulungsdatum nicht von beiden Attributen des Schlüsselskandidatens abhängig und es liegt keine BCNF vor.


3. - name, vorname -> geburtsdatum, alter
   - geburtsdatum -> alter

Angenommen das Geburtsdatum ist ein atomares Attribut, so liegt die erste NF vor.
Alle Attribute sind von den Schlüsseleinträgen abhängig, daher liegt auch die zweite NF vor.
Da das Alter aber nicht von den Schlüsseleinträgen bestimmt wird, liegt die dritte NF nicht vor.
Da die dritte NF nicht gegeben ist, kann die BCNF auch nicht gegeben sein.