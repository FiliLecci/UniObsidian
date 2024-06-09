La microarchitettura è un insieme di componenti hardware che implementano un interprete armv7 interpretando le istruzioni del linguaggio macchina ed eseguendo quello che è codificato in esse.

Il tutto è organizzato come una rete sequenziale, quello che questo livelle mete a disposizione del livello superiore è la capacità di interpretare istruzioni assembler.

La serie di operazioni che un processore è costruito per eseguire viene chiamato ***datapath***, nel nostro caso implementa il datapath **fetch-execute**:
1. fetch
2. decode
3. execute
4. wb
5. altre op
### Stato architetturale
Lo stato architetturale sono le cose che definiscono lo stato di un programma assembler.

Questo stato include un po' di cose, tra queste è molto importante un program counter che serve a dire quale sarà la prossima istruzione.

Per quanto riguarda l'architettura armv7 avremo i registri R0-R3, R4-R11, R12, R13 e R15.

Parliamo di stato architetturale in quanto prendendo una diversa architettura si avranno diversi registri con nomi e funzioni diverse, quindi un ***diverso istruction set***.

Sarà poi presente una memoria dati, dove avremo spazio per contenere i valori. Oltre a questa ci sarà una memoria nella quale tenere le istruzioni da eseguire, quasi come una ROM.

Manca infine il **cpsr** nel quale memorizzare i valori dei flag.

Altre versioni potrebbero avere registri non architetturali, dove cioè si possono scrivere dei risultati parziali ottenuti da alcune istruzioni.

## Processore single cycle
Tutti i componenti sopra citati sono realizzati con componenti che abbiamo visto fino ad ora, il *pc* è un registro (32 bit) e la stato uguale anche se basterebbero 4 bit.

Nel caso di un processore single-cycle, tutti i passi del datapath vengono eseguiti nello stesso ciclo di clock. Questo comporta varie cose tra cui la più evidente è che ogni componente può essere usato solo una volta.

Per non sacrificare quindi la velocità e rendere il componente più efficiente, possiamo usare dei multiplexer che selezionano alcuni tra i vari input.

I registri allo stesso modo fanno parte di una memoria che deve essere realizzata con la stessa tecnologia dei registri in quanto la lettura e la scrittura di diversi registri potrebbero essere necessarie nello stesso ciclo di clock.

La memoria quindi altro non è che un insieme di registri comandati da un [[DEMUX]], con un ingresso duplicato su tutti i registri per settare il *we* e uscite collegate ad un [[MUX]] che ne manda in out solo una. Sia il **MUX** che il **DEMUX** sono comandati da indirizzi.

Abbiamo poi due DEMUX che leggono, così che con 2 indirizzi diversi riusciamo a capire nello stesso ciclo di clock cosa leggere.
![[registerFile.png|300]]
![[registerFileInternal.png|500]]

Un esempio di componente completo è il seguente

![[singleCycleProcessor.png]]
### Processore multi cycle
L'idea del processore multi cycle è quella di usare i cicli di clock in modo differente.
Ad esempio usiamo il primo ciclo di clock per fare la fetch, il secondo per fare la decode, un altro per l'esecuzione e uno per il wb.

 