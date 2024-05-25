## Parallelismo spaziale
Supponiamo di dover eseguire una certa operazione (tradurre un libro) che richiede un tempo $t$ per essere completata, se procediamo ad effettuare l'operazione, ovviamente, il tempo impiegato sarà $t$; possiamo velocizzare questo tempo dividendo l'operazione in $m$ sotto-operazioni, ognuna delle quali richiede adesso un tempo $t_0 = t/m$ e viene eseguita da una persona (CPU) diversa (si dividono le pagine tra $m$ persone). In questo modo rendiamo il tempo totale necessario a completare tutta l'operazione da $t$ a $t_0$ che è $t/t_0 = m$ volte più veloce in quanto tutti possono iniziare la loro elaborazione contemporaneamente.
A questo tempo si devono aggiungere $t_{merge}$ e $t_{split}$ che sono rispettivamente il tempo necessario a riunire i risultati delle varie elaborazioni in un risultato unico ed il tempo per dividere l'operazione in sotto-operazioni; spesso questi tempi sono trascurabili e possono non essere considerati nel tempo totale necessario.
## Parallelismo temporale
Prendiamo ora una diversa situazione: dover costruire una serie di oggetti, ognuno dei quali richiede una sequenza di operazioni $f_1, ..., f_k$ ciascuna delle quali richiede un tempo $t_i$ per essere completata.
Facendo tutte operazioni da solo, per costruire $m$ oggetti impiegherei un tempo
$$
m \times \sum^k_{i=1} t_i
$$
Se invece fossimo in $k$ costruttori, ognuno di essi può essere assegnato ad una lavorazione. Così facendo l'$i$ esimo lavoratore inizierà la sua lavorazione appena la lavorazione $i-1$ sarà completata e passerà il risultato al lavoratore $i+1$.
Con questo tipo di lavorazione a catena, ogni elemento finirà la lavorazione in un tempo
$$\sum^k_{i=0}t_i$$
Siccome però ogni elemento inizia la lavorazione non appena finisce la prima lavorazione dell'elemento precedente, gli elementi inizieranno ad uscire dopo la fine della lavorazione del primo elemento e successivamente ogni qualvolta la lavorazione più lunga finisce.
Quindi il tempo totale per finire la lavorazione di $m$ pezzi sarà di
$$\sum^k_{i=0}t_i + (m-1) \times max\{t_1,...,t_k\}$$
Nel caso in cui $m >> k$ (quindi dobbiamo produrre molti più pezzi rispetto al numero di costruttori) possiamo dire che il tempo per produrre $m$ pezzi è di 
$$m \times max\{t_1,...,t_k\}$$
Il guadagno di usare $k$ lavoratori rispetto ad uno solo è di
$$
\frac{m \times \sum^k_{i=1} t_i}{m \times max\{t_1,...,t_k\}} \cong k
$$
___
Al fine di valutare gli effetti dell'introduzione delle forme di parallelismo si usano le [[Misure]].
## Forme di parallelismo
### Pipeline
Il pipeline consiste in un certo numero di stadi $S_1,...,S_k$, ognuno dei quali calcola una certa funzione (si assume che $S_i$ calcoli la funzione $f_i$). L'uscita dello stadio $S_i$ va in ingresso allo stadio $S_{i+1}$.
Il primo stadio riceve dei task $x_1,...,x_m$ ogni $T_a$, mentre l'ultimo stadio produce un numero pari a $m$ di valori di uscita.

Un pipeline può essere usato nel caso in cui si ha una sequenza di oggetti la cui elaborazione è totalmente indipendente gli uni dagli altri.

Aumenta il throughput ma non di diminuire il tempo di latenza di una computazione sequenziale.
### Farm
Una farm riceve in ingresso un insieme di dati  $\{x_1,...,x_m\}$ e li processa utilizzando un numero $n_w$ di worker. Ognuno dei worker calcola una funzione $f$ su uno dei dati $x_i$ e restituisce poi in uscita il risultato $f(x_i)$.
La farm impiega un tempo $T_{split}$ per dividere l'insieme di dati in $n_w$ sottoinsiemi ed assegnarli ai worker, impiega poi $T_{merge}$ per ricostruire il risultato a partire dai risultati dei worker.
Per il farm con $n_w$ worker che processa $m$ task in ingresso che arrivano
ogni $Ta$, assumendo di impiegare $T_{sched}$ per assegnare un task in ingresso ad
un worker, $T_{coll}$ per raccogliere un valore calcolato da un worker e spedirlo in
uscita al farm e $T_w$ per calcolare una singola $f(x)$ in uno dei worker, vale che:
$$
T_S(n_w) = max\{T_a, T_{sched}, T_{coll}, \frac{T_w}{n_W}\}
$$
$$
T_C (n_w, m) = T_{sched} + \frac{m}{n_W} T_w + T_{coll} \cong m × T_S
$$

Il massimo speedup ottenibile è $n_w$ e, come la pipeline, migliora il throughput ma non il tempo di latenza delle computazioni sequenziali
### Map
...
