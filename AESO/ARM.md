ARM era un'azienda che produceva calcolatori, ed era inizialmente un acronimo per Acorn RISC Machine. Successivamente poi il nome cambiò in Advanced RISC Machine.

L'architettura ARM presenta 16 registri da 32 bit che nel nostro caso sono rappresentate com un vettore di posizioni che vanno da `R0` a `R15`.
I registri di per sé sono tutti uguali ma assumono significati diversi:
- Da `R0` a `R3` sono registri temporanei usati dal programma anche per le chiamate di funzioni. In `R0` viene salvato il risultato della funzione;
- Da `R4` a `R11` sono le variabili ed i parametri del codice;
- `R12` è un registro temporaneo;
- `R13` è lo stack pointer (SP)
- `R14` è il link register che contiene l'indirizzo di ritorno della procedura (LR);
- `R15` mantiene l'indirizzo dell'istruzione (PC).
Siccome nei calcolatori ARM l'indirizzo va al byte, per leggere tutti e 32 i bit di un registro dobbiamo accedere a 4 indirizzi consecutivi di 8 bit ciascuno.
I bit vengono memorizzati secondo la logica [[Little endian]].
