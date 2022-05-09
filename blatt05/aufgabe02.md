# Aufgabe 2
## 1
Beim inneren Join gehen die Tupel verloren, für die kein Match gefunden werden kann.
Bei äußeren Join hingehen bleiben diese erhalten. Kann also für ein Tupel aus Tabelle A kein Match in Tabelle B gefunden werden, so bleibt das Tupel aus Tabelle A erhalten und erhält für die Attribute aus B einfach einen Wert. Das Gleiche gilt analog dafür, wenn das Tupel aus B kommt und kein Match in A enthält.

# TODO: Bild einfügen

## 2
## TODO
```SQL
select *
from (
  select *
  from t1
  union 
  select *
  from t2
)
left join t1 on t1.a=t2.a 
left join t2 on t1.a=t2.a 
```