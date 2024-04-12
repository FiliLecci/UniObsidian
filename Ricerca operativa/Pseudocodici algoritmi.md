### Edmonds & Karp

**Complessità: $O(E^2v)$** con [[Edmonds & Karp 2.4.2#Dimostrazione complessità $O(m 2n)$|Dimostrazione]]

```
pseudocodice algoritmo
```
___
### SPT L

**Complessità: $O()$**

**Varibili**
$r$ : radice;\
$Q$ : lista che contiene i nodi i cui archi uscenti potrebbero violare le condizioni di Bellman. Essendo una lista possiamo effettuare operazioni di rimozione e inserimento in testa o in coda.\
Le liste possono essere dei seguenti tipi:
- $fila$, usa il metodo FIFO;
- $coda$, usa il metodo LIFO;
- $dequeue$, inserimento sia in testa che in coda ma rimozione solo in testa;

$p[.]$ : vettore di predecessori;\
$d[.]$ : vettore di etichette dove $d[i]$ rappresenta un'approssimazione superiore del costo dell'unico cammino da $r$ a $i$;\
$M$ : costo fittizio molto elevato che viene dato inizialmente a tutti gli archi di $d[.]$.
___
```
Algoritmo da fare
```
___

### Simplesso primale

