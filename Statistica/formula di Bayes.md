Consideriamo $(\Omega, \mathcal P)$ [[Statistica/spazio di probabilità|spazio di probabilità]] e siano $A,B$ [[eventi]] non trascurabili, allora
$$\mathcal P(B|A) = \frac{\mathcal P(A|B)\cdot\mathcal P(B_i)}{\sum_{j=1}^n \mathcal P(A|B_j)\cdot \mathcal P (B_j)} \qquad \forall i = 1,...,n$$
>[!warning] Dimostrazione
>$$\mathcal P(B|A) = \frac{\mathcal P(A\cap B)}{\mathcal P(A)} = \frac{\mathcal P(A|B) \cdot \mathcal P(B)}{\mathcal(A)}$$
>La seconda formula segue dalla prima (con $B=B_i$) e dalla formula di fattorizzazione per $\mathcal P(A)$

___

Si applica per "invertire" il condizionamento, tipicamente:
- accade un evento $A$ riferito as un' "osservabile" (colore della biglia, esito test,...)
- vogliamo calcolare la [[probabilità]] di una possibile "causa" $B_i$ (una scelta, sano/malato,...)

>[!example] Esempio "biglie"
>Estraiamo una biglia rossa, cogliamo calcolare la prob. che l'estratta venga dall'urna 1:
>$$\mathcal P(urna\ 1|rossa) = \frac{\mathcal P(rossa|urna\ 1) \cdot \mathcal P(urna\ 1)}{\mathcal P(rossa)} \approx 0.385$$

>[!example] Esempio "test diagnostico"
>Il test dà esito positivo, prob. che la persona sia effettivamente malata?
>$$\mathcal P(malata|positivo) = \frac{\mathcal P(positivo|malata)\cdot \mathcal P(malata)}{\mathcal P(positivo)} = 0.25$$
>Ciò significa che in un gruppo di 100 persone se una sola è malata avremo 1 test positivo corretto dato da $\mathcal P(positivo|malato) = 0.99$ e inoltre un altro 2.5% di test positivi falsi corrispondenti a circa 3 persone.

