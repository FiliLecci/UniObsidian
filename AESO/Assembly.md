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

```assembly
loop: mov r1, #1
	  mov r2, #2
	  add r3, r1, r2
	  b loop
```

## Flag
[[ARM]] prevede 4 tipi di flag rappresentati da bit (variabili booleane):
![![AESO/#^Table5]]

### Compilazione
I programmi assembly hanno estensione .s e possono essere compilati con `gcc`.
Siccome non si dispone sempre di processori con architettura arm si usano toolchain specifici per compilare ed eseguire come se lo fossero.
Script che non ho capito se funziona per compilare:
```shell
#
echo "Compiling $*" arm-linux-gnueabihf-gcc -static -ggdb3 $* qemu-arm -g 34788 a.out & gdb-multiarch -q --nh -ex 'set architecture arm' -ex 'file a.out' -ex 'target remote localhost:34788'
```
### Direttive
Le direttive non sono istruzioni asembler ma bensì sono per il compilatore.
![![AESO/#^Table6]]
### Stack
Sulla stack si opera usando le pseudo-istruzioni `push` e `pop`.

Queste operazioni sono compilate usando `ldrm` e `strm` dove la `m` sta per `mul`.

L'operazione `push` permette di prendere uno o più registri e salvarli sullo stack.

L'operazione `pop` al contrario serve per mettere i valori contenuti nello stack dentro uno o più registri.

Sia la `push` che la `pop` seguono l'ordine LIFO.

Per lavorare su uno stack abbiamo bisogno di un riferimento che può essere o alla prima cella vuota o alla prima cella piena.

Possiamo passare registri indicandoli per nome, per range o per nome simbolico:
```assembly
push{r1, r2, r4-r8, lr} 
```

Per riuscire a mettere tutta l'istruzione in 32 bit si usa una bitmap, cioè 16 bit in cui il bit i-esimo = 1 significa che prendiamo l'i-esimo registro, altrimenti è 0.

>[!example] Esempio
>Possiamo scrivere un codice per calcolare il fattoriale nel seguente modo:
>$Fact(1) \rightarrow 1$
>$Fact(n) \rightarrow n*Fact(n-1)$
>Il codice assembly sarebbe come segue:
>```assembly
>fact: 
>	cmp r0, #1 //caso base
>	moveq pc, lr //se siamo nel caso base ritorniamo
>	push{r0, lr} //altrimenti salvo n e l'indirizzo di ritorno
>	sub r0, r0, #1 //calcolo n-1
>	bl fact //faccio la chiamata ricorsiva 
>	pop{r1, lr} //stiamo srotolando lo stack dei record di attivazione
>	mul r0, r0, r1 //calcoliamo man a mano i risultati
>	mov pc, lr //ritorniamo
>```

### Parametri da linea di comando
In C ci sono due parametri che vengono passati al programma, `argc` e `argv`. Questi parametri occupano rispettivamente `R0` e `R1`; in `R0` è contenuto il numero di elementi n, in `R1` invece è contenuto l'indirizzo dell'area di memoria che contiene il primo parametro.

Scriviamo un programma che calcola la funzione di Fibonacci che accetta un parametro da riga di comando:
>[!example] Esempio
>```assembly
>    .text
>    .global main
>    .data
>    stringa: .str "Fibo(%d) = %d\n"
>main: 
>		push{lr} //salvo l'indirizzo di ritorno
>		ldr r0, [r1, #4] //carico l'argomento 
>		bl atoi //casto l'argomento a intero 
>		push{r0} //salvo il valore iniziale 
>		bl Fibo //faccio la chiamata alla funzione 
>		mov r2, r0 //sposto il valore calcolato in r2 
>		pop{r1} //scarico il valore iniziale in r1 
>		ldr r0, =stringa //in r0 carico la stringa formattata 
>		bl printf //chiamo la printf 
>		pop{pc} //ritorno 
>Fibo: 
>		cmp r0, #1 //se siamo al caso base 
>		movle pc, lr //restituisco direttamente r0 
>		push{lr} //salvo l'indirizzo di ritorno 
>		sub r0, r0, #1 //calcolo n-1 
>		push{r0} //salvo n-1 
>		bl Fibo //calcolo fib(n-1) 
>		pop{r1} //recupero l'ultimo n-1 
>		push{r0} //salvo fib(n-1) 
>		sub r0, r1, #1 //calcolo n-2 
>		bl Fibo //calcolo fib(n-2) 
>		pop{r1} //recupero fib(n-1) 
>		add r0, r0, r1 //calcolo fib(n-2)+fib(n-1) 
>		pop{pc} //ritorno al chiamante
>```

	