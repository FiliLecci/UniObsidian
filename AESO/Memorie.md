Un componente di memoria a livello ideale è semplicemente un componente che si ricorda dei valori.

Su una memoria si possono effettuare due operazioni:
$Write(I,x)$ e $Read(I)$, dove con $I$ e $x$ si indicano rispettivamente la locazione e il dato da scrivere.

Si può costruire una memoria di $n$ posizioni ognuna da 4 bit nel seguente modo:
- Si prendono $n$ registri ognuno da 4 bit;
- Per leggere le singole uscite dei registri usiamo un [[MUX|multiplexer]];
- Per scrivere ogni registro singolarmente usiamo un segnare di ***write-enable*** collegato ad un [[DEMUX|demultiplexer]] che va ad ogni registro.
- Il segnale da scrivere è collegato direttamente a tutti i registri in quanto verranno effettivamente scritti solo quelli il cui segnale di write-enable è 1.
___
Per quanto questa implementazione sia valida, il costo del MUX è maggiore di quello del DEMUX, quindi leggere è più oneroso che scrivere, in pratica si usa infatti una diversa rappresentazione.