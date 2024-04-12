Sia $k$ un numero naturale con $0<k<100$

>[!note] Definizione k-esimo percentile
>Il dato $x_i$ t.c.
> - almeno il $k\%$ dei dati sia inferiore o uguale a $x_i$
> - almeno il $(100-k)\%$ dei dati sia superiore o uguale a $x_i$
> 
> Se due dati soddisfano questa condizione, si prende come k-esimo percentile la media aritmetica dei due

>[!warning] Osservazine
>Il k-esimo percentile si dice anche $\beta$-quantile, con $\beta=\frac{k}{100}$
>>[!example] Esempio
>>25° percentile = 1° quartile = $Q_1$
>>
>>50° percentile = 2° quartile = [[mediana campionaria|mediana]] = $Q_2$
>>
>>75° percentile = 3° quartile = $Q_3$
>

> Vedere Esempio 1.5 [[Appunti_Statistica_04_28.pdf]]

___
#### Calcolo
- ordiniamo i dati $x_{(1)} \leq x_{(2)} \leq ... \leq x_{(n)}$
- $\beta := \frac{k}{100}$
	1. Se $\beta n = \frac{k}{100} \cdot n$ ***non è un numero intero***, si prende come k-esimo percentile  $x_{(\lceil \beta_n \rceil)}$ dove $\lceil \beta_n \rceil$ è l'approssimazione per eccesso di $\beta_n$
	2.  Se $\beta n = \frac{k}{100} \cdot n$ ***è un numero intero***, si prende come k-esimo percentile $\frac{1}{2}(x_{\beta n}+x_{(\beta n +1)})$ ossia la media aritmetica tra $\beta n$ e $\beta n +1$
