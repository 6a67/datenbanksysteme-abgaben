# Aufgabe 1
## 1
Fact Table:
    Patient(Person, Bundesland, Regierungsbezirk, Landkreis, Kontaktperson, Gesundheitsamt, Infektionsdatum, Genesungsdatum, Symptome, Krankenakte, Hausarzt, Testzentrum, ...)

Dimension Tables:
    People(Vorname, Nachname, Adresse, Geburtsdatum, ...)
    Bundesland(Name, Einwohnerzahl, Regierung, ...)
    Regierungsbezirk(Name, Einwohnerzahl, Bundesland, ...)
    Landkreis(Name, Einwohnerzahl, Bundesland, Regierungsbezirk, ...)
    Kontakte(Personen)
    Gesundheitsamtsämter(Ort, PLZ, Name, Leiter, Adresse, ...)
    Daten(Datum, Tag, Monat, Jahr, Wochentag, Kalenderwoche, Quartal, Jahreszeit, ...)
    Locations(Location, Ort, PLZ, Koordinaten, ...)
    Symptome(Symptom, Ausprägung, Stärke, Dauer, ...)
    Krankenakte(Vorerkrankung, Chronisch, Seit-wann, ...)
    Hausarzt(Vorname, Nachname, Titel, Praxis, ...)
    Testzentrum(Ort, PLZ, Adresse, Koordinaten, ...)
    ...

Die Tabelle könnte noch deutlich deutlich größer sein. Daher ist auch eine ungefähre Schätzung schwer.
Es gab zurzeit ca. 27 Millionen Infektionen, daher hätte auch der Fact Table so viele Einträge.
Da das zwar viele Einträge sind, aber immer noch nicht unglaublich viele, würden wir schätzen, dass die Datenbank eher am unteren Ende der Größen liegt, also um die 100 GB

## 2
### 1
<!-- ```SQL
SELECT Bundesland.Name, Regierungsbezirk.Name, Landkreis.Name, (COUNT(Patient.Person) / Landkreis.Einwohnerzahl) * 100000 as Inzidenz
FROM Bundesland, Regierungsbezirk, Landkreis, Patient
WHERE Patient.Bundesland = Bundesland.Name
AND Patient.Regierungsbezirk = Regierungsbezirk.Name
AND Patient.Landkreis = Landkreis.Name
AND CAST(GETDATE() AS DATE) - 7 <= Patient.Infektionsdatum
GROUP BY CUBE(Bundesland.Name, Regierungsbezirk.Name, Landkreis.Name)
``` -->

```SQL
SELECT Landkreis.Name, COUNT(Patient.Person) / Landkreis.Einwohnerzahl * 100000 as LandkreisInzidenz, r.RegierungsbezirkInzidenz, b.BundeslandInzidenz
FROM Landkreis, Patient, (
    Regierungsbezirk.Name, COUNT(Patient.Person) / Regierungsbezirk.Einwohnerzahl * 100000 as RegierungsbezirkInzidenz
) as r, (
    Bundesland.Name, COUNT(Patient.Person) / Bundesland.Einwohnerzahl * 100000 as BundeslandInzidenz
) as b
WHERE Patient.Landkreis = Landkreis.Name
AND Patient.Regierungsbezirk = r.Name
AND Patient.Bundesland = b.Name
AND CAST(GETDATE() AS DATE) - 7 <= Patient.Infektionsdatum
GROUP BY Landkreis.Name
```

### 2
```SQL
SELECT Landkreis.Name, (COUNT(Patient.Person) / Landkreis.Einwohnerzahl) * 100000 as Inzidenz
FROM Landkreis, Patient, Daten
WHERE Patient.Landkreis = Landkreis.Name
AND Patient.Infektionsdatum = Daten.Datum
GROUP BY CUBE(Landkreis.Name, Daten.Kalenderwoche)
```