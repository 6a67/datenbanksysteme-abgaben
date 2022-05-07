# Aufgabe 2
$\pi_{A}(R \bowtie_{C=B}(S \bowtie_{E=D} T))$

Da der Join kommutativ ist lässt es sich in folgendes umformen: \
$\pi_{A}((T \bowtie_{D=E} S) \bowtie_{B=C} R )$

Da für den Join nur die Werte benötigt werden, welche auch Teil des Joins, lassen sich über die Projektion bereits einige Attribute vorauswählen. Dabei muss allerdings noch beachtet werden, welche Attribute für die danach folgenden Operationen noch benötigt werden. Daraus kann sich dann ergeben:

$\pi_{A}((\pi_D(T) \bowtie_{D=E} \pi_{ABE}(S)) \bowtie_{B=C} R )$

## 2
Da T auf D gejoined wird, benötigt dieses auch das Attribut D.
Da S auf E und B gejoined wird, benötigt dieses auch das Attribut E und B. 
Da R auf C gejoined wird, benötigt dieses auch das Attribut C.

Bei der ersten Anfrage muss S oder T B als Attribut enthalten. Dabei ist jedoch egal welche der beiden Relationen dieses Attribut enthält. Bei der zweiten Anfrage wird nun einfach die Annahme getroffen, dass dieses Attribut in S enthalten ist.


Bei der ersten Anfrage könnte das Attribut A aus einer der drei Relationen stammen. Somit dürfte aber auch nur eine der drei Relationen dieses enthalten, da die Projektion sonst nicht eindeutig ist . Bei der zweiten wird nun davon ausgegangen, dass dieses aus S kommt
