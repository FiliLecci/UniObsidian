Valore che differisce in modo significativo dalla "grande maggioranza dei dati".

>[!example] Esempio
>Sulle altezze di 10 italiani, troviamo 9 dati tra 1.65m e 1.85m e un dato pari a 10m o  2.10m.

Gli outlier influenzano in modo significativo alcune statistiche (media, varianza, ...) mentre altre sono più robuste (percentili).

Non c'è una regola generale su come trovare un oulier, ma ci sono alcune regole empiriche:
1. dati fuori dall'intervalli $[Q_1-1.5L, Q_3+1.5L]$ dove $L=Q_3-Q_1$ viene detto *scarto interquartile*.
#### Perché si ottiene un outlier?
- Errori di misurazione (tipo 10m)
- dati molto rari
- non si sa se errore o dato raro (tipo 2.10 che è difficile ma non impossibile per una altezza)