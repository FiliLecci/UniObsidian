[[Latch SR]]
[[D - Latch]]
[[D - flip flop]]
[[Automi]]
[[Sincronizzatori]]
[[Memorie]]
___
Una rete sequenziale ha una serie di stati discreti $\{S_0, S_1, ..., S_{k-1}\}$.
Una rete sequenziale è definita sincrona se presenta in ingresso un clock ed i suoi elementi circuitali sono interconnessi in modo tale che:
- ogni elemento o è un registro o una rete combinatoria;
- deve essere presente almeno un registro;
- tutti i registri ricevono lo stesso segnale di clock;
- ogni percorso ciclico contiene almeno un registro.

In alcune situazioni vengono invece usate reti asincrone, utili ad esempio quando la comunicazione avviene tra due sistemi con segnali di clock differenti oppure quando riceviamo ingressi in momenti arbitrari.
___
### Ritardo delle reti sequenziali
Per far sì che il flip-flop produca un'uscita ben definita gli ingressi devono essere stabili al momento della lettura.
Il **tempo di apertura** di un elemento sequenziale viene definito in due parti:
- il **tempo di setup** $t_{setup}$ è prima del fronte del clock;
- il **tempo di hold** $t_{hold}$ è dopo il fronte del clock.
Nel momento che il clock presenta il fronte di salita, si scrivono i nuovi ingressi e di conseguenza cominciano a cambiare le uscite dopo un **ritardo di contaminazione** detto $t_{ccq}$ e si devono stabilizzare su un valore definitivo entro il ritardo di propagazione $t_{pcq}$.
Per fare si che gli ingressi vengano interpretati in modo corretto essi devono essersi stabilizzati entro il $t_{setup}$ e devono restarlo per la durata di $t_{hold}$.

Il periodo del clock è quindi dato dalla somma $t_{setup} + t_{hold} +$ i tempi di scrittura e lettura del registro in modo tale da permettere a tutti i segnali di stabilizzarsi, ponendo quindi un limite alla velocità massima del sistema. Nella realtà però c'è un altro fattore che porta a dover ulteriormente rallentare il clock e cioè che esso non raggiunge tutti i flip-flop allo stesso momento, questo ritardo è chiamato **tempo di sfasamento**.

