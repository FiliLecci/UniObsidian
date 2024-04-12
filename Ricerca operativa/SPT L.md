### Spiegazione SPT.L con FIFO

L'utilizzo di una strategia FIFO corrisponde ad una visita del grafo per livelli (bfs).\
Questo tipo di visita porta all'utile conseguenza che per un generico nodo $i$, l'algoritmo determina in sequenza i cammini di costo minimo da $r$ a $i$ con un numero crescente di archi.

Per questo si introduce il concetto di $fase$: la fase 0 corrisponde all'inizializzazione, ossia $Q=\{r\}$, mentre una generica fase $k+1$ inizia quando viene estratto da $Q$ il primo nodo inserito nella fase $k$, e termina quando viene estratto da $Q$ l'ultimo nodo inserito nella fase $k$.

Per via dell'implementazione di $Q$ come una fila, i nodi che si inseriscono durante la fase $k$ vengono estratti solo dopo quelli che erano inizialmente presenti.

Definendo quindi come $\overline{d}^k_i$ come la minima tra tutte le lunghezze dei cammini tra $r$ e $i$ con al più $k$ archi ($\overline{d}^k_i = M = +\infty$ se non esiste):

> [!danger] Teorema
> Sia $d^k[.]$ il vettore delle etichette al termine della fase $k$: allora $d^k \leq \overline{d}^k$

^a54adf
___
[[Pseudocodici algoritmi#SPT L|Algoritmo SPT L]]
___
#### Esempio esecuzione

### Dimostrazione SPT L
La dimostrazione si basa sulla caratterizzazione di $\overline{d}^k_j$ come segue:
$$
\overline{d}^{k+1}_j = min \left\{ \overline{d}^k_j, \left\{ \overline{d}^k_j + c_{ij} : (i,j) \in A \right\} \right\}
$$

La correttezza di questa caratterizzazione è abbastanza semplice, infatti il cammino minimo da $r$ a $j$ con al più $k+1$ archi o è proprio formato da al più $k$ archi oppure è composto da un arco $(i,j)$ più il cammino minimo con $k$ archi da $r$ a $i$.

> [!example]- Esempio
> Nella fase $k=0$ abbiamo che il cammino minimo da $r$ a tutti i nodi a lui direttamente collegati con al più $k+1 = 1$ archi è dato o da un cammino con 0 archi (che quindi non esiste), oppure dal cammino $(r,i)$ che è ovviamente minimo.

Per semplificare la dimostrazione è utile assumere che $M=+\infty$ infatti così facendo non avremo bisogno di controllare se un nodo sia stato visitato oppure no (se $M=+\infty$, il nodo non è stato ancora visitato).

Dimostriamo ora il teorema per induzione sulle fasi. Nella prima fase la proprietà è sicuramente soddisfatta in quando si visitano tutti i nodi raggiungibili da $r$ con un cammino di lunghezza al più 1 che quindi sono tutti i nodi direttamente collegati a $r$. Viene da sé che questi cammini sono anche minimi in quanto sono l'unico modo per arrivare a quei nodi con un solo arco.
```tikz
\usepackage{tikz-cd}

\begin{document}
\begin{tikzcd}
	& A & C\\
	r \arrow[ur, cyan] \arrow[dr, cyan]\\
	& B & D

\end{tikzcd}

\end{document}
```
Ora procediamo per induzione e assumiamo che la proprietà sia vera per la fase $k$, da questo dimostriamo quindi che è vera anche al termine della fase $k+1$.\
Indichiamo con $d^k[.]$ e $Q^k$ rispettivamente i valori delle etichette e di $Q$ al termine della fase $k$. La relazione che dobbiamo dimostrare è la seguente:
$$
d^{k+1}[\ j\ ] \leq d^k[\ i\ ] + c_{ij} \qquad \forall(i,j) \in A
$$

^b9619b

Questa relazione è una sorta di "versione approssimativa delle condizioni di Bellman" un po' più facile da soddisfare in quanto sappiamo per certo che $d^{k+1}[\ i\ ] \leq d^{k}[\ i\ ]$.

Per dimostrarla distinguiamo due casi:
1. $i \in Q^k$
2. $i \notin Q^k$ 
Partiamo dal secondo caso, ossia quando $i \notin Q^k$. Se $i$ non è in $Q^k$ allora può significare solo due cose: 
1. alla fase $k$ il nodo $i$ non è ancora mai stato visitato;
2. se $i$ è stato visitato ad un certo punto nell'esecuzione dell'algoritmo allora è uscito da $Q$ e non vi è più rientrato. 

Se $i$ non è ancora stato visitato allora avremo che $d^k[\ i\ ] = +\infty$ e quindi la proprietà è soddisfatta indipendentemente dal valore di $d^k[\ j\ ]$.\
Nel caso in cui invece $i$ sia ad un certo punto stato visitato ed è entrato e poi uscito da $Q$, allora sappiamo che per come è strutturato l'algoritmo la proprietà valeva alla sua uscita.\
Visto che $i$ non appartiene alla lista allora sappiamo anche che il valore di $d^k[i]$ non è stato modificato (perché altrimenti $i$ sarebbe in $Q$. Sappiamo inoltre dal [[SPT L#^a54adf|teorema]] che ad ogni fase i valori delle etichette possono solo diminuire o restare invariati, quindi se nella fase $k$ valeva $d^k[j] \leq d^k[i]$ allora visto che $d^k[i]$ è invariato e $d^k[j]$ è invariato o diminuito, possiamo affermare che la proprietà continua a valere.

Consideriamo invece il caso in cui $i \in Q^k$; $i$ verrà estratto da $Q$ in qualche momento durante l'esecuzione della fase $k+1$ e quindi come detto nel precedente paragrafo possiamo affermare che al termine di quell'iterazione la proprietà sarà valida per tutti gli archi uscenti da $i$; si nota infatti che valgono sia $d[j] \leq d[i]+c_{ij} \quad \forall(i,j) \in FS(i)$, con $FS(i)$ l'insieme degli archi uscenti da $i$, sia $d[i]\leq d^k[i]$ in quanto è possibile che dopo la fase $k$ l'etichetta di $i$ venga diminuita. Inoltre $d[j]$ può diminuire ulteriormente nelle iterazioni successive della fase $k+1$, quindi possiamo dire che la proprietà è soddisfatta anche per tutti gli archi $(i,j) \in FS(i) \quad \forall i \in Q^k$.

Una volta dimostrato che la [[SPT L#^b9619b|proprietà]] vale per tutti gli archi non resta che applicare l'ipotesi induttiva $d^k \leq \overline{d}^k$ dalla quale otteniamo
$$
d^{k+1}[\ j\ ] \leq min\left\{d^k[\ i\ ]+c_{ij} : (i,j) \in A \right\} \leq min \left\{\overline{d}^k_i + c_{ij} : (i,j) \in A\right\}.
$$
Inoltre, $d^{k+1}[\ j\ ] \leq d^k[\ j\ ] \leq \overline{d}^k [\ j\ ]$ perché le etichette sono non crescenti.\
Infine ancora per via dell'ipotesi induttiva possiamo concludere che:
$$
d^{k+1}[\ j\ ] \leq min \left\{ \overline{d}^k_j , \{ \overline{d}^k_i + c_{ij} : (i,j) \in A\} \right\} = \overline{d}^{k+1}_j.
$$
$$\begin{multline}\\\square\end{multline}$$
>[!note] Nota
>Una conseguenza interessante dell'algoritmo è che, interrompendolo opportunamente al momento giusto, possiamo ottenere una valutazione inferiore sulla lunghezza dei cammini minimi vincolati dal numero massimo di archi $k$
