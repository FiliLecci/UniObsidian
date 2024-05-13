## Moduli
Esistono due tipi di moduli in Verilog:
### Primitive
Sono essenzialmente delle tabelle di verità.
Ogni primitiva può prendere in input un qualsiasi numero di valori ma ne può restituire solamente uno.
### Module
Sono "formule" booleane
```verilog
module prova:
	...
endmodule
```
## Dichiarazioni
```verilog
wire x;        //filo da 1 bit
wire [1:0]y;   //filo da 2 bit di cui il più significativo è y[1] e il meno y[0]

reg rg;        //registro da 1 bit
reg[7:0]ra;    //registro da 1 byte (= a sopra)

integer
```
## Blocchi
Tutti i blocchi iniziano con la dicitura `begin` e terminano con `end`.
#### Initial
Viene eseguito solo una volta all'accensione del modulo.
Viene usato per fare le inizializzazioni dei componenti
```verilog
module prova:
	...
	initial:
		begin
		... //inizializzazioni
		end
	...
endmodule
```
#### Always
Corrisponde ad uno `while(true)` e viene eseguito di continuo.
Può prendere dei parametri usando la sintassi seguente
```verilog
module prova:
	...
	always @(variabili)
		begin
		...
		end
	...
endmodule
```
in questo caso la funzione viene eseguita ogni qual volta cambia il valore di uno di essi.
#### Case
È uno switch 
```verilog
case (x):
	1: y=1;
	0: y=2;
	default: y=3;
endcase
```
___
## Simboli
![![AESO/#^Table4]]
___
## Esempio
```verilog
//half adder che calcola sia il risultato che il carry
module prova;
  reg a;
  reg b;
  wire c, r;
  
  half_adder modulodatestare(r, c, a, b);
  
  initial 
    begin
		for(i=0;i<4;i=i+1)
			begin
				{a,b}=i; //in questo modo il valore di i viene messo in a e b sotto forma di valore binario
			#1	display("%b %b : ris %b, carry %b", a, b, r, c);
			end
	    $finish;
    end
endmodule

//half adder che calcola sia il risultato che il carry

//definizione di un modulo di tipo "module" per calcolare il risultato
module half_adder_ris(output ris, input a, input b);
	assign ris = ((~a)&&b)||(a&&(~b));
endmodule

//definizione di un modulo di tipo "primitive" per calcolare il carry
primitive half_adder_carry(output carry, input a, input b);
	table
		0 0 : 0;
		0 1 : 0;
		1 0 : 0;
		1 1 : 1;
	endtable
endprimitive

//definizione modulo che usa quelli precedenti per calcolare sia risultato che carry
module half_adder(output ris, output carry, input a, input b);
	half_adder_ris module1(ris, a, b);
	half_adder_carry module2(carry, a, b);
endmodule
```
