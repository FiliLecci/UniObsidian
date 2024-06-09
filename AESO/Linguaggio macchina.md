La macchina comprende istruzioni formate da 32 bit.
Esistono 3 formati diversi, ognuno rispettivamente per le istruzioni operative, load e store, salti.
Nonostante questo hanno tutte in comune due campi: il primo è da 4 bit ed è il campo **cond**, il secondo da 2 bit e si chiama **op**.

Il campo **op** assume il valore $00$ se l'operazione è una operativa, $01$ se sono ldr o str, e $10$ se è un'operazione di salto. Il valore $11$ è riservato per altri usi.

