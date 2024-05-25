Assembly è un linguaggio di programmazione che mette a disposizione istruzioni che vanno ad agire direttamente sulle componenti hardware.

Le istruzioni vengono direttamente convertite da Assembler in binario (linguaggio macchina) ed ogni istruzione può essere rappresentata da una parola di 32 bit.

Nel corso si considereranno programmi costruiti per processori ad architettura [[ARM]].
___
Il linguaggio Assembly si basa su istruzioni che accedono direttamente alla memoria.
Un codice Assembly dovrebbe seguire le seguenti regole:
- Regolarità, ossia che cerchiamo di dare a tutte le istruzioni la stessa struttura;
- Le istruzioni più frequenti devono essere implementate in modo tale da essere eseguite il più velocemente possibile;
- Più piccolo è più bello, ossia che ridimensionare le risorse utilizzate in modo più contenuto significa che sarà tutto più veloce;
- La bontà di un progetto dipende dalla bontà dei componenti.
## Operazioni
### Operazioni operative
Servono per fare calcoli e lavorano sempre su registri.
`ADD`, `SUB`, `AND`, `OR`, `CMP`, `LSL` (logical shift left) sono tutte istruzioni che prendono due registri e scrivono il risultato in un nuovo registro.
Le operazioni che possiamo fare possono essere o aritmetiche o logiche.
Dei 3 elementi che vengono passati agli operatori, 2 sono operandi sorgenti mentre il terzo è la destinazione.
Le due sorgenti normalmente devono essere la prima un registro e la seconda o un registro o una costante.

### Operazioni sulla memoria
Servono per operare sulla memoria:
- `LDR` (load register) prende due registri ed un offset, a partire da un registro e dall’offset calcola un indirizzo di memoria e inserisce il valore della locazione ottenuta nell’altro registro;
- `STR` (store register) prende due registri e un offset, a partire da un registro e dall’offset calcola un indirizzo di memoria e inserisce il valore che ho nell’altro registro nella locazione di memoria trovata.
Le varianti `LDRB` e `STRB` si usano per scrivere solo un byte invece dell'intera parola.

### Operazioni di salto
Possiamo assegnare a blocchi di comandi delle etichette, queste etichette possono essere poi usare per saltare alla prima istruzione del blocco con dei comandi appositi.
Permettono di spostarsi in punti diversi del programma definiti dalle etichette:
- `B etichetta`, salto direttamente all'etichetta;
- `Bl etichetta`, salta all'etichetta ma salva il valore di `pc+1` in `LR` così che la procedura possa essere ripresa dal punto del salto;
- `Eq (=), Ne (!=), Lt (<), Gt (>)`, possono essere effettuate sulle branch oppure sulle operative.
Ogni istruzione in ARM sono fatte di 4 byte (32 bit), questo significa che nel momento in cui si incontra un'istruzione di salto, il `pc` deve tornare indietro di `4*n_istruzioni` byte.
```Assembly
loop: mov r1, #1
	  mov r2, #2
	  add r3, r1, r2
	  b loop
```

## Flag
[[ARM]] prevede 4 tipi di flag rappresentati da bit (variabili booleane):
![![AESO/#^Table5]]
