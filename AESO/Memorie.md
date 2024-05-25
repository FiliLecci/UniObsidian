Un componente di memoria a livello ideale è semplicemente un componente che si ricorda dei valori.

Su una memoria si possono effettuare due operazioni:
$Write(I,x)$ e $Read(I)$, dove con $I$ e $x$ si indicano rispettivamente la locazione e il dato da scrivere.

Si può costruire una memoria di $n$ posizioni ognuna da 4 bit nel seguente modo:
- Si prendono $n$ registri ognuno da 4 bit;
- Per leggere le singole uscite dei registri usiamo un [[MUX|multiplexer]];
- Per scrivere ogni registro singolarmente usiamo un segnare di ***write-enable*** collegato ad un [[DEMUX|demultiplexer]] che va ad ogni registro.
- Il segnale da scrivere è collegato direttamente a tutti i registri in quanto verranno effettivamente scritti solo quelli il cui segnale di write-enable è 1.
___
Per quanto questa implementazione sia valida, il costo del MUX è maggiore di quello del DEMUX, quindi leggere è più oneroso che scrivere, in pratica si usa infatti la seguente rappresentazione:
- Un ingresso che rappresenta un indirizzo;
- Un DEMUX;
- Una griglia (wordLine e bitLine).
In questo modo abbiamo una memoria organizzata come una matrice bidimensionale di celle di memoria. Ad ogni accesso la memoria può leggere o scrivere il contenuto di una riga, specificata da un indirizzo (address). Il valore letto o scritto si chiama dato (data). Un componente con un numero $N$ di bit di indirizzo e un numero $M$ di bit di dato possiede quindi $2^N$ parole da $M$ bit ciascuna.

In questo modo sono fatte le [[RAM e ROM|RAM]] (Random Access Memory).
___
## Memorie modulari
Le memorie modulati possono essere estese in modo tale da essere usate come un'unica memoria.
Ci sono due metodi per interlacciare due moduli, supponiamo di avere $m\in\{1,2,...\}$ moduli di capacità $C$ bit:
- Modo sequenziale:  gli indirizzi dei moduli sono sequenziali e quindi hanno i seguenti intervalli: da $0$ a $n-1$, da $n$ a $2n-1$, ..., da $(m-1)n$ a $mn-1$.
  Per collocare una parola ad un indirizzo ($ind$) dobbiamo prima ottenere l'indice del modulo ($id$)
  $$
  id = \frac{ind}{C}
  $$
  e successivamente collocare la parola nel modulo $id$ all'indirizzo
  $$ind_{modulo} = id\ \%\ C$$
- Modo interlacciato: gli indirizzo sono interlacciati e quindi in fila.
  Vengono indirizzati come
  $$id = ind\ \%\ m$$
  e si salva la parola all'indirizzo 
  $$ind_{modulo} = \frac{ind}{m}$$
La differenza tra le due modalità è che nel modo interlacciato posso leggere 2 parole consecutive in un unico ciclo di clock in quanto sono sempre su moduli differenti, mentre nel modo sequenziale ho bisogno di due accessi (e quindi due cicli di clock) allo stesso modulo.
___
## Memorie associative
Nelle memorie associative non abbiamo delle parole memorizzate a determinati indirizzi, ma bensì si usano due moduli di memoria, uno contiene le chiavi $k_i$ ed uno i valori $v_i$ associati ad esse.

Per scrivere in una memoria associativa dobbiamo prima di tutto verificare che la chiave $k$ che cerchiamo esista $k = k_i$, successivamente scrivere il valore $v$ nella cella corrispondente $v_i$.

Dal punto di vista logico questi controlli vengono fatti con tanti comparatori ai quali si passa la chiave cercata. I comparatori sono poi collegati alle celle del modulo di memoria e restituiscono 0 o 1 in base a se la chiave corrisponde o no. Le uscite dei comparatori sono messe tutte in OR che quindi confermerà o meno l'esistenza della chiave.

Per ottenere li valore cercato si collega prima dell'OR un codificatore collegato al modulo dei valori che quindi restituirà il valore cercato.

$$
Leggi(key) \rightarrow v
$$$$
Scrivi(key, v) \rightarrow sse\ \exists k_i=key \Rightarrow v_i = v
$$
