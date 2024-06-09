La macchina comprende istruzioni formate da 32 bit.
Esistono 3 formati diversi, ognuno rispettivamente per le istruzioni operative, load e store, salti.
Nonostante questo hanno tutte in comune due campi: il primo è da 4 bit ed è il campo **cond**, il secondo da 2 bit e si chiama **op**.

Il campo **op** assume il valore $00$ se l'operazione è una operativa, $01$ se sono ldr o str, e $10$ se è un'operazione di salto. Il valore $11$ è riservato per altri usi.

### Istruzioni operative
Le istruzioni operative hanno i seguenti campi:
- **cmd (4 bit)**: indica il tipo di operazione;
- **I** ed **S** (2 bit): rispettivamente indicano: se il terzo operando è un immediato o no, se è una opS oppure no S=1 imposta i flag;

Il **cpsr** (4 bit) è un registro speciale che serve a memorizzare i flag. Viene anche chiamato "registro di stato";
