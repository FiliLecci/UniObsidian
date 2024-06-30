Sono arrivato in ritardo ops
# 1°
Come posso gestire i fault con due memorie cache interlacciate
Cos'è una chiamata di sistema e come viene implementata
Che cosa vedono utente e file system in un disco di memoria
# 2°
Abbiamo fatto il full adder e multiplexer. Prendendo componenti più piccoli possiamo creare componenti più grandi che però comporta problemi. Come funziona questa cosa nel full adder e multiplexer? Come posso implementare da capo un full adder a 2 bit?
Stima dei tempi di esecuzione del primo e del secondo full adder
Ci sono casi in cui un componente "creato" va sempre meglio o peggio di uno normale?
In un processore single cycle come calcoliamo il ciclo di clock?
___
Perché ci poniamo il problema di accedere alla cache di primo livello senza fare traduzione?
Semafori: come posso realizzare un meccanismo di cooperazione dove uno manda dati solo se l'altro è libero?
C'è la possibilità che uno faccia V e poi subito dopo la P? (si e si piantano entrambi)
Come funziona la gestione delle interruzioni nel SO?
# Pomeriggio
# 1°
Istruzioni condizionali in Assembly, come si implementa questa roba nel single cycle?
cos'è un processore, qual'è il suo stato architetturale
Codice da tradurre in Assembly con e senza istruzioni condizionali:
```C
if(x == 0)
	y = 3;
else
	y ++;
```

senza condizionali
```Assembly
R0 = x
R1 = y

		cmp R0, #0
		bne else
		mov R1, #3
		b end
else:
		add R1, R1, #1
end:
```
con condizionali

```
cmp R0, #0
moveq R1, #3
addne R1, R1, #1
```

cosa cambierebbe in quanto a conveniente di uno o dell'altro se usassi un pipeline?
___
Algoritmo del banchiere a cosa serve
Un esempio di di chiamata di sistema che potrebbe richiedere risorse non disponibili (richiesta di spazio di memoria)
Come si può risolvere questa situazione?
# 2°
Come si passa dal flip-flop al d-latch
nel campo di un'istruzione assembly ho 4 bit che corrispondono alle flag e 4 di COND, come si trasforma questa roba in un vero o falso? (come è fatto il controllo di condizioni)
Come funzionano le upcall
Come funziona un segnale
Algoritmo second chance
Alternativa al Second chance (che è quella che succede di solito)
# 3°
Funzione che calcola ricorsivamente il fattoriale
A cosa servono i registri sui segnali di controllo del pipeline e quelli nel datapath
Se non mettessi quelli cosa potrei fare?
Scheduler Multi Level Feedback Queue
Sempre per le Multi level... come funzionano per un sistema multi processore
RAID2 come funziona
Differenza tra fare una wait in una variabile di condizione MESA vs HOARE?
# 4°
Differenza tra processo e thread (memoria condivisa)
Tipo di system call
Che passi facciamo per accedere ad un file in una architettura FAT
Grandezza massima di un file system FAT con 2^32 entry e  4k
Differenza tra paginazione pura e segmentazione pura