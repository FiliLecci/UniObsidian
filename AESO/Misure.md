# Misure primitive
## Latenza ($L$)
La latenza misura il tempo necessario tra l'inizio di un certo calcolo e la restituzione del relativo risultato
## Tempo di completamento ($T_C$)
Il tempo di completamento rappresenta il tempo che intercorre tra l'inizio del primo calcolo e la fine dell'ultimo calcolo di una certa funzione.
## Tempo di servizio ($T_S$)
Il tempo di servizio è il tempo che intercorre fra la produzione di due risultati consecutivi o fra l’inizio di due calcoli consecutivi.
## Throughput ($B$)
Il throughput rappresenta il numero di calcoli completati per unità di tempo. Spesso si usa anche il nome "banda di elaborazione".
___
Secondo queste definizioni quindi possiamo trarre le seguenti conclusioni:
> - diminuire la latenza significa rendere l'esecuzione di una singola operazione più veloce;
> - diminuire il tempo di servizio (e quindi aumentare il throughput) significa poter produrre più risultati nella stessa quantità di tempo.

# Misure derivate
Le misure derivate sono altri tipi di misure che usano le [[#Misure primitive]] per ottenere altri dati.
## Speedup
Il rapporto tra il **miglior tempo sequenziale** e il tempo con grado di parallelismo pari ad $n$
$$Speedup(n) = \frac{T_{seq}}{T_{par}(n)}$$
> [!note] Significato
> Lo $Speedup$ indica di quanto siamo riusciti a migliorare l'esecuzione sequenziale.
> Normalmente è un valore che sta tra la retta $y=x$ e l'asse delle ascisse, quindi vale
> $$Speedup(n) \leq n$$
## Scalabilità
Rapporto tra tempo con grado di parallelismo 1 e quello con grado di parallelismo $n$
$$Scalabilita(n) = \frac{T_{par}(1)}{T_{par}(n)}$$
> [!note] Significato
> La $Scalabilita$ indica quanto una soluzione parallela riesce ad adattarsi a livelli di parallelismo diversi. Confrontando infatti con caso con grado di parallelismo 1, si vede quanto aumentando il grado di parallelismo va ad aumentare il guadagno.
## Tempo ideale
Rapport tra tempo sequenziale e il grado di parallelismo $n$
$$T_{id} = \frac{T_{seq}}{n}$$
> [!note] Significato
> Indica il tempo minimo raggiungibile con parallelizzazione di grado $n$ eseguendo le stesse elaborazioni.
## Efficienza
Il rapport tra il tempo ideale e quello ottenuto con grado di parallelismo $n$
$$eff(n) = \frac{T_{id}(n)}{T_{par}(n)} = \frac{\frac{T_{seq}}{n}}{T_{par}(n)} 
= \frac{T_{seq}}{n \times T_{par}(n)} = \frac{speedup(n)}{n}$$
> [!note] Significato
> Ci dà un modo di capire quanto riusciamo a sfruttare le risorse a disposizione. È un valore compreso tra la retta $y=1$ e l'asse delle ascisse.
> Vale quindi
> $$eff(n) \leq 1$$
> Più l'efficienza è vicinia ad 1 meglio è.

